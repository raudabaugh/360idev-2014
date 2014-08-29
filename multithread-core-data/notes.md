# Multi-threaded Core Data Done Right - [Andrew Morrow](http://twitter.com/morrowa_de)

## Goals
1. **Never** block UI interaction
2. Efficiently handle large datasets
3. Display updated data immediately
4. Avoid data merge conflicts

## Concerns
* Move JSON parsing and saving to a background queue
* Instead of using shared app delegate managed object context, create a new one with PrivateQueueConcurrencyType - used for background tasks
* When Core Data begins a save operation, it locks the level of the stack immediately above the context it's changing
* Since the background save operation blocks the persistance store coordinator, we need a separate one for the main thread

## Write-Ahead Logging
* SQLite will allow multiple reads along with one concurrent write
* This journal mode is enabled by default in iOS 7+

## Updating the Main Thread
* Batch fetch requests
* Batched saves
* Add a completion block and use NSNotification to notify your main thread that changes are ready to be merged
* Call reloadData on your TableView
* The reloadData approach could be problematic when there are dynamic cell heights based on the data
* Can be solved by going to a single writer queue

## Summary

* Let SQLite handle your concurrency
* Only allow one concurrent write
* Keep your main thread read-only

## Reference
* Tim Eisted "Core Data Performance" WWDC 2013