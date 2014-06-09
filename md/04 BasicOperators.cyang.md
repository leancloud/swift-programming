基础运算符
------------

*运算符*是一种可以检查、修改或结合数值的特殊符号或短语。例如，加法运算符可以将两个数字相加（ `let i = 1 + 2` ）。
更复杂的例子还包括逻辑与运算符 `&&`（ `if enteredDoorCode && passedRetinaScan` ）以及可以简化增量操作的运算符 `++i`。

Swift 支持大多数标准 C 运算符，并增强了避免常见编码错误的能力。赋值运算符（ `=` ）没有返回值，这可以防止误用（ `=` ）和等于符号（ `==` ）。
算数运算符（ `+` ，`*` ）会检测且禁止数值溢出，避免因处理数据不当而导致的意外结果。你可以使用 Swift 的溢出运算符来自定义溢出行为，详情请参考 [溢出运算符](AdvancedOperators.xhtml#TP40014097-CH27-XID_37)。

Swift 并不像 C 那样允许你对浮点数做求余运算。它提供了两种 C 不曾拥有的范围运算符（ `a..b` ），这样的运算符可以非常方便地表示数据范围。

本章将会详细解读 Swift 的常用运算符。[高级运算符](AdvancedOperators.xhtml) 则涵盖了 Swift 的高级运算符，它会告诉你如何定义你自己的运算符，并为你自己的类型实现标准运算符。
‌

### 专有名词

运算符包括一元、二元和三元运算符：
    
- 	*一元*运算符只能作用于单一操作数（例如 -a）。一元*前缀*运算符位于操作数头部（例如 !b），而一元*后缀*运算符位于操作数尾部（例如 i++）。

- 	*二元*运算符作用于两个操作数（例如 2 + 3），并且位于两个操作数中间。

- 	*三元*运算符作用于三个操作数。和 C 类似，Swift只有一个三元运算符，也就是三元条件运算符（a ? b : c）。

The values that operators affect are *operands*. In the expression
1 + 2 symbol is a binary operator
and its two operands are the values 1 and 2.

运算符所影响的数值叫做*操作数*。在表达式 `1 + 2` 中，`+` 就是一个二元运算符，他的两个操作数就是数值 `1` 和 `2` 。
‌

### 赋值运算符

*赋值运算符*（ `a = b` ）可用于初始化或更改 `a` 的值。
	
	let b = 10
	var a = 5
	a = b
	// 现在 a 等于 10
    
如果赋值符号的右边是拥有多个数值的元组，那么这个元组的各个元素可以一次性分解为多个常量或变量：

	let (x, y) = (1, 2)
	// x 等于 1，y 等于 2

与 C 和 Objective-C 的赋值运算符不同，Swift 的赋值运算符并没有返回值。下面的语句是非法的：
	
	if x = y {
		// 该语句非法，因为 x = y 不会返回任何值
	}

当你想要使用等于符号（ `==` ）时，Swift的这个特性（赋值运算符无返回值）使得赋值运算符（ `=` ）很难被意外使用，并因此而带来灾难性的后果。通过将 `if x = y` 置为非法语句，Swift 可以帮助你的代码避免类似的错误。


### 算数运算符

Swift 支持所有类型的四则*算数运算符*：

-   加法（ `+` ）

-   减法（ `-` ）

-   乘法（ `*` ）

-   除法（ `/` ）
	
```
1 + 2 		// 等于 3
5 - 3 		// 等于 2
2 * 3 		// 等于 6
10.0 / 2.5  // 等于4.0
```

与 C 和 Objective-C 的算数运算符不同，Swift 的算数运算符默认禁止数值溢出。你可以使用 Swift 的溢出运算符（例如 `a &+ b`）来选择数值溢出相关行为。详情参考 [溢出运算符](AdvancedOperators.xhtml#TP40014097-CH27-XID_37)。

加法运算符也支持字符串连接：

	"hello, " + "world" // 等于 “hello, world”

两个字符，或者一个字符与一个字符串，都可以相加构造为一个新的字符串：
	
	let dog: Character = "🐶"
	let cow: Character = "🐮"
	“let dogCow = dog + cow”
	// dogCow 等于 "🐶🐮"

详情请参考 [字符串与字符连接](StringsAndCharacters.xhtml#TP40014097-CH7-XID_379)。
‌

### 求余运算符

*余数*的定义是这样的：b 减去 b 可以容纳的 a 的最大倍数，例如 `7 % 3 = 7- (3 * 2) = 1`。求余运算符（ `a % b` ）就是用来计算余数的运算符。

> **注意**
>
> 在其他语言中，求余运算符（ `%` ）也叫做*取模运算符*。而从严格意义上讲，Swift 的求余运算符对负数是做求余操作，而不是取模操作。

下面是求余运算符的工作原理。计算 `9 % 4`，首先你需要计算出 9 能容纳多少个 4：

//////image//////////

9 能容纳两个 4，余数应该为 1（橙色部分）。

在 Swift 中，上面的运算可以这样表示:
	
	9 % 4 // 等于 1

为了计算 `a % b` 的结果，`%` 运算符需要解如下方程，并输出 remainder：

```
a = (b * some multiplier) + remainder
```
其中 some mutiplier 是 b 的最大倍数。

把 9 和 4 代入上述方程，可以得到：

```
9 = (4 * 2) + 1
```
The same method is applied when calculating the remainder for a negative
value of a:

    -9

同样的方法可以用来计算某个负数的余数：

```
-9 % 4 // 等于 -1
```
把 -9 和 4 代入前文提到的方程，可以得到：

```
-9 = (4 * -2) + -1
```

最终计算出余数为 -1。

在求余计算中，负数 b 的符号会被忽略。也就是说，`a % b` 和 `a % -b` 会得到相同的结果。
‌

### 浮点求余运算

与 C 和 Objective-C 的求余运算符不同，Swift 的求余运算符可以作用于浮点数：

```
8 % 2.5 // 等于 0.5
```

‌在上面这个例子中，8 除以 2.5 等于 3，余数为 0.5，所以求余运算符返回一个 `Double` 值 0.5。
/////image/////

### 增量与减量运算符
    
和 C 类似，Swift 也提供了可以便捷的对某个数字做加一或减一操作的运算符：*增量运算符*和*减量运算符*。你可以使用者两个运算符对整型或浮点型变量做操作：
	
	var i = 0
	++i		 // 现在 i 等于 1

每当你调用 `++i`，i 的值就会加一。本质上讲，`++i` 是 `i = i + 1`的缩写。类似的，`--i` 可以作为 `i = i - 1` 的缩写。

`++` 和 `--` 这两个运算符可以用作前缀或后缀运算符。若想让 i 加一，`i++` 和 `++i`都是合法的表达式。同理，`i--` 和 `--i` 都会导致 i 减一。
    
需要注意的是，这两个运算符不仅会修改 `i` 的数值，还会产生返回值。如果只想修改存储在 `i` 中的数值，你可以忽略返回值。然而，如果要使用返回值，你需要根据如下规则来区分前缀与后缀运算符：

-	如果运算符位于变量之前，那么先修改变量，后返回数值。
-	如果运算符位于变量之后，那么先返回值，后修改变量。
    
例如：

    var a = 0
    let b = ++a
    // a 和 b 现在等于 1
    let c = a++
    // a 现在等于 2，但是 c 被赋值为 a 增长之前的值:1

在上面的例子中，`let b = ++a` 先对 a 加一，然后返回它的值。这就是为什么 a 和 b 都等于新的值 1。

然而，`let c = a++` 在返回值之后对 a 加一。这意味着 c 获得旧值 1，然后 a 被更改为 2。

‌除非你需要利用 `i++` 的特殊行为，否则在任何场景都推荐使用 `++i` 和 `--i`。因为后者总是能返回你所期望的数值，也就是对旧值加一或减一之后的结果。

### 一元负运算符

数字的符号可以通过前缀符号 `-` 来做切换，这也就是所谓的*一元负运算符*：
	
	let three = 3
	let minusThree = -three         // minusThree 等于 -3
	let plusThree = -minusThree     // plusThree 等于 3

一元负运算符（ `-` ）直接位于操作数的前面，中间不能有空格。
‌

### 一元加运算符

*一元加运算符*直接返回操作数的值，不对其做任何修改：

	let minusSix = -6
	let alsoMinusSix = +minusSix  // alsoMinusSix 等于 -6
		
‌尽管一元加运算符不会对数值做任何修改，你仍然可以使用它来提高代码可读性。比如正数与负数通过两种不同的运算符来达到一种"对称"的视觉效果。

### 复合赋值运算符 
    
与 C 类似，Swift 提供*复合赋值运算符*来结合赋值（ `=` ）与其他操作。下面是一个*加法赋值运算符*（ `+=` ）的例子：
	var a = 1
	a += 2
	// 现在 a 等于 3

表达式 `a += 2` 是 `a = a + 2` 的缩写。实际上，把加法和赋值运算符结合到一起会同时执行两个任务。

> 注意
>
> 复合赋值运算符没有返回值。例如，类似 `let b = a += 2` 这样的代码是非法的。它和前面提到的
> 增量或减量运算符有着不一样的行为。

有关复合赋值运算符的完整列表，可以参考 [表达式](Expressions.xhtml)。
‌

### 比较运算符

Swift 支持所有标准 C *比较运算符*：

-	等于（ `a == b` ）
-	不等于（ `a != b` ）
-	大于（ `a > b` ）
-	小于（ `a < b` ）
-	大于或等于（ `a >= b` ）
-	小于或等于（ `a <= b` ）


> 注意
>
> Swift 还提供了两种用于测试两个对象引用是否指向同一个对象实例的*标示运算符*（ `===` 和 `!==`）。更多信息，可以参考[对象与结构体](lassesAndStructures.xhtml)

每个比较运算符返回标示某个表达式是否为 true 的布尔值:

```
1 == 1 	// true，因为 1 等于 1
2 != 1  // true，因为 2 不等于 1
2 > 1	// true，因为 2 大于 1
1 < 2	// true，因为 1 小于 2
1 >= 1	// true，因为 1 大于或等于 1
2 <= 1	// false，因为 2 小于或等于 1
```	
    
比较运算符经常用在条件语句中，比如 if 语句：
	
	let name = "world"
	if name == "world" {
		println("hello, world")
	} else {
		println("I'm sorry \(name), but I don't recognize you")
	}
	// 因为 name 确实等于 "wolrd"，所有输出 "hello, world"

更多关于 if 语句的信息，参考[控制流](ControlFlow.xhtml)
‌

### 三元条件运算符 

*三元条件运算符*是一种特殊的运算符，拥有三个部分，通常以这样的形式存在：`question ? answer1 : answer2`。它根据 `question` 是否为 true 来决定到底对哪个表达式求值。如果 `question` 为 true，那么执行 `answer1` 并返回其值，否则执行 `answer1` 并返回其值。

三元条件运算符是下面代码的缩写:

    if question {
    	answer1
    } else {
    	answer2
    }


这是一个计算表格行像素高度的例子。如果该行有 header，那么行高应该比内容高度大 50 个像素，否则应该大 20 个像素：
	
	let contentHeight = 40
	let hasHeader = true
	let rowHeight = contentHeight + (hasHeader ? 50 : 20)
	// rowHeight 等于 90
    
前面的代码是下面这个例子的缩写：
	
	let contentHeight = 40
	let hasHeader = true
	var rowHeight = contentHeight 
	if hasHeader {
    	rowHeight = rowHeight + 50
	} else {
    	rowHeight = rowHeight + 20
	}
	// rowHeight 等于 90
   

第一个例子使用了三元条件运算符，意味着可以使用一行代码来为 rowHeight 设置正确的值。这样就比第二个例子更简洁。因为 rowHeight 的值在 if 语句的作用域里面不会被修改，根本不必将 rowHeight 声明为一个变量。

三元条件运算符提供了一种高效的缩写来决定到底应该从两个表达式中选择哪一个求值。然而，你仍然需要谨慎使用三元条件运算符。如果过度使用，它自身的简洁性可能会降低代码的可读性。因此，应该尽可能避免把多个三元条件运算符组合到一个复合表达式中。
‌

### Range Operators 

Swift includes two *range operators*, which are shortcuts for expressing
a range of values.

‌

### Closed Range Operator 

The *closed range operator* (a...b) defines a range that
runs from a, and includes the values
a.

The closed range operator is useful when iterating over a range in which
you want all of the values to be used, such as with a
for loop:

    for {
        println
    \* 5)
    }
    // 1 times 5 is 5
    // 2 times 5 is 10
    // 3 times 5 is 15
    // 4 times 5 is 20
    // 5 times 5 is 25

For more on for loops, see [Control
Flow](ControlFlow.xhtml).

‌

### Half-Closed Range Operator 

The *half-closed range operator* (a..b) defines a range
that runs from a, but does not
include b. It is said to be *half-closed* because it
contains its first value, but not its final value.

Half-closed ranges are particularly useful when you work with zero-based
lists such as arrays, where it is useful to count up to (but not
including) the length of the list:

    let,
    "Brian"]
    let
    for {
        println +
    1)
    }
    // Person 1 is called Anna
    // Person 2 is called Alex
    // Person 3 is called Brian
    // Person 4 is called Jack

Note that the array contains four items, but 0..count
only counts as far as 3 (the index of the last item in
the array), because it is a half-closed range. For more on arrays, see
[Arrays](CollectionTypes.xhtml#TP40014097-CH8-XID_135).

‌

### Logical Operators 

*Logical operators* modify or combine the Boolean logic values
true. Swift supports the three
standard logical operators found in C-based languages:

-   Logical NOT (!a)

-   Logical AND (a && b)

-   Logical OR (a || b)

‌

### Logical NOT Operator 

The *logical NOT operator* (!a) inverts a Boolean value
so that true, and
false.

The logical NOT operator is a prefix operator, and appears immediately
before the value it operates on, without any white space. It can be read
as “not a”, as seen in the following example:

    let
    if {
        println)
    }
    // prints "ACCESS DENIED"

The phrase if !allowedEntry can be read as “if not
allowed entry.” The subsequent line is only executed if “not allowed
entry” is true; that is, if allowedEntry is
false.

As in this example, careful choice of Boolean constant and variable
names can help to keep code readable and concise, while avoiding double
negatives or confusing logic statements.

‌

### Logical AND Operator 

The *logical AND operator* (a && b) creates logical
expressions where both values must be true for the
overall expression to also be true.

If either value is false, the overall expression will
also be false. In fact, if the *first* value is
false, the second value won’t even be evaluated, because
it can’t possibly make the overall expression equate to
true. This is known as *short-circuit evaluation*.

This example considers two Bool values and only allows
access if both values are true:

    let
    let
    if
    {
        println)
    } else {
        println)
    }
    // prints "ACCESS DENIED"

‌

### Logical OR Operator 

The *logical OR operator* (a || b) is an infix operator
made from two adjacent pipe characters. You use it to create logical
expressions in which only *one* of the two values has to be
true for the overall expression to be
true.

Like the Logical AND operator above, the Logical OR operator uses
short-circuit evaluation to consider its expressions. If the left side
of a Logical OR expression is true, the right side is not
evaluated, because it cannot change the outcome of the overall
expression.

In the example below, the first Bool value
(hasDoorKey, but the second
value (knowsOverridePassword.
Because one value is true, the overall expression also
evaluates to true, and access is allowed:

    let
    let
    if
    {
        println)
    } else {
        println)
    }
    // prints "Welcome!"

‌

### Combining Logical Operators 

You can combine multiple logical operators to create longer compound
expressions:

    if
    || hasDoorKey {
        println)
    } else {
        println)
    }
    // prints "Welcome!"

This example uses multiple &&
operators to create a longer compound expression. However, the
&& operators still operate on only
two values, so this is actually three smaller expressions chained
together. It can be read as:

If we’ve entered the correct door code and passed the retina scan; or if
we have a valid door key; or if we know the emergency override password,
then allow access.

Based on the values of enteredDoorCode,
passedRetinaScan, the
first two mini-expressions are false. However, the
emergency override password is known, so the overall compound expression
still evaluates to true.

‌

### Explicit Parentheses 

It is sometimes useful to include parentheses when they are not strictly
needed, to make the intention of a complex expression easier to read. In
the door access example above, it is useful to add parentheses around
the first part of the compound expression to make its intent explicit:

    if &&
    passedRetinaScan ||
    knowsOverridePassword {
        println)
    } else {
        println)
    }
    // prints "Welcome!"

The parentheses make it clear that the first two values are considered
as part of a separate possible state in the overall logic. The output of
the compound expression doesn’t change, but the overall intention is
clearer to the reader. Readability is always preferred over brevity; use
parentheses where they help to make your intentions clear.
