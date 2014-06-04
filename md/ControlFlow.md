‌‌

Control Flow 
------------

Swift provides all the familiar control flow constructs of C-like
languages. These include for
loops to perform a task multiple times; if and
switch statements to execute different branches of code
based on certain conditions; and statements such as break
and continue to transfer the flow of execution to another
point in your code.

In addition to the traditional
for
loop found in C, Swift adds a for loop
that makes it easy to iterate over arrays, dictionaries, ranges,
strings, and other sequences.

Swift’s switch statement is also considerably more
powerful than its counterpart in C. The cases of a switch
statement do not “fall through” to the next case in Swift, avoiding
common C errors caused by missing break statements. Cases
can match many different types of pattern, including range matches,
tuples, and casts to a specific type. Matched values in a
switch case can be bound to temporary constants or
variables for use within the case’s body, and complex matching
conditions can be expressed with a where clause for each
case.

‌

### For Loops 

A for loop performs a set of statements a certain number
of times. Swift provides two kinds of for loop:

    for performs a set of statements
    for each item in a range, sequence, collection, or progression.

    for
    performs a set of statements until a specific condition is met,
    typically by incrementing a counter each time the loop ends.

‌

### For-In 

You use the for loop to iterate over
collections of items, such as ranges of numbers, items in an array, or
characters in a string.

This example prints the first few entries in the five-times-table:

    for {
        println
    \* 5)
    }
    // 1 times 5 is 5
    // 2 times 5 is 10
    // 3 times 5 is 15
    // 4 times 5 is 20
    // 5 times 5 is 25

The collection of items being iterated is a closed range of numbers from
1 inclusive, as indicated by the use
of the closed range operator (...). The value of
index is set to the first number in the range
(1), and the statements inside the loop are executed. In
this case, the loop contains only one statement, which prints an entry
from the five-times-table for the current value of index.
After the statement is executed, the value of index is
updated to contain the second value in the range (2), and
the println function is called again. This process
continues until the end of the range is reached.

In the example above, index is a constant whose value is
automatically set at the start of each iteration of the loop. As such,
it does not have to be declared before it is used. It is implicitly
declared simply by its inclusion in the loop declaration, without the
need for a let declaration keyword.

Note

The index constant exists only within the scope of the
loop. If you want to check the value of index after the
loop completes, or if you want to work with its value as a variable
rather than a constant, you must declare it yourself before its use in
the loop.

If you don’t need each value from the range, you can ignore the values
by using an underscore in place of a variable name:

    let
    let
    var
    for {
        answer
    }
    println)
    // prints "3 to the power of 10 is 59049"

This example calculates the value of one number to the power of another
(in this case, 3). It
multiplies a starting value of 1 (that is,
3,
ten times, using a half-closed loop that starts with 0
and ends with 9. This calculation doesn’t need to know
the individual counter values each time through the loop—it simply needs
to execute the loop the correct number of times. The underscore
character _ (used in place of a loop variable) causes the
individual values to be ignored and does not provide access to the
current value during each iteration of the loop.

Use the for loop with an array to
iterate over its items:

    let,
    "Brian"]
    for {
        println)
    }
    // Hello, Anna!
    // Hello, Alex!
    // Hello, Brian!
    // Hello, Jack!

You can also iterate over a dictionary to access its key-value pairs.
Each item in the dictionary is returned as a (key, value)
tuple when the dictionary is iterated, and you can decompose the
(key, value) tuple’s members as explicitly named
constants for use within in the body of the
for loop. Here, the dictionary’s keys
are decomposed into a constant called animalName, and the
dictionary’s values are decomposed into a constant called
legCount:

    let,
    "ant"]
    for
    numberOfLegs {
        println)
    }
    // spiders have 8 legs
    // ants have 6 legs
    // cats have 4 legs

Items in a Dictionary may not necessarily be iterated in
the same order as they were inserted. The contents of a
Dictionary are inherently unordered, and iterating over
them does not guarantee the order in which they will be retrieved. For
more on arrays and dictionaries, see [Collection
Types](CollectionTypes.xhtml).)

In addition to arrays and dictionaries, you can also use the
for loop to iterate over the
Character values in a string:

    for {
        println)
    }
    // H
    // e
    // l
    // l
    // o

‌

### For-Condition-Increment 

In addition to for loops, Swift
supports traditional C-style for loops with a condition
and an incrementer:

    for
    \< 3 {
        println)
    }
    // index is 0
    // index is 1
    // index is 2

Here’s the general form of this loop format:

-   ~~~~ 
    for initialization; condition; increment {
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    }
    ~~~~

Semicolons separate the three parts of the loop’s definition, as in C.
However, unlike C, Swift doesn’t need parentheses around the entire
“initialization; condition; increment” block.

The loop is executed as follows:

1.  When the loop is first entered, the *initialization expression* is
    evaluated once, to set up any constants or variables that are needed
    for the loop.

2.  The *condition expression* is evaluated. If it evaluates to
    false, the loop ends, and code execution continues
    after the for loop’s closing brace
    (}). If the expression evaluates to
    true, code execution continues by executing the
    statements inside the braces.

3.  After all statements are executed, the *increment expression* is
    evaluated. It might increase or decrease the value of a counter, or
    set one of the initialized variables to a new value based on the
    outcome of the statements. After the increment expression has been
    evaluated, execution returns to step 2, and the condition expression
    is evaluated again.

The loop format and execution process described above is shorthand for
(and equivalent to) the outline below:

-   ~~~~ 
    initialization
    ~~~~

-   ~~~~ 
    while condition {
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
        increment
    ~~~~

-   ~~~~ 
    }
    ~~~~

Constants and variables declared within the initialization expression
(such as var index = 0) are only valid within the scope
of the for loop itself. To retrieve the final value of
index after the loop ends, you must declare
index before the loop’s scope begins:

    var
    for;
    ++index {
        println)
    }
    // index is 0
    // index is 1
    // index is 2
    println)
    // prints "The loop statements were executed 3 times"

Note that the final value of index after this loop is
completed is 3. The last time the
increment statement ++index is called, it sets
index, which causes
index < 3, ending the
loop.

‌

### While Loops 

A while loop performs a set of statements until a
condition becomes false. These kinds of loops are best
used when the number of iterations is not known before the first
iteration begins. Swift provides two kinds of while loop:

    while evaluates its condition at the start of each
    pass through the loop.

    do evaluates its condition at
    the end of each pass through the loop.

‌

### While 

A while loop starts by evaluating a single condition. If
the condition is true, a set of statements is repeated
until the condition becomes false.

Here’s the general form of a while loop:

-   ~~~~ 
    while condition {
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    }
    ~~~~

This example plays a simple game of *Snakes and Ladders* (also known as
*Chutes and Ladders*):

![image: ../Art/snakesAndLadders\_2x.png](Art/snakesAndLadders_2x.png)

The rules of the game are as follows:

-   The board has 25 squares, and the aim is to land on or beyond square
    25.

-   Each turn, you roll a six-sided dice and move by that number of
    squares, following the horizontal path indicated by the dotted arrow
    above.

-   If your turn ends at the bottom of a ladder, you move up that
    ladder.

-   If your turn ends at the head of a snake, you move down that snake.

The game board is represented by an array of Int values.
Its size is based on a constant called finalSquare, which
is used to initialize the array and also to check for a win condition
later in the example. The board is initialized with 26 zero
Int
through 25 inclusive):

    let
    var:
    finalSquare)

Some squares are then set to have more specific values for the snakes
and ladders. Squares with a ladder base have a positive number to move
you up the board, whereas squares with a snake head have a negative
number to move you back down the board:

    board] =
    +11;
    board
    board] =
    -11;
    board

Square 3 contains the bottom of a ladder that moves you up to square 11.
To represent this, board[03] is equal to
+08, which is equivalent to an integer value of
8 and
11) balances
with the unary minus operator (-i), and numbers lower
than 10 are padded with zeros so that all board
definitions align. (Neither stylistic tweak is strictly necessary, but
they lead to neater code.)

The player’s starting square is “square zero”, which is just off the
bottom left corner of the board. The first dice roll always moves the
player on to the board:

    var
    var
    while {
        // roll the dice
        if
    = 1
        // move by the rolled amount
        square
        if {
            // if we're still on the board, move up or down for a snake or a ladder
            square]
        }
    }
    println)

This example uses a very simple approach to dice rolling. Instead of a
random number generator, it starts with a diceRoll value
of 0 loop,
diceRoll is incremented with the prefix increment
operator (++i), and is then checked to see if it has
become too large. The return value of ++diceRoll is equal
to the value of diceRoll *after* it is incremented.
Whenever this return value equals 7, the dice roll has
become too large, and is reset to a value of 1. This
gives a sequence of diceRoll values that is always
1,
5
and so on.

After rolling the dice, the player moves forward by
diceRoll squares. It’s possible that the dice roll may
have moved the player beyond square 25, in which case the game is over.
To cope with this scenario, the code checks that square
is less than the board
property before adding the value stored in board[square]
onto the current square value to move the player up or
down any ladders or snakes.

Had this check not been performed, board[square] might
try to access a value outside the bounds of the board
array, which would trigger an error. If square is now
equal to 26, the code would try to check the value of
board[26], which is larger than the size of the array.

The current while loop execution then ends, and the
loop’s condition is checked to see if the loop should be executed again.
If the player has moved on or beyond square number 25,
the loop’s condition evaluates to false, and the game
ends.

A while loop is appropriate in this case because the
length of the game is not clear at the start of the while
loop. Instead, the loop is executed until a particular condition is
satisfied.

‌

### Do-While 

The other variation of the while loop, known as the
do loop, performs a single pass
through the loop block first, *before* considering the loop’s condition.
It then continues to repeat the loop until the condition is
false.

Here’s the general form of a do
loop:

-   ~~~~ 
    do {
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    } while condition
    ~~~~

Here’s the *Snakes and Ladders* example again, written as a
do loop rather than a
while,
board
are initialized in exactly the same way as with a while
loop:

    let
    var:
    finalSquare)
    board] =
    +11;
    board
    board] =
    -11;
    board
    var
    var

In this version of the game, the *first* action in the loop is to check
for a ladder or a snake. No ladder on the board takes the player
straight to square 25, and so it is not possible to win the game by
moving up a ladder. Therefore, it is safe to check for a snake or a
ladder as the first action in the loop.

At the start of the game, the player is on “square zero”.
board[0], and has no
effect:

    do {
        // move up or down for a snake or ladder
        square]
        // roll the dice
        if
    = 1
        // move by the rolled amount
        square
    } while
    println)

After the code checks for snakes and ladders, the dice is rolled, and
the player is moved forward by diceRoll squares. The
current loop execution then ends.

The loop’s condition (while square < finalSquare) is the
same as before, but this time it is not evaluated until the *end* of the
first run through the loop. The structure of the
do loop is better suited to this
game than the while loop in the previous example. In the
do loop above,
square += board[square] is always executed *immediately
after* the loop’s while condition confirms that
square is still on the board. This behavior removes the
need for the array bounds check seen in the earlier version of the game.

‌

### Conditional Statements 

It is often useful to execute different pieces of code based on certain
conditions. You might want to run an extra piece of code when an error
occurs, or to display a message when a value becomes too high or too
low. To do this, you make parts of your code *conditional*.

Swift provides two ways to add conditional branches to your code, known
as the if
statement. Typically, you use the if statement to
evaluate simple conditions with only a few possible outcomes. The
switch statement is better suited to more complex
conditions with multiple possible permutations, and is useful in
situations where pattern-matching can help select an appropriate code
branch to execute.

‌

### If 

In its simplest form, the if statement has a single
if condition. It executes a set of statements only if
that condition is true:

    var
    if {
        println)
    }
    // prints "It's very cold. Consider wearing a scarf."

The preceding example checks whether the temperature is less than or
equal to 32 degrees Fahrenheit (the freezing point of water). If it is,
a message is printed. Otherwise, no message is printed, and code
execution continues after the if statement’s closing
brace.

The if statement can provide an alternative set of
statements, known as an *else clause*, for when the if
condition is false. These statements are indicated by the
else keyword:

    temperatureInFahrenheit
    if {
        println)
    } else {
        println)
    }
    // prints "It's not that cold. Wear a t-shirt."

One of these two branches is always executed. Because the temperature
has increased to 40 degrees Fahrenheit, it is no longer
cold enough to advise wearing a scarf, and so the else
branch is triggered instead.

You can chain multiple if statements together, to
consider additional clauses:

    temperatureInFahrenheit
    if {
        println)
    } else \>=
    86 {
        println)
    } else {
        println)
    }
    // prints "It's really warm. Don't forget to wear sunscreen."

Here, an additional if statement is added to respond to
particularly warm temperatures. The final else clause
remains, and prints a response for any temperatures that are neither too
warm nor too cold.

The final else clause is optional, however, and can be
excluded if the set of conditions does not need to be complete:

    temperatureInFahrenheit
    if {
        println)
    } else \>=
    86 {
        println)
    }

In this example, the temperature is neither too cold nor too warm to
trigger the if conditions, and
so no message is printed.

‌

### Switch 

A switch statement considers a value and compares it
against several possible matching patterns. It then executes an
appropriate block of code, based on the first pattern that matches
successfully. A switch statement provides an alternative
to the if statement for responding to multiple potential
states.

In its simplest form, a switch statement compares a value
against one or more values of the same type:

-   ~~~~ 
    switch some value to consider {
    ~~~~

-   ~~~~ 
    case value 1:
    ~~~~

-   ~~~~ 
        respond to value 1
    ~~~~

-   ~~~~ 
    case value 2,
    ~~~~

-   ~~~~ 
    value 3:
    ~~~~

-   ~~~~ 
        respond to value 2 or 3
    ~~~~

-   ~~~~ 
    default:
    ~~~~

-   ~~~~ 
        otherwise, do something else
    ~~~~

-   ~~~~ 
    }
    ~~~~

Every switch statement consists of multiple possible
*cases*, each of which begins with the case keyword. In
addition to comparing against specific values, Swift provides several
ways for each case to specify more complex matching patterns. These
options are described later in this section.

The body of each switch case is a separate branch of code
execution, in a similar manner to the branches of an if
statement. The switch statement determines which branch
should be selected. This is known as *switching* on the value that is
being considered.

Every switch statement must be *exhaustive*. That is,
every possible value of the type being considered must be matched by one
of the switch cases. If it is not appropriate to provide
a switch case for every possible value, you can define a
default catch-all case to cover any values that are not addressed
explicitly. This catch-all case is indicated by the keyword
default, and must always appear last.

This example uses a switch statement to consider a single
lowercase character called someCharacter:

    let
    switch {
    case,
    "u":
        println)
    case,
    "g",
    "n",
    "t":
        println)
    default:
        println)
    }
    // prints "e is a vowel"

The switch statement’s first case matches all five
lowercase vowels in the English language. Similarly, its second case
matches all lowercase English consonants.

It is not practical to write all other possible characters as part of a
switch statement
provides a default case to match all other characters
that are not vowels or consonants. This provision ensures that the
switch statement is exhaustive.

‌

### No Implicit Fallthrough 

In contrast with switch statements in C and Objective-C,
switch statements in Swift do not fall through the bottom
of each case and into the next one by default. Instead, the entire
switch statement finishes its execution as soon as the
first matching switch case is completed, without
requiring an explicit break statement. This makes the
switch statement safer and easier to use than in C, and
avoids executing more than one switch case by mistake.

Note

You can still break out of a matched switch case before
that case has completed its execution if you need to. See [Break in a
Switch Statement](ControlFlow.xhtml#TP40014097-CH9-XID_176) for details.

The body of each case *must* contain at least one executable statement.
It is not valid to write the following code, because the first case is
empty:

    let =
    "a"
    switch {
    case:
    case:
        println)
    default:
        println)
    }
    // this will report a compile-time error

Unlike a switch statement in C, this
switch
and "A". Rather, it reports a compile-time error that
case "a": does not contain any executable statements.
This approach avoids accidental fallthrough from one case to another,
and makes for safer code that is clearer in its intent.

Multiple matches for a single switch case can be
separated by commas, and can be written over multiple lines if the list
is long:

-   ~~~~ 
    switch some value to consider {
    ~~~~

-   ~~~~ 
    case value 1,
    ~~~~

-   ~~~~ 
    value 2:
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    }
    ~~~~

Note

To opt in to fallthrough behavior for a particular switch
case, use the fallthrough keyword, as described in
[Fallthrough](ControlFlow.xhtml#TP40014097-CH9-XID_178).

‌

### Range Matching 

Values in switch cases can be checked for their inclusion
in a range. This example uses number ranges to provide a
natural-language count for numbers of any size:

    let
    let =
    "stars in the Milky Way"
    var
    switch {
    case:
        naturalCount
    case:
        naturalCount
    case:
        naturalCount
    case:
        naturalCount
    case:
        naturalCount
    case:
        naturalCount
    default:
        naturalCount
    }
    println)
    // prints "There are millions and millions of stars in the Milky Way."

‌

### Tuples 

You can use tuples to test multiple values in the same
switch statement. Each element of the tuple can be tested
against a different value or range of values. Alternatively, use the
underscore (_) identifier to match any possible value.

The example below takes an (x, y) point, expressed as a simple tuple of
type (Int, Int), and categorizes it on the graph that
follows the example:

    let)
    switch {
    case):
        println)
    case):
        println)
    case):
        println)
    case):
        println)
    default:
        println)
    }
    // prints "(1, 1) is inside the box"

![image:
../Art/coordinateGraphSimple\_2x.png](Art/coordinateGraphSimple_2x.png)

The switch statement determines if the point is at the
origin (0, 0); on the red x-axis; on the orange y-axis; inside the blue
4-by-4 box centered on the origin; or outside of the box.

Unlike C, Swift allows multiple switch cases to consider
the same value or values. In fact, the point (0, 0) could match all
*four* of the cases in this example. However, if multiple matches are
possible, the first matching case is always used. The point (0, 0) would
match case (0, 0) first, and so all other matching cases
would be ignored.

‌

### Value Bindings 

A switch case can bind the value or values it matches to
temporary constants or variables, for use in the body of the case. This
is known as *value binding*, because the values are “bound” to temporary
constants or variables within the case’s body.

The example below takes an (x, y) point, expressed as a tuple of type
(Int, Int) and categorizes it on the graph that follows:

    let)
    switch {
    case):
        println)
    case):
        println)
    case):
        println)
    }
    // prints "on the x-axis with an x value of 2"

![image:
../Art/coordinateGraphMedium\_2x.png](Art/coordinateGraphMedium_2x.png)

The switch statement determines if the point is on the
red x-axis, on the orange y-axis, or elsewhere, on neither axis.

The three switch cases declare placeholder constants
x, which temporarily take on one or
both tuple values from anotherPoint. The first case,
case (let x, 0), matches any point with a
y and assigns the point’s
x.
Similarly, the second case, case (0, let y), matches any
point with an x and assigns the
point’s y value to the temporary constant
y.

Once the temporary constants are declared, they can be used within the
case’s code block. Here, they are used as shorthand for printing the
values with the println function.

Note that this switch statement does not have a
default case. The final case,
case let (x, y), declares a tuple of two placeholder
constants that can match any value. As a result, it matches all possible
remaining values, and a default case is not needed to
make the switch statement exhaustive.

In the example above, x are declared
as constants with the let keyword, because there is no
need to modify their values within the body of the case. However, they
could have been declared as variables instead, with the
var keyword. If this had been done, a temporary variable
would have been created and initialized with the appropriate value. Any
changes to that variable would only have an effect within the body of
the case.

‌

### Where 

A switch clause to
check for additional conditions.

The example below categorizes an (x, y) point on the following graph:

    let)
    switch {
    case
    x:
        println)
    case
    x:
        println)
    case):
        println)
    }
    // prints "(1, -1) is on the line x == -y"

![image:
../Art/coordinateGraphComplex\_2x.png](Art/coordinateGraphComplex_2x.png)

The switch statement determines if the point is on the
green diagonal line where x == y, on the purple diagonal
line where x == -y, or neither.

The three switch cases declare placeholder constants
x, which temporarily take on the two
tuple values from point. These constants are used as part
of a where clause, to create a dynamic filter. The
switch case matches the current value of
point clause’s condition
evaluates to true for that value.

As in the previous example, the final case matches all possible
remaining values, and so a default case is not needed to
make the switch statement exhaustive.

‌

### Control Transfer Statements 

*Control transfer statements* change the order in which your code is
executed, by transferring control from one piece of code to another.
Swift has four control transfer statements:

    continue

    break

    fallthrough

    return

The control and
fallthrough statements are described below. The
return statement is described in
[Functions](Functions.xhtml).

‌

### Continue 

The continue statement tells a loop to stop what it is
doing and start again at the beginning of the next iteration through the
loop. It says “I am done with the current loop iteration” without
leaving the loop altogether.

Note

In a
for
loop, the incrementer is still evaluated after calling the
continue statement. The loop itself continues to work as
usual; only the code within the loop’s body is skipped.

The following example removes all vowels and spaces from a lowercase
string to create a cryptic puzzle phrase:

    let =
    "great minds think alike"
    var
    for {
        switch {
        case,
    "u":
            continue
        default:
            puzzleOutput
        }
    }
    println)
    // prints "grtmndsthnklk"

The code above calls the continue keyword whenever it
matches a vowel or a space, causing the current iteration of the loop to
end immediately and to jump straight to the start of the next iteration.
This behavior enables the switch block to match (and ignore) only the
vowel and space characters, rather than requiring the block to match
every character that should get printed.

‌

### Break 

The break statement ends execution of an entire control
flow statement immediately. The break statement can be
used inside a switch statement or loop statement when you
want to terminate the execution of the switch or loop
statement earlier than would otherwise be the case.

‌

### Break in a Loop Statement 

When used inside a loop statement, break ends the loop’s
execution immediately, and transfers control to the first line of code
after the loop’s closing brace (}). No further code from
the current iteration of the loop is executed, and no further iterations
of the loop are started.

‌

### Break in a Switch Statement 

When used inside a switch
causes the switch statement to end its execution
immediately, and to transfer control to the first line of code after the
switch).

This behavior can be used to match and ignore one or more cases in a
switch
statement is exhaustive and does not allow empty cases, it is sometimes
necessary to deliberately match and ignore a case in order to make your
intentions explicit. You do this by writing the break
statement as the entire body of the case you want to ignore. When that
case is matched by the switch statement, the
break statement inside the case ends the
switch statement’s execution immediately.

Note

A switch case that only contains a comment is reported as
a compile-time error. Comments are not statements and do not cause a
switch case to be ignored. Always use a
break case.

The following example switches on a Character value and
determines whether it represents a number symbol in one of four
languages. Multiple values are covered in a single switch
case for brevity:

    let
    // Simplified Chinese for the number 3
    var?
    switch {
    case:
        possibleIntegerValue
    case:
        possibleIntegerValue
    case:
        possibleIntegerValue
    case:
        possibleIntegerValue
    default:
        break
    }
    if =
    possibleIntegerValue {
        println)
    } else {
        println)
    }
    // prints "The integer value of 三 is 3."

This example checks numberSymbol to determine whether it
is a Latin, Arabic, Chinese, or Thai symbol for the numbers
1. If a match is found, one of the
switch statement’s cases sets an optional
Int?
to an appropriate integer value.

After the switch statement completes its execution, the example uses
optional binding to determine whether a value was found. The
possibleIntegerValue variable has an implicit initial
value of nil by virtue of being an optional type, and so
the optional binding will succeed only if
possibleIntegerValue was set to an actual value by one of
the switch statement’s first four cases.

It is not practical to list every possible Character
value in the example above, so a default case provides a
catchall for any characters that are not matched. This
default case does not need to perform any action, and so
it is written with a single break statement as its body.
As soon as the default statement is matched, the
break
statement’s execution, and code execution continues from the
if let statement.

‌

### Fallthrough 

Switch statements in Swift do not fall through the bottom of each case
and into the next one. Instead, the entire switch statement completes
its execution as soon as the first matching case is completed. By
contrast, C requires you to insert an explicit break
statement at the end of every switch case to prevent
fallthrough. Avoiding default fallthrough means that Swift
switch statements are much more concise and predictable
than their counterparts in C, and thus they avoid executing multiple
switch cases by mistake.

If you really need C-style fallthrough behavior, you can opt in to this
behavior on a case-by-case basis with the fallthrough
keyword. The example below uses fallthrough to create a
textual description of a number:

    let
    var =
    "The number 
    switch {
    case,
    13:
        description
        fallthrough
    default:
        description
    }
    println)
    // prints "The number 5 is a prime number, and also an integer."

This example declares a new String variable called
description and assigns it an initial value. The function
then considers the value of integerToDescribe using a
switch statement. If the value of
integerToDescribe is one of the prime numbers in the
list, the function appends text to the end of
description, to note that the number is prime. It then
uses the fallthrough keyword to “fall into” the
default case
adds some extra text to the end of the description, and the
switch statement is complete.

If the value of integerToDescribe is *not* in the list of
known prime numbers, it is not matched by the first
switch case at all. There are no other specific cases,
and so integerToDescribe is matched by the catchall
default case.

After the switch statement has finished executing, the
number’s description is printed using the println
function. In this example, the number 5 is correctly
identified as a prime number.

Note

The fallthrough keyword does not check the case
conditions for the switch case that it causes execution
to fall into. The fallthrough keyword simply causes code
execution to move directly to the statements inside the next case (or
default case) block, as in C’s standard
switch statement behavior.

‌

### Labeled Statements 

You can nest loops and switch statements inside other
loops and switch statements in Swift to create complex
control flow structures. However, loops and switch
statements can both use the break statement to end their
execution prematurely. Therefore, it is sometimes useful to be explicit
about which loop or switch statement you want a
break statement to terminate. Similarly, if you have
multiple nested loops, it can be useful to be explicit about which loop
the continue statement should affect.

To achieve these aims, you can mark a loop statement or
switch statement with a *statement label*, and use this
label with the break
statement to end or continue the execution of the labeled statement.

A labeled statement is indicated by placing a label on the same line as
the statement’s introducer keyword, followed by a colon. Here’s an
example of this syntax for a while loop, although the
principle is the same for all loops and switch
statements:

-   ~~~~ 
    label name: while condition {
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    }
    ~~~~

The following example uses the break and
continue
loop for an adapted version of the *Snakes and Ladders* game that you
saw earlier in this chapter. This time around, the game has an extra
rule:

-   To win, you must land *exactly* on square 25.

If a particular dice roll would take you beyond square 25, you must roll
again until you roll the exact number needed to land on square 25.

The game board is the same as before:

![image: ../Art/snakesAndLadders\_2x.png](Art/snakesAndLadders_2x.png)

The values of finalSquare,
square are initialized in
the same way as before:

    let
    var:
    finalSquare)
    board] =
    +11;
    board
    board] =
    -11;
    board
    var
    var

This version of the game uses a while loop and a
switch statement to implement the game’s logic. The
while loop has a statement label called
gameLoop, to indicate that it is the main game loop for
the Snakes and Ladders game.

The while loop’s condition is
while square != finalSquare, to reflect that you must
land exactly on square 25:

    gameLoop !=
    finalSquare {
        if
    = 1
        switch {
        case:
            // diceRoll will move us to the final square, so the game is over
            break
        case
    newSquare:
            // diceRoll will move us beyond the final square, so roll again
            continue
        default:
            // this is a valid move, so find out its effect
            square
            square]
        }
    }
    println)

The dice is rolled at the start of each loop. Rather than moving the
player immediately, a switch statement is used to
consider the result of the move, and to work out if the move is allowed:

-   If the dice roll will move the player onto the final square, the
    game is over. The break gameLoop statement transfers
    control to the first line of code outside of the
    while loop, which ends the game.

-   If the dice roll will move the player *beyond* the final square, the
    move is invalid, and the player needs to roll again. The
    continue gameLoop statement ends the current
    while loop iteration and begins the next iteration of
    the loop.

-   In all other cases, the dice roll is a valid move. The player moves
    forward by diceRoll squares, and the game logic
    checks for any snakes and ladders. The loop then ends, and control
    returns to the while condition to decide whether
    another turn is required.

Note

If the break statement above did not use the
gameLoop label, it would break out of the
switch statement.
Using the gameLoop label makes it clear which control
statement should be terminated.

Note also that it is not strictly necessary to use the
gameLoop label when calling
continue gameLoop to jump to the next iteration of the
loop. There is only one loop in the game, and so there is no ambiguity
as to which loop the continue statement will affect.
However, there is no harm in using the gameLoop label
with the continue statement. Doing so is consistent with
the label’s use alongside the break statement, and helps
make the game’s logic clearer to read and understand.
