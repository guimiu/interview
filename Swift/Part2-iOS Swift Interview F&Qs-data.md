[TOC]

## What is UIApplicationDelegate? 
It is the main point of entry into iOS apps. 
It is a protocol that get notified user for events such as 
    - app launch, 
    - app goes into background or foreground, 
    - app is terminated, 
    - a push notification was opened, etc.

## How to create an appDelegate object? 
```swift
let appDelegate = UIApplication.shared.delegate as! AppDelegate 
```

## What is AppDelegate LifeCycle? 

[life cycle](https://docs-assets.developer.apple.com/published/c63cd35863/4d403429-fa30-4706-863f-5e3617ee21d0.png)

`application: willFinishLaunchingWithOptions:-> Bool`. 
> Used for initial application setup. 

**Launch Methods:**  
`application: didFinishLaunchingWithOptions: -> Bool` 
> Called when an application has finished launching and restored state and can do final initialisation such as creating UI. 

`applicationWillEnterForeground:`  
> Called after application: didFinishLaunchingWithOptions: 
> or if your app becomes active again after receiving a phone call or other system interruption. 

`applicationDidBecomeActive:` 
> Called after applicationWillEnterForeground: to finish up the transition to the foreground. 

**Termination Methods:**  
`applicationWillResignActive:`
> Called when the app is about to become inactive
- The phone receives a call or 
- User hits the Home button 

`applicationDidEnterBackground:`
> Called when your app enters a background state. 
> You have approximately five seconds to run any tasks you need to back things up  after it the app gets terminated automatically. 

`applicationWillTerminate:`
> This is called when your app is about to be purged from memory. Call any final cleanups here. 

## What is the View controller Life Cycle? 
`loadView`
> This method is used when view Controllers are created from code . 

`viewDidLoad:` 
> It's Called When all the views are loaded. Some common tasks in this method :
- Network call which needs Once. 
- User Interface 
- Others Task Those are Need to do Once 

`viewWillAppear:` 
> Called every time before the view are visible to and before any animations are configured. 
Task done in this methods like:
- Displaying the view such as to hide fields or disable actions before the view becomes visible.

`viewWillLayoutSubviews:` 
> It doesn't do anything by default. When a view’s bounds change, the view adjusts the position of its subviews. View controller can override this method to make changes before the view lays out its subviews. 

`viewDidLayoutSubviews:`
> Called after the viewController has been adjust to its subview following a change on its bound. Add code here if you want to make change to subviews after they have been set. 

`viewDidAppear:` 
> Called after the view present on the screen. Example : save data to core data or start animation or start playing a video or a sound, or to start collecting data from the network. 

`viewWillDisappear:` 
> Called before the view is removed from the view hierarchy. 
- Add code here to handle timers, 
- ide the keyboard,  
- cancel network requests,  
- revert any changes to the parent UI. 

`viewDidDisappear:` 
> Called after the VC’s view has been removed from the view hierarchy. 
Use this method to stop listening for notifications or device sensors. 

`deinit` 
> Before a view controller is removed from memory, it gets deinitialized. 
Override `deinit()` to clean resources that the view controller has allocated that are not freed by ARC. 

`didReceiveMemoryWarning` 
> When memory starts to fill up, iOS does not automatically move data from memory to its limited hard disk space. You are responsible for clearing some objects out of memory. It can be a case of crash to the end user. 

`viewWillTransition(to:with:)` 
> When the interface orientation changes, UIKit calls this method on the window’s root view controller before the size changes are about to be made.

## Difference Between AppDelegate & SceneDelegate Class Life Cycle Methods In Xcode 11 iOS 13. 
**Before iOS version 13:** 
> AppDelegate class manages all the iOS app’s life cycle methods (Process Lifecycle + UI Lifecycle) 

**iOS version 13:** 
> AppDelegate: Manages the app’s **Process Lifecycle** methods. 

```swift
optional func applicationDidBecomeActive(_ application: UIApplication)
optional func applicationWillResignActive(_ application: UIApplication)
optional func applicationDidReceiveMemoryWarning(_ application: UIApplication)
optional func applicationWillTerminate(_ application: UIApplication)
...
```

> SceneDelegate: Manage the app’s **UI Lifecycle** methods.

```swift
optional func sceneDidBecomeActive(_ scene: UIScene)
optional func sceneWillResignActive(_ scene: UIScene)
optional func sceneWillEnterForeground(_ scene: UIScene)
optional func sceneDidEnterBackground(_ scene: UIScene)
...
```

## AppDelegate Class Functions for iOS13. 
```swift
func application(_ application: UIApplication, configurationForConnecting connectingSceneSession: UISceneSession, options: UIScene.ConnectionOptions) -> UISceneConfiguration
```
> This function is called when it creates a session object for this scene. 

```swift
func application(_ application: UIApplication, didDiscardSceneSessions sceneSessions: Set<UISceneSession>)
```
> This function is called when a user discards a scene session. 

## SceneDelegate Class UI LifeCycle Methods.
```swift
// Used to refer to the scene UI window. iOS app can has multiple scenes. 
var window: UIWindow? :  

// Called when this scene is initialized and connect to the window. 
// You can create the root view controller object and assign the root view controller object to the SceneDelegate class’s window property in this function.
func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions):  

// Called when the scene transit from background to foreground.
func sceneWillEnterForeground(_ scene: UIScene):  

// Called when the scene state is changed from inactive to active.
func sceneDidBecomeActive(_ scene: UIScene):  

// Called when the scene state is changed to inactive from active.
func sceneWillResignActive(_ scene: UIScene):  

// Called when the iOS app enters the background.
func sceneDidEnterBackground(_ scene: UIScene):  

// Called a little while after the iOS app entered the iOS background.
func sceneDidDisconnect(_ scene: UIScene):  
```

## What is Application Scene Manifest? 
It is resides in `info.plist` file 
It lists all the scenes configuration data. 

You can edit the scene’s 
- Configuration Name
- Delegate Class Name   
- Storyboard Name. 

## Scene Delegate debug log. 
```
application ---> connectingSceneSession 
scene ---> willConnectTo. 
scene ---> sceneWillEnterForeground. 
scene ---> sceneDidBecomeActive. 
scene ---> sceneWillResignActive. 
scene ---> sceneDidEnterBackground. 
scene ---> sceneDidDisconnect. 
application ---> didDiscardSceneSessions 
```

## What is SafeArea? 
- `Safe Area` is a layout guide (Safe Area Layout Guide). 
- The layout guide represents the portion of your view that is unobscured by bars and other content. 
- In iOS 11+, Apple is deprecating the top and bottom layout guides and replacing them with a single safe area layout guide. 

## What is the maximum limit of Priority in Swift?
- Required (1000) 
- High(750)
- Low(250) 

## How to change Priority in Swift? 
```Swift
myConstraint.priority = UILayoutPriority(rawValue : 999.0)
```

## Diagram of Content compression and hugging priority. 

                            
```
                    Content compression  
                  <--------------------->
>----------------|--o    Text Content    o--|-----------------<
Content hugging                         Content hugging
```

## What is Content hugging priority? 
Setting a larger value to this priority indicates that we **don’t want the view to grow larger than its intrinsic content size**. 
In below example both label has : 
- top
- trailing 
- both has horizontal content hugging priority = 251
- leading given. But width is not given so, it will create conflict. 
Now we set horizontal content hugging priority of 
`green(250)` - It will grow. 
`blue(251)` - it will remain stick to it’s intrinsic content size. 

## What is compression resistance priority? 
Setting a larger value to this priority indicates that we **don’t want the view to shrink smaller than its intrinsic content size**. 
Example : 
Consider a button with a really long name: 
Let the name be "Button with a larger name". 
- width = 44 points.

So, the button is completely unreadable. To, solve this:
- Horizontal Compression Resistance Priority to 1000. 
- Width constraint to any value between 0 to 999. 

## What is iOS Silent Push Notifications? 
When you send a Silent push notification and 
- if the app is `suspended` -> `wakes up` -> `background running` state. 
- If the app is killed by a user manually then it will not wake up. 

Instead of displaying a notification alert, the application will be awakened in background by Silent notification 
iOS wakes up your app in the background and gives it up to 30 seconds to run. 

Payload’s aps dictionary includes the content-available = 1. 
JSON payload for Silent Push notifications: 
```JSON
{ 
    "aps" = { 
        "content-available": 1, 
        "sound": "" 
    }; 
    // You can add a custom key-value pair here... 
} 
```
In iOS, the system delivers background update notifications by calling the ``application:didReceiveRemoteNotification:fetchCompletionHandler:`` method of your app delegate.

## Difference between APPID and BundleID. 
**AppID**: 
- It is a combination of TeamID and BundleID. 
- It is generated by Apple 
- It can link 1/more applications from a development team in Apple's system. 

**Example**: 
- TeamID = abcd1234 
- BundleID = `com.abc.xyz` 
- AppID = `abcd1234.com.abc.xyz` 
- WildCard AppID = `abcd1234.com.xyz.*` 

**BundleID**: 
- It is generated by Developer 
- No 2 application have same BundleID 
- To avoid conflict reverse domain name notation used

**Example** :  
`com.abc.xyz` 
Note: When you flip switch for any capability from xcode it will automatically update for apple developer account. 
- Capabilities Like : 
- iCloud, Background Fetch, Push Notification, ApplePay, GameCenter. 

## List out storage options. 
- **In-Memory** Array, Dictionary, Set 
- **NSUserDefaults** / **Keychain** 
- **File/Disk** storage 
- **CoreData**, **Realm** 
- **SQLite** 

## List Networking implementation and HTTP 
- AFNetworking 
- Alamofire 

## List Mapping in IOS. 
- XML / JSON parsing 
- Object Mapper 
- Codable / Decodable 
- SwiftyJSON (JSON Serialization) 

## Design Patterns in IOS. 
- MVC, MVP, MVVM, VIPER, Singleton, Delegate Observer 
- Factory Method 
- Adapter 
- Decorator 
- Command 
- Template 

## Layouting UI in IOS. 
- AutoLayout 
- CGRect
- Autoresizing Mask 
- SwiftUI  
- React Implementation on iOS, RxSwift 
- Component Kit       
- Flexbox 

## Dependency Management 
- Cocoapods 
- Carthage 
- SPM(Swift Package Management) 

## Debugging & Profile things in IOS 
- NSLogging 
- Print
- BreakPoints
- XCTests measure block   
- Quick & Nimble 

## Optimize scrolling performance of dynamically sized table / collectionview 
- Calculate cell height by contents 
- Autolayout 
- ASDK(Texture) : calculate cell height in background thread make super performant 

## Asynchronous task on iOS 
- GCD 
- NSOperations
- RXSwift 

## Difference between Internal and External Tester. 
**Internal Tester**: 
- Users who receives update without approval / review 
- Maximum 25 users allowed 
- When app is uploaded users get notified 
- Manage Users & Roles (Permissions) 
- It does not have 60 days limit as External Tester

**External Tester**: 
- Applications have to submit for review 
- It takes upto 48 hours for review     
- Upto 2000 email(External Testers) can be added 
- It has a 60 days limit to download application for testing. 

## What is wrapping and unwrapping? 
- Optional is that the variable can be nil 
- Wrapping 
```swift
var name = "abc"       
name = nil //(it gives error)  
```
     
- UnWrapping 
```swift
var name: String? = "abc" 
name = nil //(It will not give error because of ‘?’) 
```

## What is Certificates? 
- It authenticate you as an entity 
- It represents you as an entity 
- It is safeguard for APNS spoofing 
- SSL is used for submit app on AppStore 
- For APNS Push Notification it is used. 

**Steps**: 
- Create `CSR` (Certificate Signing Request) 
- Create Provisioning Profile by CSR. 

## What is Provisioning Profile? 
- It indicates the devices for which an app is correctly signed 
- It assigns the certificate to APP ID. 
- It is a link between Certificate and Identifier. 
- It shows "Application with this identifier signed with this certificate’s private key are okay to run on these devices" 
- 2 types of provisioning profiles 
- Development Provisioning Profile. Limited to 100 devices. 
- Distribution Provisioning Profile `AdHoc` and `Appstore` 
- Identifier : It is unique id for your mobile application 

## Difference between : `AppBundle` - `FileDirectory` 
**AppBundle**: 
> erarchical structure that has executable code & resources used by code 

**FileDirectory**: 
>  has files like .app, .bundle, .framework, .plugin 

## What is NSPredicate in CoreData? 
- Filtering data before fetching from core data 
- Ex: var strName = "Amar" 
- Request.predicate = NSPredicate(format "name = %@",strName) 

**NSPredicate on Collection** 
```swift
let manan = Person(firstName = "Manana", age : 28) 
let sagar = Person(firstName = "Manana", age : 25) 
let people = [manan,sagar] as NSArray 
let thirtiesPredicates = NSPredicate(format "age >= 27") 
people.filtered(using:thirtiesPredicates) 
//Output : Manan object will  return.
```
## Is Device token change/not when uninstalling / re-install? 
- When re-install the app it is changed 
- If user restore backup data to a new device it is changed `didRegisterForRemoteNotificationsWithDeviceToken` called 

## Differance : `Cocoa` - `CocoaTouch`
**Cocoa** 
- It is an Application framework for MacOSx
- Frameworks : Foundation, AppKit 
- API : NS is Prefix 
- Example : NSTextField

**CocoaTouch** 
- It is an Application framework for iPhone, iPod Touch 
- Frameworks : UIKit 
- API : UI is Prefix -         
Example : UITextField 

## Class hierarchy of below components 
**UITableView** -> `UIScrollView` : `UIView` : `UIResponder` : `NSObject` 
**UIButton** -> `UIControl` : `UIView` :`UIResponder` : `NSObject` 

## Difference : If let and Guard let. 
**If let**
```swift
If let count = 40 { 
    print("count available") 
} else { 
    print("count is nil") 
} 
```
- If the condition not meet it will print else statement 
- return is optional in it 
- Optional binding 

**Guard let** 
```swift
var count: String?
guard let count = count else { 
    print("count is nil") 
    return
}
print(count)
```
- If the condition not meets it return out of scope 
- Early exit from scope like , return, throw 

37. Difference : UIWindow - UIView 
**UiWindow** : 
- It contains view 
- Only 1 through the application

**UIView** : 
- It contains some content 
- It can be multiple 

Hierarchy: 
UiWindow -> UiView 
- UIButton 
- UILabel 
- UITextFiled 

## Create AppDelegate object 
```swift
let  appDelegate = UIApplication.shared.delegate as! AppDelegate 
appDelegate.anyAppDelegateVar / Method 
```

## What is type aliasing? 
Giving new name to existing data type 

**Example 1**: 
```swift
typealias StudentName = String 
let name: StudentName = "John"
```

**Example 2**: 
```swift
class Student {} 
var students: Array<Student> = [] 

typealias students = Array<Student> 

var students: Students = []  
```

## Datatypes in swift. 
`Bool`, `Integer`, `Int8`, `UInt`, `Float`, `Double`, `Character`, `String` 

## Swift Optional. ? ! ?? 
- `?` -> Optional can be nil 
- `!` -> Compulsory not nil 
- `??` -> it checks whether optional contains value or not. If not then return default value 

**Example**: 
```swift
var a: Int!
var a: Int? = 10
let b = 5 
let c: Int = a ?? b 
print(c) 
// Output : 5
// Output : 10 
```

## InApp Purchase in Swift 
- StoreKit framework is used for it

- **Consumable**
> Products which can be bought again and again after users have consumed them. 
> **Example**:Game coins, Energy etc. 

- **Non Consumable** 
> Products bought just once. In subsequent app installations users do not pay again to acquire them; instead these products are restored from the App Store. 
> **Example** : Pro version of the application 

- **Non Recurring**
> Users can buy content or features for a certain period of time. Upon expiration, subscription is renewed automatically. Users always have the option to cancel.
> **Example** : A sports season 

- **Auto Renewing** 
> Similar as Non - Recurring, but the subscription does not renew automatically. 
> **Example** : NetFlix Subscription 

43. Singleton class in IOS 
- Singleton class means you can create only one object for class.
- You can create a singleton class by making its constructor as private, so that you can restrict the creation of the object. 
- Provide a static method to get instance of the object, wherein you can handle the object creation inside the class only. 

**Example**: 
```swift
import UIKit 

final class GlobalData: NSObject { 
    static let sharedInstance = GlobalData() 
    
    private override init() { } 
    
    func foo() { } 
} 

let glblData = GlobalData.sharedInstance 
GlobalData.sharedInstance.foo() 
```

## Error handling in swift. 
```swift
enum UserDetailError : Error { 
    case noValidName 
    case  noValidAge 
} 

func userTest(age: Int, name: String) throws { 
    guard age > 0 else { 
        throw UserDetailError.noValidName 
    } 
} 

do { 
    try userTest(age:-1, name : "") 
} catch UserDetailError.noValidName { 
    print("Name is not valid")
} catch UserDetailError.noValidAge { 
    print("Age is not valid")
} catch let error { 
    print("unspecified error : \(error)") 
} 
```

## Differance : try try? Try!

```swift
do { 
    try student(name : "A") 
} catch { 
    print(error.localDescriptionString) 
}
```

- Used when error is optional 
```swift
 var t1 = try? student(name: nil)
```

- Used when it is confirm that error will not occur 
```swift
 var t2 = try! student(name:"Ajay")
```


## What is closure in swift? 
You can think of a closure as being a function that doesn't have a name of its own and captures any values from its environment. 

**Example 1**: 
```swift
let simpleClauser = {} 
simpleClauser() 
```

**Example 2**: 
```swift
let simpleClauser = { print("hello") } 
simpleClauser()
```
 
**Example 3**: 
```swift
let simpleClauser : (String) -> () = { print(name) } 
simpleClauser("Ajay") 
```

**Example 4**: 
```swift
let simpleClauser:(String) -> (String) = { name in 
    ...
}

let result = simpleClauser("Hello world") 
```

**Example 5**: 
```swift
func fun1(someClauser: () -> ()) { 
    ... 
} 

fun1(someClauser: {...}) 
```

**Example 6**: 
> As a completion handler 
```swift
func fun1(completion:() -> ()) {} 
fun1(completion: { ... }) 
```

## What is the completion block in swift? 
Time consuming tasks (like : webservice response) are written in it, so when it is completed it will notify the user instead of delegate 

**Example**: 
```swift
func longTask(completion : () -> ()) { 
    dispatch_async(dispatch_get_global.queue(DISPATCH_QUEUE_PRIORITY_DEFUALT, 0)) { 
        //Task 
        dispatch_async(dispatch_get_main_queue() { 
            completion() 
        }) 
    } 
} 
```

## What is the SafeAreLayoutGuide? 
> It helps to avoid underlying system UI elements when you put contents & controls. 
> 
**SystemUI Elements**: 
- StatusBar, NavigationBar, ToolBar, TabBar 
So, when you put this element, SafeArea will shrink.
In `iPhone X` SafeArea has additional inset 
- from top, bottom in portrait and 
- from leading, trailing in landscape mode We can enable SafeArea layout guide from class inspector 

## What is enum in swift? 
> It is symbolic name of set of values 

**Example**: 
```swift
Enum ErrorsToThrow : Error { 
    case fileNotFound 
    case fileNotReadable
    case fileSizeTooHigh 
} 

func readFile(path:String) throws -> String { 
    If path == "" { 
        throw ErrorsToThrow.fileNotFound 
    } 
    return "Data from file" 
} 

// Calling above function 
do { 
    let dataFromString = try? readFile(path:"") 
    print(dataFromString) 
} catch ErrorsToThrow.fileNotFound { 
    print("error generated : fileNotFound") 
} catch ErrorsToThrow.fileNotReadable { 
    print("error generated : fileNotReadable") 
} catch ErrorsToThrow.fileSizeIsTooHigh { 
    print("error generated : fileSizeIsTooHigh") 
} 
```

## How many ways can we present ViewController?
- Model Presentation 
```swift
[self presentViewController: VC2 animated: Yes completion : nil];
```

- ViewController Containment 
    
```swift
[self addChldViewController: VC2]; 
[self.view addSubView: VC2.view]; 
[self didMoveToParentViewController: self]; 
```
Here : VC1 is self nad VC2 is childeViewController of VC1