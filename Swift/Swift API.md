# Fundamentals

- Diesgn APIs to make the uses of entities (like methods and properties) clear and concise. 
- Clarity is more important than being compact. 
- Write a documentaiton comment for every declaration.
- If you have trouble describing your API's functionality, you designed the wrong API.

## Swift's dialect of markdown

Markup reference: https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/

1. Begin with summary that describes the entity. 

   ```swift
   /// Returns a "view" of `self` containing the same elements in
   /// reverse order.
   func reversed() -> ReverseCollection
   ```

   Use a single sentence *fragment* ending with a period. Or form summaries using multiple sentence fragments separated by semicolon.  

   Describe what the function/method *does* and what it *returns*.

   Thinka bout what the entity *is*, what a subscript *accesses*, or what the initializer *creates*.

2. Continue with paragraphs and bullet items.![Screen Shot 2020-07-06 at 2.32.35 PM](/Users/trxn/Library/Application Support/typora-user-images/Screen Shot 2020-07-06 at 2.32.35 PM.png)

# Naming

## Clear Usage

Remove ambiguity but also needless words that repeat type information. For example a function named `remove()` would be better than `removeElement()`.

Name variables, parameters, and associated types according to their role rather than their type constraints. `var string` should e named `var greeting` to optimize clarity and expressive and describes the entity's *role*, not its *type*.

Compensate for weak type information. To add clarity, precede each weakly typed parameters with a noun describint its role. Change `func add(_observer: NSObject, for keyPath: String)` to `func addObserver(_ observer:NSObject, forKeyPath path: Stirng)`.

## Fluent Usage

Use grammatical English phrases for method and function names. `insert(y, at: z)` reads like english compared to `x.insert(y, position: z)`.

Begin names of factory methods with "make" , e.g. `x.makeIterator()`. Its first arguments to these calls should not form a phrase starting with the base name like this: `x.makeWidget(havingGearCount: 42, andSpindleCount: 13)`. It should be like this `x.makeWidget(gears: 42, spindles: 13)`.

Name functions and methods according to their side-effects. Those who have side-effects should read as imperitave verb phrases and those without shoudl read as noun phrases.

Mutating and nonmutating method pairs should be named consistently. Mutating: `x.sort()` and `y.formUnion(z)` ; nonmutating: `x.sorted()` (past participal) and `y.union(z)`.

Boolean methods and properties should read as assertions, e.g. `x.isEmpty` or `line1.intersects(line2)`.

Protocols that describe *what something is*, types, properties, variables, and constants should read as nouns. Protocols that describe a *capability* should be named usign suffixes (`able`, `ible`, or `ing`)

## Use Terminology Well

- Avoid obscure terms: use "skin", not "epidermis".
- Terms of art are unecessary. Use the most common word. Only go technical if *precisely* expresses something ambiguous or unclear.
- No abbreviations
- Embrace precedent. `sin(x)` is commonly used so no need to use the word `sine`.

# Conventions

## General Conventions

- Document the complexity of any computed property that is not O(1)
- Prefer methods and properites to free functions.
  - Free functions only used (1) when there's no obvious `self`: `min(x,y,z)`, (2) when function is inconstrained generic: `print(x)`, or (3) when function syntax is part of established domain notation: `sin(x)`.
- Names of types/protocols are `UpperCamelCase` and everything else is `lowerCamelCase`.
- Methods share base names when they share the same meaning or when they operate in distinct domains. 
  - `func contains(_ other: Point) -> Bool {...}` and `func contains(_ other: Shape) -> Bool {...}` are fine because the methods do the same thing.
  - an `index()` function that rebuilds the search index and an `index(_, inTable)` function which returns the nth row in a given table are not okay because these methods have different semantics.

## Parameters

`func move(from start: Point, to end: Point)`

- Choose names to serve documentation. Should be make documentation read naturally.

- Use defaulted parameteres when it simplifies common uses.

  - ```swift
    public func compare(
    	_ other: String, options: CompareOptions = [],
    	range: Range? = nil, locale: Locale? = nil
    	) -> Ordering
    ```

  - Having members of a method family means excessive documentation (that would be identical) so a single method with defaults is much better.

- Put parameters with defaults towards the end because they are less essential and provide stable initial pattern when invoked.

## Argument Labels

```swift
func move(from start: Point, to end: Point)
x.move(from x, to: y)
```

- Don't use labels when arguments can't be distinguished like `min(num1, num2)`.
- Initializers that perform value preserving type conversions don't need the first argument label: `Int64(someuInt32)`.
  - Exception when the first 2 arguments represents parts of a single abstraction: `a.moveTo(x: b, y: c).
- If first argument forms part of a grammatical phrase, omit labels: `x.addSubview(y)`.

# Special Instructions

- Lable tuple members and name closure parameters where they appear. 
  - Names have explanatory power and can be referenced from documentation comments.
- Take extra care with unconstrained polymorphism (e.g. `Any`, `AnyObject`) to avoid ambiguities.
  - Eliminate the ambiguity by naming it more explicity (with argument label).

