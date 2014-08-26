Offline is Not a Special Case - [Daniel Pfeiffer](http://twitter.com/mediabounds)
=============================

* UX should not be conditional on internet connections
###### Exceptions
* Action must be immediately verified by an authority (e.g. bank)
* Stale data could impact behavior of user (e.g. stock app)
* Timeliness of the data is important (e.g. password change)
* Attempting to control another device in real time (e.g. thermostat)

Retrieving Data From Server
---------------------------
### Problems
* Mixing business logic with ViewController - VC should not be managing data freshness
* Error messages may get in the way
* Inefficient in managing data - requests too frequently or not at the right time
* Allows factors out of our control to directly impact UX - leaves too much up to luck

### A Better Approach
* Store server responses in a local db/cache first
* Process (e.g. JSON parse) in a background queue

### When should you get fresh data? It depends.
* Predefined interval
* App comes to foreground
* Response to push notification
* User requests

### How to keep views fresh on new data
* Key Value Observing (KVO), ReactiveCocoa, NSNotification
* Do not interrupt the user by moving stuff (e.g. remember their scrollview position)

Sending Data To Server
----------------------
* User input goes directly into local cache
* Sync when you can - difficult so try not to overdo it

### Strategies
* Send entire data set to server and let the server sort it out (only for small datasets)* 
##### Add a sync flag to your data model that indicates whenever an object has been changed
* Find all models that need synced/deleted
* Change sync flag or delete model after server response
##### Create a queue of changes to send to the server
* FIFO of operations persisted to disk so it can be rebuilt, remove them after they succeed

API Considerations
------------------
### Many small requests or one large request? It depends.
* Each request comes with overhead (delegates, coordination, management)
* Large response could be progressively parsed as it arrives
* Easier to handle failure of one response than one out of many
* Rule of thumb: about 1 request per screen of your app

### Strategies for Managing Content
* Use UUIDs
* Design endpoints to be able to update multiple objects with one request

### Entity tags or content hashes (revision ID) are better than timestamps
* Could be MD5 hash of the response
* User clock is not absolutely trustworthy
* Provides a way to manage data concurrency
* Use HTTP/1.1 ETag and If-None-Match headers on your server to compare content

When Things Go Wrong
--------------------
* Keep what data you can so you can resume later (e.g. large video download fails partway) 
* Error handling is part of your app architecture
* Always handle network errors immediately, do not TODO them for later
* Ugly, informative errors are better than vague, catch-all messages for your support team
* Report error occurrences to your analytics service

Summary
-------
* Being offline is not the only scenario where your app cannot communicate with server
* Views should only be built with local data
* User input should be immediately stored in a local database and synced later
* Take advantage of iOS 7+ features like background fetch
* Use entity tags to identify data states
* Error handling is part of your app architecture
* Offline is not the special case

Other Resources
---------------
* Background Fetch on Steroids (360iDev 2014 session)
* Building Connected Apps with Mobile Services (360iDev 2014 session)
* [Mastering Mobile Learning book from Float Mobile Learning](http://floatlearning.com/book/mastering-mobile-learning/)
* [float.ly/360idan](http://float.ly/360idan)
