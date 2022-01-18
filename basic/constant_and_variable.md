# Constants and Variables

## What is constants and variables
Constants and variables must be declared before they’re used. You declare constants with the let keyword and variables with the var keyword.

"let" is constant compile time such as "const" in Dart.

```swift
let maximumNumberOfLoginAttempts = 10
var currentLoginAttempt = 0
//https://docs.swift.org/swift-book/LanguageGuide/TheBasics.html
```

You can declare multiple constants or multiple variables on a single line, separated by commas:

```swift
var x = 0.0, y = 0.0, z = 0.0
```

and "How to use" ...

## Type Annotations

Write a type annotation by placing a colon after the constant or variable name, followed by a space, followed by the name of the type to use.

```swift
var welcomeMessage: String
```

You can define multiple related variables of the same type on a single line, separated by commas, with a single type annotation after the final variable name:

```swift
var red, green, blue: Double
```
## Naming Constants and Variables

Constant and variable names can contain almost any character, including Unicode characters:

```swift
let π = 3.14159
let 你好 = "你好世界"
let 🐶🐮 = "dogcow"
```
Constant and variable names can’t contain whitespace characters, mathematical symbols, arrows, private-use Unicode scalar values, or line- and box-drawing characters. Nor can they begin with a number, although numbers may be included elsewhere within the name.

**If you need to give a constant or variable the same name as a reserved Swift keyword, surround the keyword with backticks (`) when using it as a name. However, avoid using keywords as names unless you have absolutely no choice.**

```swift
print("The current value of friendlyWelcome is \(friendlyWelcome)")
```
## Comments

Comments in Swift are very similar to comments in C. Single-line comments begin with two forward-slashes (//). Multiline comments start with a forward-slash followed by an asterisk (/* ) and end with an asterisk followed by a forward-slash (*/)::

```swift
// This is a comment.
/* This is
a comment. */
```
## Semicolons

Unlike many other languages, Swift doesn’t require you to write a semicolon (;) after each statement in your code, although you can do so if you wish. However, semicolons are required if you want to write multiple separate statements on a single line

## Integers

Swift provides signed and unsigned integers in 8, 16, 32, and 64 bit forms. These integers follow a naming convention similar to C
- On a 32-bit platform, Int is the same size as Int32.
- On a 64-bit platform, Int is the same size as Int64.

## Floating-Point Numbers

Swift provides two signed floating-point number types:
- Double represents a 64-bit floating-point number.
- Float represents a 32-bit floating-point number.

## Type Safety and Type Inference
Swift is a type-safe language. A type safe language encourages you to be clear about the types of values your code can work with. If part of your code requires a String, you can’t pass it an Int by mistake.

Integer literals can be written as:

- A decimal number, with no prefix
- A binary number, with a 0b prefix
- An octal number, with a 0o prefix
- A hexadecimal number, with a 0x prefix

```swift
let cannotBeNegative: UInt8 = -1
// UInt8 can't store negative numbers, and so this will report an error
let tooBig: Int8 = Int8.max + 1
// Int8 can't store a number larger than its maximum value,
// and so this will also report an error
```
## Change run time type
You can change run time type of variable by < TYPE >(variable)
```swift
let integerPi = Int(pi)
// integerPi equals 3, and is inferred to be of type Int
```

## Type Aliases
Type aliases define an alternative name for an existing type. You define type aliases with the typealias keyword.

```swift
typealias AudioSample = UInt16
var maxAmplitudeFound = AudioSample.min
// maxAmplitudeFound is now 0
```
## Booleans
```swift
let orangesAreOrange = true
let turnipsAreDelicious = false
let isTrue: Bool = 1
let isFalse: Bool = 0
```

## Tuples
Tuples group multiple values into a single compound value. The values within a tuple can be of any type and don’t have to be of the same type as each other.
```swift
let http404Error = (404, "Not Found")
// http404Error is of type (Int, String), and equals (404, "Not Found")
```
You can decompose a tuple’s contents into separate constants or variables, which you then access as usual:

```swift
let (statusCode, statusMessage) = http404Error
print("The status code is \(statusCode)")
// Prints "The status code is 404"
print("The status message is \(statusMessage)")
// Prints "The status message is Not Found"
let (justTheStatusCode, _) = http404Error
print("The status code is \(justTheStatusCode)")
// Prints "The status code is 404"
print("The status code is \(http404Error.0)")
// Prints "The status code is 404"
print("The status message is \(http404Error.1)")
// Prints "The status message is Not Found"
let http200Status = (statusCode: 200, description: "OK")
```
## nil
This is "null" in Dart

You set an optional variable to a valueless state by assigning it the special value nil:

```swift
var serverResponseCode: Int? = 404
// serverResponseCode contains an actual Int value of 404
serverResponseCode = nil
// serverResponseCode now contains no value
```
## Error Handling

When a function encounters an error condition, it throws an error. That function’s caller can then catch the error and respond appropriately.

```swift
func canThrowAnError() throws {
    // this function may or may not throw an error
}
```
Swift automatically propagates errors out of their current scope until they’re handled by a catch clause.

```swift
do {
    try canThrowAnError()
    // no error was thrown
} catch {
    // an error was thrown
}
```
Here’s an example of how error handling can be used to respond to different error conditions:

```swift
func makeASandwich() throws {
    // ...
}

do {
    try makeASandwich()
    eatASandwich()
} catch SandwichError.outOfCleanDishes {
    washDishes()
} catch SandwichError.missingIngredients(let ingredients) {
    buyGroceries(ingredients)
}
```
You write an assertion by calling the **assert**(_:_:file:line:) function from the Swift standard library. You pass this function an expression that evaluates to true or false and a message to display if the result of the condition is false.

```swift
let age = -3
assert(age >= 0, "A person's age can't be less than zero.")
// This assertion fails because -3 isn't >= 0.
```

If the code already checks the condition, you use the **assertionFailure**(_:file:line:) function to indicate that an assertion has failed. For example:

```swift
if age > 10 {
    print("You can ride the roller-coaster or the ferris wheel.")
} else if age >= 0 {
    print("You can ride the ferris wheel.")
} else {
    assertionFailure("A person's age can't be less than zero.")
}
```
Use a **precondition** whenever a condition has the potential to be false, but must definitely be true for your code to continue execution

```swift
// In the implementation of a subscript...
precondition(index > 0, "Index must be greater than zero.")
```