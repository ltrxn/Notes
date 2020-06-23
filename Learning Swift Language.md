Notes from Swift's [Language Guide](https://docs.swift.org/swift-book/LanguageGuide/TheBasics.html)

Overview

[I. The Basics](#I. The Basics)

[II. Basic Operators](#II. Basic Operators)

[III. Strings and Characters](#III. Strings and Characters)

[IV. Collection Types](#IV. Collection Types)

[V. Control Flow](#V. Control Flow)

[VI. Functions](#VI. Functions)

[VII. Closures]() -

[VIII. Enumerations]() -

[IX. Classes and Structures](# IX. Classes and Structures)

[X.Properties](# X. Properties)

[XI. Methods](# XI. Methods)

[XII. Subscripts]()-

[XIII. Inheritance](# XIII. Inheritance)

[XIV. Initialization](# XIV. Initialization)

---



# I. The Basics

## Constants and Variables

Constants are declared with `let` and variables with `var`. Declare multiple on a single line by separating with commas. The following line can be read as “declare a new constant called `variableName`, and give it a value of 5”

```swift
let variableName = 5
var variableOne = 5, variableTwo = 10, variableThree == 15
```

### Type Annotations

Provide a *type annotation* to be clear about the kind of values the variable can store. Read as “...of type…”. Define multiple by adding a single type annotation after the final variable name.

```swift
var welcomeMessage: String
```

Once a variable is declared, you can’t declare it again, change it to store values of a different type, or change it into a constant.

### Printing Constants and Variables

To print the current value of a variable, use the `print(_:separator:terminator:)` function.

```swift
print(“Hello World”)
```

 By default, the function terminates with a line break. To print without a line break

```swift
print(someValue, terminator: “”)
```

Swift uses *string interpolation* to include the name of a constant or variable as a placeholder in a longer string. Prompt Swift to replace it with the value of the variable by wrapping the name in parentheses and escape it with a black slash.

```swift
print(“Value of friendlyWelcome is \(friendlyWelcome)”)
```

## Comments

Comments are used to include non executable text, like a note or reminder. They are ignored by the Swift compiler. Single line comments begin with two forward-slashes:

```swift
// This is a single line comment.
```

Multiline comments start with `/*` and end with `*/`. You can nest multiline comments*

```swift
/* This is a comment written

over many lines. */
```

## Semicolons

Semicolons are not required. Although you can do so if you wish. However, semicolons are required if you want to write multiple separate statements on a single line.

## Integers

Integers are whole numbers with no fractional component.

An 8-bit unsigned integer is of type `UInt8`, and a 32-bit signed is of type `Int32`.

Access the minimum and maximum values of each integer type with its `min` and `max` properties:

```swift
let minValue = UInt8.min //minValue is equal to 0 and is type UInt8
```

Swift provides the integer type, `Int`, which has the same size as the current platform’s native word size (on 32-bit, `Int` is the same size as `Int32`). `Int` will typically always be used. UInt is the unsigned integer type. It also has the same size as the platform’s native word size (on 64-bit, `UInt` is the same size as `UInt64`).

## Floating-Point Numbers

Numbers with a fractional component. Floating-point types can represent a wider range of values than integer types. Swift has two signed floating-point number types: `Double` (64-bit, precision at least 15 decimal digits) and `Float` (32-bit, precision at least 6 decimal digits).

## Type Safety and Type Inference

Swift is a *type-safe* language. This means the type of values your code uses is clear (can’t pass an `Int` into a code that requires a `String`). Swift performs *type checks* when compiling your code and flags any mismatched types as errors. 

If the type of a constant or variable is not declared, swift uses *type inference* to work out the appropriate type by examining the values you provide. Type inference is useful when you declare a constant or variable with an initial value because you assign a *literal value* (a value that appears directly in your source code like `42` or `3.14`) to it. 

## Numeric Literals

Integer literals can be written as: *decimal* number (no prefix), *binary* number (`0b` prefix), *octal* number (`0o` prefix), or *hexadecimal* number (`0x` prefix.) All these integer literals will have a decimal value of 17: `17`, `0b10001`, `0o21`, `0x11`.

Floating-point literals can be decimal (with no prefix). They must always have a number on both sides of the decimal point. Decimal floats can also have an optional *exponent*, indicated by an `e` (or `p` for hexadecimal floats). `1.25e2` means 1.25 x 10^2^ or 125.0.

Numeric literals can contain extra formatting for readability. You can pad with extra zeros (`0012.34)` and add underscores (`1_000_000`).

## Numeric Type Conversion

If you are adding two integers with different types, you can create a new variable that is initialized with the inferred and correct type.

Conversions between integers and floating-point numeric types must be made explicit. Without a conversion, you cannot add an integer to a double:

```swift
let three = 3
let pointOneFour = 0.14
let pi = Double(three) + pointOneFour
```

An integer type can be initialized with a Double or Float value:

```swift
let integerPi = Int(pi)
```

## Type Aliases

*Type aliases* define an alternative name for an existing type through the `typealias` keyword. They are useful if you want to refer to an existing type with a contextually more appropriate name, such as working with data of a specific size from an external source. Then, you can use the alias anywhere you might use the original name:

```swift
typealias AudioSample = UInt16var
maxAmplitudeFound = AudioSample.min //actually calls UInt16.min.
```

## Booleans

Swift has a basic *Boolean* type called `Bool`. The two Boolean constant values are `true` and `false`. Results of comparisons are of type `Bool`. 

## Tuples

*Tuples* group multiple values into a single compound value. The values can be of any type. A tuple can group an `Int` and `String` to give the variable or constant two seperate values (“a tuple of type (`Int`, `String`)”):

```swift
let http404Error = (404, “Not Found”)
```

You can then decompose a tuple’s content into separate constants or variables:

```swift
let (statusCode, statusMessage) = http404Error
let (justStatusCode, _) = http404Error //ignore the second part of the tuple
```

Alternatively, access the individual element values in a tuple using index numbers:

```swift
print(“status code is \(http404Error.0)”) // prints “status code is 404”
```

Or, name the elements in the tuple so you can use the element names later to access:

```swift
let http200Status = (statusCode:200, description: “ok”)
print(“status code is \(http200Status.statusCode)”) // prints “status code is 200”
```

## Optionals

Use *optionals* in situations where a value may be absent. An optional represents two possibilities: there *is* a value, and you can unwrap the optional to access that value; or there *isn’t* a value at all. Here’s an example of when an optional will be used. The `Int` type has an initializer that tries to convert a `String` into an `Int` (`“123”` to `123`). However, not every string can be converted into an integer (like `“hello”`). Because the initializer has a potential to fail, it returns an *optional* `Int`. An optional `Int` is written as `Int`?. The question mark indicates that the value contains either an `Int` or nothing at all.

### nil

To set an optional to a valueless state, assign it to the value `nil`. If you define an optional without providing a default value, the variable is automatically set to `nil` for you. `nil` is the absence of value.

### Forced Unwrapping

You can use an `if` statement to find out whether an optional contains a value by comparing the optional against `nil` through the “equal to” (`==`) or “not equal to” (`!=`) operator. Once its determined that the optional *does* contain a value, you can access its underlying value, or *force unwrap*, by adding an exclamation mark (`!`) to the end of the optional’s name. 

```swift
if convertedNumber != nil {
  print(“convertedNumber is \(convertedNumber!)”)
}
```

### Optional Binding

*Optional binding* is another way to find out whether an optional contains a value, and if so, to make the value available as a temporary constant or variable. Optional binding can be used with if and while statements to extract the value into a constant or variable as a single action:

```swift
if let constantName = someOptional {
  //statements 
} else {
  //statements
}
```

Code above can be read as “if `someOptional` contains a value, then set a new constant called `constantName` to the value contained the optional.” If it is successful, then the `constantName` constant becomes available for use.

You can include multiple optional bindings and Boolean conditions in a single `if` statement, separated by commas:

```swift
if let firstNumber = Int(“4”), let secondNumber = Int(“3”) {
  //statements
}
```

### Implicity Unwrapped Optionals

*Implicitly unwrapped optionals* are optionals that will *always* have a value, after that value is first set. These optionals remove the need to check and unwrap the optional’s value every time because it can be safely assumed to have a value all the time. To write an implicitly unwrapped optional, place an exclamation mark (`String!`) rather than a question mark (`String?`). The primary use is during class initialization, when the optional's value is confirmed to exist immediately after the optional is first defined and every point after. You can access implicitly unwrapped optionals without an exclamation mark. 

It's like giving permission for the optional to be force-unwrapped if needed.

## Error Handling

Use *error handling* to respond to error conditions that your program may encounter during execution. Error handling allows you to determine the underlying cause of failure. When a function encounters an error condition, it *throws* an error, which the function’s caller can then *catch*. 

```swift
func canThrowAnError() throws { }
```

When you call a function that can throw an error, you prepend the try keyword to the expression:

```swift
do {
  try canThrowAnError () {
    //no error was thrown
  } catch {
    //an error was thrown
  }
```

A `do` statement creates a new containing scope, allowing errors to be propagated to one or more `catch` clauses:

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

## Assertions and Preconditions

These are checks that happen at runtime. Use them to make sure an essential condition is satisfied before executing any further. Use assertions and preconditions to express the assumptions you make and expectations you have. Assertions help you find mistakes and incorrect assumptions, and preconditions help you detect issues in production. Assertions are checked only in debug builds, but preconditions are checked in debug and production builds. This means, you can add as many assertions without impacting performance.

Write an assertion by calling the `assert(_:_:file:line)` function. Pass this function with a boolean expression and a message to display if the result of the condition is false:

```swift
let age = -3
assert(age >= 0, “a person’s age cannot be less than zero”)
//the assertion is false, so message is displayed
```

If your code already checks the condition, use `assertionFailue(_:file:line:)` function to indicate that an assertion has failed. Use it when the code has already chcekd that an assertion has failed:

```swift
if age<0 {
	assertionFailure("A person's age cannot be less than zero")
}
```

Use a precondition whenever a condition has the potential to be false, but *must* be true for your code to continue execution. For example, checking that a subscript is not out of bounds. Call the `precondition(_:_:file:line:)` function:

```swift
precondition(index > 0, “Index must be greater than zero”) //runs
```

There’s also the `preconditionFailure(_:file:line:)` function.

`assert` is for sanity checks during testing, whereas `precondition` is for guarding against things that, it they happen, would mean your program could not reasonably proceed.

# II. Basic Operators

An *operator* is a special symbol/phrase that can be used to check, change, or combine values.

## Terminology

*Unary* operators operate on a single target (called *operands*. Unary *prefix* operators appear immediately before their target (`!b`), and unary *postfix* operators appear immediately after (`c!`).

*Binary* operators operate on two targets (`2+3`) and are infix (appear between two targets). 

*Ternary* operators operate on three targets (`a ? b : c`)

## Assignment Operator

The *assignment operator* initializes or updates. `a = b` updates the value of a with the value of `b`.

Elements can be decomposed into multiple variables: `let (x, y) = (1, 2)`

The assignment operator does not itself return a value.

## Arithmetic Operators

Addition (`+`), subtraction (`-`), multiplication (`*`), division (`/`), remainder operator (`%`).

*Unary minus operator* toggles the sign of a numeric value. Use the prefix `-`.

*Unary plus operator* (`+`) returns the value it operates on without change.

## Compound Assignment Operators

These combine assignments with another operation. For example, `+=`.

## Comparison Operators

- Equal to `=`
- Not equal to `!=`
- Greater than `>`
- Less than `<`
- Greater than or equal to `>=`
- Less than or equal to `<=`.

You can compare two tuples if they have the same type and the same number of values. If all elements are equal, then the tuples are equal. Comparisons are made left-to-right. They are determined by the tuple’s first element. However, if they are the same, the second elements are compared. Two tuples of type `(String, Bool)` cannot be compared with `<` operator because it can't be applied to `Bool` values

## Ternary Conditional Operator

A special operator with three parts, taking the form `question ? answer1 : answer2`. It’s a shortcut for evaluating one of the two expressions based on whether `question` is true or false. If it’s true, it evaluates `answer1`; otherwise, it evaluates `answer2`.

## Nil-Coalescing Operator

*Nil-coalescing* operator `(a ?? b)` unwraps an optional (`a`) if it contains a value, or returns a default value (`b`) if the optional is nil. This operator is shorthand for `a != nil ? a! : b`.

## Range Operators

*Range operators* are shortcuts for expressing a range of values. 

The *closed range operator* `(a...b)` defines a range that runs from a to b, and *includes* the value `a` and `b`. Useful for iterating over a range like in a `for-in` loop.

```swift
for index in 1...5 {
	print("\(index) times 5 is \(index*5)")
}
```

The *half-open range operator* `(a..<b)` defines a range from `a` to `b`, but doesn’t include `b`. Good for zero-based lists.

*One-sided range* is created when you omit the value from one side of the range operator. `(2…)` or `(...<2)`. For example, a range that includes all elements of an array from index 2 to the end of the array:

```swift
for name in names[2...] {
    print(name)
}
```

You can't iterate over a one-sided range that omits a first value, because it isn't clear where iteration should begin. However, you *can* iterate over a one-side range that omits a final value, but include an explicit end condition for the loop.

## Logical Operators

They modify or combine the Boolean logic. Logical NOT (`!a`), logical AND (`a && b`), and logical OR (`a || b`)

Combine multiple logical operators to create longer compound expressions. Swift logical operators are left-associative, meaning that compound expressions evaluate the leftmost subexpression first. You can also add parentheses to make its intent explicit.

# III. Strings and Characters

A *string* is a series of characters.

## String Literals

Predefined String values are *string literals*. A string literal is a sequence of characters surrounded by quotation marks (`“`).

 To create a multiline string literal, surround a sequence of characters by three double quotation marks (`“””`). When your source code includes a line break, write a backslash (`\`). Example:

```swift
let lineBreaks = """

This string starts with a line break.
It also ends with a line break.

"""
```

Escaped *special characters*: `\0` (null character), `\` (backslash), `\t` (horizontal tab), `\n` (line feed), `\r` (carriage return), `\”` (double quotation mark), `\’` (single quotation mark).

An arbitrary Unicode scalar value, written as `\u{n}` where `n` is a 1.8 digit hexadecimal number can create other special characters. Example:

```swift
let sparklingHeart = "\u{1F496}" // 💖, Unicode scalar U+1F496
```

Place string literal within *extended delimiters* to include special characters in a string without invoking their effect. Place `#` around `“”` like this `#"Line\nLine2"#`. It will print the line escape sequence rather than printing the string across two lines. When using pound-signs, you change the escape sequence from a single backslash to a backslash infixed with the same number of pound signs. So to actually print across two lines you must write as `#"Line\#nLine2"#`

## Initializing an Empty

StringEmpty string literal: `var emptyString = “”` or use initializer syntax: `var emptyString = String()`.

## String are Value Type

Swift’s `String` type is a *value type*. When you create a new `String` value, the `String` value is *copied* when passed to a function or method. When it’s assigned, a new copy is made. It makes it clear that you wont hat exact `String` value, allowing you to be confident that the string you are passed won't be modified.

## Working with Characters

You can access individual `Character` values for a string by iterating over the string with for-in loop. Alternatively, you can use a stand-alone `Character` variable.

String values can be constructed by passing an array of `Character` values as an argument to its initializer. `let catString = String([“c”, “a”, “t”])`

## Concatenating Strings and Characters

You can add together (concatenate) `String` values with the addition operator. You can also append a `Character` value to a `String` variable with the String type’s `append()` method. 

## String Interpolation

*String interpolation* is a way to construct a new String value from constants, variables, literals, and expressions by including their value inside a string literal. Example:

```swift
let multiplier = 3
let message = “\(multiplier) times 2 is \(Double(multiplier)*2.5)
```

## Unicode

Is an international standard for encoding, representing, and processing text in different writing systems.

## Counting Characters

`count` property of string retrieves a count of the character values in a string. 

```swift
let word = “hello”
Word.count // would be 5
```

## Accessing and Modifying a String

### String Indices

Each string value has an associated *index* type, `String.Index`, which corresponds to the position of each character in the string.

`startIndex` property accesses the position of the first Character of a string. `endIndex` property is the position after the last character in a String. 

Access the indices before and after a given index using the `index(before:)` and `index(after:)` methods of String. To access an index farther away from the given index, you can use `index(_:offsetBy:)`. Example:

```swift
let greeting = “Guten Tag!”
greeting[greeting.startIndex] // G
greeting[greeting.index(before: greeting.endIndex)] // !
greeting[greeting.index(after: greeting.startIndex) // u
let index = greeting.index(greeting.startIndex, offsetBy: 7)
greeting[index] // a
```

The `indices` property accesses all of the indices of individual characters in a string. (`for index in greeting.indices`).

### Inserting and Removing

Insert a single character into a string at a specified index using the `insert(_:at:)` method or `insert(contentsOf:at:)`:

```swift
var welcome = “hello”
welcome.insert(“!”, at: welcome.endIndex) //makes “hello!”
welcome.insert(contents of: “ there”, at: welcome.index(before: welcome.endIndex)) //makes “hello there!”
```

Remove a single character with `remove(at:)` or remove a substring a a specified range with `removeSubrange(_:)`

```swift
welcome.remove(at: welcome.index(before: welcome.endIndex))
// welcome now equals "hello there"

let range = welcome.index(welcome.endIndex, offsetBy: -6)..<welcome.endIndex
welcome.removeSubrange(range)
// welcome now equals "hello"
```

## Substrings

Substrings have most of the same methods as strings. However, use substrings for only a short amount of time which performing actions on a string. Convert substring to instance of string to store the result for a longer time: `let newString = String(subString)`. You can get substrings from a strong using a subscript or a method like `prefix(_:)`.

## Comparing Strings

String and character equality is checked with the “equal to” operator (`==`) and “not equal to operator (`!=`). Two String or Character values are considered equal if their extended grapheme clusters are canonically equivalent. 

Prefix and suffix equality to check whether a string has a particular string prefix or suffix. Call the string’s `hasPrefix(_:)` and `hasSuffix(_:)`. 

# IV. Collection Types

Three primary *collection* types are arrays, sets, and dictionaries. Arrays are ordered, sets are unordered, and dictionaries are unordered collections of key-value associations. You cannot insert a value of the wrong type into a collection by mistake.

## Mutability of Collections

Collections assigned to a variable are *mutable*, and those assigned to a constant are *immutable*. 

## Array

An *array* stores values of the same type in an ordered list. The same value can appear in an array multiple times at different positions.

The type of a Swift array is written in full as `Array<Element>`, where `Element` is the type of values the array is allowed to store. Array in shorthand is `[Element]`. Create an empty array:

```swift
varsomeInt = [Int]()
```

To set all its values to the same default value with a certain size, pass the initializer a default value (called `repeating`) and the number of times you the value is repeated in the new array (called `count`):

```swift
var threeDoubles = Array(repeating: 0.0, count: 3)
//type [Double], and equals [0.0, 0.0, 0.0]
```

Add two existing arrays with compatible types with the addition operator.

```swift
var anotherThreeDoubles = Array(repeating: 2.5, count: 3)
var sixDoubles = threeDoubles + anotherThreeDoubles
```

Initialize an array with an *array literal*:

```swift
var shoppingList: [String] = [“eggs”, “milk”]
var shoppingList = [“eggs”, “milk”]
```

To find out the number of items in an array, use the `count` property.
Boolean `isEmpty` property checks if the `count` property is equal to 0.

Add a new item to the end of the array by calling the array’s `append(_:)` method. Alternatively, you can append items with the addition assignment operator (`+=`)

Retrieve a value of the array by using *subscript syntax*. Arrays in Swift are always zero-indexed:

```swift
var firstItem = shoppingList[0]
```

You can also use subscript syntax to change a range of value at once:

``` swift
 shoppingList[4...6] = ["bananas", "apples"] //replaces three items with two
```

Insert an item into the array at a specified index with `insert(_:at:)` method. Remove an item from the array with `remove(at:)`. This method will return the removed item. You can also use the `removeLast()` method. 

You can iterate over the entire set of values in an array with the `for`-in loop:

```swift
for item in shoppingList {
	print(item)
}

```

Use the `enumerated()` method for the integer index of each item as well as its value. For each item, this method returns a tuple composed of an integer and the item:

```swift
for (index, value) in shoppingList.enumerated() {
	print(“Item \(index+1): \(value)”)
}
```

## Sets

A *set* stores distinct values of the same type in a collection with no defined ordering. Use it when ordering is not important or you need to ensure that there are no duplicates.

A type must be *hashable* inorder to be stored in a set, meaning that it has to be able to compute a *hash value* for itself. A has value is an `Int` value that is the same for all object to compute equally, such that if `a==b`, then `a.hashValue==b.hasValue`.

Create an empty set by using initializer syntax or with an array literal. The set type cannot be inferred from an array literal so you must explicitly declare `Set`:

```swift
var letters = Set<Character>()
var favoriteGenres: Set<String> = [“Rock”, “Classical”, “Hip hop”]
// <String> is unecessary because all the values in the array literal are of the same type.
favoriteGenres = [] // favoriteGenres is now an empty set, but still of type Set<String>
```

`.count` property checks the number of items. `.isEmpty` to check if count is equal to zero.

 `.insert(_:)` method to add a new item. `.remove(_:)` removes the item if it's a member of the set and returns the removed value or `nil` if the set did not contain it. All items can be removed with `.removeAll()`. 

Check if a list contains a particular item through `contains(_:)` method.

### Set Operations

`a.intersection(b)` method creates a new set with only the values common in both sets. `a.symmetricDifference(b)` creates a new set with values in either sets, but not both. `a.union(b)` creates a new set with all the values in both sets. `a.subtracting(b)` creates a new set with values not in the specific set (keeps `a`’s values).

### Set Membership

`==` determines whether two sets contain all of the same values.

`isSubset(of:)` determines whether all of the values of a set are contained in the specified set. 

`isSuperset(of:)` determines whether a set contains all of the values in a specified set. 

`isStrictSubset(of:)`/`isStrictSuperset(of:)` determines whether a set is a subset or superset, but not equal to, a specified set. 

`isDisjoint(with:)` determines whether two sets have no values in common.

## Dictionaries

A *dictionary* stores associations between keys and values (of the same type) in a collection with no defined ordering. Each value has a unique *key*. Use a dictionary when you need to look up values based on their identifier.

The type of a Swift dictionary written in full: `Dictionary<Key, Value>`. In shorthand form: `[Key: Value]`.

Create an empty dictionary of a certain type with its initializer syntax: 

```swift
var namesOfIntegers = [Int: String]()
var namesOfIntegers2 = [:] // when context provides the type
```

 Create a dictionary with a dictionary literal written as *key-value pairs*:

```swift
var airports: [String: String] = [“YYZ”: “Toronto Pearson”, “DUB: “Dublin”]
var airports = [“YYZ”: “Toronto Pearson”, “DUB: “Dublin”] //shorter form
```



Find out the number of items with its read-only `count` property. Use Boolean `isEmpty` property to check if count is equal to 0.

Add new item with subscript syntax; use a new key as the subscript index: 

```swift
airports[“LHR”] = “London”
```

`updateValue(_:forKey:)` can update the value for a particular key and returns the *old* value after update. It returns an optional value because it returns `nil` if no value existed previously:

```swift
if let oldValue = airports.updateValue("Dublin Airport", forKey: "DUB") {
	prints("The old calue for DUB was \(oldValue).")
}
```

Use subscript syntax for retrieving a value from the dictionary using a key, but it will return an optional value. You can also use subscript syntax to remove a key-value pair by assigning a value of nil for that key:

```swift
aiports["APL"] = "Apple International"
airports["APL"] = nil
//APL removed from dictionary
```

 Or, you can remove a pair with the `removeValue(forKey:)` method (returns removed value if it exists, or returns `nil` if no value existed.

When iterating over a dictionary with a `for-in` loop, each item is returned as a `(key, value)` tuple. Decompose by:

```swift
for (airportCode, airportName) in airports { … }
```

Access an iterable collection of a dictionary’s keys or values by accessing its `keys` and `values` properties. Able to put it in an array as well:

```swift
for airportCode in airports.keys { … }
let airportNames = airports.values
```

Since `dictionary` lacks defined ordering, use `sorted()` on a dictionary’s `keys` or `values` property to iterate in a specific order.

# V. Control Flow

Swift has a variety of control flow statements such as the following: `if`, `guard`, `while` loops, `switch` statements, and `for-in` loops. Statements like `break` and `continue`transfer the flow of execution to another point in your code.

## For-In Loops

Use *for-in* loops to iterate over a sequence. Use them to iterate through arrays, dictionaries, or ranges.

```swift
for index in 1...5 {...}
```

The sequence is being iterated from 1 to 5, inclusive. The value of `index` is initially set to the first number of the range, `1`. After the statements are executed, `index` is updated to contain the second value of the range, `2`. `index` is constant whose value is set at the start of each iteration of the loop.

Ignore the values by using an underscore in place of a variable name.:

```swift
for _ in 0...<5 {...} //runs statements five times.
```

`stride(from:to:by:)` function skips values. `stride(from:through:by:)` is a closed range.

## While Loops

A *while loop* performs a set of statements until a condition becomes `false`.  The two types:

- `while` evaluates its condition at the start of each pass.
- `repeat-while` evaluates its condition at the end of each pass through the loop.

### While

Starts by evaluating a single condition. A set of statements is repeated until the condition becomes fault:

```swift
while CONDITION {
	STATEMENTS
}
```

### Repeat-While

Performs a single pass through the loop block first before considering the condition:

```swift
repeat {
	STATEMENTs
} while CONDITION
```

## Conditional Statements

Two ways to add conditional branches to code: the `if` statement (simple conditions with few possible outcomes) and `switch` statement (complex conditions with multiple possible permutations).

### If

An `if` with a single condition executes a set of statements if the condition is true. 

An `else` clause provides an alternative set of statements if the condition is false.

`else if` makes additional `if` statements.

## Switch

A `switch` statement considers a value  and compares it against several possible matching patterns. Then executing an appropriate block of code based on the first pattern it matches successfully. 

```
switch SOME VALUE TO CONSIDER {
	case VALUE1:
		RESPOND TO VALUE1
	case VALUE2, VALUE 3:
		RESPOND TO VALUE 2 or 3
	default:
		OTHERWISE, DO SOMTHING ELSE
}
```

The `switch` statement consists of multiple posible *cases*. Every `switch` statement must be *exhaustive*, every possible value of the type being considered  must be matched by one of the `switch` cases. If this isn't possible, a default case can be indicated by the `default` keyword (must appear last). The `default`case ensures that the statement is exhaustive.

The entire `swift` statement finishes its execution as soon as the first matching `switch` case is completed, without requiring an explicit `break` statement, avoiding the possibility of executing more than one switch case by mistake.

Case bodies cannot be empty.

### Interval Matching

Values in switch cases can be checked for their inclusion in an interval.  Example of using number interval to provide natural-language count for numbers of any size:

```swift
let approximateCount = 62
let naturalCount: String
switch approximateCount {
	case 0:
  	naturalCount = "no"
  case 1..<5:
  	naturalCount = "a few"
  case 5..<12:
  	naturalCount = "several"
  default:
  	naturalCount = "many"
}
```

### Tuples

You can use tuples to test multiple values. Each individual element of the tuple can be tested against a different value or interval of values. Use the underscore character (`_`), to match any possible value.

```swift
let somePoint = (1, 1)
switch somePoint {
case (0, 0):
    print("\(somePoint) is at the origin")
case (_, 0):
    print("\(somePoint) is on the x-axis")
case (0, _):
    print("\(somePoint) is on the y-axis")
case (-2...2, -2...2):
    print("\(somePoint) is inside the box")
default:
    print("\(somePoint) is outside of the box")
}
// Prints "(1, 1) is inside the box"
```

### Value Bindings

A `switch` case can name the value(s) it matches to temporary variables for use in the body of the case. This is called *value binding* because values are temporarily bounded to constants/variables.

````swift
let anotherPoint = (2, 0)
switch anotherPoint {
case (let x, 0):
    print("on the x-axis with an x value of \(x)")
case (0, let y):
    print("on the y-axis with a y value of \(y)")
case let (x, y):
    print("somewhere else at (\(x), \(y))")
}
// Prints "on the x-axis with an x value of 2"
````

The placeholder constant `x` and `y`temporarily take on one or both tuple values from `anotherPoint`. The value x is assigned to `2`. This switch statement does not have a default case because the final case declares a tuple of two placeholder constants that can match any possible remaining values, making it exhaustive.

### Where

A `where` cause can check for additional conditions,  creating a dynamic filter. 

```swift
case let (x,y) where x==y:
```

`x` and `y` will only match the current value if the where clause's condition is true.

### Compound Cases

Multiple switch cases that share the same body can be combined by writing several patterns after `case`, with a comma between each of hte patterns.

```swift
case "a", "e", "i", "o", "u":
```

When including value blinding, all patterns of a compound case have to include the same set of value bindings, and each binding has to get a vlaue of the same type from all patterns in the compound case, ensuring that the body can always access a value for the bindings.

```swift
case (let distance, 0), (0, let distance):
```

## Control Transfer Statements

These statements can change the order which code is executed:

- `continue`
- `break`
- `fallthrough`
- `return`
- `throw`

### Continue

Tells a loop to stop what it's doing and start again at the beginning of the next iteration. 

```swift
let puzzleInput = "great minds think alike"
var puzzleOutput = ""
let charactersToRemove: [Character] = ["a", "e", "i", "o", "u", " "]
for character in puzzleInput {
    if charactersToRemove.contains(character) {
        continue
    }
    puzzleOutput.append(character)
}
print(puzzleOutput)
// Prints "grtmndsthnklk"
```

### Break

Ends execution of entire control flow statement (in `switch` or loop statement) immidiately.

When used in a `switch` statement, control transfers to the code after the closing brace `{`. This behavior can be used to match and ignore one or more cases in a `switch` statement. Because the `switch` statement is exhaustive and does not allow empty cases, it is sometimes necessary to deliberately match and ignore a case in order to make your intentions explicit. Write a `break` statement in the body of the case you want to ignore. 

```swift
let numberSymbol: Character = "三"  // Chinese symbol for the number 3
var possibleIntegerValue: Int?
switch numberSymbol {
case "1", "١", "一", "๑":
    possibleIntegerValue = 1
case "2", "٢", "二", "๒":
    possibleIntegerValue = 2
case "3", "٣", "三", "๓":
    possibleIntegerValue = 3
case "4", "٤", "四", "๔":
    possibleIntegerValue = 4
default:
    break
}
if let integerValue = possibleIntegerValue {
    print("The integer value of \(numberSymbol) is \(integerValue).")
} else {
    print("An integer value could not be found for \(numberSymbol).")
}
```

Optional binding is used to determine whether the value was found. `possibleIntegerValue` variable has an implicit initial value of `nil` by being an optional type.

### Fallthrough

`switch` statements don't fall through the bottom of each case into the next one. Execution completes as soon as the first matching case is completed (you don't need an explicit `break` statement at the end of every case to prevent fall through). Swift `switch` statements are more concise and predictable, avoiding executing multiple cases by mistake.

If you need C-style fallthrough behavior, use the `fallthrough` keyword:

```swift
let integerToDescribe = 5
var description = "The number \(integerToDescribe) is"
switch integerToDescribe {
case 2, 3, 5, 7, 11, 13, 17, 19:
    description += " a prime number, and also"
    fallthrough
default:
    description += " an integer."
}
print(description)
// Prints "The number 5 is a prime number, and also an integer."
```

Even if the case is executed, it will "fallthrough" and run the `default` case as well (otherwise, directly the next case). 

### Labeled Statements

Sometimes it's useful to be explicit about which loop or conditional statement you want a `break` statement to terminate or the `continue` statement to affect. Mark a loop/conditional statement with a *statement* label. 

A labeled statement is inicated by a label followed by a colon:

```swift
LABEL NAME: while CONDITION {
	STATEMENTS
  break LABEL NAME //this breaks the loop with the same label name
}
```

## Early Exit

`guard` statement executes if the condition is true and continues after the closing brace. `guard` statement always has an `else` clause.

```swift
func greet(person: [String: String]) {
    guard let name = person["name"] else {
        return
    }

    print("Hello \(name)!")
```

Any variables/constants  assigned are available for the rest of the code block that the statement appears in.

If the `else` branch is executed, it must transfer control to exit the code block by using a control transfer statement such as return, break, continue, throw, or `fatalError(_:file:line:)`.

`guard` improves readability of your code. It lets you write the code that's typicaly executed without wrapping it in an `else` block so that it handles a violated requirement. 

## Checking API Availability

Swift checks API availability ensures that you don't accidentally use APIs that are unavailable. If unavailable swift reports an error.

*Use an availability condition* in an `if` or `guard` statement to conditionally execute a block of code to verify that the APIs in that block of code are available:

```swift
if #available(ios 10, macOS 20.12, *) {
	//use iOS 10 APIs on iOS, and use macOS 10.12 APIs on macOs
} else {
	//fall back to earlier iOS and macOS APIs
}
```

The availability condition specifies that in iOS, the body of the `if` statement executes only in iOS 10 and later, or macOS 10.12 and later. `*` argument is required and specifies that on any other platform, the body of the `if` executes on the minimum deployment target specified by your target. 

This condition takes a list of [platform names](https://docs.swift.org/swift-book/ReferenceManual/Attributes.html#ID348) and versions:

```swift
if #available(PLATFORM NAME VERSION, ..., *) {
	STATEMENTS TO EXXECUTE IF APIs ARE AVAILABLE
} else {
	FALL BACK STATEMENTS
}
```



# VI. Functions

*Functions* are named chunks of that performs a specific task. Each has a specfic type: its parameter types and return types. 

## Defining and Calling Functions

*Parameters* are values that the function takes as input. *Return type* is a type of value that the funciton will pass back as output. *Function name* describes the task it performs and you will "call" the function with its name. 

This funtion will take a name as input and return a greeting. It has one input parameter (`String` value) and a return type of `String`:

```swift
func greet (person: String) -> String {
	let greeting = "Hello, "  + person + "!"
	return greeting
}
```

Prefix `func` keyword defines the function. The return arrow `->` followed by the type to indicate the function's return type.

Call the function using its definition: 

```swift
print(greet(person:"Anna"))
```

## Parameters and Return Values

Functions are not required to define input parameters: `func sayHelloWorld() -> String { }.`

Multiple input parameters are separated by commas. `func greet(person: String, alreadyGreeted: Bool) -> String`.

A function can have multiple return values: `func minMax(array: [int]) -> (min: Int, max: Int)`. Access the tuple by using `TUPLENAME.min` or `TUPLENAME.ma`.

An *optional* tuple can be used if the function has a potential to have "no value".

Function implicity returns the expression if the entire body of the function is a single expression.

## Function Argument Labels and Parameters Names

*Argument label* is written before the argument when calling the function; each argument is written in the function call with its argument label before it. The *parameter name* is used in the function. By default, the argument label is their parameter name.

```swift
func someFuction(argumentLabel parameterName:Int) {
	//use parameterName to refer to the argument value
}
```

use `_` if you don't want an argument label: `func someFunction(_ parameterName:int)`

### Default Parameter Values

`func someFunction( parameterWithDefault: Int = 12)` If the default value is defined, you can omit that parameter when calling the function. 

### Variadic Parameters

A *variadic parameter* written by inserting `...` after parameter's type name to to accept zero or more values of that type.

```swift
func arithmeticMean(_ numbers: Double...) -> {
	var total: Double = 0
  for number in numbers {
  	total += number
  }
  return total / Double(numbers.count)
}

//calling the method
arithmeticMean(1, 2, 3, 4, 5)
```

### In-Out Parameters

Changing a value of a parameter within the body of that function results in a compile-time error. If you do want to modify a parameter's value and keep those changes after the call ends, then define that parameter as an *in-out parameter* using the keyword `inout` right before the parameter's type. 

Only variables can be passed as the argument for an in-out parameter, no literals or constants. Place an ampersand (`&`) before a variable's name when you pass it as an argument to indicate it can be modified. Example function:

```swift
func swapTwoInts(_ a: inout Int, _ b: inout Int) {
	let tempA = a
	a=b
	b= tempA
}

//in the body:
var intOne = 3
var intTwo = 4
swapTwoInts(&intOne, &intTwo)
```

## Function Types

Each function has a specific *function type* made up of the parameter types and return type. Example: this function's type is `(Int, Int) -> Int`. Read as "a function that has two parameters, both of type `Int`, and returns a value of type `Int`"
Define a constant or variable to be a function type and assign it a function:

```swift
var mathFunction: (Int, Int) -> Int = addTwoInts //could have been inferred
//and use it later:
print(mathFunction(2,3))
```

Function types can also be used as parameters or return types.

## Nested Functions

You can define functions inside the bodies of other functions. These nested functions are hidden from the outside world but can be called by their enclosing function. The enclosing function can return one of its nested function to be used in another scope.

# IX. Classes and Structures

*Structures* and *classes* are general and flexible constructs used as building blocks. Define properties and methods to  your strucutres and classes using the same syntax to define constants, variables, and functions. 



## Comparing structures and classes

Both structures and classes have the following in common:

- Define properties to store values
- Define methods to provide functionality
- Define subscripts to provide access to their values using subscript syntax
- Define initializers to set up their initial state
- Be extended to expand their functionality beyond a default implementation
- Conform to protocols to provide standard functionality of a certain kind

Classes have additional capabilities but are more complex:

- Inheritance enables one class to inherit the characteristics of another.
- Type casting enables you to check and interpret the type of a class instance at runtime.
- Deinitializers enable an instance of a class to free up any resources it has assigned.
- Reference counting allows more than one reference to a class instance.



**Defining a structure and class:**

```swift
struct Resolution {
	//structure definition
  var width = 0
  var height = 0
}
class VideoMode {
  //class definition
  var resolution = Resolution()
  var framerate = 0.0
  var name: String? //default value nil
}
```

**Structure and class instances:**

```swift
let someResolution = Resolution()
let someVideoMode = VideoMode()
//properties are initialized to their default values
```

**Access properties:**

```swift
//dot syntax
print("Width is \(someResolution.width))
//subproperties:
print(someVideoMode.resolution.width)
```

**Initialize:**

```SWIFT
let vga = Resolution(width: 640, height: 480)
```

All structures have an automatically generated *memberwise initializer*, which initializes the member properties of new structure instances. 

## Structures and enumerations are value types

A *value type* is a type whose valueis copied when it's assigned to a variable/constant or passed to a function. All basic types are value types. Structures and enumerations are value types. 

```swift
let hd = Resolution(width: 1920, height: 1080)
var cinema = hd //A copy of hd was made and assigned to cinema
```

if cinema.width was changed, the hd.width would remain unchanged

## Classes are reference types

*Reference types* are not copied when assigned or passed; the same existing instance is used.

**Identity Operators**

- `===` "identical to" checks whether two constants or variables refer to exactly the same instance of a class. It's different to *equal to*, which means two instances have equal values (which you decide what qualifies as being equal to).
- `!==` "not identical to"

**Pointers**

Swift uses *pointers* to refer to addresses in memory. 

# X. Properties

*Properties* associate values with a particular class, structure, or enumeration. They typically have a particular type.



## Stored properties

*Stored properties* store constant ("constant stored properties") and variable values ("value stored properties") as part of an instance. Introduce with `var` or `let` keyword.

Default value can be set as part of its definition. Stored property value can be set or modified during initialization:

```swift
struct FixedLengthRange {
	var firstValue: Int
	let length: Int
}
var exampleRange = FixedLengthRange(firstValue: 0, length: 3)
exampleRange.firstValue = 6;
//length cannot be changed because it is a constant
```

### Lazy stored properties

A property whose initial value is not calculated until the first time it is used. Indicate a lazy stored property using `lazy` modifer before its declaration (must be a variable).

Use when the property is dependent on outside factors that are known only after the instance's initialization.

## Computed Properties

*Computed properties* calculate a value. They provide a getter and an optional setter to retrieve and set other properties and values indirectly.

```swift
struct Point {
    var x = 0.0, y = 0.0
}
struct Size {
    var width = 0.0, height = 0.0
}
struct Rect {
    var origin = Point()
    var size = Size()
    var center: Point {
        get {
            let centerX = origin.x + (size.width / 2)
            let centerY = origin.y + (size.height / 2)
            return Point(x: centerX, y: centerY)
        }
        set(newCenter) {
            origin.x = newCenter.x - (size.width / 2)
            origin.y = newCenter.y - (size.height / 2)
        }
    }
}
var square = Rect(origin: Point(x: 0.0, y: 0.0),
                  size: Size(width: 10.0, height: 10.0))
let initialSquareCenter = square.center
square.center = Point(x: 15.0, y: 15.0)
print("square.origin is now at (\(square.origin.x), \(square.origin.y))")
// Prints "square.origin is now at (10.0, 10.0)"
```

### Read-only computer properties

Returns a value, but cannot be set to a different value:

```swift
struct Cuboid {
	var width = 0.0, height = 0.0, depth = 0.0
	var volume: Double {
		return width*height*depth
	}
}
```

## Property Observers

*Property observers* can monitor changes in a property's value, and respond with custom actions.

Cannot be added to lazy stored properties. Can be added to inherited properties.

- `willSet` is called before the value is stored. The passed new property value acts as a constant parameter which you must specify a name for (default name `newValue`)
- `didSet` is called immediately after new value is stored. (Default name `oldValue`)

```swift
class StepCounter {
    var totalSteps: Int = 0 {
        willSet(newTotalSteps) {
            print("About to set totalSteps to \(newTotalSteps)")
        }
        didSet {
            if totalSteps > oldValue  {
                print("Added \(totalSteps - oldValue) steps")
            }
        }
    }
}
```



## Property Wrappers

*Property wrapper* manages how a property is stored and the code that defines a property.

`TwelveOrLess` structure ensures the value it wraps is always 12 or less:

```swift
@propertyWrapper
struct TwelveOrLess {
  private var number: Int
  init() { self.number = 0 }
  var wrappedValue: Int {
    get { return number }
    set { number = min(newValue, 12) } //stores 12 if larger than 12.
  }
}
```

Now apply this wrapper to a property by writing the wrapper's name before the property:

```swift
struct SmallRectangle {
	@TwelveOrLess var height: Int
	@TwelveOrLess var width: Int
}
```

When you apply a wrapper to a property, the compiler synthesizes code that provides storage for the wrapper and code that provides access to the property through the wrapper

### Initial value for wrapped properties

Codes that use this property wrapper can't specify a different initial value for the property that's being wrapped, so you need to create a initializer for the property wrapper. Expanded version of `TwelveOrLess`:

```swift
@propertyWrapper
struct SmallNumber {
    private var maximum: Int
    private var number: Int

    var wrappedValue: Int {
        get { return number }
        set { number = min(newValue, maximum) }
    }

    init() {
        maximum = 12
        number = 0
    }
    init(wrappedValue: Int) {
        maximum = 12
        number = min(wrappedValue, maximum)
    }
    init(wrappedValue: Int, maximum: Int) {
        self.maximum = maximum
        number = min(wrappedValue, maximum)
    }
}
```

When you apply it to a property but don't specify initial value, `init()` is used. When initial value is specified, `init(wrappedValue:)` is used to set up the wrapper. `=1` is translated to a call to `SmallNumber(wrappedValue: 1)` here:

```swift
struct UnitRectangle {
    @SmallNumber var height: Int = 1
    @SmallNumber var width: Int = 1
}
```

To use `init(wrappedValue:maximum:)` :

```swift
struct NarrowRectangle {
    @SmallNumber(wrappedValue: 2, maximum: 5) var height: Int
    @SmallNumber(maximum: 9) var width: Int = 1
  	//specied initial value using assignment
}
```



### Projecting value from property wrapper

A property wrapper can define a *projected value* that can be accessed by putting a dollar sign (`$`) in front of the name of the wrapped value. 

If a `var projectedValue: bool` was added to `SmallNumber` property wrapper and is used like this:

```swift
struct SomeStructure {
	@SmallNumber var someNumber: Int
}

print(someStructure.$someNumber)
//would access the wrapper's projected value
```

## Global and Local Variables

Global variables are variables defined outside of any function, method, closure, or type context. Local variables are variables defined within a closure context.

*Stored variables* provide storage for a value of a certain type and allow that value to be set and retrieved.

*Computer variables* define observers for stored variables. They calculate their value rather than storing it, written in teh same way as computed properties.

## Type Properties

*Type properties* are properties associated with the type itself, not to any one instance of that type. There can only be one copy of these properties. Used to define values that are universal to *all* instances of a particular type (like a constant that all instances can use). 

Type properties are written as part of the type's using the `static` keyword. For compute type properties that can be overriden by subclasses, use the `class` keyword instead:

```swift
class SomeClass {
	static var storedTypeProperty = "some value"
	static var computedType Property:Int {
		return 27
	}
	class var overridableComputedTypeProperty: Int {
		return 107
	}
}
```



### Querying and setting

Type properties are queried and set using the dot syntax.

```swift
SomeClass.storedTypeProperty = "another value"
```

Notice the new value was set on the *type* (`SomeClass`), and not on an instance of `SomeClass`

# XI. Methods

*Methods* are functions associated with a particular type. Classes, structures, and enumerations can all define instance or type methods.

## Instance Methods

*Instance Methods* are functions that belong to instances of a particular class, structure, or enumeration. An instance method has implicit access to all other instance methods and properties of that type.

This  `Counter` class has three instance methods.:

```swift
class Counter {
    var count = 0
    func increment() {
        count += 1
    }
    func increment(by amount: Int) {
        count += amount
    }
    func reset() {
        count = 0
    }
}
```

These instance methods are called using dot syntax:

```swift
let counter = Counter()
counter.increment(by: 5)
counter.reset()
```

### Self property

Every instance of a type has an implicit property called `self` which is the instance itself. Use it to refer to the current instance within its own instance method:

```swift
func increment() {
	self.count +=1
}
```

Often assumed that `count` refers to `self.count`. When parameter name of a method has teh same name as a property of that instance, then the `self` property refers to the property of the instance. 

### Modifying value types

Strucutres and enumeration are *value type*, meaning that its properties cannot be modified within its instance methods. However, if you do need to modify the properties of your strucutre or enumeration, you utilize *mutating* behavior for that method. Now, the method can mutate ("change") its properties from within the method. 

Place the `mutating` keyword before the `func` keyword:

```swift
struct Point {
	var x = 0.0, y = 0.0
	mutating func moveBy (x deltaX: Double, y deltaY: Double) {
		x += deltaX
		y += deltaY
	}
}
```

The mutating `moveBy(x:y:)` method modifies the point on which it was called instead of returning a new point. Calling a mutated method on a constant would not work.

### Assigning to self within a mutating method

Use mutating methods to to assign a new instance to `self` property.

Same `Point` example can be written like this:

```swift
struct Point {
	var x = 0.0, y = 0.0
	mutating func moveBy (x deltaX: Double, y deltaY: Double) {
		self = Point(x: x+deltaX, y: y+deltaY)
	}
}
```

You could use `self` to be a different case from the same enumeration. This code switches cycles between three different power states when `next()` is called:

```swift
enum TriStateSwitch {
    case off, low, high
    mutating func next() {
        switch self {
        case .off:
            self = .low
        case .low:
            self = .high
        case .high:
            self = .off
        }
    }
}
```

## Type Methods

Define methods that are called on teh typ eitself by writing `static` keyword (or `class` for classes) before `func`.

Type methods are called with dot syntax on the type:

```swift
class SomeClass {
    class func someTypeMethod() {
        // type method implementation goes here
    }
}
SomeClass.someTypeMethod()
```

Inside a type method, `self` property refers to the type itself, and not the instance. A type method can call another type method using just the method's name (no prefix).

`@discardableResult` attribute marks functions that have a return value that can be ignored.

# XIII. Inheritance

A class can *inherit* characteristics from another class. This class will be known as the *subclass* and the class it inherits from is known as its *superclass*. 

Inheritance is a fundamental behavior that is unique to the class type. Classes can call and access methods, properties, and subscripts belonging to their superclass or override them. 

Property observers can be added to inherited properties.

## Defining a Base Class

Any class that does not *inherit* is known as a *base class*.

This `Vehicle` class defines common characteristics for an arbitrary vehicle. Needs to be refined:

```swift
class Vehicle {
	var currentSpeed = 0.0
  var description: String {
    return "travelling at \(currentSpeed) miles per hour"
  }
  func MakeNoise() { }
}

//create new instance with initializer syntax
let someVehicle = Vehicle()
```

## Subclassing

A subclass will inherit characteristics that can be refined and you can add new characteristics.

Indicate a subclass has a superclass by writing the subclass name before the superclass name, separated by a colon:

```swift
class SomeSubclass: SomeSuperclass {}
```

`Bicycle` will be a subclass of `Vehicle`:

```swift
class Bicycle: Vehicle {
	var hasBasket = false
}
```

Subclasses can be subclassed. A tandem is a two-seater bicycle:

```swift
class Tandem: Bicycle {
	var currentNumberOfPassengers = 0
}
```

## Overriding

A subclass uses *overriding* to provide its own custom implementation of a method, property, or subscript. 

Prefix overriding definition with `override` keyword. It prompts the compiler to check that your overriding class's superclass has a declaration that matches the one you provided.

### Accessing Superclass 

Access the superclass version of the method, prefix, or subscript using the `super` prefix.

- `super.someMethod()` can be called within the overriden method named `someMethod()`. 
- Overriden proeprty `someProperty` can access superclass version as `super.someProperty` within the overriding getter or setter implementation.

### Overriding Methods

Provide a tailored or alternative implementation of the method within your subclass.

A new subclass of `Vehicle` called `Train`:

```swift
class Train: Vehicle {
	override func makeNoise() {
		print("Choo choo")
	}
}
```

### Overriding Properties

Provide custom getter and setter for that property, or to add property observers to enable the overriding property to observe when the underlying property value changes

An inherited read-only property can be presented as a read-write property by providing a getter and setter. You cannot do the opposite.

`Car` is a subclass of `Vehicle` which modifies the `description` property:

```swift
class Car: Vehicle {
    var gear = 1
    override var description: String {
        return super.description + " in gear \(gear)"
    }
}
```

**Override property observers**

The `AutomaticCar` class represents a car with an automatic gearbox:

```swift
class AutomaticCar: Car {
    override var currentSpeed: Double {
        didSet {
            gear = Int(currentSpeed / 10.0) + 1
        }
    }
}
```

Now, whenever `currentSpeed` is set, the `gear` property is also set.

## Preventing Overrides

Prevent a method, property, or subscript from being overriden by marking it as *final*. the `final` modifier is placed before the introducer keyword (`final var`, `final func`, `final class func`, or `final subscript`)

Attempts to override will report as a compile-time error.

An entire class can be marked final by writing `final` before `class` keyword in class definition. Any attempts to subclass will not work.

# XIV. Initialization

*Initialization* is the process of preparing an instance of a class, structure, or enumeration for use. Sets up for the instance to be ready to use.

## Setting Initial Values for Stored Properties

All stored properties *must* have an initial value.

**Initializers** are called to create a new instance. Written using the `init` keyword:

```swift
init() {
  //perform initializations here
  //you can set initial values here
}
```

**Default property values** specified as part of the declaration:

```swift
struct Fahrenheit {
	var temperature = 32.0
}
```

## Customizing Initialization

*Initialization parameters* defines values that customizes the initialization process.

Two custom initializers can be used for `Celsius` structure. Last initializer has a clear intent without argument label:

```swift
struc Celsius {
	var temperatureInCelsius Double
		init(fromFahrenheit fahrenheit: Double) {
    	temperatureInCelsius = (fahrenheit - 32.0) / 1.8
    }
    init(fromKelvin kelvin: Double) {
    	temperatureInCelsius = kelvin - 273.15
    }
  	init(_ celsius: Double) {
      temperatureInCelsius = celsius
    }
}
```



## Default Initializers

## Class Inheritance and Initialization

## Failable Initializers

## Required Initializers

## Setting a Default Property Value with a Closure or Function