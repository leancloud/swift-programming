Swift 概览
------------

按照传统，一门新语言的第一个程序应该在屏幕上打印出「Hello, world」。在 Swift 中这可以用一行完成：

    println("Hello, world")

如果你曾经用 C 或 Objective-C 写过程序，这样的写法应该看起来很熟悉 -- 在 Swift 中，这行代码是一个完整的程序。你不需要为输入输出或操作字符串这样的功能导入任何单独的库。在全局范围的代码会作为程序的入口运行，所以你不需要写一个 `main` 函数。你也无需用 `;` 来结束每个语句。

通过说明如果完成各种编程任务，这篇概览将让你得到足够的信息以开始编写 Swift 程序。即使碰到有什么你还不明白的也不用担心 -- 概览中介绍的所有内容都会在本书的后面章节中有详细解释。

> **建议**
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

> **实验**
> 创建一个显示指定为 `Float` 类型的值为 `4` 的常量。

值永远不会被自动转换为其他类型。如果你需要把一个值转换为其他类型，需要创建一个所需类型的实例。

    let label = "The width is "
    let width = 94
    let widthLabel = label + String(width)

> **实验**
> 试试从最后一行里把到 `String` 的转换去掉。你看到什么错误？

有一个更简单的在字符串中包含值的方法：把值写在括号中，并在括号前面加一个反斜杠（`\`）。例如：

    let apples = 3
    let oranges = 5
    let appleSummary = "I have \(apples) apples."
    let fruitSummary = "I have \(apples + oranges) pieces of fruit."

> **实验**
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

当类型信息可以被推导出来时，你可以用 `[]` 表示一个空 array 或用 `[:]` 表示一个空 dictionary -- 例如，当你给变量赋值或给函数传递参数时。

    shoppingList = [] // Went shopping and bought everything.

‌

### 控制流

使用 `if` 和 `switch` 来构造条件，使用 `for`-`in`、`for`、`while` 和 `do`-`while` 来构造循环。在条件或循环变量两边的括号是可选的，在主体两边的花括号是必须的。

    let individualScores = [75, 43, 103, 87, 12]
    var teamScore = 0
    for score in individualScores {
        if score > 50 {
            teamScore += 3
        } else {
            teamScore += 1
        }
    }
    teamScore

在 `if` 语句中，条件必须是布尔表达式 -- 也就是说像 `if score { ... }` 这样的代码是错误的，它不是一个与零的隐式比较。

你可以把 `if` 和 `let` 在一起用以操作可能为空的值。这些值被表示为可选的。一个可选值要么有一个值，要么是 `nil` 以表示值不存在。在一个值的类型类型后面加一个问号（`?`）来把它标记为可选的。

    var optionalString: String? = "Hello"
    optionalString == nil

    var optionalName: String? = "John Appleseed"
    var greeting = "Hello!"
    if let name = optionalName {
        greeting = "Hello, \(name)"
    }

> **实验**
> 把 `optionalName` 改为 `nil`。你得到怎么样的问候？加一个 `else` 子句以在 `optionalName` 为 `nil` 时设定一个不同的问候语。

当可选值为 `nil` 时，条件为 `false`，那么花括号里的语句就被跳过了。否则 `optionalName` 里的值就被赋值给 `let` 之后的常量，它让这个值在后面的代码块中可用。

`switch` 支持任何类型的数据以及多种比较操作 -- 并不仅限于整数和对相等的测试。

    let vegetable = "red pepper"
    switch vegetable {
    case "celery":
        let vegetableComment = "Add some raisins and make ants on a log."
    case "cucumber", "watercress":
        let vegetableComment = "That would make a good tea sandwich."
    case let x where x.hasSuffix("pepper"):
        let vegetableComment = "Is it a spicy \(x)?"
    default:
        let vegetableComment = "Everything tastes good in soup."
    }

> **实验**
> 试着把 `default` 部分去掉，你会看到什么错误？

执行完匹配的 `case` 后，程序会跳出整个 `switch` 语句而不会继续执行下一个 `case`，所以不需要在每一个 `case` 的最后显式地跳出。

你可以通过在 `for-in` 语句中提供一对名字表示每对 key-value 来迭代访问一个 dictionary 的每个元素。

    let interestingNumbers = [
        "Prime": [2, 3, 5, 7, 11, 13],
        "Fibonacci": [1, 1, 2, 3, 5, 8],
        "Square": [1, 4, 9, 16, 25],
    ]
    var largest = 0
    for (kind, numbers) in interestingNumbers {
        for number in numbers {
            if number > largest {
                largest = number
            }
        }
    }
    largest

> **实验**
> 增加一个变量来在追踪最大数字的同时也追踪那个数字的类别。

使用 `while` 来重复执行一段代码直到条件改变。

一个循环的条件也可以在循环的尾部，这样循环主体会执行至少一次。

    var n = 2
    while n < 100 {
        n = n * 2
    }
    n

    var m = 2
    do {
        m = m * 2
    } while m < 100
    m

你可以在循环中使用一个索引 -- 可以用 `..` 来创建一个索引的范围或者显式地写出初始化、条件、递增。下面的两个循环做的事是一样的：

    var firstForLoop = 0
    for i in 0..3 {
        firstForLoop += i
    }
    firstForLoop

    var secondForLoop = 0
    for var i = 0; i < 3; ++i {
        secondForLoop += 1
    }
    secondForLoop

用 `..` 创建不包含上限值的范围，用 `...` 创建包含两端的范围。

### 函数和闭包

用 `func` 来声明一个函数。通过在函数名后接上用括号包住的参数列表来调用一个函数。用 `->` 来分割参数名和函数的返回类型。

    func greet(name: String, day: String) -> String {
        return "Hello \(name), today is \(day)."
    }
    greet("Bob", "Tuesday")

> **实验**
> 去掉 `day` 参数。增加一个参数以把当天的午餐特价菜包含在问候中。

用一个 tuple 来从函数返回多个值。

    func getGasPrices() -> (Double, Double, Double) {
        return (3.59, 3.69, 3.79)
    }
    getGasPrices()

函数也可以接受可变个数的参数，参数被收集到一个 array 里。

    func sumOf(numbers: Int...) -> Int {
        var sum = 0
        for number in numbers {
            sum += number
        }
        return sum
    }
    sumOf()
    sumOf(42, 597, 12)

> **实验**
> 写一个计算所有参数平均值的函数。

函数是可以嵌套的。嵌套的函数可以访问在外层函数声明的变量。你可以用嵌套函数来组织一个很长或很复杂的函数中的代码。

    func returnFifteen() -> Int {
        var y = 10
        func add() {
            y += 5
        }
        add()
        return y
    }
    returnFifteen()

函数是一个一级的类型。这意味着一个函数可以把另一个函数作为它的返回值返回。

    func makeIncrementer() -> (Int -> Int) {
        func addOne(number: Int) -> Int {
            return 1 + number
        }
        return addOne
    }
    var increment = makeIncrementer()
    increment(7)

一个函数也可以作为另一个函数的参数。

    func hasAnyMatches(list: Int[], condition: Int -> Bool) -> Bool {
        for item in list {
            if condition(item) {
                return true
            }
        }
        return false
    }
    func lessThanTen(number: Int) -> Bool {
        return number < 10
    }
    var numbers = [20, 19, 7, 12]
    hasAnyMatches(numbers, lessThanTen)

函数事实上是闭包（closure）的一种特殊形式。可以在花括号（`{}`）之间包含代码来构造一个匿名的闭包。使用 `in` 把参数和返回值类型与主体分隔开。

    numbers.map({
        (number: Int) -> Int in
        let result = 3 * number
        return result
        })

> **实验**
> 重写这个闭包，让它对所有奇数返回零。

你有几种更简洁地表示闭包的方式。当已知一个闭包的类型时，如作为 delegate 的回调时，你可以省略参数的类型、返回值类型、或两者。单语句的闭包隐式地返回这个语句的结果。

    numbers.map({ number in 3 * number })

你可以用数字而不是名称来引用参数 -- 这种方式对很短的闭包特别有用。被作为最后的参数传递给一个函数的闭包可以出现在括号后面。

    sort([1, 5, 3, 12, 2]) { $0 > $1 }

### 对象和类

用 `class` 后面跟上类名来创建一个类。类里的属性是用与常量和变量相同的方式声明的，只不过是在一个类的上下文中而已。同理，方法的声明也和函数一样。

    class Shape {
        var numberOfSides = 0
        func simpleDescription() -> String {
            return "A shape with \(numberOfSides) sides."
        }
    }

> **实验**
> 用 `let` 增加一个常量属性，并增加另一个接受一个参数的方法。

通过把一对括号放在类名后面可以创建一个类的实例。用点操作符可以访问这个实例的属性和方法。

    var shape = Shape()
    shape.numberOfSides = 7
    var shapeDescription = shape.simpleDescription()

这个版本的 `Shape` 类还少了样重要的东西：一个在实例创建时用来做设置的构造方法。用 `init` 可以创建一个。

    class NamedShape {
        var numberOfSides: Int = 0
        var name: String

        init(name: String) {
            self.name = name
        }

        func simpleDescription() -> String {
            return "A shape with \(numberOfSides) sides."
        }
    }

注意 `self` 用来区分叫 `name` 的属性和传递给构造方法的 `name` 参数。构造方法的参数在创建实例时以函数参数同样的方式传递。所有的属性都需要被赋予一个值 -- 要么在声明里（如 `numberOfSides`），要么在构造方法里（如 `name`）。

如果你希望在对象被清除时进行一些清理工作，可以用 `deinit` 来创建一个析构方法。

定义子类时把父类的名称放在后面，用冒号隔开。类不需要继承任何标准的根类，所以你可以根据需要包含或省略父类。

子类里重载父类实现的方法需要标记 `override` -- 没有 `override` 而偶然地重载一个方法会被编译器检测为一个错误。编译器也会检测有 `override` 却并没有实际重载一个父类方法的情况。

    class Square: NamedShape {
        var sideLength: Double

        init(sideLength: Double, name: String) {
            self.sideLength = sideLength
            super.init(name: name)
            numberOfSides = 4
        }

        func area() ->  Double {
            return sideLength * sideLength
        }

        override func simpleDescription() -> String {
            return "A square with sides of length \(sideLength)."
        }
    }
    let test = Square(sideLength: 5.2, name: "my test square")
    test.area()
    test.simpleDescription()

> **实验**
> 创建另一个叫 `Circle` 的 `NameShape` 的子类，它的构造方法接受一个半径和一个名称作为参数。实现一个 `area` 和一个 `describe` 函数。

除了只是简单存储的属性外，属性也可以有 getter 和 setter。

    class EquilateralTriangle: NamedShape {
        var sideLength: Double = 0.0

        init(sideLength: Double, name: String) {
            self.sideLength = sideLength
            super.init(name: name)
            numberOfSides = 3
        }

        var perimeter: Double {
        get {
            return 3.0 * sideLength
        }
        set {
            sideLength = newValue / 3.0
        }
        }

        override func simpleDescription() -> String {
            return "An equilateral triagle with sides of length \(sideLength)."
        }
    }
    var triangle = EquilateralTriangle(sideLength: 3.1, name: "a triangle")
    triangle.perimeter
    triangle.perimeter = 9.9
    triangle.sideLength

在 `perimeter` 的 setter 里，参数有一个叫 `newValue` 的隐式名称。你也可以在 `set` 后的括号内提供一个显式名称。

注意 `EquilateralTriangle` 类的构造方法有三个步骤：

1. 设定这个子类声明的三个属性的值。
2. 调用父类的构造方法。
3. 改变父类里声明的属性的值。任何其他使用方法、getter、setter 的工作也可以在这里进行。

如果你不需要计算出一个属性的值，但需要确保一些代码在设定一个新值之前或之后运行，使用 `willSet` 和 `didSet`。比如，下面的类会确保它的三角形的边长总是和它的方形的边长相等。

    class TriangleAndSquare {
        var triangle: EquilateralTriangle {
        willSet {
            square.sideLength = newValue.sideLength
        }
        }
        var square: Square {
        willSet {
            triangle.sideLength = newValue.sideLength
        }
        }
        init(size: Double, name: String) {
            square = Square(sideLength: size, name: name)
            triangle = EquilateralTriangle(sideLength: size, name: name)
        }
    }
    var triangleAndSquare = TriangleAndSquare(size: 10, name: "another test shape")
    triangleAndSquare.square.sideLength
    triangleAndSquare.triangle.sideLength
    triangleAndSquare.square = Square(sideLength: 50, name: "larger square")
    triangleAndSquare.triangle.sideLength

与函数相比，类的方法有一个重要的不同点。函数的参数名只在函数内部使用，而方法的参数名也在调用这个方法时使用（第一个参数除外）。默认情况下，一个方法的参数名在调用时和在方法内部是一样的。你也可以指定一个只在方法内部使用的名称。

    class TriangleAndSquare {
        var triangle: EquilateralTriangle {
        willSet {
            square.sideLength = newValue.sideLength
        }
        }
        var square: Square {
        willSet {
            triangle.sideLength = newValue.sideLength
        }
        }
        init(size: Double, name: String) {
            square = Square(sideLength: size, name: name)
            triangle = EquilateralTriangle(sideLength: size, name: name)
        }
    }
    var triangleAndSquare = TriangleAndSquare(size: 10, name: "another test shape")
    triangleAndSquare.square.sideLength
    triangleAndSquare.triangle.sideLength
    triangleAndSquare.square = Square(sideLength: 50, name: "larger square")
    triangleAndSquare.triangle.sideLength

在对待可选值时，你可以在调用方法、访问属性、下标等操作前使用 `?`。如果 `?` 之前的值为 `nil`，所有 `?` 之后的东西都会被忽略，整个表达式的值就是 `nil`。否则的话 `?` 后面的操作就作用在这个打开的值上。在这两种情况下，整个表达式的值都是可选值。

    let optionalSquare: Square? = Square(sideLength: 2.5, name: "optional square")
    let sideLength = optionalSquare?.sideLength

### 枚举和结构

用 `enum` 来创建一个枚举。就像类和其他命名的类型一样，枚举可以有相应的方法。

    enum Rank: Int {
        case Ace = 1
        case Two, Three, Four, Five, Six, Seven, Eight, Nine, Ten
        case Jack, Queen, King
        func simpleDescription() -> String {
            switch self {
            case .Ace:
                return "ace"
            case .Jack:
                return "jack"
            case .Queen:
                return "queen"
            case .King:
                return "king"
            default:
                return String(self.toRaw())
            }
        }
    }
    let ace = Rank.Ace
    let aceRawValue = ace.toRaw()

> **实验**
> 写一个函数来通过比较原始值来比较两个 `Rank` 的值。

在上面的例子中，因为枚举的原始值类型是 `Int`，你只需要给出第一个原始值。剩下的原始值会按顺序赋值。你也可以用字符串或浮点数作为枚举的原始值类型。

使用 `toRaw` 和 `fromRaw` 方法来在原始值和枚举值之间转换。

    if let convertedRank = Rank.fromRaw(3) {
        let threeDescription = convertedRank.simpleDescription()
    }

枚举的成员值是真实的值，而并不只是原始值的别称。事实上，但不存在有意义的原始值时，你不需要提供原始值。

    enum Suit {
        case Spades, Hearts, Diamonds, Clubs
        func simpleDescription() -> String {
            switch self {
            case .Spades:
                return "spades"
            case .Hearts:
                return "hearts"
            case .Diamonds:
                return "diamonds"
            case .Clubs:
                return "clubs"
            }
        }
    }
    let hearts = Suit.Hearts
    let heartsDescription = hearts.simpleDescription()

> **实验**
> 为 `Suit` 增加一个 `color` 方法。"spades" 和 "clubs" 返回 "black"，"hearts" 和 "diamonds" 返回 "red"。

注意引用上面枚举的 `Hearts` 成员的两种方式：但给 `hearts` 常量赋值时，使用全名 `Suit.Hearts` 引用，因为这个常数没有一个指定的类型。在 `switch` 中，使用了缩略形式 `.Hearts`，因为已经知道 `self` 是 `Suit` 类型的。在任何已经知道值的类型时都可以使用这种缩略形式。

使用 `struct` 来创建一个结构。结构支持类的很多行为和特性，包括方法、构造方法等等。结构和类的最重要差别之一是当结构在程序中传递时总是被复制，而类被传递时总是按引用传递。

    struct Card {
        var rank: Rank
        var suit: Suit
        func simpleDescription() -> String {
            return "The \(rank.simpleDescription()) of \(suit.simpleDescription())"
        }
    }
    let threeOfSpades = Card(rank: .Three, suit: .Spades)
    let threeOfSpadesDescription = threeOfSpades.simpleDescription()

> **实验**
> 给 `Card` 增加一个函数来创建全套扑克牌，包括花色和大小的所有组合。

一个枚举成员的实例可以有关联的值。同一个枚举成员的不同实例可以有不同的值想关联。在创建实例的时候，你提供关联的值。这个关联的值和原始值是不同的：一个枚举成员的原始值对它的所有实例都是相同的，并且你在定义这个枚举的时候就给出了原始值。

举个例子，假设你要从服务器读取日出和日落的时间。服务器要么返回你要的信息，要么返回一些错误。

    enum ServerResponse {
        case Result(String, String)
        case Error(String)
    }

    let success = ServerResponse.Result("6:00 am", "8:09 pm")
    let failure = ServerResponse.Error("Out of cheese.")

    switch success {
    case let .Result(sunrise, sunset):
        let serverResponse = "Sunrise is at \(sunrise) and sunset is at \(sunset)."
    case let .Error(error):
        let serverResponse = "Failure...  \(error)"
    }

> **实验**
> 给 `ServerResponse` 增加第三种情况。

留意日出和日落的时间是如何作为 `switch` 分支匹配的一部分从 `ServerResponse` 的值里被提取出来的。

### 协议和扩展

使用 `protocol` 来声明一个协议。

    protocol ExampleProtocol {
        var simpleDescription: String { get }
        mutating func adjust()
    }

类、枚举和结构都可以服从协议。

    class SimpleClass: ExampleProtocol {
        var simpleDescription: String = "A very simple class."
        var anotherProperty: Int = 69105
        func adjust() {
            simpleDescription += "  Now 100% adjusted."
        }
    }
    var a = SimpleClass()
    a.adjust()
    let aDescription = a.simpleDescription

    struct SimpleStructure: ExampleProtocol {
        var simpleDescription: String = "A simple structure"
        mutating func adjust() {
            simpleDescription += " (adjusted)"
        }
    }
    var b = SimpleStructure()
    b.adjust()
    let bDescription = b.simpleDescription

> **实验**
> 写一个服从这个协议的枚举。

注意在 `SimpleStructure` 的声明里使用了 `mutating` 关键字来标注了改变这个结构的一个方法。`SimpleClass` 的声明中不需要这样的标注，因为类的方法都可以改变它。

使用 `extension`（扩展）来为现有类型增加新的功能，比如新的方法和计算出的属性。你也可以用扩展来为一个在其他地方声明的类型（甚至是一个从第三方库或者框架导入的类型）增加对协议的服从性。

    extension Int: ExampleProtocol {
        var simpleDescription: String {
        return "The number \(self)"
        }
        mutating func adjust() {
            self += 42
        }
    }
    7.simpleDescription

> **实验**
> 为 `Double` 类型写一个扩展，增加一个 `absoluteValue` 属性。

你可以像任何命名的类型一样使用一个协议名 -- 比如创建一个包含不同类型但服从同一协议的对象的集合。在你操作协议类型的值时，协议之外的方法是不可用的。

    let protocolValue: ExampleProtocol = a
    protocolValue.simpleDescription
    // protocolValue.anotherProperty  // Uncomment to see the error

虽然 `protocolValue` 变量的运行时类型是 `SimpleClass`, 编译器把它作为声明的 `ExampleProtocol` 类型对待。这意味着你不能访问这个类在除协议规定之外另外实现的方法和属性。

### 泛型

通过把类型变量写在方括号里来创建一个泛型函数或类型。

    func repeat<ItemType>(item: ItemType, times: Int) -> ItemType[] {
        var result = ItemType[]()
        for i in 0..times {
            result += item
        }
        return result
    }
    repeat("knock", 4)

你可以创建泛型形式的函数和方法，以及类、枚举和结构。

    // Reimplement the Swift standard library's optional type
    enum OptionalValue<T> {
        case None
        case Some(T)
    }
    var possibleInteger: OptionalValue<Int> = .None
    possibleInteger = .Some(100)

在类型变量后面加上 `where` 来指定一系列的需求 -- 例如，要求类型服从某个协议，要求两个类型相同，或者要求一个类有某个特定的父类。

    func anyCommonElements <T, U where T: Sequence, U: Sequence, T.GeneratorType.Element: Equatable, T.GeneratorType.Element == U.GeneratorType.Element> (lhs: T, rhs: U) -> Bool {
        for lhsItem in lhs {
            for rhsItem in rhs {
                if lhsItem == rhsItem {
                    return true
                }
            }
        }
        return false
    }
    anyCommonElements([1, 2, 3], [3])

> **实验**
> 修改 `anyCommonElements` 函数让他返回两个序的共有元素的数组。

在简单情况下，你可以省略 `where` 而把协议名或类名写在冒号之后。`<T: Equatable>` 和 `<T where: T: Equatable>` 是等价的。