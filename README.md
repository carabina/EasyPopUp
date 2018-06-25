<p align="center">
	<img src="https://github.com/mohammadZ74/EasyPopUp/blob/master/EasyPopUp/Assets/1.png" width="500">
</p>
<p align="center">
    <img src="https://img.shields.io/badge/Swift-4.1-green.svg" />
        <img src="https://img.shields.io/badge/platform-ios-green.svg" />
    <a href="https://opensource.org/licenses/MIT">
      <img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License" />
    </a>
</p>
<p>&nbsp;</p>

# Introduction

With EasyPopup you can easily convert your views/UViewController's to Popups.

<p>&nbsp;</p>

# Installation

EasyPopUp is available through [CocoaPods](http://cocoapods.org). Simply add the following to your Podfile:

```ruby
use_frameworks!

target '<Your Target Name>'
pod 'EasyPopUp'
```

# Demo
You can easily find and run the demo app in example folder.

# Usage
EasyPopup divided to two classes one for views and the other for ViewControllers.
## View Usage

for view usage you should just pass your superView of your view and your view that you want to be your popup.
you can give your custom config file ( will explain deep down below ) for custom transtions,shadows,corners,... .

```swift
public init(superView: UIView, viewTopop view: UIView, config: EasyPopupConfig = default)
// example
let popupView = EasyPopup(superView: self.view, viewTopop: viewToPop)
```

then you can show your popup with:

```swift
public func Showpopup(completion: ((Bool) -> Void)? = nil)
// example 
popupView.showPopup { (isfinished) in
          // do after showing popup 
}
```
you can just show your popup or with completion handler do anything after popup animation is finished.

and for dismissing popup :

```swift
public func removePopup(completion: ((Bool) -> Void)? = nil)
// example 
popupView.removePopup { (isfinished) in
          // do after dismissing popup 
}
```
## ViewController Usage
for viewController usage your view controller must conform to `EasyPopUpViewControllerDatasource`
you should pass your view ( which is in your view controller ) that you want to popup.
note that your view should have constraints in your view controller.
```swift
public init(sourceViewController: UIViewController, destinationViewController: UIViewController, config: EasyPopupConfig = default)
}
```
`sourceViewController` : the source viewController that you want to appear popup on.
`destinationViewController` : the popup viewController that you want to show.
`config` : the EasyPopup config file for giving custom shadow,transitions,cornerRadius,... .

Usage Example:

in your popup viewController class: 

```swift
class popViewController: UIViewController {
    @IBOutlet weak var popupContentView: UIView!
}
extension popViewController : EasyPopUpViewControllerDatasource {
    var popupView: UIView {
        return popupContentView
    }
}
```
and in your source viewController:
```swift
let popupVC = self.storyboard?.instantiateViewController(withIdentifier: "popViewController") as! popViewController
let easePopUp = EasyViewControllerPopup(sourceViewController: self, destinationViewController: popupVC )
```
for showing popup use the `showVCAsPopup` method
```swift
easePopUp.showVCAsPopup()
```
for dismissing simply dismiss the viewController. don't worry easypopup ovverride the default transition.

If the usage guide wasn't useful,please run and look the example project.It will boost you 😇

# Customization

Easypopup uses configuration for custom transitions,Blurs,cornerRadius and shadows.


# License

PopupDialog is available under the MIT license. See the LICENSE file for more info.
