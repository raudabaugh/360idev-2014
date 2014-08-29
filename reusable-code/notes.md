# Writing Reusable Code - [Daniel Pfeiffer](http://twitter.com/mediabounds)

## Reusable code is...
* Not (necessarily) code that is distributed through static libraries or CocoaPods
* Code with a lifecycle beyond a given project
* Able to completely fulfill its responsibility inside your app
* Maintainable without being rewritten

## Benefits of code reuse mindfulness
* Not solving the same problems time and time again
* Saving time in development and testing
* Frees up budget to allocate towards advancing your or your company's capabilities

## Principles
### Loose Coupling
* Each component should know as little as possible - if anything at all - about surrounding components
* Reduces dependencies
* Prevents changes from having unanticipated consequences
* Can use protocols - not just for delegates, but for the developer and compiler. They define expected behavior of object, promote agnosticism between classes.
* Protocol Example - File Retrieval from Dropbox, Google Drive, Box
* Easier to add functionality when it impacts fewer members
* Can use generics in Swift

#### Evidence of Tightly Coupled Code
* When changes in one component force updates in many other components
* When fixing one bug introduces three more

### Superclassing
* Focus on solving the problem at hand
* Create reusable code through refactoring
* Don't waste time with unneeded architecture
* Example: Core Data Table View Controller

#### Where Inheritance Doesn't Help
* When you don't know / don't trust the parent implementation
* When you can't reuse functionality because you can't subclass the class containing the functionality
* When the parent contains functionality irrelevant to its children
* When children are simply enabling/disabling functionality of the parent

#### Problems with Pre-emptive Subclassing
* Produces over-engineered solutions by "solving" problems that never existed
* Adds unneeded layers of complexity
* Paralysis by analysis
* Do not equate a tall inheritance tree with good architecture

### Composition
* SRP - every context should have a single responsibility, and that responsibility should be entirely fulfilled by the context
* You must determine the strictness of "single responsibility" definition (e.g. "talk to server" vs. "talk to single API endpoint") - specificity could change as project matures
* Can use categories - add function to a base class that can be available for all instances - e.g. Foundation class (shuffle/sort NSArray)
* Can use protocols - delegate out-of-scope responsibilities, separate content from behavior, inheritance is not a means to customize content
* Model-View-View Model encourages composition by moving presentation logic closer to the model

### Documentation
* Not just for others - helps you understand your code by formalizing responsibilities of various contexts
* Forces you to ask prodding questions that may uncover hidden edge cases
* Helps you remember what you were thinking when you wrote it the first time

## Summary
* Focus on solving actual problems
* Find and remove unneeded dependencies
* Work backwards - refactor into reusable code
* Don't use inheritance to customize content
* Achieve full functionality by compositing several classes, each with discrete responsibility
* Define responsibilities and behaviors in your app; organize code accordingly
* Document your code

## Resources
* Good Intentions - Jay Thrash (360iDev 2014)
* How I Discovered MVVM (360iDev 2014)