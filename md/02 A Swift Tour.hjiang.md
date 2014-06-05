Swift 概览
------------

按照传统，一门新语言的第一个程序应该在屏幕上打印出「Hello, world」。在 Swift 中这可以用一行完成：

    println("Hello, world")

如果你曾经用 C 或 Objective-C 写过程序，这样的写法应该看起来很熟悉 --- 在 Swift 中，这行代码是一个完整的程序。你不需要为输入输出或操作字符串这样的功能导入任何单独的库。在全局范围的代码会作为程序的入口运行，所以你不需要写一个 `main` 函数。你也无需用 `;` 来结束每个语句。

通过说明如果完成各种编程任务，这篇概览将让你得到足够的信息以开始编写 Swift 程序。即使碰到有什么你还不明白的也不用担心 --- 概览中介绍的所有内容都会在本书的后面章节中有详细解释。

> 建议
>
> 为得到最好的体验，请在 Xcode 中学习本章。Xcode 的 Playgrounds 让你可以在编辑代码之后马上看到结果。

### 简单的值

用 `let` 来创建一个常量，用 `var` 来创建一个变量。一个常量的值不需要在编译时确定，但必须只被赋值一次。也就是说你可以用常量来为一个你会在多个地方使用但只会确定一次的值命名。

    var myVariable = 42
    myVariable = 50
    let myConstant = 42

一个常量或变量的类型必须和你想要赋值给它的值的类型一致，但你并不需要总把类型写出来。如果你在创建变量或常量时提供一个值，编译器会推导出它的类型。在上面的例子里，编译器推导出 `myVariable` 是一个整型变量，因为它的初始值是一个整数。

如果初始值没有提供足够的信息（或者没有初始值），那么你需要在变量或常量后面指定类型，两者用冒号隔开。

    let implicitInteger = 70
    let implicitDouble = 70.0
    let explicitDouble: Double = 70

> 实验
>
> 创建一个显示指定为 `Float` 类型的值为 `4` 的常量。

值永远不会被自动转换为其他类型。如果你需要把一个值转换为其他类型，需要创建一个所需类型的实例。

    let label = "The width is "
    let width = 94
    let widthLabel = label + String(width)

> 实验
>
> 试试从最后一行里把到 `String` 的转换去掉。你看到什么错误？

有一个更简单的在字符串中包含值的方法：把值写在括号中，并在括号前面加一个反斜杠（`\`）。例如：

    let apples = 3
    let oranges = 5
    let appleSummary = "I have \(apples) apples."
    let fruitSummary = "I have \(apples + oranges) pieces of fruit."

> 实验
>
> 用 `\()` 在一个字符串中包含一个浮点数计算，并把某人的名字包含在一个问候中。

用方括号（`[]`）来创建数组（array）和字典（dictionary），并通过把索引或 key 写在方括号中来访问他们的元素。

    var shoppingList = ["catfish", "water", "tulips", "blue paint"]
    shoppingList[1] = "bottle of water"
    
    var occupations = [
        "Malcolm": "Captain",
        "Kaylee": "Mechanic",
    ]
    occupations["Jayne"] = "Public Relations”

可以用初始化的语法来创建空的 array 或 dictionary。

    let emptyArray = String[]()
    let emptyDictionary = Dictionary<String, Float>()

If type information can be inferred, you can write an empty array as
[]—for
example, when you set a new value for a variable or pass an argument to
a function.

    shoppingList = []
    // Went shopping and bought everything.

‌

### Control Flow 

Use if to make conditionals,
and use for,
while to make
loops. Parentheses around the condition or loop variable are optional.
Braces around the body are required.

    let,
    103]
    var
    for {
        if {
            teamScore
        } else {
            teamScore
        }
    }
    teamScore

In an if statement, the conditional must be a Boolean
expression—this means that code such as if score 
is an error, not an implicit comparison to zero.

You can use if together to work
with values that might be missing. These values are represented as
optionals. An optional value either contains a value or contains
nil to indicate that the value is missing. Write a
question mark (?) after the type of a value to mark the
value as optional.

    var? =
    "Hello"
    optionalString
     
    var? =
    "John Appleseed"
    var
    if {
        greeting
    }

Experiment

Change optionalName. What greeting
do you get? Add an else clause that sets a different
greeting if optionalName.

If the optional value is nil, the conditional is
false and the code in braces is skipped. Otherwise, the
optional value is unwrapped and assigned to the constant after
let, which makes the unwrapped value available inside the
block of code.

Switches support any kind of data and a wide variety of comparison
operations—they aren’t limited to integers and tests for equality.

    let
    switch {
    case:
        let =
    "Add some raisins and make ants on a log."
    case:
        let =
    "That would make a good tea sandwich."
    case
    x):
        let =
    "Is it a spicy 
    default:
        let =
    "Everything tastes good in soup."
    }

Experiment

Try removing the default case. What error do you get?

After executing the code inside the switch case that matched, the
program exits from the switch statement. Execution doesn’t continue to
the next case, so there is no need to explicitly break out of the switch
at the end of each case’s code.

You use for to iterate over items in a
dictionary by providing a pair of names to use for each key-value pair.

    let = [
        "Prime",
    11],
        "Fibonacci",
    5],
        "Square",
    25],
    ]
    var
    for
    interestingNumbers {
        for {
            if {
                largest
            }
        }
    }
    largest

Experiment

Add another variable to keep track of which kind of number was the
largest, as well as what that largest number was.

Use while to repeat a block of code until a condition
changes. The condition of a loop can be at the end instead, ensuring
that the loop is run at least once.

    var
    while {
        n
    }
    n
     
    var
    do {
        m
    } while
    m

You can keep an index in a loop—either by using .. to
make a range of indexes or by writing an explicit initialization,
condition, and increment. These two loops do the same thing:

    var
    for {
        firstForLoop
    }
    firstForLoop
     
    var
    for \<
    3 {
        secondForLoop
    }
    secondForLoop

Use .. to make a range that omits its upper value, and
use ... to make a range that includes both values.

‌

### Functions and Closures 

Use func to declare a function. Call a function by
following its name with a list of arguments in parentheses. Use
-> to separate the parameter names and types from the
function’s return type.

    func,
    day {
        return
    "Hello 
    }
    greet)

Experiment

Remove the day parameter. Add a parameter to include
today’s lunch special in the greeting.

Use a tuple to return multiple values from a function.

    func,
    Double) {
        return)
    }
    getGasPrices()

Functions can also take a variable number of arguments, collecting them
into an array.

    func...) -\>
    Int {
        var
        for {
            sum
        }
        return
    }
    sumOf()
    sumOf)

Experiment

Write a function that calculates the average of its arguments.

Functions can be nested. Nested functions have access to variables that
were declared in the outer function. You can use nested functions to
organize the code in a function that is long or complex.

    func {
        var
        func() {
            y
        }
        add()
        return
    }
    returnFifteen()

Functions are a first-class type. This means that a function can return
another function as its value.

    func -\>
    Int) {
        func) -\>
    Int {
            return
        }
        return
    }
    var()
    increment)

A function can take another function as one of its arguments.

    func[],
    condition {
        for {
            if) {
                return
            }
        }
        return
    }
    func) -\>
    Bool {
        return
    }
    var,
    12]
    hasAnyMatches)

Functions are actually a special case of closures. You can write a
closure without a name by surrounding code with braces
( to separate the arguments and
return type from the body.

    numbers({
        (number
        let
        return
        })

Experiment

Rewrite the closure to return zero for all odd numbers.

You have several options for writing closures more concisely. When a
closure’s type is already known, such as the callback for a delegate,
you can omit the type of its parameters, its return type, or both.
Single statement closures implicitly return the value of their only
statement.

    numbers
    \* number)

You can refer to parameters by number instead of by name—this approach
is especially useful in very short closures. A closure passed as the
last argument to a function can appear immediately after the
parentheses.

    sort])
    

‌

### Objects and Classes 

Use class followed by the class’s name to create a class.
A property declaration in a class is written the same way as a constant
or variable declaration, except that it is in the context of a class.
Likewise, method and function declarations are written the same way.

    class {
        var
        func
    {
            return
    "A shape with 
        }
    }

Experiment

Add a constant property with let, and add another method
that takes an argument.

Create an instance of a class by putting parentheses after the class
name. Use dot syntax to access the properties and methods of the
instance.

    var()
    shape
    var =
    shape()

This version of the Shape class is missing something
important: an initializer to set up the class when an instance is
created. Use init to create one.

    class {
        var
        var
        
        init) {
            self
        }
        
        func
    {
            return
    "A shape with 
        }
    }

Notice how self is used to distinguish the
name argument to
the initializer. The arguments to the initializer are passed like a
function call when you create an instance of the class. Every property
needs a value assigned—either in its declaration (as with
numberOfSides) or in the initializer (as with
name).

Use deinit to create a deinitializer if you need to
perform some cleanup before the object is deallocated.

Subclasses include their superclass name after their class name,
separated by a colon. There is no requirement for classes to subclass
any standard root class, so you can include or omit a superclass as
needed.

Methods on a subclass that override the superclass’s implementation are
marked with override—overriding a method by accident,
without override, is detected by the compiler as an
error. The compiler also detects methods with override
that don’t actually override any method in the superclass.

    class {
        var
        
        init,
    name) {
            self
            super)
            numberOfSides
        }
        
        func {
            return
        }
        
        override()
    -\> String {
            return
    "A square with sides of length 
        }
    }
    let:
    5.2)
    test()
    test()

Experiment

Make another subclass of NamedShape called
Circle that takes a radius and a name as arguments to its
initializer. Implement an area and a
describe class.

In addition to simple properties that are stored, properties can have a
getter and a setter.

    class {
        var
        
        init,
    name) {
            self
            super)
            numberOfSides
        }
        
        var {
        get {
            return
        }
        set {
            sideLength
        }
        }
        
        override()
    -\> String {
            return
    "An equilateral triagle with sides of length 
        }
    }
    var =
    EquilateralTriangle,
    name)
    triangle
    triangle
    triangle

In the setter for perimeter, the new value has the
implicit name newValue. You can provide an explicit name
in parentheses after set.

Notice that the initializer for the EquilateralTriangle
class has three different steps:

1.  Setting the value of properties that the subclass declares.

2.  Calling the superclass’s initializer.

3.  Changing the value of properties defined by the superclass. Any
    additional setup work that uses methods, getters, or setters can
    also be done at this point.

If you don’t need to compute the property but still need to provide code
that is run before and after setting a new value, use
willSet. For example, the class
below ensures that the side length of its triangle is always the same as
the side length of its square.

    class {
        var {
        willSet {
            square =
    newValue
        }
        }
        var {
        willSet {
            triangle =
    newValue
        }
        }
        init:
    String) {
            square:
    size)
            triangle =
    EquilateralTriangle,
    name)
        }
    }
    var =
    TriangleAndSquare:
    "another test shape")
    triangleAndSquare
    triangleAndSquare
    triangleAndSquare =
    Square:
    "larger square")
    triangleAndSquare

Methods on classes have one important difference from functions.
Parameter names in functions are used only within the function, but
parameters names in methods are also used when you call the method
(except for the first parameter). By default, a method has the same name
for its parameters when you call it and within the method itself. You
can specify a second name, which is used inside the method.

    class {
        var
        func,
    numberOfTimes) {
            count
        }
    }
    var()
    counter,
    numberOfTimes)

When working with optional values, you can write ? before
operations like methods, properties, and subscripting. If the value
before the ?, everything after the
? is ignored and the value of the whole expression is
nil. Otherwise, the optional value is unwrapped, and
everything after the ? acts on the unwrapped value. In
both cases, the value of the whole expression is an optional value.

    let? =
    Square:
    "optional square")
    let =
    optionalSquare

‌

### Enumerations and Structures 

Use enum to create an enumeration. Like classes and all
other named types, enumerations can have methods associated with them.

    enum {
        case
        case,
    Five,
    Ten
        case
        func
    {
            switch {
            case:
                return
            case:
                return
            case:
                return
            case:
                return
            default:
                return
    String())
            }
        }
    }
    let
    let()

Experiment

Write a function that compares two Rank values by
comparing their raw values.

In the example above, the raw value type of the enumeration is
Int, so you only have to specify the first raw value. The
rest of the raw values are assigned in order. You can also use strings
or floating-point numbers as the raw type of an enumeration.

Use the toRaw functions to
convert between the raw value and the enumeration value.

    if =
    Rank) {
        let =
    convertedRank()
    }

The member values of an enumeration are actual values, not just another
way of writing their raw values. In fact, in cases where there isn’t a
meaningful raw value, you don’t have to provide one.

    enum {
        case,
    Diamonds
        func
    {
            switch {
            case:
                return
            case:
                return
            case:
                return
            case:
                return
            }
        }
    }
    let
    let =
    hearts()

Experiment

Add a color that returns
“black” for spades and clubs, and returns “red” for hearts and diamonds.

Notice the two ways that the Hearts member of the
enumeration is referred to above: When assigning a value to the
hearts constant, the enumeration member
Suit.Hearts is referred to by its full name because the
constant doesn’t have an explicit type specified. Inside the switch, the
enumeration is referred to by the abbreviated form
.Hearts is
already known to be a suit. You can use the abbreviated form anytime the
value’s type is already known.

Use struct to create a structure. Structures support many
of the same behaviors as classes, including methods and initializers.
One of the most important differences between structures and classes is
that structures are always copied when they are passed around in your
code, but classes are passed by reference.

    struct {
        var
        var
        func
    {
            return
    "The 
        }
    }
    let:
    .Three)
    let =
    threeOfSpades()

Experiment

Add a method to Card that creates a full deck of cards,
with one card of each combination of rank and suit.

An instance of an enumeration member can have values associated with the
instance. Instances of the same enumeration member can have different
values associated with them. You provide the associated values when you
create the instance. Associated values and raw values are different: The
raw value of an enumeration member is the same for all of its instances,
and you provide the raw value when you define the enumeration.

For example, consider the case of requesting the sunrise and sunset time
from a server. The server either responds with the information or it
responds with some error information.

    enum {
        case)
        case)
    }
     
    let =
    ServerResponse,
    "8:09 pm")
    let =
    ServerResponse)
     
    switch {
    case,
    sunset):
        let =
    "Sunrise is at 
    case):
        let =
    "Failure...  
    }

Experiment

Add a third case to ServerResponse and to the switch.

Notice how the sunrise and sunset times are extracted from the
ServerResponse value as part of matching the value
against the switch cases.

‌

### Protocols and Extensions 

Use protocol to declare a protocol.

    protocol {
        var {
    get
        mutating()
    }

Classes, enumerations, and structs can all adopt protocols.

    class {
        var =
    "A very simple class."
        var =
    69105
        func() {
            simpleDescription +=
    "  Now 100% adjusted."
        }
    }
    var()
    a()
    let =
    a
     
    struct
    {
        var =
    "A simple structure"
        mutating() {
            simpleDescription
        }
    }
    var()
    b()
    let =
    b

Experiment

Write an enumeration that conforms to this protocol.

Notice the use of the mutating keyword in the declaration
of SimpleStructure to mark a method that modifies the
structure. The declaration of SimpleClass doesn’t need
any of its methods marked as mutating because methods on a class can
always modify the class.

Use extension to add functionality to an existing type,
such as new methods and computed properties. You can use an extension to
add protocol conformance to a type that is declared elsewhere, or even
to a type that you imported from a library or framework.

    extension {
        var {
        return
        }
        mutating() {
            self
        }
    }
    7

Experiment

Write an extension for the Double type that adds an
absoluteValue property.

You can use a protocol name just like any other named type—for example,
to create a collection of objects that have different types but that all
conform to a single protocol. When you work with values whose type is a
protocol type, methods outside the protocol definition are not
available.

    let =
    a
    protocolValue
    // protocolValue.anotherProperty  // Uncomment to see the error

Even though the variable protocolValue has a runtime type
of SimpleClass, the compiler treats it as the given type
of ExampleProtocol. This means that you can’t
accidentally access methods or properties that the class implements in
addition to its protocol conformance.

‌

### Generics 

Write a name inside angle brackets to make a generic function or type.

    func:
    ItemType[] {
        var[]()
        for {
            result
        }
        return
    }
    repeat)

You can make generic forms of functions and methods, as well as classes,
enumerations, and structures.

    // Reimplement the Swift standard library's optional type
    enum\> {
        case
        case)
    }
    var:
    OptionalValue
    possibleInteger)

Use where after the type name to specify a list of
requirements—for example, to require the type to implement a protocol,
to require two types to be the same, or to require a class to have a
particular superclass.

    func
    where,
    T,
    T ==
    U,
    rhs {
        for {
            for {
                if {
                    return
                }
            }
        }
        return
    }
    anyCommonElements],
    [3])

Experiment

Modify the anyCommonElements function to make a function
that returns an array of the elements that any two sequences have in
common.

In the simple cases, you can omit where and simply write
the protocol or class name after a colon. Writing
<T: Equatable> is the same as writing
<T where T: Equatable>.
