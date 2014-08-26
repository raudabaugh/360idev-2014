Cocoa Design Patterns in Swift - [Michele Titolo](http://twitter.com/MicheleTotolo)
==============================

New Language Features
---------------------
* Tuples: group multiple values into single compound value
* Generics (<T>) - create functions without declaring type
* Closures: like blocks but better
* let: immutable
* "if let" statements can be powerful
* Structs: first class citizens, pass by value
* Enums: pass by value
* Structs + Enums can have methods, conform to protocols

Functional Patterns
-------------------
* Function Passing is one functional pattern that is core to Swift development
* Means you can treat functions as objects
* Pass functions into functions
* Return functions from functions

Patterns
--------
* Composition
### Protocols
* Cuts down on duplicated functionality caused by creating classes for everything in ObjC-land
### Factories
* Abstract away object creation and composition
* Flexibility because you can return functions that retain state
### Command
* A delegate chain that returns a function
* Functions are more explicit than closures and more flexible (can be nested)
### Enumerations
* New operations on collections - sorting, etc.
* No more NSPredicates!
### Encapsulation
* Cut down on number of needed functions by packaging things together (e.g. with tuples)

Anti-Patterns
-------------
* Implementing some protocols can still be messy (e.g. table view data source)
* Avoid temptation to use tuples everywhere
* Operator overloading can make code harder to read
* Be careful with AnyObject - be explicit where you can

Summary
-------
* Swift gives us a lot of new tools but working with Obj-C (e.g. protocols) will be around 
for awhile
