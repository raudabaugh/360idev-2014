# Making Apps Dynamic - [Andria Jensen](http://twitter.com/andriajensen)

## Getting Started
* Create UIDynamicAnimator with reference view (e.g. view controller's entire view)

## UISnapBehavior
* Snaps view to a specified point like a spring
* Higher damping value means lower springiness
* Adding behavior to the animator triggers a single snap

## UIGravityBehavior
* Standard UIKit gravity: 1 = 1000 points/second^2
* gravityDirection: default is 0, 1 for a standard downward force
* (angle & magnitude) OR gravityDirection
* Only one allowed per animator

## UIPushBehavior
* A continuous or instantaneous force
* Similar to gravity behavior, but takes view size into account
* Adjust (angle & magnitude) OR pushDirection
* UIKit Newton measurement - 1N = Force to move a 100x100 view at 100 pixels/second^2
* Use the active property to turn a push behavior on/off

## UIAttachmentBehavior
* Anchors an item to a specific point, or another item
* Can adjust length, frequency, damping
* Think of attachments like springs between items
* Default attachment point is item's center
* Use with gestures to make moving views around easy

## UICollisionBehavior
* Collisions between boundaries or items
* Uses translatesReferenceBoundsIntoBoundary to make your reference view's frame the boundary
* Use collisionMode to specify whether items collide with boundaries, other items, or both
* Multiple collision behaviors can be added to an animator
* Use UICollisionDelegate to know when collisions occur

## Composite Behaviors
* Combine sveral behaviors
* Use UIDynamicBehavior subclass
* addChildBehavior