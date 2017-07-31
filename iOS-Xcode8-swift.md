# iOS, Xcode 8, & Swift

This markdown was created as a quickstart and reference guide to getting up and productive with iOS, Xcode, and Swift.


## Playground

The playground when run is code that is being stored on the memory on the computer. 

`Import UIKit` allows us to use the features of iOS. It also includes Swift.



### ViewController

When you add a Button or another object to the interface, you also need to add it to the code.

- Click the `ViewController.swift` and click the "Assistant Editor" button that looks like 2 circles. 
- Hold `control` and click the object to drag it into the `ViewController` code.

Problem - Changing the name of an IBOutlet object after you've moved it to the code, you receive an app crash error.
- Go to your Main storyboard from the far left menu > right-click the ViewController in the submenu > and look for any yellow triangle warnings.


## Functions

````Swift
//: func NAME(parameter: Type, parameter2: Type2) ->(RETURN) Type { }
func calculateArea(length: Int, width: Int) -> Int {
    let area = length * width
    return area
}
````