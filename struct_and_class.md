# Struct and Class

## What are Struct and Class
Structures and classes are general-purpose

In Swift, you define a structure or class in a single file, and the external interface to that class or structure is automatically made available for other code to use.

## Comparing Structures and Classes
Structures and classes in Swift have many things in common. Both can:

- Define properties to store values
- Define methods to provide functionality
- Define subscripts to provide access to their values using subscript syntax
- Define initializers to set up their initial state
- Be extended to expand their functionality beyond a default implementation
- Conform to protocols to provide standard functionality of a certain kind

**Classes have additional capabilities that structures don’t have:**
- Inheritance enables one class to inherit the characteristics of another.
- Type casting enables you to check and interpret the type of a class instance at runtime.
- Deinitializers enable an instance of a class to free up any resources it has assigned.
- Reference counting allows more than one reference to a class instance.

## Definition Syntax

```swift
struct SomeStructure {
    // structure definition goes here
}
class SomeClass {
    // class definition goes here
}

struct Resolution {
    var width = 0
    var height = 0
}
class VideoMode {
    var resolution = Resolution()
    var interlaced = false
    var frameRate = 0.0
    var name: String?
}
```
## Structure and Class Instances
```swift
let someResolution = Resolution()
let someVideoMode = VideoMode()
```
## Accessing Properties
You can access the properties of an instance using dot syntax. In dot syntax, you write the property name immediately after the instance name, separated by a period (.), without any spaces:

```swift
print("The width of someResolution is \(someResolution.width)")
// Prints "The width of someResolution is 0"
```

## Memberwise Initializers for Structure Types
All structures have an automatically generated memberwise initializer
```swift
let vga = Resolution(width: 640, height: 480)
```
## Structures and Enumerations Are Value Types
A value type is a type whose value is copied when it’s assigned to a variable or constant, or when it’s passed to a function.
```swift
let hd = Resolution(width: 1920, height: 1080)
var cinema = hd
```

![copy of Struct](/images/sharedStateStruct_2x.png) 

The same behavior applies to enumerations:
```swift
enum CompassPoint {
    case north, south, east, west
    mutating func turnNorth() {
        self = .north
    }
}
var currentDirection = CompassPoint.west
let rememberedDirection = currentDirection
currentDirection.turnNorth()

print("The current direction is \(currentDirection)")
print("The remembered direction is \(rememberedDirection)")
// Prints "The current direction is north"
// Prints "The remembered direction is west"
```
## Classes Are Reference Types
Unlike value types, reference types are not copied when they’re assigned to a variable or constant, or when they’re passed to a function. Rather than a copy, a reference to the same existing instance is used.


![copy of Struct](/images/sharedStateClass_2x.png) 