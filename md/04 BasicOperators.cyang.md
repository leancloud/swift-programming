基础运算符
------------

*运算符*是一种可以检查、修改或结合数值的特殊符号或短语。例如，加法运算符可以将两个数字相加（ `let i = 1 + 2` ）。
更复杂的例子还包括逻辑与运算符 `&&`（ `if enteredDoorCode && passedRetinaScan` ）以及可以简化增量操作的运算符 `++i`。

Swift 支持大多数标准 C 运算符，并增强了避免常见编码错误的能力。赋值运算符（ `=` ）没有返回值，这可以防止误用（ `=` ）和等于符号（ `==` ）。
算数运算符（ `+` ，`*` ）会检测且禁止数值溢出，避免因处理数据不当而导致的意外结果。你可以使用 Swift 的溢出运算符来自定义溢出行为，详情请参考 [溢出运算符](https://www.zybuluo.com/ghosert/note/16198#overflow-operators)。

Swift 并不像 C 那样允许你对浮点数做求余运算。它提供了两种 C 不曾拥有的范围运算符（ `a..b` ），这样的运算符可以非常方便地表示数据范围。

本章将会详细解读 Swift 的常用运算符。[高级运算符](https://www.zybuluo.com/ghosert/note/16198#advanced-operators) 则涵盖了 Swift 的高级运算符，它会告诉你如何定义你自己的运算符，并为你自己的类型实现标准运算符。

### 专有名词
运算符包括一元、二元和三元运算符：
    
- 	*一元*运算符只能作用于单一操作数（例如 -a）。一元*前缀*运算符位于操作数头部（例如 !b），而一元*后缀*运算符位于操作数尾部（例如 i++）。

- 	*二元*运算符作用于两个操作数（例如 2 + 3），并且位于两个操作数中间。

- 	*三元*运算符作用于三个操作数。和 C 类似，Swift只有一个三元运算符，也就是三元条件运算符（a ? b : c）。

运算符所影响的数值叫做*操作数*。在表达式 `1 + 2` 中，`+` 就是一个二元运算符，他的两个操作数就是数值 `1` 和 `2` 。

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

与 C 和 Objective-C 的算数运算符不同，Swift 的算数运算符默认禁止数值溢出。你可以使用 Swift 的溢出运算符（例如 `a &+ b`）来选择数值溢出相关行为。详情参考 [溢出运算符](https://www.zybuluo.com/ghosert/note/16198#overflow-operators)。

加法运算符也支持字符串连接：

	"hello, " + "world" // 等于 “hello, world”

两个字符，或者一个字符与一个字符串，都可以相加构造为一个新的字符串：
	
	let dog: Character = "d"
	let cow: Character = "c"
	let dogCow = dog + cow
	// dogCow 等于 "dc"

详情请参考 [字符串与字符连接](https://www.zybuluo.com/ghosert/note/16162#concatenating-strings-and-characters)。
‌
### 求余运算符
*余数*的定义是这样的：b 减去 b 可以容纳的 a 的最大倍数，例如 `7 % 3 = 7- (3 * 2) = 1`。求余运算符（ `a % b` ）就是用来计算余数的运算符。

> **注意**
>
> 在其他语言中，求余运算符（ `%` ）也叫做*取模运算符*。而从严格意义上讲，Swift 的求余运算符对负数是做求余操作，而不是取模操作。

下面是求余运算符的工作原理。计算 `9 % 4`，首先你需要计算出 9 能容纳多少个 4：

![image](https://blog.avoscloud.com/wp-content/uploads/2014/06/remainder-1.png)

9 能容纳两个 4，余数应该为 1（橙色部分）。在 Swift 中，上面的运算可以这样表示:
	
	9 % 4 // 等于 1

为了计算 `a % b` 的结果，`%` 运算符需要解如下方程，并输出 remainder：

```
a = (b * some multiplier) + remainder
```
其中 some mutiplier 是 b 的最大倍数。把 9 和 4 代入上述方程，可以得到：

```
9 = (4 * 2) + 1
```

同样的方法可以用来计算某个负数的余数：

```
-9 % 4 // 等于 -1
```
把 -9 和 4 代入前文提到的方程，可以得到：

```
-9 = (4 * -2) + -1
```

最终计算出余数为 -1。在求余计算中，负数 b 的符号会被忽略。也就是说，`a % b` 和 `a % -b` 会得到相同的结果。
‌
### 浮点求余运算
与 C 和 Objective-C 的求余运算符不同，Swift 的求余运算符可以作用于浮点数：

```
8 % 2.5 // 等于 0.5
```

‌在上面这个例子中，8 除以 2.5 等于 3，余数为 0.5，所以求余运算符返回一个 `Double` 值 0.5。
![image](https://blog.avoscloud.com/wp-content/uploads/2014/06/remainder-2.png)

### 增量与减量运算符
和 C 类似，Swift 也提供了可以便捷的对某个数字做加一或减一操作的运算符：*增量运算符*和*减量运算符*。你可以使用者两个运算符对整型或浮点型变量做操作：
	
	var i = 0
	++i		 // 现在 i 等于 1

每当你调用 `++i`，i 的值就会加一。本质上讲，`++i` 是 `i = i + 1`的缩写。类似的，`--i` 可以作为 `i = i - 1` 的缩写。`++` 和 `--` 这两个运算符可以用作前缀或后缀运算符。若想让 i 加一，`i++` 和 `++i`都是合法的表达式。同理，`i--` 和 `--i` 都会导致 i 减一。
    
需要注意的是，这两个运算符不仅会修改 `i` 的数值，还会产生返回值。如果只想修改存储在 `i` 中的数值，你可以忽略返回值。然而，如果要使用返回值，你需要根据如下规则来区分前缀与后缀运算符：

-	如果运算符位于变量之前，那么先修改变量，后返回数值。
-	如果运算符位于变量之后，那么先返回值，后修改变量。
    
例如：

    var a = 0
    let b = ++a
    // a 和 b 现在等于 1
    let c = a++
    // a 现在等于 2，但是 c 被赋值为 a 增长之前的值:1

在上面的例子中，`let b = ++a` 先对 a 加一，然后返回它的值。这就是为什么 a 和 b 都等于新的值 1。然而，`let c = a++` 在返回值之后对 a 加一。这意味着 c 获得旧值 1，然后 a 被更改为 2。除非你需要利用 `i++` 的特殊行为，否则在任何场景都推荐使用 `++i` 和 `--i`。因为后者总是能返回你所期望的数值，也就是对旧值加一或减一之后的结果。

### 一元减法运算符
数字的符号可以通过前缀符号 `-` 来做切换，这也就是所谓的*一元减法运算符*：
	
	let three = 3
	let minusThree = -three         // minusThree 等于 -3
	let plusThree = -minusThree     // plusThree 等于 3

一元减法运算符（ `-` ）直接位于操作数的前面，中间不能有空格。
‌

### 一元加法运算符
*一元加法运算符*直接返回操作数的值，不对其做任何修改：

	let minusSix = -6
	let alsoMinusSix = +minusSix  // alsoMinusSix 等于 -6
		
‌尽管一元加法运算符不会对数值做任何修改，你仍然可以使用它来提高代码可读性。比如正数与负数通过两种不同的运算符来达到一种"对称"的视觉效果。

### 复合赋值运算符     
与 C 类似，Swift 提供*复合赋值运算符*来结合赋值（ `=` ）与其他操作。下面是一个*加法赋值运算符*（ `+=` ）的例子：
	var a = 1
	a += 2
	// 现在 a 等于 3

表达式 `a += 2` 是 `a = a + 2` 的缩写。实际上，把加法和赋值运算符结合到一起会同时执行两个任务。

> **注意**
>
> 复合赋值运算符没有返回值。例如，类似 `let b = a += 2` 这样的代码是非法的。它和前面提到的
> 增量或减量运算符有着不一样的行为。

有关复合赋值运算符的完整列表，可以参考 [表达式](https://www.zybuluo.com/ghosert/note/16206#expressions)。
‌

### 比较运算符
Swift 支持所有标准 C *比较运算符*：

-	等于（ `a == b` ）
-	不等于（ `a != b` ）
-	大于（ `a > b` ）
-	小于（ `a < b` ）
-	大于或等于（ `a >= b` ）
-	小于或等于（ `a <= b` ）


> **注意**
>
> Swift 还提供了两种用于测试两个对象引用是否指向同一个对象实例的*标示运算符*（ `===` 和 `!==`）。更多信息，可以参考[对象与结构体](https://www.zybuluo.com/ghosert/note/16180#classes-and-structures)

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

更多关于 if 语句的信息，参考[控制流](https://www.zybuluo.com/ghosert/note/16164#control-flow)
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
### 范围运算符 
Swift 包含两种*范围运算符*。使用范围运算符，可以非常简洁地表示数值范围。
‌
### 封闭范围运算符
*封闭范围运算符*（ `a...b` ）定义了一个由 a 到 b，并且包含 a 和 b 的范围。当你想要遍历某个范围内所有的元素，封闭范围运算符就可以派上用场，例如 `for` 循环：
	
	for index in 1...5 {
    	println("\(index) times 5 is \(index * 5)")
	}
	// 1 times 5 is 5
	// 2 times 5 is 10
	// 3 times 5 is 15
	// 4 times 5 is 20
	// 5 times 5 is 25

更多有关 `for-in` 循环的信息，可以参考[控制流](https://www.zybuluo.com/ghosert/note/16164#control-flow)。

### 半闭范围运算符
*半闭范围运算符*（ `a..b` ）定义了一个由 a 到 b，但不包含 b 的范围。之所以称作*半闭*，是因为它包含起始元素，但不包含结束元素。当你使用 0-based 列表比如数组时，半闭范围运算符就显得特别有用。可以用它来计数至列表长度（不包含这个上限值）：

	et names = ["Anna", "Alex", "Brian", "Jack"]
	let count = names.count
	for i in 0..count {
    	println("Person \(i + 1) is called \(names[i])")
	}
	// Person 1 is called Anna
	// Person 2 is called Alex
	// Person 3 is called Brian
	// Person 4 is called Jack

‌需要说明的是，数组包含四个元素，由于 `0..count`是半闭范围，故只会计数到 3（数组最后一个元素的索引）。更多有关数组的信息，可以参考[数组](https://www.zybuluo.com/ghosert/note/16163#arrays)

### 逻辑运算符
*逻辑运算符*用于修改或合并布尔值：true 和 false。Swift 支持三种标准逻辑运算符：

-	逻辑非（ `!a` ）
-	逻辑与（ `a && b` ）
-	逻辑或（ `a || b` ）

### Logical NOT Operator 
*逻辑非运算符*（!a）把布尔值反转，也就是说 true 会变成 false，false 会变成 true。逻辑非运算符是一种前缀运算符，其位于操作数的头部，且两者直接不能有空格。`!a` 可以发音为 "not a"，例子如下：
	
	let allowedEntry = false
	if !allowedEntry {
    	println("ACCESS DENIED")
	}
	// prints "ACCESS DENIED"

`if !allowedEntry` 可以读作 “if not allowed entry”。紧接其后的那行代码只会在 “not allowed entry” 为 true 的时候才会执行；也就意味着allowedEntry 为 false。就像上面这个例子一样，谨慎命名布尔常量或变量除了可以保证代码的可读性和简洁度，还能避免双重否定或其他一些混乱的逻辑语句。
‌
### 逻辑与运算符
由*逻辑与运算符*（ `a && b` ）构造的逻辑表达式，只有当所有布尔值都为 true 的时候，整个表达式的值才为 true。

如果其中某个布尔值为 false，那么整个表达式的值都为 false。实际上，如果*第一个*值为 false，第二个值将会被忽略，因为它不可能再更改整个表达式的真值。这也就是所谓的*短路求值*（short-circuit evaluation）。

这个例子测试两个布尔值，当且仅当两个个值都为 true 才允许访问：
	
	let enteredDoorCode = true
	let passedRetinaScan = false
	if enteredDoorCode && passedRetinaScan {
    	println("Welcome!")
	} else {
    	println("ACCESS DENIED")
	}
	// 输出 "ACCESS DENIED"
	‌
### 逻辑或运算符 
*逻辑或运算符*（ `a || b` ）是由两个邻接的管道符号构成的中缀运算符。用它来构造的逻辑表达式，只要其中一个布尔值为 true，整个表达式的值即可为 true。

同逻辑与运算符类似，逻辑或运算符也遵循短路求值的规则。如果逻辑或运算符左侧的值为 true，那么就不必再对右边求值。因为右边这个值已经无法对整个表达式的真值产生任何影响。

接下来的例子中，第一个布尔值（hasDoorKey）为false，但是第二个布尔值（knowsOverridePassword）为 true。因为其中有一个值为 true，整个表达式的真值为 true，故允许访问：
	
	let hasDoorKey = false
	let knowsOverridePassword = true
	if hasDoorKey || knowsOverridePassword {
    	println("Welcome!")
	} else {
    	println("ACCESS DENIED")
	}
	// 输出 "Welcome!"
	
### 合并逻辑运算符
你可以通过合并多个逻辑运算符来构造更长的复合表达式：
	
	if enteredDoorCode && passedRetinaScan || hasDoorKey || knowsOverridePassword {
    	println("Welcome!")
	} else {
    	println("ACCESS DENIED")
	}
	// 输出 "Welcome!"
    
这个例子使用多个 `&&` 和 `||` 运算符来构造更长的复合表达式。然而，`&&` 和 `||` 运算符只能作用于两个布尔值，因此这实际上是三个较短的表达式链接而成的。可以换一种表达方式：

> 如果我们输入了正确的门牌号并且通过了视网膜扫描；或者如果我们拥有有效的钥匙；抑或如果我们知道紧急覆盖密码，那么我们将会拥有访问权限。

根据 enteredDoorCode，passedRetinaScan，以及 hasDoorKey 等布尔值，前面两个表达式的值为 false。然而，因为紧急覆盖密码是已知的，所以整个表达式为 true。

### 显式的括号
有时候，引入括号有助于提升复杂表达式的可读性，尽管这些括号并不是必须的。在上面的门禁示例中，对第一部分表达式添加括号，可以让代码更清晰易懂：
	
	if (enteredDoorCode && passedRetinaScan) || hasDoorKey || knowsOverridePassword {
    	println("Welcome!")
	} else {
    	println("ACCESS DENIED")
	}
	// 输出 "Welcome!"

括号可以让表达式前两个值看起来相对独立。尽管整个表达式的真值不会因为这对括号而改变，但整行代码的意图却变得清晰明了。可读性总是比简洁性更重要；使用括号有助于明确你的代码意图。