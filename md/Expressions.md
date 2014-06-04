‌‌

Expressions 
-----------

In Swift, there are four kinds of expressions: prefix expressions,
binary expressions, primary expressions, and postfix expressions.
Evaluating an expression returns a value, causes a side effect, or both.

Prefix and binary expressions let you apply operators to smaller
expressions. Primary expressions are conceptually the simplest kind of
expression, and they provide a way to access values. Postfix
expressions, like prefix and binary expressions, let you build up more
complex expressions using postfixes such as function calls and member
access. Each kind of expression is described in detail in the sections
below.

Grammar of an expression

‌ expression →
[prefix-expression](Expressions.xhtml#prefix-expression)[binary-expressions](Expressions.xhtml#binary-expressions)~opt~

‌ expression-list → [expression](Expressions.xhtml#expression)
[expression](Expressions.xhtml#expression),[expression-list](Expressions.xhtml#expression-list)

‌

### Prefix Expressions 

*Prefix expressions* combine an optional prefix operator with an
expression. Prefix operators take one argument, the expression that
follows them.

The Swift standard library provides the following prefix operators:

    ++ Increment

    -- Decrement

    ! Logical NOT

    ~ Bitwise NOT

    + Unary plus

    - Unary minus

For information about the behavior of these operators, see [Basic
Operators](BasicOperators.xhtml) and [Advanced
Operators](AdvancedOperators.xhtml).

In addition to the standard library operators listed above, you use
& immediately before the name of a variable that’s being
passed as an in-out argument to a function call expression. For more
information and to see an example, see [In-Out
Parameters](Functions.xhtml#TP40014097-CH10-XID_226).

Grammar of a prefix expression

‌ prefix-expression →
[prefix-operator](LexicalStructure.xhtml#prefix-operator)~opt~[postfix-expression](Expressions.xhtml#postfix-expression)

‌ prefix-expression →
[in-out-expression](Expressions.xhtml#in-out-expression)

‌ in-out-expression →
&[identifier](LexicalStructure.xhtml#identifier)

‌

### Binary Expressions 

*Binary expressions* combine an infix binary operator with the
expression that it takes as its left-hand and right-hand arguments. It
has the following form:

-   ~~~~ 
    left-hand argument operator right-hand argument
    ~~~~

The Swift standard library provides the following binary operators:

-   Exponentiative (No associativity, precedence level 160)
    :       << Bitwise left shift

            >> Bitwise right shift

-   Multiplicative (Left associative, precedence level 150)
    :       * Multiply

            / Divide

            % Remainder

            &* Multiply, ignoring overflow

            &/ Divide, ignoring overflow

            &% Remainder, ignoring overflow

            & Bitwise AND

-   Additive (Left associative, precedence level 140)
    :       + Add

            - Subtract

            &+ Add with overflow

            &- Subtract with overflow

            | Bitwise OR

            ^ Bitwise XOR

-   Range (No associativity, precedence level 135)
    :       .. Half-closed range

            ... Closed range

-   Cast (No associativity, precedence level 132)
    :       is Type check

            as Type cast

-   Comparative (No associativity, precedence level 130)
    :       < Less than

            <= Less than or equal

            > Greater than

            >= Greater than or equal

            == Equal

            != Not equal

            === Identical

            !== Not identical

            ~= Pattern match

-   Conjunctive (Left associative, precedence level 120)
    :       && Logical AND

-   Disjunctive (Left associative, precedence level 110)
    :       || Logical OR

-   Ternary Conditional (Right associative, precedence level 100)
    :       ? Ternary conditional

-   Assignment (Right associative, precedence level 90)
    :       = Assign

            *= Multiply and assign

            /= Divide and assign

            %= Remainder and assign

            += Add and assign

            -= Subtract and assign

            <<= Left bit shift and assign

            >>= Right bit shift and assign

            &= Bitwise AND and assign

            ^= Bitwise XOR and assign

            |= Bitwise OR and assign

            &&= Logical AND and assign

            ||= Logical OR and assign

For information about the behavior of these operators, see [Basic
Operators](BasicOperators.xhtml) and [Advanced
Operators](AdvancedOperators.xhtml).

Note

At parse time, an expression made up of binary operators is represented
as a flat list. This list is transformed into a tree by applying
operator precedence For example, the expression 2 + 3 * 5
is initially understood as a flat list of five items, 2,
+.
This process transforms it into the tree (2 + (3 \* 5)).

Grammar of a binary expression

‌ binary-expression →
[binary-operator](LexicalStructure.xhtml#binary-operator)[prefix-expression](Expressions.xhtml#prefix-expression)

‌ binary-expression →
[assignment-operator](Expressions.xhtml#assignment-operator)[prefix-expression](Expressions.xhtml#prefix-expression)

‌ binary-expression →
[conditional-operator](Expressions.xhtml#conditional-operator)[prefix-expression](Expressions.xhtml#prefix-expression)

‌ binary-expression →
[type-casting-operator](Expressions.xhtml#type-casting-operator)

‌ binary-expressions →
[binary-expression](Expressions.xhtml#binary-expression)[binary-expressions](Expressions.xhtml#binary-expressions)~opt~

‌

### Assignment Operator 

The *assigment operator* sets a new value for a given expression. It has
the following form:

-   ~~~~ 
    expression = value
    ~~~~

The value of the *expression* is set to the value obtained by evaluating
the *value*. If the *expression* is a tuple, the *value* must be a tuple
with the same number of elements. (Nested tuples are allowed.)
Assignment is performed from each part of the *value* to the
corresponding part of the *expression*. For example:

    (a,
    9.45))
    // a is "test", b is 12, c is 3, and 9.45 is ignored

The assignment operator does not return any value.

Grammar of an assignment operator

‌ assignment-operator → =

‌

### Ternary Conditional Operator 

The *ternary conditional operator* evaluates to one of two given values
based on the value of a condition. It has the following form:

-   ~~~~ 
    condition ? expression used if true : expression used if false
    ~~~~

If the *condition* evaluates to true, the conditional
operator evaluates the first expression and returns its value.
Otherwise, it evaluates the second expression and returns its value. The
unused expression is not evaluated.

For an example that uses the ternary conditional operator, see [Ternary
Conditional Operator](BasicOperators.xhtml#TP40014097-CH6-XID_84).

Grammar of a conditional operator

‌ conditional-operator →
?

‌

### Type-Casting Operators 

There are two type-casting operators, the as operator and
the is operator. They have the following form:

-   ~~~~ 
    expression as type
    ~~~~

-   ~~~~ 
    expression as? type
    ~~~~

-   ~~~~ 
    expression is type
    ~~~~

The as operator performs a cast of the *expression* to
the specified *type*. It behaves as follows:

-   If conversion to the specified *type* is guaranteed to succeed, the
    value of the *expression* is returned as an instance of the
    specified *type*. An example is casting from a subclass to a
    superclass.

-   If conversion to the specified *type* is guaranteed to fail, a
    compile-time error is raised.

-   Otherwise, if it’s not known at compile time whether the conversion
    will succeed, the type of the cast expresion is an optional of the
    specified *type*. At runtime, if the cast succeeds, the value of
    *expression* is wrapped in an optional and returned; otherwise, the
    value returned is nil. An example is casting from a
    superclass to a subclass.

    class
    class
    class
    let()
     
    let
    // known to succeed; type is SomeSuperType
    let
    // known to fail; compile-time error
    let
    // might fail at runtime; type is SomeChildType?

Specifying a type with as provides the same information
to the compiler as a type annotation, as shown in the following example:

    let
    // Type information from 'as'
    let
    // Type information from an annotation

The is operator checks at runtime to see whether the
*expression* is of the specified *type*. If so, it returns
true.

The check must not be known to be true or false at compile time. The
following are invalid:

    "hello"
    "hello"

For more information about type casting and to see more examples that
use the type-casting operators, see [Type Casting](TypeCasting.xhtml).

Grammar of a type-casting operator

‌ type-casting-operator → is[type](Types.xhtml#type)
as~opt~[type](Types.xhtml#type)

‌

### Primary Expressions 

*Primary expressions* are the most basic kind of expression. They can be
used as expressions on their own, and they can be combined with other
tokens to make prefix expressions, binary expressions, and postfix
expressions.

Grammar of a primary expression

‌ primary-expression →
[identifier](LexicalStructure.xhtml#identifier)[generic-argument-clause](GenericParametersAndArguments.xhtml#generic-argument-clause)~opt~

‌ primary-expression →
[literal-expression](Expressions.xhtml#literal-expression)

‌ primary-expression →
[self-expression](Expressions.xhtml#self-expression)

‌ primary-expression →
[superclass-expression](Expressions.xhtml#superclass-expression)

‌ primary-expression →
[closure-expression](Expressions.xhtml#closure-expression)

‌ primary-expression →
[parenthesized-expression](Expressions.xhtml#parenthesized-expression)

‌ primary-expression →
[implicit-member-expression](Expressions.xhtml#implicit-member-expression)

‌ primary-expression →
[wildcard-expression](Expressions.xhtml#wildcard-expression)

‌

### Literal Expression 

A *literal expression* consists of either an ordinary literal (such as a
string or a number), an array or dictionary literal, or one of the
following special literals:

Literal

Type

Value

__FILE__

String

The name of the file in which it appears.

__LINE__

Int

The line number on which it appears.

__COLUMN__

Int

The column number in which it begins.

__FUNCTION__

String

The name of the declaration in which it appears.

Inside a function, the value of __FUNCTION__ is the name
of that function, inside a method it is the name of that method, inside
a property getter or setter it is the name of that property, inside
special members like init it
is the name of that keyword, and at the top level of a file it is the
name of the current module.

An *array literal* is an ordered collection of values. It has the
following form:

-   ~~~~ 
    [value 1, value 2, ...]
    ~~~~

The last expression in the array can be followed by an optional comma.
An empty array literal is written as an empty pair of brackets
([]). The value of an array literal has type
T[] is the type of the
expressions inside it. If there are expressions of multiple types,
T is their closest common supertype.

A *dictionary literal* is an unordered collection of key-value pairs. It
has the following form:

-   ~~~~ 
    [key 1: value 1, key 2: value 2, ...]
    ~~~~

The last expression in the dictionary can be followed by an optional
comma. An empty dictionary literal is written as a colon inside a pair
of brackets ([:]) to distinguish it from an empty array
literal. The value of a dictionary literal has type
Dictionary<KeyType, ValueType>, where
KeyType is the type of its key expressions and
ValueType is the type of its value expressions. If there
are expressions of multiple types, KeyType and
ValueType are the closest common supertype for their
respective values.

Grammar of a literal expression

‌ literal-expression → [literal](LexicalStructure.xhtml#literal)

‌ literal-expression → [array-literal](Expressions.xhtml#array-literal)
[dictionary-literal](Expressions.xhtml#dictionary-literal)

‌ literal-expression → __FILE__
__COLUMN__

‌ array-literal →
[

‌ array-literal-items →
[array-literal-item](Expressions.xhtml#array-literal-item),~opt~
[array-literal-item](Expressions.xhtml#array-literal-item),[array-literal-items](Expressions.xhtml#array-literal-items)

‌ array-literal-item → [expression](Expressions.xhtml#expression)

‌ dictionary-literal →
[
[

‌ dictionary-literal-items →
[dictionary-literal-item](Expressions.xhtml#dictionary-literal-item),~opt~
[dictionary-literal-item](Expressions.xhtml#dictionary-literal-item),[dictionary-literal-items](Expressions.xhtml#dictionary-literal-items)

‌ dictionary-literal-item →
[expression](Expressions.xhtml#expression):[expression](Expressions.xhtml#expression)

‌

### Self Expression 

The self expression is an explicit reference to the
current type or instance of the type in which it occurs. It has the
following forms:

-   ~~~~ 
    self
    ~~~~

-   ~~~~ 
    self.member name
    ~~~~

-   ~~~~ 
    self[subscript index]
    ~~~~

-   ~~~~ 
    self(initializer arguments)
    ~~~~

-   ~~~~ 
    self.init(initializer arguments)
    ~~~~

In an initializer, subscript, or instance method, self
refers to the current instance of the type in which it occurs. In a
static or class method, self refers to the current type
in which it occurs.

The self expression is used to specify scope when
accessing members, providing disambiguation when there is another
variable of the same name in scope, such as a function parameter. For
example:

    class {
        var
        init) {
            self
        }
    }

In a mutating method of value type, you can assign a new instance of
that value type to self. For example:

    struct {
        var
        mutating
    moveByX:
    Double) {
            self +
    deltaX)
        }
    }

Grammar of a self expression

‌ self-expression → self

‌ self-expression →
self[identifier](LexicalStructure.xhtml#identifier)

‌ self-expression →
self

‌ self-expression → self

‌

### Superclass Expression 

A *superclass expression* lets a class interact with its superclass. It
has one of the following forms:

-   ~~~~ 
    super.member name
    ~~~~

-   ~~~~ 
    super[subscript index]
    ~~~~

-   ~~~~ 
    super.init(initializer arguments)
    ~~~~

The first form is used to access a member of the superclass. The second
form is used to access the superclass’s subscript implementation. The
third form is used to access an initializer of the superclass.

Subclasses can use a superclass expression in their implementation of
members, subscripting, and initializers to make use of the
implementation in their superclass.

Grammar of a superclass expression

‌ superclass-expression →
[superclass-method-expression](Expressions.xhtml#superclass-method-expression)
[superclass-subscript-expression](Expressions.xhtml#superclass-subscript-expression)
[superclass-initializer-expression](Expressions.xhtml#superclass-initializer-expression)

‌ superclass-method-expression →
super[identifier](LexicalStructure.xhtml#identifier)

‌ superclass-subscript-expression →
super

‌ superclass-initializer-expression →
super

‌

### Closure Expression 

A *closure expression* creates a closure, also known as a *lambda* or an
*anonymous function* in other programming languages. Like function
declarations, closures contain statements which they execute, and they
capture values from their enclosing scope. It has the following form:

-   ~~~~ 
    { (parameters) -> return type in
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    }
    ~~~~

The *parameters* have the same form as the parameters in a function
declaration, as described in [Function
Declaration](Declarations.xhtml#TP40014097-CH34-XID_545).

There are several special forms that allow closures to be written more
concisely:

-   A closure can omit the types of its parameters, its return type, or
    both. If you omit the parameter names and both types, omit the
    in keyword before the statements. If the omitted
    types can’t be inferred, a compile-time error is raised.

-   A closure may omit names for its parameters. Its parameters are then
    implicitly named $ followed by their position:
    $0, and so on.

-   A closure that consists of only a single expression is understood to
    return the value of that expression. The contents of this expression
    is also considered when performing type inference on the surrounding
    expression.

The following closure expressions are equivalent:

    myFunction {
        (x) -\>
    Int
        return
    }
     
    myFunction {
        (x
        return
    }
     
    myFunction
     
    myFunction

For information about passing a closure as an argument to a function,
see [Function Call
Expression](Expressions.xhtml#TP40014097-CH32-XID_747).

A closure expression can explicitly specify the values that it captures
from the surrounding scope using a *capture list*. A capture list is
written as a comma separated list surrounded by square brackets, before
the list of parameters. If you use a capture list, you must also use the
in keyword, even if you omit the parameter names,
parameter types, and return type.

Each entry in the capture list can be marked as weak or
unowned to capture a weak or unowned reference to the
value.

    myFunction
    // strong capture
    myFunction
    print
    myFunction
    print

You can also bind arbitrary expression to named values in the capture
list. The expression is evaluated when the closure is formed, and
captured with the specified strength. For example:

    // Weak capture of "self.parent" as "parent"
    myFunction =
    self
    print

For more information and examples of closure expressions, see [Closure
Expressions](Closures.xhtml#TP40014097-CH11-XID_119).

Grammar of a closure expression

‌ closure-expression →


‌ closure-signature →
[parameter-clause](Declarations.xhtml#parameter-clause)[function-result](Declarations.xhtml#function-result)~opt~in

‌ closure-signature →
[identifier-list](LexicalStructure.xhtml#identifier-list)[function-result](Declarations.xhtml#function-result)~opt~in

‌ closure-signature →
[capture-list](Expressions.xhtml#capture-list)[parameter-clause](Declarations.xhtml#parameter-clause)[function-result](Declarations.xhtml#function-result)~opt~in

‌ closure-signature →
[capture-list](Expressions.xhtml#capture-list)[identifier-list](LexicalStructure.xhtml#identifier-list)[function-result](Declarations.xhtml#function-result)~opt~in

‌ closure-signature →
[capture-list](Expressions.xhtml#capture-list)in

‌ capture-list →
[

‌ capture-specifier → weak
unowned(safe)

‌

### Implicit Member Expression 

An *implicit member expression* is an abbreviated way to access a member
of a type, such as an enumeration case or a class method, in a context
where type inference can determine the implied type. It has the
following form:

-   ~~~~ 
    .member name
    ~~~~

For example:

    var
    x

Grammar of a implicit member expression

‌ implicit-member-expression →
.[identifier](LexicalStructure.xhtml#identifier)

‌

### Parenthesized Expression 

A *parenthesized expression* consists of a comma-separated list of
expressions surrounded by parentheses. Each expression can have an
optional identifier before it, separated by a colon (:).
It has the following form:

-   ~~~~ 
    (identifier 1: expression 1, identifier 2: expression 2, ...)
    ~~~~

Use parenthesized expressions to create tuples and to pass arguments to
a function call. If there is only one value inside the parenthesized
expression, the type of the parenthesized expression is the type of that
value. For example, the type of the parenthesized expression
(1).

Grammar of a parenthesized expression

‌ parenthesized-expression →
(

‌ expression-element-list →
[expression-element](Expressions.xhtml#expression-element)
[expression-element](Expressions.xhtml#expression-element),[expression-element-list](Expressions.xhtml#expression-element-list)

‌ expression-element → [expression](Expressions.xhtml#expression)
[identifier](LexicalStructure.xhtml#identifier):[expression](Expressions.xhtml#expression)

‌

### Wildcard Expression 

A *wildcard expression* is used to explicitly ignore a value during an
assignment. For example, in the following assignment 10 is assigned to
x and 20 is ignored:

    (x)
    // x is 10, 20 is ignored

Grammar of a wildcard expression

‌ wildcard-expression → _

‌

### Postfix Expressions 

*Postfix expressions* are formed by applying a postfix operator or other
postfix syntax to an expression. Syntactically, every primary expression
is also a postfix expression.

The Swift standard library provides the following postfix operators:

    ++ Increment

    -- Decrement

For information about the behavior of these operators, see [Basic
Operators](BasicOperators.xhtml) and [Advanced
Operators](AdvancedOperators.xhtml).

Grammar of a postfix expression

‌ postfix-expression →
[primary-expression](Expressions.xhtml#primary-expression)

‌ postfix-expression →
[postfix-expression](Expressions.xhtml#postfix-expression)[postfix-operator](LexicalStructure.xhtml#postfix-operator)

‌ postfix-expression →
[function-call-expression](Expressions.xhtml#function-call-expression)

‌ postfix-expression →
[initializer-expression](Expressions.xhtml#initializer-expression)

‌ postfix-expression →
[explicit-member-expression](Expressions.xhtml#explicit-member-expression)

‌ postfix-expression →
[postfix-self-expression](Expressions.xhtml#postfix-self-expression)

‌ postfix-expression →
[dynamic-type-expression](Expressions.xhtml#dynamic-type-expression)

‌ postfix-expression →
[subscript-expression](Expressions.xhtml#subscript-expression)

‌ postfix-expression →
[forced-value-expression](Expressions.xhtml#forced-value-expression)

‌ postfix-expression →
[optional-chaining-expression](Expressions.xhtml#optional-chaining-expression)

‌

### Function Call Expression 

A *function call expression* consists of a function name followed by a
comma-separated list of the function’s arguments in parentheses.
Function call expressions have the following form:

-   ~~~~ 
    function name(argument value 1, argument value 2)
    ~~~~

The *function name* can be any expression whose value is of a function
type.

If the function definition includes names for its parameters, the
function call must include names before its argument values separated by
a colon (:). This kind of function call expression has
the following form:

-   ~~~~ 
    function name(argument name 1: argument value 1, argument name 2: argument value 2)
    ~~~~

A function call expression can include a trailing closure in the form of
a closure expression immediately after the closing parenthesis. The
trailing closure is understood as an argument to the function, added
after the last parenthesized argument. The following function calls are
equivalent:

    // someFunction takes an integer and a closure as its arguments
    someFunction)
    someFunction

If the trailing closure is the function’s only argument, the parentheses
can be omitted.

    // someFunction takes a closure as its only argument
    myData
    myData

Grammar of a function call expression

‌ function-call-expression →
[postfix-expression](Expressions.xhtml#postfix-expression)[parenthesized-expression](Expressions.xhtml#parenthesized-expression)

‌ function-call-expression →
[postfix-expression](Expressions.xhtml#postfix-expression)[parenthesized-expression](Expressions.xhtml#parenthesized-expression)~opt~[trailing-closure](Expressions.xhtml#trailing-closure)

‌ trailing-closure →
[closure-expression](Expressions.xhtml#closure-expression)

‌

### Initializer Expression 

An *initializer expression* provides access to a type’s initializer. It
has the following form:

-   ~~~~ 
    expression.init(initializer arguments)
    ~~~~

You use the initializer expression in a function call expression to
initialize a new instance of a type. Unlike functions, an initializer
can’t be used as a value. For example:

    var =
    SomeClass
    var
    // error

You also use an initializer expression to delegate to the initializer of
a superclass.

    class {
        init() {
            // subclass initialization goes here
            super()
        }
    }

Grammar of an initializer expression

‌ initializer-expression →
[postfix-expression](Expressions.xhtml#postfix-expression).

‌

### Explicit Member Expression 

A *explicit member expression* allows access to the members of a named
type, a tuple, or a module. It consists of a period (.)
between the item and the identifier of its member.

-   ~~~~ 
    expression.member name
    ~~~~

The members of a named type are named as part of the type’s declaration
or extension. For example:

    class {
        var
    }
    let()
    let
    // Member access

The members of a tuple are implicitly named using integers in the order
they appear, starting from zero. For example:

    var)
    t
    // Now t is (20, 20, 30)

The members of a module access the top-level declarations of that
module.

Grammar of an explicit member expression

‌ explicit-member-expression →
[postfix-expression](Expressions.xhtml#postfix-expression).[decimal-digit](LexicalStructure.xhtml#decimal-digit)

‌ explicit-member-expression →
[postfix-expression](Expressions.xhtml#postfix-expression).[identifier](LexicalStructure.xhtml#identifier)[generic-argument-clause](GenericParametersAndArguments.xhtml#generic-argument-clause)~opt~

‌

### Postfix Self Expression 

A postfix self expression consists of an expression or
the name of a type, immediately followed by .self. It has
the following forms:

-   ~~~~ 
    expression.self
    ~~~~

-   ~~~~ 
    type.self
    ~~~~

The first form evaluates to the value of the *expression*. For example,
x.self.

The second form evaluates to the value of the *type*. Use this form to
access a type as a value. For example, because
SomeClass.self
type itself, you can pass it to a function or method that accepts a
type-level argument.

Grammar of a self expression

‌ postfix-self-expression →
[postfix-expression](Expressions.xhtml#postfix-expression).

‌

### Dynamic Type Expression 

A dynamicType expression consists of an expression,
immediately followed by .dynamicType. It has the
following form:

-   ~~~~ 
    expression.dynamicType
    ~~~~

The *expression* can’t be the name of a type. The entire
dynamicType expression evaluates to the value of the
runtime type of the *expression*, as the following example shows:

    class {
        class() {
            println)
        }
    }
    class {
        override
    printClassName() {
            println)
        }
    }
    let =
    SomeSubClass()
    // someInstance is of type SomeBaseClass at compile time, but
    // someInstance is of type SomeSubClass at runtime
    someInstance()
    // prints "SomeSubClass"

Grammar of a dynamic type expression

‌ dynamic-type-expression →
[postfix-expression](Expressions.xhtml#postfix-expression).

‌

### Subscript Expression 

A *subscript expression* provides subscript access using the getter and
setter of the corresponding subscript declaration. It has the following
form:

-   ~~~~ 
    expression[index expressions]
    ~~~~

To evaluate the value of a subscript expression, the subscript getter
for the *expression*’s type is called with the *index expressions*
passed as the subscript parameters. To set its value, the subscript
setter is called in the same way.

For information about subscript declarations, see [Protocol Subscript
Declaration](Declarations.xhtml#TP40014097-CH34-XID_619).

Grammar of a subscript expression

‌ subscript-expression →
[postfix-expression](Expressions.xhtml#postfix-expression)[

‌

### Forced-Value Expression 

A *forced-value expression* unwraps an optional value that you are
certain is not nil. It has the following form:

-   ~~~~ 
    expression!
    ~~~~

If the value of the *expression* is not nil, the optional
value is unwrapped and returned with the corresponding nonoptional type.
Otherwise, a runtime error is raised.

Grammar of a forced-value expression

‌ forced-value-expression →
[postfix-expression](Expressions.xhtml#postfix-expression)!

‌

### Optional-Chaining Expression 

An *optional-chaining expression* provides a simplified syntax for using
optional values in postfix expressions. It has the following form:

-   ~~~~ 
    expression?
    ~~~~

On its own, the postfix ? operator simply returns the
value of its argument as an optional.

Postfix expressions that contain an optional-chaining expression are
evaluated in a special way. If the optional-chaining expression is
nil, all of the other operations in the postfix
expression are ignored and the entire postfix expression evaluates to
nil. If the optional-chaining expression is not
nil, the value of the optional-chaining expression is
unwrapped and used to evaluate the rest of the postfix expression. In
either case, the value of the postfix expression is still of an optional
type.

If a postfix expression that contains an optional-chaining expression is
nested inside other postfix expressions, only the outermost expression
returns an optional type. In the example below, when c is
not nil, its value is unwrapped and used to evaluate both
.property, and the
entire expression c?.property.performAction() has a value
of an optional type.

    var?
    var? =
    c()

The following example shows the behavior of the example above without
using optional chaining.

    if {
        result =
    unwrappedC()
    }

Grammar of an optional-chaining expression

‌ optional-chaining-expression →
[postfix-expression](Expressions.xhtml#postfix-expression)?
