# Swift book

The proposal of this repository is to create a document that contains a resume of all features in Swift. Besides that, to show examples of code with snippets.

- [Proposal](#proposal)
- [The Basics](#the-basics)
    - [Constants and variables](#constants-and-variables)
    - [Type Annotations](#type-annotations)
    - [Comments](#comments)


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


