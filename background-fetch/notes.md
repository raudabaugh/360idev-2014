# Background Fetch - [Mike Oliver](http://twitter.com/moliver816)

## What is background fetch?
* Wakes your app periodically throughout the day
* Optimized around network calls and phone usage

## The Rise of the Silent App
* "A whole class of apps that don't need to be opened at all to add value" - Matthew Panzarino
* "Now some apps are disappearing altogether" - Mary Meeker

## Runkeeper Breeze
* Needed to access the Steps API, uses BG Fetch

## The Basics


### Get Started
* Turn it on (checkbox in Xcode)
* Do something in performFetchWithCompletionHandler:(void (^)(UIBackgroundFetchResult result))completionHandler

### Careful...
* "When background fetch is enabled you are essentially building a botnet"

## Lessons Learned

### Testing
* Debug -> Simulate Background Fetch

### App Lifecycle
* didFinishLaunchingWithOptions can get called
* viewDidLoad, viewWillAppear, viewDidAppear can get called
* Check for UIApplicationStateBackground in shared application

### Analytics
* Every background fetch will count as a session and screw up numbers

### Avoid the Keychain
* Device may be locked or have just unlocked, which can block keychain access
* You only have 30 seconds, don't want to spend it waiting on keychain access

### Frequency of Fetches
* 20-40x / day
* Optimized to be more likely to happen when user is engaged with phone (unlocking, checking email, connecting to WiFi)
* Can reasonably predict when the user wakes up

## Turn it Up to 11 
### Disclaimer
* With great power...
* Battery life
* Data plan costs
* Privacy

### Query Battery Life and State
* UIDevice batteryLevel/batteryState properties
* If battery is high/charging, go to town
* If battery is low, reduce fetch frequency

### Check Reachability
* If user is on Wifi, download all the things!
* If not, tread carefully

### Get More Time
* Create a Background Task for operations > 30 seconds

### Local Notification
* Firing a local notification with background fetch saves you backend architecture hassle
* Neanderthal debugging - hard to debug background fetch issues with breakpoints, so you may have to fire local notifications

### Fetching Local Info
In addition to the network, you might query:

* M7 (is the user walking, driving, etc)
* Calendar (is the user in a meeting)
* Address Book
* Recent Photos
* Reminders
* Don't forget privacy
* Make sure first-time permissions prompts are fired when user is actively using your app

### Update Your Multitasking Screenshot
* When Background Fetch finishes, your multitasking screenshot is updated
* First thing users see when they return to the app
* Part of your 30 seconds
* If you go beyond the 30 seconds, the OS treats it as a crash, and your user will be starting the app from scratch

### HealthKit and HomeKit
* HealthKit Notification "You burned X calories today, way to go"
* HomeKit Notifications "You left your lights on" or "Phone is fully charged, turning off outlet"