‌‌

Closures 
--------

*Closures* are self-contained blocks of functionality that can be passed
around and used in your code. Closures in Swift are similar to blocks in
C and Objective-C and to lambdas in other programming languages.

Closures can capture and store references to any constants and variables
from the context in which they are defined. This is known as *closing*
over those constants and variables, hence the name “closures”. Swift
handles all of the memory management of capturing for you.

Note

Don’t worry if you are not familiar with the concept of “capturing”. It
is explained in detail below in [Capturing
Values](Closures.xhtml#TP40014097-CH11-XID_129).

Global and nested functions, as introduced in
[Functions](Functions.xhtml), are actually special cases of closures.
Closures take one of three forms:

-   Global functions are closures that have a name and do not capture
    any values.

-   Nested functions are closures that have a name and can capture
    values from their enclosing function.

-   Closure expressions are unnamed closures written in a lightweight
    syntax that can capture values from their surrounding context.

Swift’s closure expressions have a clean, clear style, with
optimizations that encourage brief, clutter-free syntax in common
scenarios. These optimizations include:

-   Inferring parameter and return value types from context

-   Implicit returns from single-expression closures

-   Shorthand argument names

-   Trailing closure syntax

‌

### Closure Expressions 

Nested functions, as introduced in [Nested
Functions](Functions.xhtml#TP40014097-CH10-XID_233), are a convenient
means of naming and defining self-contained blocks of code as part of a
larger function. However, it is sometimes useful to write shorter
versions of function-like constructs without a full declaration and
name. This is particularly true when you work with functions that take
other functions as one or more of their arguments.

*Closure expressions* are a way to write inline closures in a brief,
focused syntax. Closure expressions provide several syntax optimizations
for writing closures in their simplest form without loss of clarity or
intent. The closure expression examples below illustrate these
optimizations by refining a single example of the sort
function over several iterations, each of which expresses the same
functionality in a more succinct way.

‌

### The Sort Function 

Swift’s standard library provides a function called sort,
which sorts an array of values of a known type, based on the output of a
sorting closure that you provide. Once it completes the sorting process,
the sort function returns a new array of the same type
and size as the old one, with its elements in the correct sorted order.

The closure expression examples below use the sort
function to sort an array of String values in reverse
alphabetical order. Here’s the initial array to be sorted:

    let,
    "Ewa"]

The sort function takes two arguments:

-   An array of values of a known type.

-   A closure that takes two arguments of the same type as the array’s
    contents, and returns a Bool value to say whether the
    first value should appear before or after the second value once the
    values are sorted. The sorting closure needs to return
    true if the first value should appear *before* the
    second value, and false otherwise.

This example is sorting an array of String values, and so
the sorting closure needs to be a function of type
(String, String) -> Bool.

One way to provide the sorting closure is to write a normal function of
the correct type, and to pass it in as the sort
function’s second parameter:

    func,
    s2 {
        return
    }
    var,
    backwards)
    // reversed is equal to ["Ewa", "Daniella", "Chris", "Barry", "Alex"]

If the first string (s1) is greater than the second
string (s2 function will
return true should
appear before s2 in the sorted array. For characters in
strings, “greater than” means “appears later in the alphabet than”. This
means that the letter "B" is “greater than” the letter
"A" is greater than
the string "Tim". This gives a reverse alphabetical sort,
with "Barry",
and so on.

However, this is a rather long-winded way to write what is essentially a
single-expression function (a > b). In this example, it
would be preferable to write the sorting closure inline, using closure
expression syntax.

‌

### Closure Expression Syntax 

Closure expression syntax has the following general form:

-   ~~~~ 
    { (parameters) -> return type in
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    }
    ~~~~

Closure expression syntax can use constant parameters, variable
parameters, and inout parameters. Default values cannot
be provided. Variadic parameters can be used if you name the variadic
parameter and place it last in the parameter list. Tuples can also be
used as parameter types and return types.

The example below shows a closure expression version of the
backwards function from earlier:

    reversed:
    String
        return
        })

Note that the declaration of parameters and return type for this inline
closure is identical to the declaration from the
backwards function. In both cases, it is written as
(s1: String, s2: String) -> Bool. However, for the inline
closure expression, the parameters and return type are written *inside*
the curly braces, not outside of them.

The start of the closure’s body is introduced by the in
keyword. This keyword indicates that the definition of the closure’s
parameters and return type has finished, and the body of the closure is
about to begin.

Because the body of the closure is so short, it can even be written on a
single line:

    reversed:
    String
    return )

This illustrates that the overall call to the sort
function has remained the same. A pair of parentheses still wrap the
entire set of arguments for the function. However, one of those
arguments is now an inline closure.

‌

### Inferring Type From Context 

Because the sorting closure is passed as an argument to a function,
Swift can infer the types of its parameters and the type of the value it
returns from the type of the sort function’s second
parameter. This parameter is expecting a function of type
(String, String) -> Bool. This means that the
String
types do not need to be written as part of the closure expression’s
definition. Because all of the types can be inferred, the return arrow
(->) and the parentheses around the names of the
parameters can also be omitted:

    reversed,
    s2 )

It is always possible to infer parameter types and return type when
passing a closure to a function as an inline closure expression. As a
result, you rarely need to write an inline closure in its fullest form.

Nonetheless, you can make the types explicit if you wish, and doing so
is encouraged if it avoids ambiguity for readers of your code. In the
case of the sort function, the purpose of the closure is
clear from the fact that sorting is taking place, and it is safe for a
reader to assume that the closure is likely to be working with
String values, because it is assisting with the sorting
of an array of strings.

‌

### Implicit Returns from Single-Expression Closures 

Single-expression closures can implicitly return the result of their
single expression by omitting the return keyword from
their declaration, as in this version of the previous example:

    reversed,
    s2 )

Here, the function type of the sort function’s second
argument makes it clear that a Bool value must be
returned by the closure. Because the closure’s body contains a single
expression (s1 > s2
value, there is no ambiguity, and the return keyword can
be omitted.

‌

### Shorthand Argument Names 

Swift automatically provides shorthand argument names to inline
closures, which can be used to refer to the values of the closure’s
arguments by the names $0,
$2, and so on.

If you use these shorthand argument names within your closure
expression, you can omit the closure’s argument list from its
definition, and the number and type of the shorthand argument names will
be inferred from the expected function type. The in
keyword can also be omitted, because the closure expression is made up
entirely of its body:

    reversed \>
    $1 )

Here, $0 refer to the closure’s
first and second String arguments.

‌

### Operator Functions 

There’s actually an even *shorter* way to write the closure expression
above. Swift’s String type defines its string-specific
implementation of the greater-than operator (>) as a
function that has two parameters of type String, and
returns a value of type Bool. This exactly matches the
function type needed for the sort function’s second
parameter. Therefore, you can simply pass in the greater-than operator,
and Swift will infer that you want to use its string-specific
implementation:

    reversed, \>)

For more about operator functions, see [Operator
Functions](AdvancedOperators.xhtml#TP40014097-CH27-XID_43).

‌

### Trailing Closures 

If you need to pass a closure expression to a function as the function’s
final argument and the closure expression is long, it can be useful to
write it as a *trailing closure* instead. A trailing closure is a
closure expression that is written outside of (and *after*) the
parentheses of the function call it supports:

    func
    someFunctionThatTakesAClosure: () -\> ()) {
        // function body goes here
    }
     
    // here's how you call this function without using a trailing closure:
     
    someFunctionThatTakesAClosure({
        // closure's body goes here
        })
     
    // here's how you call this function with a trailing closure instead:
     
    someFunctionThatTakesAClosure() {
        // trailing closure's body goes here
    }

Note

If a closure expression is provided as the function’s only argument and
you provide that expression as a trailing closure, you do not need to
write a pair of parentheses () after the function’s name
when you call the function.

The string-sorting closure from the [Closure Expression
Syntax](Closures.xhtml#TP40014097-CH11-XID_121) section above can be
written outside of the sort function’s parentheses as a
trailing closure:

    reversed \>
    $1

Trailing closures are most useful when the closure is sufficiently long
that it is not possible to write it inline on a single line. As an
example, Swift’s Array
method which takes a closure expression as its single argument. The
closure is called once for each item in the array, and returns an
alternative mapped value (possibly of some other type) for that item.
The nature of the mapping and the type of the returned value is left up
to the closure to specify.

After applying the provided closure to each array element, the
map method returns a new array containing all of the new
mapped values, in the same order as their corresponding values in the
original array.

Here’s how you can use the map method with a trailing
closure to convert an array of Int values into an array
of String
is used to create the new array
["OneSix", "FiveEight", "FiveOneZero"]:

    let = [
        0:
    "Two",
        5:
    "Seven"
    ]
    let]

The code above creates a dictionary of mappings between the integer
digits and English-language versions of their names. It also defines an
array of integers, ready to be converted into strings.

You can now use the numbers array to create an array of
String values, by passing a closure expression to the
array’s map method as a trailing closure. Note that the
call to numbers.map does not need to include any
parentheses after map
method has only one parameter, and that parameter is provided as a
trailing closure:

    let {
        (var
        var
        while {
            output %
    10
            number
        }
        return
    }
    // strings is inferred to be of type String[]
    // its value is ["OneSix", "FiveEight", "FiveOneZero"]

The map function calls the closure expression once for
each item in the array. You do not need to specify the type of the
closure’s input parameter, number, because the type can
be inferred from the values in the array to be mapped.

In this example, the closure’s number parameter is
defined as a *variable parameter*, as described in [Constant and
Variable Parameters](Functions.xhtml#TP40014097-CH10-XID_224), so that
the parameter’s value can be modified within the closure body, rather
than declaring a new local variable and assigning the passed
number value to it. The closure expression also specifies
a return type of String, to indicate the type that will
be stored in the mapped output array.

The closure expression builds a string called output each
time it is called. It calculates the last digit of number
by using the remainder operator (number % 10), and uses
this digit to look up an appropriate string in the
digitNames dictionary.

Note

The call to the digitNames dictionary’s subscript is
followed by an exclamation mark (!), because dictionary
subscripts return an optional value to indicate that the dictionary
lookup can fail if the key does not exist. In the example above, it is
guaranteed that number % 10 will always be a valid
subscript key for the digitNames dictionary, and so an
exclamation mark is used to force-unwrap the String value
stored in the subscript’s optional return value.

The string retrieved from the digitNames dictionary is
added to the *front* of output, effectively building a
string version of the number in reverse. (The expression
number % 10 for
16, and
0.)

The number.
Because it is an integer, it is rounded down during the division, so
16 becomes
5.

The process is repeated until number /= 10 is equal to
0 string is
returned by the closure, and is added to the output array by the
map function.

The use of trailing closure syntax in the example above neatly
encapsulates the closure’s functionality immediately after the function
that closure supports, without needing to wrap the entire closure within
the map function’s outer parentheses.

‌

### Capturing Values 

A closure can *capture* constants and variables from the surrounding
context in which it is defined. The closure can then refer to and modify
the values of those constants and variables from within its body, even
if the original scope that defined the constants and variables no longer
exists.

The simplest form of a closure in Swift is a nested function, written
within the body of another function. A nested function can capture any
of its outer function’s arguments and can also capture any constants and
variables defined within the outer function.

Here’s an example of a function called makeIncrementor,
which contains a nested function called incrementor. The
nested incrementor function captures two values,
runningTotal, from its
surrounding context. After capturing these values,
incrementor
as a closure that increments runningTotal by
amount each time it is called.

    func
    amount {
        var
        func {
            runningTotal
            return
        }
        return
    }

The return type of makeIncrementor is
() -> Int. This means that it returns a *function*,
rather than a simple value. The function it returns has no parameters,
and returns an Int value each time it is called. To learn
how functions can return other functions, see [Function Types as Return
Types](Functions.xhtml#TP40014097-CH10-XID_232).

The makeIncrementor function defines an integer variable
called runningTotal, to store the current running total
of the incrementor that will be returned. This variable is initialized
with a value of 0.

The makeIncrementor function has a single
Int parameter with an external name of
forIncrement.
The argument value passed to this parameter specifies how much
runningTotal should be incremented by each time the
returned incrementor function is called.

makeIncrementor defines a nested function called
incrementor, which performs the actual incrementing. This
function simply adds amount to
runningTotal, and returns the result.

When considered in isolation, the nested incrementor
function might seem unusual:

    func {
        runningTotal
        return
    }

The incrementor function doesn’t have any parameters, and
yet it refers to runningTotal
from within its function body. It does this by capturing the *existing*
values of runningTotal from its
surrounding function and using them within its own function body.

Because it does not modify amount,
incrementor actually captures and stores a *copy* of the
value stored in amount. This value is stored along with
the new incrementor function.

However, because it modifies the runningTotal variable
each time it is called, incrementor captures a
*reference* to the current runningTotal variable, and not
just a copy of its initial value. Capturing a reference ensures sure
that runningTotal does not disappear when the call to
makeIncrementor ends, and ensures that
runningTotal will continue to be available the next time
that the incrementor function is called.

Note

Swift determines what should be captured by reference and what should be
copied by value. You don’t need to annotate amount or
runningTotal to say that they can be used within the
nested incrementor function. Swift also handles all
memory management involved in disposing of runningTotal
when it is no longer needed by the incrementor function.

Here’s an example of makeIncrementor in action:

    let =
    makeIncrementor)

This example sets a constant called incrementByTen to
refer to an incrementor function that adds 10 to its
runningTotal variable each time it is called. Calling the
function multiple times shows this behavior in action:

    incrementByTen()
    // returns a value of 10
    incrementByTen()
    // returns a value of 20
    incrementByTen()
    // returns a value of 30

If you create another incrementor, it will have its own stored reference
to a new, separate runningTotal variable. In the example
below, incrementBySeven captures a reference to a new
runningTotal variable, and this variable is unconnected
to the one captured by incrementByTen:

    let =
    makeIncrementor)
    incrementBySeven()
    // returns a value of 7
    incrementByTen()
    // returns a value of 40

Note

If you assign a closure to a property of a class instance, and the
closure captures that instance by referring to the instance or its
members, you will create a strong reference cycle between the closure
and the instance. Swift uses *capture lists* to break these strong
reference cycles. For more information, see [Strong Reference Cycles for
Closures](AutomaticReferenceCounting.xhtml#TP40014097-CH20-XID_61).

‌

### Closures Are Reference Types 

In the example above, incrementBySeven and
incrementByTen are constants, but the closures these
constants refer to are still able to increment the
runningTotal variables that they have captured. This is
because functions and closures are *reference types*.

Whenever you assign a function or a closure to a constant or a variable,
you are actually setting that constant or variable to be a *reference*
to the function or closure. In the example above, it is the choice of
closure that incrementByTen *refers to* that is constant,
and not the contents of the closure itself.

This also means that if you assign a closure to two different constants
or variables, both of those constants or variables will refer to the
same closure:

    let
    alsoIncrementByTen()
    // returns a value of 50
