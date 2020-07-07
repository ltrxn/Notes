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

