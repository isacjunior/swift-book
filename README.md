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
> **_NOTE:_** It's rare that you need to write type annotations in practice. If you provide an initial value for a constant or variable, Swift can almost always infer the type to be used for that constant or variable.

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

> **_NOTE:_** Tuples are particularly useful as the return values of functions.

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

