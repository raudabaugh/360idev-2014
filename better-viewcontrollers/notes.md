Good Intentions - A Path to Building Better ViewControllers - [Jay Thrash](http://twitter.com/jaythrash)
===========================================================

* Lost our MVC way - Misused/Mistreated View Controllers
* Think of delegate as a verb rather than delegate as a noun - VCs should delegate more to
other classes
* Too much responsibility on the VC leads to code that is harder to test, maintain, and reuse

2 Principles
------------
* Separation of Concerns
* Single Responsibility Principle

3 Techniques
------------
* Stores - encapsulates access to external sources of data
* Delegate(v) the DataSources
* Intentions

Stores
------
* Big Nerd Ranch iOS book talks about MVCS (Model View Data Store)
* Manage shared resources - data loading/caching, system resources
* Usually implemented as singletons

### Candidates for Stores
* Web Services
* Databases
* Filesystem
* Location/Motion Services
* Camera

Delegating the DataSources
--------------------------
* A lot of tutorials put all responsibility on TVC. Valid way of doing it, but cumbersome for
complex apps
* ViewController -> DataSource -> Backing Store (@[x, y, z], plist, CoreData)
* Easier to test a Data Source that is encapsulated in its own object without instantiating VC

Intentions
----------
* Can encapsulate IBActions, IBOutlets, form entry into an Intention object
* Add as custom NSObjects to View Controller Scene in Interface Builder (generic orange cube)

References
---------
* [Lighter View Controllers (objc.io Issue #1)](http://www.objc.io/issue-1/lighter-view-controllers.html)
* [Bendyworks - SRP & iOS](http://bendyworks.com/single-responsibility-principle-ios/)
* [Chris Eidhof - Intentions](http://chris.eidhof.nl/posts/intentions.html)
