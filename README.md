# Swift book

The proposal of this repository is to create a document that contains a resume of all features in Swift. Besides that, to show examples of code with snippets.

- [Proposal](#proposal)
- [The Basics](#the-basics)
    - [Constants and variables](#constants-and-variables)
    - [Type Annotations](#type-annotations)
    - [Comments](#comments)
    - [Type Aliases](#type-aliases)
    - [Tuples](#tuples)
    - [Optionals](#optionals)
    - [Forced Unwrapping](#forced-unwrapping)
    - [Optional Binding](#optional-binding)
    - [Error Handling](#error-handling)
- [Basic Operators](#basic-operators)
    - [Nil-Coalescing Operator](#nil-coalescing-operator)
    - [Closed Range Operator](#closed-range-operator)
    - [Half-Open Range Operator](#half-open-range-operator)
    - [One-Sided Ranges](#one-sided-ranges)
- [String and Characters](string-and-characters)
    - [Multiple String literals](#multiple-string-literals)
    - [Working with characters](#working-with-characters)
    - [String Interpolation](#string-interpolation)
- [Collection Types](#collection-types)
- [Control Flow](#control-flow)
    - [For-in Loops](#for-in-loops)
    - [Switch](#switch)
    - [Early Exit](#early-exit)
- [Functions](#functions)
    - [Functions with Multiple Return Values](#functions-with-multiple-return-values)
    - [Specifying Argument Labels](#specifying-argument-labels)
    - [Omitting Argument Labels](#omitting-argument-labels)
    - [In-Out Parameters](#in-out-parameters)
    - [Implicit Return](#implicit-return)
    - [Using Function Types](using-function-types)
    - [Function Types as Parameters Types](#function-types-as-parameters)
    - [Function Types as Return Types](#function-types-as-return-types)
    - [Nested Function](#nested-functions)
- [Closures](#closures)

# The Basics

Swift is a new programming language for iOS, macOS, watchOS, and tvOS app development.

## Constants and variables

The value of a constant can't be changed once it's set, whereas a variable can be set to a different value in the future.

```swift
let maximumNumberOfLoginAttempts = 10
var currentLoginAttempt = 0
```

You can declare multiple constants or multiple variables on a single line, separated by commas:

```swift
var x = 0.0, y = 0.0, z = 0.0
```

## Type Annotations

This example provides a type annotations for a variable called `welcomeMessage, to indicate that the variable can store `String` values:

```swift
var welcomeMessage: String
```

The `welcomeMessage` variable can now be set to any string value:

```swift
welcomeMessage = "Hello"
```

You can define multiple related variables of the same type on a single line.

```swift
var red, green, blue: Double
```
> **NOTE:** It's rare that you need to write type annotations in practice. If you provide an initial value for a constant or variable, Swift can almost always infer the type to be used for that constant or variable.

## Comments

Use comments to include no executable text in your code.

```swift
// This is a comments
```

Multiline comments

```swift
/* This is also a comment
but is written over multiple lines */
```

## Type Aliases

Type aliases define an alternative name for an existing type. You define type aliases with the `typealias` keyword.

```swift
typealias Students = Array<Student>
```

## Tuples

`Tuples` group multiple values into a single compound value.

```swift
let http404Error = (404, "Not Found")
// http404Error is of type (Int, String), and equals (404, "Not Found")
```

You can decompose a tuple`s contents into separate constants or variables:

```swift
let (statusCode, statusMessage) = http404Error
print("The status code is \(statusCode)")
```

If you only need some of the tuple`s values, ignore parts of the tuple with an underscore(_):

```swift
let (statusCode, _) = http404Error
print("The status code is \(statusCode)")
```

Alternatively, access the individual element values in a tuple using index:

```swift
print("The status code is \(http404Error.0)")
```

You can name the individual elements in a tuple when the tuple is defined:

```swift
let http200Status = (statusCode: 200, description: "OK")
print("The status code is \(http200Status.statusCode)")
```

> **NOTE:** Tuples are particularly useful as the return values of functions.

## Optionals

You use `optionals` in situations where a value may be absent.

```swift
let possibleNumber: String = "123"
let convertedNumber: Int? = Int(possibleNumber)
print(type(of: convertedNumber)) // Optional<Int>
```

If you define an optional variable without providing a default value, the variable is automatically set to `nil` for you:

```swift
var surveyAnswer: String? // nil
```

## Forced Unwrapping

The exclamation point effectively says, "I know that this optional has a value".

```swift
if convertedNumber != nil {
    print("convertedNumber has a integer value of \(convertedNumber!)")
}
```

> **NOTE:**
Always make sure that an optional contains a non-nil value before using `!` to avoid runtime error.

## Optional Binding

You use optional binding to find out whether an optional contains a value, and if so, to make that value available as a temporary constant or variable.

```swift
let possibleNumber = "123"

if let actualNumber = Int(possibleNumber) {
    print("The string \"\(possibleNumber)\" has an integer value of \(actualNumber)")
} else {
    print("The string \"\(possibleNumber)\" could not be converted to an integer")
}
```
> **NOTE:** Constant and variables created with optional binding is available only within the body of the body statement.

## Error handling

You use `error handling` to respond to error conditions your program may encounter during execution.

```swift 
func canThrowAnError() throws {
    // ...
}

do {
    try canThrowAnError()
    // no error was thrown
} catch {
    // an error was thrown
}
```

# Basic Operators

## Nil-Coalescing Operator

The nil-coalescing operator is shorthand for the code below:

```swift
a != nil ? a! : b
```

The example below uses the nil-coalescing operator to choose between a default color name and an optional user-defined color name:

```swift
let defaultColorName = "red"
var userDefinedColorName: String?

var colorNameToUse = userDefinedColorName ?? defaultColorName
// userDefinedColorName is nil, so colorNameToUse is set to the default of "red"
```

## Closed Range Operator

The `closed range operator (a...b)` defines a range the runs from `a` to `b`, and includes the values `a` and `b`. The value of `a` not be greater than `b`.

```swift
for index in 1...5 {
    print("index: \(index)")
}
```

## Half-Open Range Operator

The `half-open range operator (a..<b)` defines a range that runs from `a` to `b`, but doesn't include `b`.

```swift
let names = ["Anna", "Alex", "Brian", "Jack"]
let count = names.count
print(count) // 4
for i in 0..<count {
    print(i) // 0,1,2,3
}
```

## One-Sided Ranges

```swift 
for name in names[2...] {
    print(name) // Brian, Jack
}
```

# String and Characters

## Multiple String literals

```swift
let quotation = """
The White Rabbit put on his spectacles.  "Where shall I begin,
please your Majesty?" he asked.
"""
```

- The escaped special characters \0 (null character), \\ (backslash), \t (horizontal tab), \n (line feed), \r (carriage return), \" (double quotation mark) and \' (single quotation mark)

## Working with characters

You can access the individual `Character` values for a `String` by iterating over the string with a for-in loop:

```swift
for character in "Dog!🐶" {
    print(character) // D, o, g, !, 🐶
}
```

## String Interpolation

```swift
let multiplier = 3
let message = "\(multiplier) time 2.5 is \(Double(multiplier) * 2.5)" // 3 times 2.5 is 7.5
```

# Collection Types

Swift provides three primary collection types, know as arrays, sets, and dictionaries.

![](https://docs.swift.org/swift-book/_images/CollectionTypes_intro_2x.png)

```swift
// Array
var arraySyntax = Array<Int>()
var arrayShortSyntax = [Int]()

// Set
var setSyntax = Set<Character>()

// Dictionaries
var dictionariesSyntax = Dictionary<Int, String>()
var dictionariesShortSyntax = [Int: String]()
```

# Control Flow

Swift provides a variety of control flow statements.

## For-in Loops

```swift
// Array
let names = ["Anna", "Alex", "Brian", "Jack"]
for name in names {
    print("Hello \(name)!")
}

// Dictionary
let numberOfLegs = ["spider": 8, "ant": 6, "cat": 4]
for (animalName, legCount) in numberOfLegs {
    print("\(animalName)s have \(legCount) legs")
}
```

## Switch

```swift
let anotherCharacter: Character = "a"
switch anotherCharacter {
    case "a", "A":
        print("The letter A")
    default:
        print("Not the letter A")
}
```

## Early Exit

a `guard` statement, like a `if` statement, executes statements depending on the Boolean value of an expression.

```swift
func greet(person: [String: String]) {
    guard let name = person["name"] else {
        return
    }

    print("Hello \(name)")

    guard let location = person["location"] else {
        print("I hope the weather is nice near your")
        return
    }

    print("I hope the weather is nice in \(location)")
}
```

# Functions

## Functions with Multiple Return Values

```swift
func minMax(array: [Int]) -> (min: Int, max: Int) {
    var currentMin = array[0]
    var currentMax = array[0]
    for value in array[1..<array.count] {
        if value < currentMin {
            currentMin = value
        } else if value > currentMax {
            currentMax = value
        }
    }
    return (currentMin, currentMax)
}
let (min, max) = minMax(array: [1,2,5,6])
```

## Specifying Argument Labels

You write an argument label before the parameter name, separated a space:\

```swift
func greeting(for person: String) {
    print("Hello \(person)")
}
greeting(for: "Anna")
```

## Omitting Argument Labels

If you don't want an argument labels for a parameter, write an underscore(_) instead of an explicit argument label for that parameter.

```swift
func greeting(_ person: String) {
    print("Hello \(person)")
}
greeting("Anna")
```

## In-Out Parameters

Function parameters are constants by default. If you want to modify a parameters value, define that parameter as an `in-out parameters` instead.

```swift
func greeting(_ person: inout String) {
    person = "Alex"
    print("Hello \(person)")
}
var name = "Ana"
greeting(&name) // Hello Alex
print(name) // Alex
```

> **NOTE:**
`in-out parameters are an alternative way for a function to have an effect outside of the scope of its function body.`

## Implicit Return

```swift
func addTwoInt(_ a: Int, _ b: Int) -> Int {
    a + b
}
```

## Using Function Types

You use function type just like any other types in Swift.

```swift
var mathFunction: (Int, Int) -> Int = addTwoInt
print("\(mathFunction(2, 3))") // 5
```

## Function Types as Parameter Types

```swift
func printMathResult(_ mathFunction: (Int, Int) -> Int, _ a: Int, _ b: Int) {
    print("Result: \(mathFunction(a, b))")
}
printMathResult(addTwoInt, 3, 5) // 8
```

## Function Types as Return Types

```swift
func stepForward(_ input: Int) -> Int {
    input + 1
}
func stepBackward(_ input: Int) -> Int {
    input - 1
}

func chooseStepFunction(backward: Bool) -> (Int) -> Int {
    backward ? stepBackward : steForward
}
```

## Nested Functions

```swift
func chooseStepFunction(backward: Bool) -> (Int) -> Int {
    func stepForward(input: Int) -> Int { return input + 1 }
    func stepBackward(input: Int) -> Int { return input - 1 }
    return backward ? stepBackward : stepForward
}
```

## Closures


Closure Expression Syntax
```
{ (parameters) -> return type in
    statements
}
```

The example below shows a closure expression version of the `backward(_:_:)` function:

```swift
reversedNames = names.sorted(by: { (s1: String, s2: String) -> Bool in
    return s1 > s2
})
```

### Inferring Type From Context

```swift
reversedNames = names.sorted(by: { s1, s2 in return s1 > s2 } )
```

### Implicit Returns from Single-Expression Closures

```swift
reversedNames = names.sorted(by: { s1, s2 in s1 > s2 })
```

### Shorthand Argument Names

```swift
reversedNames = names.sorted(by: { $0 > $1 } )
```

### Operator Methods

```swift
reversedNames = names.sorted(by: >)
```





