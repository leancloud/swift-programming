‌‌

Advanced Operators 
------------------

In addition to the operators described in [Basic
Operators](BasicOperators.xhtml), Swift provides several advanced
operators that perform more complex value manipulation. These include
all of the bitwise and bit shifting operators you will be familiar with
from C and Objective-C.

Unlike arithmetic operators in C, arithmetic operators in Swift do not
overflow by default. Overflow behavior is trapped and reported as an
error. To opt in to overflow behavior, use Swift’s second set of
arithmetic operators that overflow by default, such as the overflow
addition operator (&+). All of these overflow operators
begin with an ampersand (&).

When you define your own structures, classes, and enumerations, it can
be useful to provide your own implementations of the standard Swift
operators for these custom types. Swift makes it easy to provide
tailored implementations of these operators and to determine exactly
what their behavior should be for each type you create.

You’re not just limited to the predefined operators. Swift gives you the
freedom to define your own custom infix, prefix, postfix, and assignment
operators, with custom precedence and associativity values. These
operators can be used and adopted in your code just like any of the
predefined operators, and you can even extend existing types to support
the custom operators you define.

‌

### Bitwise Operators 

*Bitwise operators* enable you to manipulate the individual raw data
bits within a data structure. They are often used in low-level
programming, such as graphics programming and device driver creation.
Bitwise operators can also be useful when you work with raw data from
external sources, such as encoding and decoding data for communication
over a custom protocol.

Swift supports all of the bitwise operators found in C, as described
below.

‌

### Bitwise NOT Operator 

The *bitwise NOT operator* (~) inverts all bits in a
number:

![image: ../Art/bitwiseNOT\_2x.png](Art/bitwiseNOT_2x.png)

The bitwise NOT operator is a prefix operator, and appears immediately
before the value it operates on, without any white space:

    let =
    0b00001111
    let
    // equals 11110000

UInt8 integers have eight bits and can store any value
between 0. This example
initializes a UInt8 integer with the binary value
00001111, which has its first four bits set to
0. This
is equivalent to a decimal value of 15.

The bitwise NOT operator is then used to create a new constant called
invertedBits, which is equal to
initialBits, but with all of the bits inverted. Zeroes
become ones, and ones become zeroes. The value of
invertedBits, which is equal
to an unsigned decimal value of 240.

‌

### Bitwise AND Operator 

The *bitwise AND operator* (&) combines the bits of two
numbers. It returns a new number whose bits are set to 1
only if the bits were equal to 1 in *both* input numbers:

![image: ../Art/bitwiseAND\_2x.png](Art/bitwiseAND_2x.png)

In the example below, the values of firstSixBits and
lastSixBits both have four middle bits equal to
1. The bitwise AND operator combines them to make the
number 00111100, which is equal to an unsigned decimal
value of 60:

    let =
    0b11111100
    let =
    0b00111111
    let &
    lastSixBits

‌

### Bitwise OR Operator 

The *bitwise OR operator* (|) compares the bits of two
numbers. The operator returns a new number whose bits are set to
1 in *either*
input number:

![image: ../Art/bitwiseOR\_2x.png](Art/bitwiseOR_2x.png)

In the example below, the values of someBits and
moreBits. The
bitwise OR operator combines them to make the number
11111110, which equals an unsigned decimal of
254:

    let
    let
    let |
    moreBits

‌

### Bitwise XOR Operator 

The *bitwise XOR operator*, or “exclusive OR operator”
(^), compares the bits of two numbers. The operator
returns a new number whose bits are set to 1 where the
input bits are different and are set to 0 where the input
bits are the same:

![image: ../Art/bitwiseXOR\_2x.png](Art/bitwiseXOR_2x.png)

In the example below, the values of firstBits and
otherBits in a
location that the other does not. The bitwise XOR operator sets both of
these bits to 1 in its output value. All of the other
bits in firstBits match and
are set to 0 in the output value:

    let
    let
    let \^
    otherBits

‌

### Bitwise Left and Right Shift Operators 

The *bitwise left shift operator* (<<) and *bitwise right
shift operator* (>>) move all bits in a number to the
left or the right by a certain number of places, according to the rules
defined below.

Bitwise left and right shifts have the effect of multiplying or dividing
an integer number by a factor of two. Shifting an integer’s bits to the
left by one position doubles its value, whereas shifting it to the right
by one position halves its value.

‌

### Shifting Behavior for Unsigned Integers 

The bit-shifting behavior for unsigned integers is as follows:

1.  Existing bits are moved to the left or right by the requested number
    of places.

2.  Any bits that are moved beyond the bounds of the integer’s storage
    are discarded.

3.  Zeroes are inserted in the spaces left behind after the original
    bits are moved to the left or right.

This approach is known as a *logical shift*.

The illustration below shows the results of 11111111 << 1
(which is 11111111 shifted to the left by
1 (which is
11111111 place).
Blue numbers are shifted, gray numbers are discarded, and orange zeroes
are inserted:

![image: ../Art/bitshiftUnsigned\_2x.png](Art/bitshiftUnsigned_2x.png)

Here’s how bit shifting looks in Swift code:

    let
    // 00000100 in binary
    shiftBits
    shiftBits
    shiftBits
    shiftBits
    shiftBits

You can use bit shifting to encode and decode values within other data
types:

    let
    let &
    0xFF0000
    let &
    0x00FF00
    let &
    0x0000FF

This example uses a UInt32 constant called
pink to store a Cascading Style Sheets color value for
the color pink. The CSS color value #CC6699 is written as
0xCC6699 in Swift’s hexadecimal number representation.
This color is then decomposed into its red (CC), green
(66) components by the
bitwise AND operator (&) and the bitwise right shift
operator (>>).

The red component is obtained by performing a bitwise AND between the
numbers 0xCC6699. The zeroes
in 0xFF0000 effectively “mask” the second and third bytes
of 0xCC6699 to be
ignored and leaving 0xCC0000 as the result.

This number is then shifted 16 places to the right
(>> 16). Each pair of characters in a hexadecimal number
uses 8 bits, so a move 16 places to the right will convert
0xCC0000. This is the same
as 0xCC.

Similarly, the green component is obtained by performing a bitwise AND
between the numbers 0xCC6699,
which gives an output value of 0x006600. This output
value is then shifted eight places to the right, giving a a value of
0x66.

Finally, the blue component is obtained by performing a bitwise AND
between the numbers 0xCC6699,
which gives an output value of 0x000099. There’s no need
to shift this to the right, as 0x000099 already equals
0x99.

‌

### Shifting Behavior for Signed Integers 

The shifting behavior is more complex for signed integers than for
unsigned integers, because of the way signed integers are represented in
binary. (The examples below are based on 8-bit signed integers for
simplicity, but the same principles apply for signed integers of any
size.)

Signed integers use their first bit (known as the *sign bit*) to
indicate whether the integer is positive or negative. A sign bit of
0
means negative.

The remaining bits (known as the *value bits*) store the actual value.
Positive numbers are stored in exactly the same way as for unsigned
integers, counting upwards from 0. Here’s how the bits
inside an Int8:

![image:
../Art/bitshiftSignedFour\_2x.png](Art/bitshiftSignedFour_2x.png)

The sign bit is 0 (meaning “positive”), and the seven
value bits are just the number 4, written in binary
notation.

Negative numbers, however, are stored differently. They are stored by
subtracting their absolute value from 2 to the power of
n is the number of value bits. An
eight-bit number has seven value bits, so this means 2 to
the power of 7.

Here’s how the bits inside an Int8 look for the number
-4:

![image:
../Art/bitshiftSignedMinusFour\_2x.png](Art/bitshiftSignedMinusFour_2x.png)

This time, the sign bit is 1 (meaning “negative”), and
the seven value bits have a binary value of 124 (which is
128 - 4):

![image:
../Art/bitshiftSignedMinusFourValue\_2x.png](Art/bitshiftSignedMinusFourValue_2x.png)

The encoding for negative numbers is known as a *two’s complement*
representation. It may seem an unusual way to represent negative
numbers, but it has several advantages.

First, you can add -1, simply by
performing a standard binary addition of all eight bits (including the
sign bit), and discarding anything that doesn’t fit in the eight bits
once you’re done:

![image:
../Art/bitshiftSignedAddition\_2x.png](Art/bitshiftSignedAddition_2x.png)

Second, the two’s complement representation also lets you shift the bits
of negative numbers to the left and right like positive numbers, and
still end up doubling them for every shift you make to the left, or
halving them for every shift you make to the right. To achieve this, an
extra rule is used when signed integers are shifted to the right:

-   When you shift signed integers to the right, apply the same rules as
    for unsigned integers, but fill any empty bits on the left with the
    *sign bit*, rather than with a zero.

![image: ../Art/bitshiftSigned\_2x.png](Art/bitshiftSigned_2x.png)

This action ensures that signed integers have the same sign after they
are shifted to the right, and is known as an *arithmetic shift*.

Because of the special way that positive and negative numbers are
stored, shifting either of them to the right moves them closer to zero.
Keeping the sign bit the same during this shift means that negative
integers remain negative as their value moves closer to zero.

‌

### Overflow Operators 

If you try to insert a number into an integer constant or variable that
cannot hold that value, by default Swift reports an error rather than
allowing an invalid value to be created. This behavior gives extra
safety when you work with numbers that are too large or too small.

For example, the Int16 integer type can hold any signed
integer number between -32768.
Trying to set a UInt16 constant or variable to a number
outside of this range causes an error:

    var =
    Int16
    // potentialOverflow equals 32767, which is the largest value an Int16 can hold
    potentialOverflow
    // this causes an error

Providing error handling when values get too large or too small gives
you much more flexibility when coding for boundary value conditions.

However, when you specifically want an overflow condition to truncate
the number of available bits, you can opt in to this behavior rather
than triggering an error. Swift provides five arithmetic *overflow
operators* that opt in to the overflow behavior for integer
calculations. These operators all begin with an ampersand
(&):

-   Overflow addition (&+)

-   Overflow subtraction (&-)

-   Overflow multiplication (&*)

-   Overflow division (&/)

-   Overflow remainder (&%)

‌

### Value Overflow 

Here’s an example of what happens when an unsigned value is allowed to
overflow, using the overflow addition operator (&+):

    var
    // willOverflow equals 255, which is the largest value a UInt8 can hold
    willOverflow
    // willOverflow is now equal to 0

The variable willOverflow is initialized with the largest
value a UInt8, or
11111111 in binary). It is then incremented by
1 using the overflow addition operator
(&+). This pushes its binary representation just over the
size that a UInt8 can hold, causing it to overflow beyond
its bounds, as shown in the diagram below. The value that remains within
the bounds of the UInt8 after the overflow addition is
00000000, or zero:

![image: ../Art/overflowAddition\_2x.png](Art/overflowAddition_2x.png)

‌

### Value Underflow 

Numbers can also become too small to fit in their type’s maximum bounds.
Here’s an example.

The *smallest* value that a UInt8 can hold is 0 (which is
00000000 in eight-bit binary form). If you subtract
1 using the overflow
subtraction operator, the number will overflow back round to
11111111 in decimal:

![image:
../Art/overflowUnsignedSubtraction\_2x.png](Art/overflowUnsignedSubtraction_2x.png)

Here’s how that looks in Swift code:

    var
    // willUnderflow equals 0, which is the smallest value a UInt8 can hold
    willUnderflow
    // willUnderflow is now equal to 255

A similar underflow occurs for signed integers. All subtraction for
signed integers is performed as straight binary subtraction, with the
sign bit included as part of the numbers being subtracted, as described
in [Bitwise Left and Right Shift
Operators](AdvancedOperators.xhtml#TP40014097-CH27-XID_34). The smallest
number that an Int8,
which is 10000000
from this binary number with the overflow operator gives a binary value
of 01111111, which toggles the sign bit and gives
positive 127, the largest positive value that an
Int8 can hold:

![image:
../Art/overflowSignedSubtraction\_2x.png](Art/overflowSignedSubtraction_2x.png)

Here’s the same thing in Swift code:

    var
    // signedUnderflow equals -128, which is the smallest value an Int8 can hold
    signedUnderflow
    // signedUnderflow is now equal to 127

The end result of the overflow and underflow behavior described above is
that for both signed and unsigned integers, overflow always wraps around
from the largest valid integer value back to the smallest, and underflow
always wraps around from the smallest value to the largest.

‌

### Division by Zero 

Dividing a number by zero (i / 0), or trying to calculate
remainder by zero (i % 0), causes an error:

    let
    let

However, the overflow versions of these operators (&/ and
&%) return a value of zero if you divide by zero:

    let
    let
    // y is equal to 0

‌

### Precedence and Associativity 

Operator *precedence* gives some operators higher priority than others;
these operators are calculated first.

Operator *associativity* defines how operators of the same precedence
are grouped together (or *associated*)—either grouped from the left, or
grouped from the right. Think of it as meaning “they associate with the
expression to their left,” or “they associate with the expression to
their right.”

It is important to consider each operator’s precedence and associativity
when working out the order in which a compound expression will be
calculated. Here’s an example. Why does the following expression equal
4?

    2
    // this equals 4

Taken strictly from left to right, you might expect this to read as
follows:

-   2 plus 3 equals 5;

-   5 times 4 equals 20;

-   20 remainder 5 equals 0

However, the actual answer is 4.
Higher-precedence operators are evaluated before lower-precedence ones.
In Swift, as in C, the multiplication operator (*) and
the remainder operator (%) have a higher precedence than
the addition operator (+). As a result, they are both
evaluated before the addition is considered.

However, multiplication and remainder have the *same* precedence as each
other. To work out the exact evaluation order to use, you also need to
consider their associativity. Multiplication and remainder both
associate with the expression to their left. Think of this as adding
implicit parentheses around these parts of the expression, starting from
their left:

    2)

(3 * 4), so this is equivalent to:

    2)

(12 % 5), so this is equivalent to:

    2

This calculation yields the final answer of 4.

For a complete list of Swift operator precedences and associativity
rules, see [Expressions](Expressions.xhtml).

Note

Swift’s operator precedences and associativity rules are simpler and
more predictable than those found in C and Objective-C. However, this
means that they are not the same as in C-based languages. Be careful to
ensure that operator interactions still behave in the way you intend
when porting existing code to Swift.

‌

### Operator Functions 

Classes and structures can provide their own implementations of existing
operators. This is known as *overloading* the existing operators.

The example below shows how to implement the arithmetic addition
operator (+) for a custom structure. The arithmetic
addition operator is a *binary operator* because it operates on two
targets and is said to be *infix* because it appears in between those
two targets.

The example defines a Vector2D structure for a
two-dimensional position vector (x, y), followed by a
definition of an *operator function* to add together instances of the
Vector2D structure:

    struct {
        var
    }
    @infix,
    right {
        return:
    left:
    left)
    }

The operator function is defined as a global function called
+, which takes two input parameters of type
Vector2D and returns a single output value, also of type
Vector2D. You implement an infix operator by writing the
@infix keyword
when declaring the operator function.

In this implementation, the input parameters are named
left to represent the
Vector2D instances that will be on the left side and
right side of the + operator. The function returns a new
Vector2D and
y properties are initialized with the sum of the
x properties from the two
Vector2D instances that are added together.

The function is defined globally, rather than as a method on the
Vector2D structure, so that it can be used as an infix
operator between existing Vector2D instances:

    let:
    3.0)
    let:
    2.0)
    let +
    anotherVector
    // combinedVector is a Vector2D instance with values of (5.0, 5.0)

This example adds together the vectors (3.0, 1.0) and
(2.0, 4.0),
as illustrated below.

![image: ../Art/vectorAddition\_2x.png](Art/vectorAddition_2x.png)

‌

### Prefix and Postfix Operators 

The example shown above demonstrates a custom implementation of a binary
infix operator. Classes and structures can also provide implementations
of the standard *unary operators*. Unary operators operate on a single
target. They are *prefix* if they precede their target (such as
-a) and *postfix* operators if they follow their target
(such as i++).

You implement a prefix or postfix unary operator by writing the
@prefix attribute before the
func keyword when declaring the operator function:

    @prefix)
    -\> Vector2D {
        return:
    -vector)
    }

The example above implements the unary minus operator
(-a instances. The unary
minus operator is a prefix operator, and so this function has to be
qualified with the @prefix attribute.

For simple numeric values, the unary minus operator converts positive
numbers into their negative equivalent and vice versa. The corresponding
implementation for Vector2D instances performs this
operation on both the x properties:

    let:
    3.0)
    let
    // negative is a Vector2D instance with values of (-3.0, -4.0)
    let
    // alsoPositive is a Vector2D instance with values of (3.0, 4.0)

‌

### Compound Assignment Operators 

*Compound assignment operators* combine assignment (=)
with another operation. For example, the addition assignment operator
(+=) combines addition and assignment into a single
operation. Operator functions that implement compound assignment must be
qualified with the @assignment attribute. You must also
mark a compound assignment operator’s left input parameter as
inout, because the parameter’s value will be modified
directly from within the operator function.

The example below implements an addition assignment operator function
for Vector2D instances:

    @assignment:
    Vector2D) {
        left
    }

Because an addition operator was defined earlier, you don’t need to
reimplement the addition process here. Instead, the addition assignment
operator function takes advantage of the existing addition operator
function, and uses it to set the left value to be the left value plus
the right value:

    var:
    1.0)
    let:
    3.0)
    original
    // original now has values of (4.0, 6.0)

You can combine the @assignment attribute with either the
@prefix attribute, as in this
implementation of the prefix increment operator (++a) for
Vector2D instances:

    @prefix ++
    (inout {
        vector,
    y)
        return
    }

The prefix increment operator function above takes advantage of the
addition assignment operator defined earlier. It adds a
Vector2D
values of 1.0 on which it
is called, and returns the result:

    var:
    3.0)
    let
    // toIncrement now has values of (4.0, 5.0)
    // afterIncrement also has values of (4.0, 5.0)

Note

It is not possible to overload the default assignment operator
(=). Only the compound assignment operators can be
overloaded. Similarly, the ternary conditional operator
(a ? b : c) cannot be overloaded.

‌

### Equivalence Operators 

Custom classes and structures do not receive a default implementation of
the *equivalence operators*, known as the “equal to” operator
(==). It
is not possible for Swift to guess what would qualify as “equal” for
your own custom types, because the meaning of “equal” depends on the
roles that those types play in your code.

To use the equivalence operators to check for equivalence of your own
custom type, provide an implementation of the operators in the same way
as for other infix operators:

    @infix,
    right {
        return ==
    right ==
    right)
    }
    @infix,
    right {
        return)
    }

The above example implements an “equal to” operator (==)
to check if two Vector2D instances have equivalent
values. In the context of Vector2D, it makes sense to
consider “equal” as meaning “both instances have the same
x values”, and so this is the
logic used by the operator implementation. The example also implements
the “not equal to” operator (!=), which simply returns
the inverse of the result of the “equal to” operator.

You can now use these operators to check whether two
Vector2D instances are equivalent:

    let:
    2.0)
    let =
    Vector2D)
    if {
        println)
    }
    // prints "These two vectors are equivalent."

‌

### Custom Operators 

You can declare and implement your own *custom operators* in addition to
the standard operators provided by Swift. Custom operators can be
defined only with the characters
/ = - + * % < > ! & | ^ . ~.

New operators are declared at a global level using the
operator keyword, and can be declared as
prefix:

    operator

The example above defines a new prefix operator called
+++. This operator does not have an existing meaning in
Swift, and so it is given its own custom meaning below in the specific
context of working with Vector2D instances. For the
purposes of this example, +++ is treated as a new “prefix
doubling incrementer” operator. It doubles the x and
y instance, by adding
the vector to itself with the addition assignment operator defined
earlier:

    @prefix +++
    (inout {
        vector
        return
    }

This implementation of +++ is very similar to the
implementation of ++, except
that this operator function adds the vector to itself, rather than
adding Vector2D(1.0, 1.0):

    var:
    1.0)
    let
    // toBeDoubled now has values of (2.0, 8.0)
    // afterDoubling also has values of (2.0, 8.0)

‌

### Precedence and Associativity for Custom Infix Operators 

Custom infix operators can also specify a *precedence*
and an *associativity*. See [Precedence and
Associativity](AdvancedOperators.xhtml#TP40014097-CH27-XID_41) for an
explanation of how these two characteristics affect an infix operator’s
interaction with other infix operators.

The possible values for associativity are
left.
Left-associative operators associate to the left if written next to
other left-associative operators of the same precedence. Similarly,
right-associative operators associate to the right if written next to
other right-associative operators of the same precedence.
Non-associative operators cannot be written next to other operators with
the same precedence.

The associativity
if it is not specified. The precedence value defaults to
100 if it is not specified.

The following example defines a new custom infix operator
called +- associativity and a
precedence of 140:

    operator
    left
    func:
    Vector2D {
        return:
    left:
    left)
    }
    let:
    1.0)
    let:
    3.0)
    let +-
    secondVector
    // plusMinusVector is a Vector2D instance with values of (4.0, -2.0)

This operator adds together the x values of two vectors,
and subtracts the y value of the second vector from the
first. Because it is in essence an “additive” operator, it has been
given the same associativity and precedence values (left
and 140) as default additive infix operators such as
+. For a complete list of the
default Swift operator precedence and associativity settings, see
[Expressions](Expressions.xhtml).
