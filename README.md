# IOS Best Practices
[![Generic badge](https://img.shields.io/badge/Version-1.0-<COLOR>.svg)](https://www.figma.com/file/06ttgSCYrRxiWO1xbjeEYq/Z?node-id=0%3A1)
Project Description here
## Required Tools

- MacOS 11.2.1 or Later
- [Xcode](https://apps.apple.com/in/app/xcode/id497799835?mt=12) 12.4 or later
- [Cocoapods](https://guides.cocoapods.org/using/getting-started.html)
- iPhone or iOS Simulator running iOS version 11.0+

## Development environment

- Software desgin pattern : MVVM
- Deployment Platform: iPhone
- Minimum Deployment Version: iOS 11.0
- Device Orientation: Potrait
- Programming Language: Swift 5
- Life Cycle: UIKit App Delegate
- Supported Devices: iPhone 5S and later
- Source Control tool : [Gitlab](https://gitlab.com)

##### Why MVVM?
- MVVM makes the view controller simpler by moving a lot of business logic out of it.
- The view model better expresses the business logic for the view.
-  A view model is much easier to test than a view controller. You end up testing business logic without having to worry about view implementations.

 # Naming Conventions
We are following the below-naming conventions to achieve Readability, Clarity, Consistency in code.
#### Application Namespace:

Use a prefix that identifies the application (example: TP for an app called Test Project). Use this prefix when naming classes, functions, constants and typedef structures wherever needed.

#### Class Names:

**App prefix** + **PascalCase** Description 

- Start class names with the app prefix
- Class names should be as descriptive as possible, avoid shorthand and abbreviations
- If subclassing, make it obvious by using the superclasses name in the new name

| TSTableVC | ❌ |
| :---: | :---: |
| TSTableViewController | ✅ |

#### Identifiers

**Lower-case identifier** + **PascalCase description**

The lower-case identifier prefixes are designed to provide information, or metadata, about the variable. This helps with debugging and general readability by removing any ambiguity about the origin of the variable or the intended use of the variable.

**Local Identifiers**
Starts With 'a' or 'an'

    let aPostItems : [String] = [
         "Item 1",
         "Item 2"
    ]
        
    let anItem : String = "Item"
        

**Local Private Members**
Starts with "__" and is followed by PascalCase Description

     let __MyPosts : [String] = [
        "Item 1",
        "Item 2"
    ]
        
**Global/Local Constant Members**
CAPITAL + Snake_Case Description

    public static let MY_APP_NAME: String = "Project-Z"
       
**Global Members**
Starts with "g" and is followed by PascalCase Description

    let gNumberOfRetries : Int = 10
    
#### Protocols and Delegate

**Protocols**

- Protocol Names must start with Class Names and follow by the word "Delegate"
- Protocol function must be the same as the Class name and must have the class's instance as an argument.
- Second argument of a Protocol function must describe the function with camelCase.
- Should use the form "Did", "Will" and "Should".


     protocol TSTableViewControllerDelegate{
        func TSTableViewController(_ TableViewController : TSTableViewController, delegate didCalled : Bool)
    }
    
**Delegate**
A delegate must be in a smaller case and with weak keyword to avoid strong reference cycles. by default should be nil.

    weak var delegate : TSTableViewControllerDelegate? = nil
    
    
#### Enums
Enums must have either class prefix or App Name prefix based on their access scope and its cases must be followed by the Underscore(_) and PascalCase description.

    enum TSUserState{
        case TSUserState_Authorised
        case TSUserState_UnAuthorised
    }

#### Methods and Functions
Method names start with a lower case letter followed by camel casing:

    func loginUser(_ email : String,_ password : String){}
    
**Private Method** Naming must be starts with Single "_" ad followed by camelCase description:

    func _getMyDetails(_ byId : Int){}
    
#### Blocks
A completion block handler must have to be in camelCase and ends with "CompletionBlock".

    var userLoginCompletionBlock : ((_ loginStatus : Bool) -> (Void)) = { _ in }
    
A completion block may or may not have the arguments. if it has the arguments it must have the label to indicate its purpose

#### Notificaiton names:
Notification names should follow camelCase and use the form "Did", "Will" and "Should".
**Example** : dataDidChanged, userWillLogout, shouldGetUser

# Whitespace

 To maintain a high-quality and consistent code base, everyone is required to follow the formatting guidelines and giving proper whitespace is also an important part of it.
 
 #### Identifiers

| let a: Int = 10 | ❌ |
| :---: | :---: |
| let a : Int =10 | ❌ |
| let a : Int = 10 | ✅ | 

 #### if/else/for/while

    if aUserCount == 0{
        // do something
    }else{
        // do something else
    }
    
    for aPostItem in aPostItems{
        // do something with aPostItem
    }
  
 #### Methods
 ```swift
func getPosts(_ page : Int){
    // do something
}
```

# Code Documenting
- Each Identifier, enum, class, completion block, protocol, extension and some logical expression must have a single or multiline comment in such a manner as to easily describe (in English) the purpose of the code used to accomplish the purpose.
- A function, method or extension must have a multiline comment describing its purpose, arguments and returning value.

#### Single Line Comment
```swift
// create a variable 
var aName = "Cartman"
// print the value
print(name)
```
#### Multiline Line Comment
```swift
/*  
    create a variable
    to store salary of employees
    var aSalary = 10000
    print(aSalary)
*/
```
#### Documentation Comments
```swift
/**
This Function will do sum of two-argument
- Any Other Explanation to be added by bullet points
- parameter aFirstArgument : first value want to sum with the second value
- parameter aSecondArgument : second value want to sum with the first value
- parameter parameterName: give parameter name here to describe each parameter
- returns: integer value which will be the sum of the aFirstArgument and aSecondArgument
*/
func sumTwoIdentifiers(_ aFirstArgument : Int, aSecondArgument : Int) -> Int{
    return aFirstArgument + aSecondArgument
}
```    
# Libraries and Frameworks

Third Party Package Manager : [Cocoapods](https://guides.cocoapods.org/using/getting-started.html)
Cocoapods is a dependency manager which is used to include third-party libraries in iOS projects. All the libraries that are needed to be included in the project are added in a Podfile and then we simply run a pod command on the terminal to install the added dependencies in the podfile. When installing, the libraries are downloaded and linked to an Xcode workspace which then onwards is used to move further with the project.

##### List of libraries:
 - [SDWebImage](https://github.com/SDWebImage/SDWebImage) : This library provides an async image downloader with cache support.
 - [PhoneNumberKit](https://github.com/marmelroy/PhoneNumberKit) : framework for parsing, formatting and validating phone numbers.
 
# Directory Structure
We have a predefined directory structure being used for each module development to keep the source tree more efficient and easy to navigate.


```
Project-Z
│   README.md
│   Project-Z.xcodeproj    
│   Project-Z.xcworkspace    
│   Podfile # Pod file containing the frameworks and Libraries
└─── Utilities # Store Utility swhich can only be used in this project.
└─── Extensions # Store extensions which can be user even outside of project 
└─── Resources # Outside of project resources such as mp3 or video files.
└─── Scenes #Include files Containing Main Logic of the App
│   │
│   └─── SceneName / ModuleName
│           │   └─── SceneName / ModuleName
|           |   |  └─── Model 
|           |   |       | SModelNameModel.swift
|           |   |  └─── View 
|           |   |       | SModelNameModel.storyboard
|           |   |       | └─── XIBs
|           |   |       |    | SNibName.xib
|           |   |  └─── ViewModel 
|           |   |       | SViewModelNameViewModel.swift
└─── Helpers # All files  which can be used without any dependancy on the project.
└─── Stores # Local Database related files
└─── Project-ZTests #  Test Cases
└─── Project-ZUITests # UI-Test Cases
└─── Pods # All 3rd Party Frame work and libraries 
```
##### Scenes

All Scenes taking place in app has to have Main Directory with a descriptive name. This directory must have 3 sub-directories Model, View and ViewModel.

**Model**
This folder will contain all the files with app data that the app operates on. Mostly structs and codables.

**View**
This folder will contain all user interface's visual elements and View Controller file. Mostly storyboard and xib files and thier controller class.

**ViewModel**
 Files in this folderIt receives information from VC, handles all this information, and sends it back to VC.
 
 **Example** :
 
 ```
 │   │
│   └───  Scene
│       └─── Employee  Manager
|       |   └─── Model 
|       |   |      | Employee.swift
|       |   └─── View 
|       |   |   | Employee.storyboard
|       |   |   | EmployeeViewController.storyboard
|       |   |   | └─── XIBs
|       |   |   |  | EmployeeSkill.xib
|       |   └─── ViewModel 
|       |   |       | EmployeeViewModel.swift
 ```
 
 # Coding Conventions
 We follow and recommend below conventions to give a uniform appearance to the codes written by different engineers. It improves readability, and maintainability of the code and it reduces complexity also. It also helps in code reuse and helps to detect error easily.
 
 ##### Identfier Usage Conventions
 
 - Prefer ``let`` bindings over ``var``bindings wherever possible. Only use var if you absolutely have to (i.e. you know that the value might change, e.g. when using the weak storage modifier)
 
##### Return or Break Concentions
When you have to meet certain criteria to continue execution, try to exit early. So, instead of this:
 ```swift
 if n.isNumber {
    // Use n here
} else {
    return
}
```
use this:
```swift
guard n.isNumber else {
    return
}
// Use n here
```
You can also do it with if statement, but using guard is preferred, because guard statement without return, break or continue produces a compile-time error, so exit is guaranteed.
##### Value Un-Wraping Conventions
**Avoid Using Force-Unwrapping of Optionals.** 
If you have an identifier foo of type FooType? or FooType!, don't force-unwrap it to get to the underlying value (foo!) if possible.
Instead, prefer this:
```swift
if let foo = foo {
    // Use unwrapped `foo` value in here
} else {
    // If appropriate, handle the case where the optional is nil
}
```
Alternatively, you might want to use Swift's Optional Chaining in some of these cases, such as:
```swift
print(foo ?? derfaultValue)
```
**Avoid Using Implicitly Unwrapped Optionals**
