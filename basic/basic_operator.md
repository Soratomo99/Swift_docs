# Basic Operators

## What is Basic Operators
An operator is a special symbol or phrase that you use to check, change, or combine values.

```swift
let i = 1 + 2
if enteredDoorCode && passedRetinaScan
```
Swift also provides range operators that aren’t found in C, such as **a..<b** and **a...b**, as a shortcut for expressing a range of values.

## Unary Minus Operator
The sign of a numeric value can be toggled using a prefixed -, known as the unary minus operator:

```swift
let three = 3
let minusThree = -three       // minusThree equals -3
let plusThree = -minusThree   // plusThree equals 3, or "minus minus three"
```
## Unary Plus Operator
The unary plus operator (+) simply returns the value it operates on, without any change:
```swift
let minusSix = -6
let alsoMinusSix = +minusSix  // alsoMinusSix equals -6
```
## Nil-Coalescing Operator
The nil-coalescing operator is shorthand for the code below:
```swift
a != nil ? a! : b
var colorNameToUse = userDefinedColorName ?? defaultColorName
```
## Range Operators
Swift includes several range operators, which are shortcuts for expressing a range of values.
### Closed Range Operator
The closed range operator is useful when iterating over a range in which you want all of the values to be used
```swift
for index in 1...5 {
    print("\(index) times 5 is \(index * 5)")
}
```
### Half-Open Range Operator
Half-open ranges are particularly useful when you work with zero-based lists such as arrays, where it’s useful to count up to (but not including) the length of the list:
```swift
let names = ["Anna", "Alex", "Brian", "Jack"]
let count = names.count
for i in 0..<count {
    print("Person \(i + 1) is called \(names[i])")
}
// Person 1 is called Anna
// Person 2 is called Alex
// Person 3 is called Brian
// Person 4 is called Jack
```
### One-Sided Ranges
The closed range operator has an alternative form for ranges that continue as far as possible in one direction
```swift
for name in names[2...] {
    print(name)
}
// Brian
// Jack

for name in names[...2] {
    print(name)
}
// Anna
// Alex
// Brian

for name in names[..<2] {
    print(name)
}
// Anna
// Alex
```