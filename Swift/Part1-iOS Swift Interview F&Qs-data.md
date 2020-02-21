[TOC]

## What is the Swift and its advantages? 

Swift is a general-purpose, multi-paradigm, compiled time programming language developed by Apple Inc. for iOS, macOS, watchOS, tvOS, and Linux. 

- Language designers: Apple  
- Parent language: Objective-C  
- Language paradigms: Compiled language  


## Advantages of Swift language. 

- Readability — Clean syntax, which makes it easier to read and write.  
- Maintenance — Less Code & Less Legacy — one file .swift.  
- Safer Platform — You can compile, and fix the errors while writing the code.  
- High Speed — The incredibly quick and high-performing LLVM compiler transforms the Swift code into optimized native code to get the most out of its devices. The syntax and standard library have also been tuned to make the code perform optimally.  
- Swift Supports Dynamic Libraries  
- Open Source  

## Is Swift Object-Oriented Programing ? 

Yes 

## How to write Comments in Swift? 
They are ignored by the compiler. 

- Multi-line comment : 
```
/* 
Multi-line comment
My first program in Swift Hello world
*/ 
```

- Single-line comment : 
```
// My first program in Swift 
```

## Data types in Swift. 

- `Int or UInt` − This is used for whole numbers. More specifically, you can use Int32, Int64 to define 32 or 64 bit signed integer, whereas UInt32 or UInt64 to define 32 or 64 bit unsigned integer variables. For example, 42 and -23. 
- `Float` − This is used to represent a 32-bit floating-point number and numbers with smaller decimal points. For example, 3.14159, 0.1, and -273.158. 
- `Double` − This is used to represent a 64-bit floating-point number and used when floating-point values must be very large. For example, 3.14159, 0.1, and -273.158. 
- `Bool` − This represents a Boolean value which is either true or false. 
- `String` − This is an ordered collection of characters. For example, "Hello, World!" 
- `Character` − This is a single-character string literal. For example, "C" 
- `Optional` − This represents a variable that can hold either a value or no value. 
- `Tuples` − This is used to group multiple values in single Compound Value. 

## What is `Optionals` (?) in swift? 
Swift 4 also introduces Optionals type, which handles the absence of a value. 
Optionals say either "there is a value, and it equals x" or "there isn't a value at all". 
An Optional is a type on its own, actually one of Swift 4’s new super-powered enums. 
It has two possible values, None and Some(T), where T is an associated value of the correct data type available in Swift 4. 

```swift
var myString: String? = nil 
if myString != nil { 
    print(myString) 
} else { 
    print("myString has nil value") 
} 
```
When we run the above program using playground, we get the following result − myString has nil value. 
Optionals are similar to using nil with pointers in Objective-C, but they work for any type, not just classes. 

## What is Forced `Unwrapping` ? 
If you define a variable as optional, then to get the value from this variable, you will have to unwrap it. This just means putting an exclamation mark (!) at the end of the variable. 

Let's take a simple example − 
```swift
var myString:String? 
myString = "Hello, Swift 4!" 
if myString != nil { 
    print(myString) 
} else { 
    print("myString has nil value") 
} 

// Output : Optional("Hello, Swift 4!") 
```

Now let's apply unwrapping to get the correct value of the variable − 
```swift
var myString:String? 
myString = "Hello, Swift 4!" 
if myString != nil { 
    print( myString! ) 
} else {
    print("myString has nil value") 
} 

Output :  Hello, Swift 4! 
```

## Automatic `Unwrapping`? (!) 
You can declare optional variables using exclamation (!) mark instead of a question mark. 
Such optional variables will unwrap automatically and you do not need to use any further exclamation mark at the end of the variable to get the assigned value. 

```swift
var myString: String! 
myString = "Hello, Swift 4!" 
if myString != nil { 
    print(myString) 
} else {
    print("myString has nil value") 
} 

// Output :  Hello, Swift 4! 
```

## What is `Optional` Binding in Swift? 
Use optional binding to find out whether an optional contains a value, and if so, to make that value available as a temporary constant or variable. 

An optional binding for the if statement is as follows − 
```
if let constantName = someOptional { 
    statements 
} 
```
Example : 

```swift
var myString: String? 
myString = "Hello, Swift 4!" 
if let yourString = myString { 
    print("Your string has - \(yourString)") 
} else { 
    print("Your string does not have a value") 
} 

// Output : Your string has - Hello, Swift 4! 
```

## What are the control transfer statement in swift? 
- `Continue` 
- `Break`  
- `Fallthrough`  
- `Return`
   
## What are swift `pattern` matching techniques?. 
**Tuple pattern**
Used to match values of corresponding tuple types. 
**Type-casting pattern**
Allow you to cast or match types. 
**Wildcard pattern**
Match and ignore any kind and type of value. 
**Optional pattern**  
Used to match optional values. 
**Enumeration case pattern**  
Match cases of existing enumeration types. 
**Expression pattern**  
Allow you to compare a given value against a given expression. 

## Explain difference between `class` and `struct`. 
There are mainly four differences between `class` and `struct` in swift. 
Classes have below additional capabilities that structures do not: 
1. `Type Casting`: Type casting enables you to check and interpret the type of a class instance at runtime. 
1. `Reference counting` allows more than one reference to a class instance. (Structs are value types and Classes are reference types.)
1. `Inheritance` enables one class to inherit the characteristics of another.  
1. `Deinitializers` enable an instance of a class to free up any resources it has assigned.

`Structures` are always copied when they are passed around in your code, and do not use reference counting. 
`Structure` instances are always passed by value, and `class` instances are always passed by reference. 

## When to use `class` and when to use `struct`? 
As a general guideline, consider creating a `structure` when one or more of these conditions apply: 

- The structure’s primary purpose is to encapsulate a few relatively simple data values.
- It is reasonable to expect that the encapsulated values will be copied rather than referenced when you assign or pass around an instance of that structure.
- Any properties stored by the structure are themselves value types, which would also be expected to be copied rather than referenced.
- The structure does not need to inherit properties or behavior from another existing type.  In all other cases, define a class, and create instances of that class to be managed and passed by reference. 

## How to pass a variable as a reference? 
We can pass variable as a reference using inout parameter. 
`inout` means that modifying the local variable will also modify the passed-in parameters. 

```swift
var value: String = “Swift” 
func changeString(newValue:inout String) { 
    newValue = “IOS” print(newValue) 
    // Output:IOS print(value) 
    // Output:IOS 
} 

changeString(newValue:&value)
```

## What is swift `module`? 
- A module is a single unit of code distribution.  
- A framework or application that is built and shipped as a single unit and that can be imported by another module with Swift’s import keyword.  
- Each build target (such as an app bundle or framework) in Xcode is treated as a separate module in Swift.  


## What are the different Access Levels in swift? 
Swift provides five different access levels for entities within your code. 

1. `open` access: 
> Classes with open access can be subclassed or overridden by subclasses within the module where they’re defined and within any module that imports the module where they’re defined.
1. `public` access: 
> Classes with public access can be subclassed or overridden by subclasses only within the module where they’re defined.
1. `internal` access: 
> enables entities to be used within any source file from their defining module, but not in any source file outside of that module.
1. `fileprivate` access: 
> restricts the use of an entity to its own defining source file.
1. `private` access: 
> restricts the use of an entity to the enclosing declaration, and extensions of that declaration that are in the same file.  

`Open` access is the highest (least restrictive) access level and private access is the lowest (most restrictive) access level. 
All entities in your code (with a few specific exceptions) have a **default access level** of `internal`. 


## Explain `lazy` in Swift ? 
A lazy stored property is a property whose initial value is not calculated until the first time it is used. 
You indicate a lazy stored property by writing the lazy modifier before its declaration. 
Example : 
> Consider a struct called `InterviewCandidate`. It has an optional bool value to decide if the candidate is applying for ios or android.
Resume description for iOS and android are declared as lazy variables. So, in the following code, the person is an iOS developer and the lazy variable `iOSResumeDesc` will be initialized when called for printing. `androidResumeDesc` will be nil. 

```swift
import UIKit 

struct InterviewCandidate {

    var isiOS: Bool?
    
    lazy var iOSResumeDesc: String = {
        return "I am an iOS developer"
    }()
    
    lazy var androidResumeDesc: String = {
        return "I'm an Android developer" 
    }()
}

var person = InterviewCandidate()
person.isiOS = true

if person.isiOS {
    print(person.iOSResumeDesc)
} else {
    print(person.androidDesc)
}

```

## What are rules for `lazy`? 
- You can’t use lazy with `let`.  
- You can’t use it with `computed properties`. Because, a `computed property` returns the value every time we try to access it after executing the code inside the `computation block`.  
- You can use `lazy` only with members of struct and class.  
- `lazy` variables are not initialised atomically and so is not thread safe.  

## What is a `Tuple` in swift ? 
A `tuple` is a group of zero or more values represented as one value. 
They are commonly used to return multiple values from a function call.
Tuple = `Dictionary`(can be created on the fly) + `Struct`(hold very specific types of data) 
There are two types of Tuple in swift

1. **Named Tuple** 
```swift
let nameAndAge = (name: "Amar", age:25) 

// Access the values like: 
nameAndAge.name 
// Output: Amar 
nameAndAge.age 
// Output: 25 
```

1. **Unnamed Tuple**
In unnamed tuple we don’t specify the name for its elements. 

```swift
let nameAndAge = ("Amar", 25) 
// Access the values like: 
nameAndAge.0 
// Output: Amar 
nameAndAge.1 
// Output: 25 20. 
```

## What is `Enumeration`? 
It defines a common type for a group of related values and enables you to work with those values in a `type-safe` way within your code. 
Unlike `C` and `Objective-C`, `Swift` enumeration cases are not assigned a default integer value when they are created. 

```swift
enum CompassPoint { 
    case north case south case east case west 
} 
var directionToHead = CompassPoint.west 
```
OR 
```swift
enum Planet { 
    case mercury, venus, earth, mars, jupiter, saturn, uranus, neptune 
} 
var planetName = Planet.mars 
```

## What is `Generics` in Swift? 
Swift 4 language provides `Generic` features to write flexible and reusable functions and types. 
`Generics` are used to avoid duplication and to provide abstraction. 
Swift 4 standard libraries are built with generics code. 
Swift 4 `Arrays` and `Dictionary` types belong to `generic collections`. 
With the help of arrays and dictionaries the arrays are defined to hold `Int` values and `String` values or any other types. 

```swift
func exchange(a inout Int, b: inout Int) {
    let temp = a
    a = b
    b = temp
}

var num1 = 100
var num2 = 200

print("Before Swapping values are: \(num1) and \(num2)")
exchange(a: &num1, b: &num2)
print("After Swapping values are: \(num1) and \(num2)")

// Before Swapping Int values are: 100 and 200 
// After Swapping Int values are: 200 and 100
```

## What is `Generics Functions`: Type Parameters in Swift ? 
Generic functions can be used to access any data type like 'Int' or 'String'.


```swift
func exchange<T>(a inout T, b: inout T) {
    let temp = a
    a = b
    b = temp
}

var num1 = 100
var num2 = 200

print("Before Swapping values are: \(num1) and \(num2)")
exchange(a: &num1, b: &num2)
print("After Swapping values are: \(num1) and \(num2)")

var str1 = "Generics"
var str2 = "Functions"

print("Before Swapping values are: \(str1) and \(str2)")
exchange(a: &str1, b: &str2)
print("After Swapping values are: \(str1) and \(str2)")

// Before Swapping Int values are: 100 and 200 
// After Swapping Int values are: 200 and 100
// Before Swapping String values are: Generics and Functions 
// After Swapping String values are: Functions and Generics 
```

## What is `Tuple` in Swift? 
Tuples are used to group multiple values in a single compound Value. 
The values in a tuple can be of any type, and do not need to be of the same type. 
Example : (“Tutorials Point", 123) is a tuple with two values, one of string Type, and other is integer type. 
Here’s the syntax of Tuple declaration − 
```swift
var TupleName = (value1, value2,… any number of values)
```
You can name the variables of a tuple while declaring, and you can call them using their names 
```swift
var error501 = (errorCode: 501, description: "Not Implemented") 
print(error501.errorCode)   
// prints 501. 
```
**Note** − Tuples are useful for temporary values and are not suited for complex data. 

## What is `Arrays` in Swift? 
`Arrays` are used to store ordered lists of values of the same type. 
Swift 4 puts strict checking which does not allow you to enter a wrong type in an array, even by mistake. 
If you assign a created array to a variable, then it is always mutable, which means you can change it by adding, removing, or changing its items; 
but if you assign an array to a constant, then that array is immutable, and its size and contents cannot be changed. Example : 
```swift
var someInts: [Int] = [10, 20, 30] 
// OR 
var someInts = [Int](count: 3, repeatedValue: 10) 
var someVar = someInts[0] 
print( "Value of first element is \(someVar)") 
print( "Value of second element is \(someInts[1])") 
print( "Value of third element is \(someInts[2])" ) 
// OUTPUT : 
// Value of first element is 10 
// Value of second element is 20 
// Value of third element is 30 

// Modifying Arrays 
someInts += [40] 
print( "Value of fourth element is \(someInts[3])”) 
//Value of third element is 40

// Iterating Array
var someStrs = [String]() 
someStrs.append("Apple") 
someStrs.append("Amazon") 
someStrs += ["Google"] 
for item in someStrs { 
    print(item) 
} 
// OUTPUT : Apple Amazon Google
```

**Note** : `count` (find length of array) and `isEmpty` (check array is empty or not)  properties are also used in array. 

## What is Sets in Swift? 
`Sets` are used to store distinct values of **same types** but they don’t have a **definite ordering** as arrays have. 

You can use sets instead of arrays if ordering of elements is not an issue, or if you want to ensure that there are no duplicate values. (sets allow only distinct values.) 
Example : 
```swift
var someSet = Set<Character>() 
someSet.count           // prints the number of elements 
someSet.insert("c")     // adds the element to Set. 
someSet.isEmpty         // returns true or false 
someSet.remove("c")     /* removes an element , removeAll() can be used to remove all elements*/ 
someSet.contains("c")    // to check if set contains this value. 
```

**Iterating over a Set** 
```swift
for items in someSet { 
    print(someSet) 
} 
```

Sets are not in an ordered way, to iterate over a set in ordered way use 
```swift
for items in someSet.sorted() { 
    print(someSet) 
} 
```
 
**Performing Set Operations** 
Following are the methods for performing set operations − 
- Intersection 
- Union 
- subtracting

```swift
let evens: Set = [10,12,14,16,18] 
let odds: Set = [5,7,9,11,13] 
let primes = [2,3,5,7] 
odds.union(evens).sorted() 
// Output : [5,7,9,10,11,12,13,14,16,18] 
odds.intersection(evens).sorted() 
// Output  : [] 
odds.subtracting(primes).sorted() 
// Output : [9, 11, 13] 
```


## What is `Dictionary` in Swift? 
Dictionaries are used to store **unordered** lists of values of the **same type**. 
It uses unique identifier known as a key to store a value which later can be referenced and looked up through the same key. 
Unlike items in an array, items in a dictionary do not have a specified order. 
You can use a dictionary when you need to look up values based on their identifiers. 
A dictionary key can be either an integer or a string without a restriction, but it should be unique within a dictionary.
Example : 
```swift
var someDict:[Int: String] = [1: "One", 2: "Two", 3: "Three"] 
```

- Sequence Based Initialization 
```swift
var cities = ["Delhi", "Bangalore", "Hyderabad"] 
var Distance = [2000, 10, 620] 
```

- Here is an example to create a dictionary from a set of given values − 
```swift
let cityDistanceDict = Dictionary(uniqueKeysWithValues: zip(cities, Distance))
print(cityDistanceDict) 
// Output : [“Delhi": 2000, "Bangalore": 10, "Hyderabad": 620] 
```

- **Filtering** 
```swift
var closeCities = cityDistanceDict.filter { $0.value < 1000 } 
print(closeCities) 
// Output : ["Bangalore" : 10 , "Hyderabad" : 620] 
```

- **Dictionary Grouping** 
```swift
var cities = ["Delhi", "Bangalore", "Hyderabad", "Dehradun", "Bihar"] 
var GroupedCities = Dictionary(grouping: cities ) { $0.first! } 
// Output : [“D” :["Delhi","Dehradun"], "B" : ["Bengaluru","Bihar"], "H" : ["Hyderabad"]]
```

- **Accessing Dictionaries **
```swift
var someDict:[Int:String] = [1: "One", 2: "Two", 3: "Three"] 
var someVar = someDict[1] 
print( "Value of key = 1 is \(someVar)" ) 
// Output : Value of key = 1 is Optional("One")
```

- **Modifying Dictionaries** 
```swift
var oldVal = someDict.updateValue("New value of one", forKey: 1) 
print( "Value of key = 1 is \(someVar)" ) 
// Output : Value of key = 1 is Optional("New value of one") 
```

- **Remove Key-Value Pairs**
```swift
var someDict:[Int:String] = [1:"One", 2:"Two", 3:"Three"] 
var removedValue = someDict.removeValue(forKey: 2) 
print( "Value of key = 1 is \(someDict[1])" ) 
print( "Value of key = 2 is \(someDict[2])" ) 
print( "Value of key = 3 is \(someDict[3])" ) 
// Output : Value of key = 1 is Optional("One") Value of key = 2 is nil Value of key = 3 is Optional("Three") 
```

- **Iterating Over a Dictionar**
```swift
var someDict:[Int:String] = [1:"One", 2:"Two", 3:"Three"] 
for (key, value) in someDict.enumerated() { 
    print("Dictionary key \(key) - Dictionary value \(value)") 
} 
Dictionary key 0 - Dictionary value (key: 2, value: "Two") 
Dictionary key 1 - Dictionary value (key: 3, value: "Three")
Dictionary key 2 - Dictionary value (key: 1, value: "One") 
```

- **Convert to Arrays**
```swift
var someDict:[Int:String] = [1:"One", 2:"Two", 3:"Three"] 
let dictKeys = [Int](someDict.keys) 
let dictValues = [String](someDict.values)

print("Print Dictionary Keys") 
for (key) in dictKeys { 
    print("\(key)")
} 

print("Print Dictionary Values") 
for (value) in dictValues { 
    print("\(value)") 
}
// Output: Print Dictionary Keys 2 3 1 
// Output: Print Dictionary Values Two Three One The count Property 
var someDict1:[Int:String] = [1: "One", 2: "Two", 3: "Three"] 
print("Total items in someDict1 = \(someDict1.count)") 
// Output: Total items in someDict1 = 3 The empty Property 

var someDict1:[Int:String] = [1: "One", 2: "Two", 3: "Three"] 
print("someDict1 = \(someDict1.isEmpty)") someDict1 = false 
```

## What is `Closure` in Swift? 
`Closure` is similar to that of **self-contained functions** organized as **blocks** and called anywhere like C and Objective C languages. 

- Example 1: 
```swift
let studname = { print("Welcome to Swift Closures") } 
studname() 
// Output :  Welcome to Swift Closures
```

- Example 2: 
```swift
let divide = { (val1: Int, val2: Int) -> Int in 
    return val1 / val2 
}
let result = divide(200, 20) 
print (result) 
// Output : 10 
```

- **Expressions in Closures** 
```swift
func ascend(s1: String, s2: String) -> Bool { 
    return s1 > s2 
} 
let stringcmp = ascend(s1: "Swift 4", s2: "great") 
print (stringcmp) 
// Output : true 
```

- **Known Type Closures** 
```swift
let sub = { (no1: Int, no2: Int) -> Int in 
    return no1 - no2 
} 
let digits = sub(10, 20) 
print(digits) 
// Output: -10
```
 
- **Declaring Shorthand Argument Names as Closures** 
```swift
var shorthand: (String, String) -> String 
shorthand = { $1 } 
print(shorthand("100", "200")) 
// Output: 200 
```

- **Closures as Operator Functions**
```swift
let numb = [98, -20, -30, 42, 18, 35] 
var sortedNumbers = numb.sorted ({ (left: Int, right: Int) -> Bool in 
    return left < right 
}) 
let asc = numb.sorted(<) print(asc) 
// Output: [-30, -20, 18, 35, 42, 98]
```

- **Closures as Trailers** 
```swift
import Foundation 
 
var letters = ["North", "East", "West", "South"] 
let twoletters = letters.map({ (state: String) -> String in 
   return state.substringToIndex(advance(state.startIndex, 2)).uppercaseString 
}) 
let stletters = letters.map() { $0.substringToIndex(advance($0.startIndex, 2)).uppercaseString } 
print(stletters) 
// Output :[NO, EA, WE, SO] 
```

- **Capturing Values and Reference Types **
```swift
func calcDecrement(forDecrement total: Int) -> () -> Int { 
    var overallDecrement = 100
    
    func decrementer() -> Int { 
        overallDecrement -= total 
        print(overallDecrement) 
        return overallDecrement 
    } 
    return decrementer 
} 
let decrem = calcDecrement(forDecrement: 18) 
decrem() 
decrem() 
decrem()
// Output: 82 64 46
```

## What is `Enum` in Swift? 
An enumeration is a user-defined data type which consists of a set of related values. 
Keyword `enum` is used to defined enumerated data type. 
- It is declared in a class and its values are accessed through the instance of that class.
- Initial member value is defined using enum initializers.
- Its functionality is also extended by ensuring standard protocol functionality. 

```swift
enum names { 
    case Swift 
    case Closures 
}
var lang = names.Closures 
lang = .Closures 
switch lang { 
case .Swift: 
    print("Welcome to Swift") 
case .Closures: 
    print("Welcome to Closures") 
default:
    print("Introduction") 
}
// Output: Welcome to Closures 
```

- **Enumeration with Switch Statement**
```swift
enum Climate { 
    case India 
    case America 
    case Africa 
    case Australia 
} 
var season = Climate.America 
season = .America 
switch season { 
case .India:  
    print("Climate is Hot") 
case .America :
    print("Climate is Cold") 
case .Africa:      
    print("Climate is Moderate") 
case .Australia:
    print("Climate is Rainy") 
} 
// Output : Climate is Cold 
```

- **Enum with Associated Values **

```swift
enum Student { 
    case Name(String)
    case Mark(Int, Int, Int) 
} 

var studDetails = Student.Name("Swift 4") 
var studMarks = Student.Mark(98,97,95) 
switch studMarks { 
case .Name(let studName): 
    print("Student name is: \(studName).") 
case .Mark(let Mark1, let Mark2, let Mark3): 
    print("Student Marks are: \(Mark1),\(Mark2),\(Mark3).") 
} 
// Output : Student Marks are: 98,97,95. 
```

- **Enum with Raw Values** 
```swift
enum Month: Int { 
    case January = 1, February, March, April, May, June, July, August, September, October, November, December 
} 
let yearMonth = Month.May.rawValue 
print("Value of the Month is: \(yearMonth).") 
// Output : Value of the Month is: 5. 
```

## What is `Inheritance` in Swift? 
The ability to take than more form is defined as Inheritance. 
Generally a class can inherit methods, properties and functionalities from another class. 
Classes can be further categorized in to subclass and superclass. 
- **Subclass** − when a class inherits properties, methods and functions from another class it is called as subclass. 
- **SuperClass** − Class containing properties, methods and functions to inherit other classes from itself is called a super class.

Classes contain superclass which calls and access methods, properties, functions and overriding methods. 
Also, property observers are also used to add a property and modify the stored or computed property methods. 

## What is Base Class in Swift? 
A Class that does not inherit methods, properties or functions from another class is called as 'Base Class'. 

## What is SubClass in Swift? 
The act of basing a new class on an existing class is defined as `Subclass`. 
The subclass inherits the properties, methods and functions of its base class. 
To define a subclass ':' is used before the base class name 

- Example : 
```swift
class StudDetails { 
    //This is superclass (Base) 
    var mark1: Int
    var mark2: Int
    
    init(stm1:Int, results stm2:Int) { 
        mark1 = stm1
        mark2 = stm2 
    } 
    
    func print() { 
        print("Mark1:\(mark1), Mark2:\(mark2)") 
    }
}
class display: StudDetails {
    //This is subclass class
    init() {
        super.init(stm1: 93, results: 89) 
    } 
} 
let marksobtained = display() 
marksobtained.print() 
// Output : Mark1:93, Mark2:89 
```

## What is Method Overriding in Swift? 
Inherited instance and type methods can be overridden by the `override` keyword to our methods defined in our subclass. Here print() is overridden in subclass to access the type property mentioned in the super class print(). 
Also new instance of cricket() super class is created as `cricinstance`. 

- Example : 
```swift
class cricket { 
    func print() { 
        print("Welcome to Swift Super Class") 
    } 
}

class tennis: cricket { 
    override func print() { 
        print("Welcome to Swift Sub Class")
    } 
}

let cricinstance = cricket() 
cricinstance.print() 
let tennisinstance = tennis() 
tennisinstance.print() 
// Output : Welcome to Swift Super Class Welcome to Swift Sub Class 
```

## What is the use of `final` keyword in Swift? 
When the user need not want others to access super class methods, properties or subscripts then `final` property to prevent `overriding`. 

```swift
final class Circle { 
    final var radius = 12.5 
    var area: String { 
        return "of rectangle for \(radius)" 
    } 
} 

class Rectangle: Circle { 
    var print = 7 
    override var area: String { 
        return super.area + " is now overridden as \(print)" 
    }    
} 
let rect = Rectangle() 
rect.radius = 25.0 
rect.print = 3 
print("Radius \(rect.area)") 

class Square: Rectangle { 
    override var radius: Double { 
        didSet { 
            print = Int(radius/5.0)+1 
        } 
    } 
}
let sq = Square() 
sq.radius = 100.0
print("Radius \(sq.area)") 
```
//Output : 
```
<stdin>:14:18: error: var overrides a 'final' 
var override var area: String { 
^ 
<stdin>:7:9: note: overridden declaration is here 
var area: String { 
^ 
<stdin>:12:11: error: inheritance from a final class 'Circle' 
class Rectangle: Circle { 
^ 
<stdin>:25:14: error: var overrides a 'final' 
var override var radius: Double { 
^ 
<stdin>:6:14: note: overridden declaration is here 
final var radius = 12.5 
```

Since the super class is declared as 'final' and its data types are also declared as 'final' the program won't allow to create subclasses further and it will throw errors. 

## What is the Deinitialization in Swift? 
Swift 4 automatically deallocates your instances when they are no longer needed, to free up resources. 
Swift 4 handles the memory management of instances through automatic reference counting (ARC), as described in Automatic Reference Counting. 
Typically you don't need to perform manual clean-up when your instances are deallocated. 
However, when you are working with your own resources, you might need to perform some additional clean-up yourself. 
For example, if you create a custom class to open a file and write some data to it, you might need to close the file before the class instance is deallocated.

Example : 
```swift
var counter = 0; 
// for reference counting 
class baseclass { 
    init() { 
        counter++; 
    } 
    
    deinit { 
        counter--; 
    } 
} 
var item: baseclass? = baseclass() 
print(counter)      // Output : 1 
item = nil 
print(counter)      // Output : 0 
// print = nil statement is omitted the values of the counter retains the same since it is not deinitialized. 
//And if we write like this : 
var item: baseclass? = baseclass() 
print(counter)      // Output : 1 
print(counter)      // Output : 1 
```

## What is `ARC` (Automatic reference counting) in Swift? 
`ARC` is used to initialize and deinitialize the system resources thereby releasing memory spaces used by the class instances when the instances are no longer needed. 
`ARC` keeps track of information about the relationships between our code instances to manage the memory resources effectively. 

## ARC (Automatic reference counting) functionalities in Swift? 
- ARC allocates a chunk of memory to store the information each and every time when a new class instance is created by init(). 
- Information about the instance type and its values are stored in memory.    
- When the class instance is no longer needed it automatically frees the memory space by deinit() for further class instance storage and retrieval.  
- ARC keeps in track of currently referring class instances properties, constants and variables so that deinit() is applied only to those unused instances.    
- ARC maintains a `strong reference` to those class instance property 

## What is `Optional Chaining` in Swift? 
The process of querying, calling properties, subscripts and methods on an optional that may be 'nil' is defined as optional chaining. Optional chaining return two values −   
- if the optional contains a 'value' then calling its related property, methods and subscripts returns values
- if the optional contains a 'nil' value all its its related property, methods and subscripts returns nil
  
Example: 
```swift
class ElectionPoll { 
    var candidate: Pollbooth? 
    // value is not here so, it is nill here for candidate variable 
}

class Pollbooth { 
    var name = "MP" 
} 
let cand = ElectionPoll() 
let candname = cand.candidate!.name 
// Output : fatal error: unexpectedly found nil while unwrapping an Optional value 
  
```

But if we write like this: 
```swift
if let candname = cand.candidate?.name { 
    print("Candidate name is \(candname)") 
} else {
    print("Candidate name cannot be retrieved") 
} 
// Output : Candidate name cannot be retrieved 
```

## What is Extensions in Swift? 
Functionality of an existing class, structure or enumeration type can be added with the help of extensions. 
Type functionality can be added with extensions but overriding the functionality is not possible with extensions. 

- Example : 
```swift
extension Int { 
    var add: Int { 
        return self + 100 
    } 
} 
let addition = 3.add 
print("Addition is \(addition)") 
//Output : Addition is 103 
```
  
## What is Protocol in Swift? 
Protocols provide a blueprint for Methods, properties and other requirements functionality. 
It is just described as a methods or properties skeleton instead of implementation. 
Methods and properties implementation can further be done by defining classes, functions and enumerations. 
Conformance of a protocol is defined as the methods or properties satisfying the requirements of the protocol. 

- Example : 
```swift
protocol tcpprotocol { 
    init(no1: Int) 
} 

class mainClass { 
    var no1: Int        // local storage 
    
    init(no1: Int) { 
        self.no1 = no1  // initialization 
    } 
} 
    
class subClass: mainClass, tcpprotocol { 
    var no2: Int 
    
    init(no1: Int, no2 : Int) { 
        self.no2 = no2 
        super.init(no1:no1) 
    }
    
    // Requires only one parameter for convenient method 
    required override convenience init(no1: Int) { 
        self.init(no1:no1, no2:0) 
    }
} 
let res = mainClass(no1: 20) 
let print = subClass(no1: 30, no2: 50) 
print("res is: \(res.no1)")
// Output   : 20 print("res is: \(print.no1)")
// Output   : 30 print("res is: \(print.no2)")
// Output   : 50 
```

## Cocoa and Cocoa Touch in Swift? 
`Cocoa` is for Mac App Development(OSX)
`Cocoa Touch` is for apple touch devices(iOS) that provide all development environment. 

## What is meaning of “atomic” and “nonatomic” keyword? 
`Atomic` : The synthesised setter/getter will ensure that a whole value is always returned from the getter or set by the setter. 
Only single thread can access variable to get or set value at a time 
`NonAtomic` : No such guarantee that value is returned from variable in same that setter sets at the same time. 
It is Thread unsafe

## What is the main difference between `Frame` and `Bounds`? 
`Frame` of view is rectangle, expressed as a location(x,y) and size (width, height) relative to the super view it is contained within.
`Bounds` of view is the rectangle, expressed as a location(x,y) and size(width, height) relative to it’s own co-ordinate system (0,0). 

## What is class hierarchy for a UIButton ? 
`UIButton` > `UIControl` -> `UiView` -> `UIResponder` -> `NSObject`  

## What is use of defer keyword? 
It provides a `block` of code that executes when the execution is leaving the current scope. 
Example : 
```Swift
func updateImage() { 
    defer { 
        print("Did update image") 
    } 
    print("Will update image") 
    imageView.image = updatedImage 
} 
// Output: Will update Image 
// Output: Did update image 
```

## What is the output of below code? 
```Swift
let numbers = [1,2,3,4] 
let sumOfNumber = numbers.reduce(0, {$0 + $1}) 
print(sumOfNumber) 
// Output: 10 
```

46. Difference between `Swift` and `Objective-C`. 
`Swift`:
    - Variables and constants are declared before used. 
    - `var` keyword is used for variable and `let` keyword is used for constants 
    - No need to end statement with (`;`) semi-colon 
    - Not require to create separate interface like `Objective-C` 
    - We can define methods in class, structure or enumeration. 
    - Only 1 file is used like .swift 
`Objective-C` 
    - We need to end code with semi-colon 
    - We can declare constant as int and variable as NSString. 
    - 2 files we have to create like .h and .m file. 

47. Structure can be inherited? (Yes, No) 
No 

## What is meaning of `assign` in Swift? 
It specifies that the setter uses simple assignment. 
Uses on attribute of scalar type like `float`, `int`. 

## What type of compiler used by Apple? 
GNU Compiler Collection 

## What are the location services? 
Applications like Maps, Camera, Compassions are allowed to use information from `cellular`, `WiFi` and `GPS` for determining the approximate locations. 

Location is displayed on the screen using the `blue marker`.