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

当类型信息可以被推导出来时，你可以用 `[]` 表示一个空 array 或用 `[:]` 表示一个空 dictionary - 例如，当你给变量赋值或给函数传递参数时。

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

在 `if` 语句中，条件必须是布尔表达式 - 也就是说像 `if score { ... }` 这样的代码是错误的，它不是一个与零的隐式比较。

你可以把 `if` 和 `let` 在一起用以操作可能为空的值。这些值被表示为可选的。一个可选值要么有一个值，要么是 `nil` 以表示值不存在。在一个值的类型类型后面加一个问号（`?`）来把它标记为可选的。

    var optionalString: String? = "Hello"
    optionalString == nil

    var optionalName: String? = "John Appleseed"
    var greeting = "Hello!"
    if let name = optionalName {
        greeting = "Hello, \(name)"
    }

> 实验
>
> 把 `optionalName` 改为 `nil`。你得到怎么样的问候？加一个 `else` 子句以在 `optionalName` 为 `nil` 时设定一个不同的问候语。

当可选值为 `nil` 时，条件为 `false`，那么花括号里的语句就被跳过了。否则 `optionalName` 里的值就被赋值给 `let` 之后的常量，它让这个值在后面的代码块中可用。

`switch` 支持任何类型的数据以及多种比较操作 - 并不仅限于整数和对相等的测试。

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

> 实验
>
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

> 实验
>
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

你可以在循环中使用一个索引 - 可以用 `..` 来创建一个索引的范围或者显式地写出初始化、条件、递增。下面的两个循环做的事是一样的：

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

> 实验
>
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

> 实验
>
> 写一个计算所有参数平均值的函数。

函数是可以嵌套的。嵌套的函数可以访问在外层函数声明的变量。你可以用嵌套函数来组织一个很长或很复杂的函数中的代码。