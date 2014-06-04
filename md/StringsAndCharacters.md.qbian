‌‌

Strings and Characters 
----------------------

A *string* is an ordered collection of characters, such as
"hello, world". Swift
strings are represented by the String type, which in turn
represents a collection of values of Character type.

Swift’s String types provide
a fast, Unicode-compliant way to work with text in your code. The syntax
for string creation and manipulation is lightweight and readable, with a
similar syntax to C strings. String concatenation is as simple as adding
together two strings with the + operator, and string
mutability is managed by choosing between a constant or a variable, just
like any other value in Swift.

Despite this simplicity of syntax, Swift’s String type is
a fast, modern string implementation. Every string is composed of
encoding-independent Unicode characters, and provides support for
accessing those characters in various Unicode representations.

Strings can also be used to insert constants, variables, literals, and
expressions into longer strings, in a process known as string
interpolation. This makes it easy to create custom string values for
display, storage, and printing.

Note

Swift’s String type is bridged seamlessly to Foundation’s
NSString class. If you are working with the Foundation
framework in Cocoa or Cocoa Touch, the entire NSString
API is available to call on any String value you create,
in addition to the String features described in this
chapter. You can also use a String value with any API
that requires an NSString instance.

For more information about using String with Foundation
and Cocoa, see *Using Swift with Cocoa and Objective-C*.

‌

### String Literals 

You can include predefined String values within your code
as *string literals*. A string literal is a fixed sequence of textual
characters surrounded by a pair of double quotes ("").

A string literal can be used to provide an initial value for a constant
or variable:

    let =
    "Some string literal value"

Note that Swift infers a type of String for the
someString constant, because it is initialized with a
string literal value.

String literals can include the following special characters:

-   The escaped special characters \0 (null character),
    \\ (horizontal tab),
    \n (carriage return),
    \" (single
    quote)

-   Single-byte Unicode scalars, written as \xnn, where
    nn is two hexadecimal digits

-   Two-byte Unicode scalars, written as \unnnn, where
    nnnn is four hexadecimal digits

-   Four-byte Unicode scalars, written as \Unnnnnnnn,
    where nnnnnnnn is eight hexadecimal digits

The code below shows an example of each kind of special character. The
wiseWords constant contains two escaped double quote
characters. The dollarSign,
and sparklingHeart constants demonstrate the three
different Unicode scalar character formats:

    let =
    "\"Imagination is more important than knowledge\" - Einstein"
    // "Imagination is more important than knowledge" - Einstein
    let
    // $,  Unicode scalar U+0024
    let
    // ♥,  Unicode scalar U+2665
    let
    // 💖, Unicode scalar U+1F496

‌

### Initializing an Empty String 

To create an empty String value as the starting point for
building a longer string, either assign an empty string literal to a
variable, or initialize a new String instance with
initializer syntax:

    var
    // empty string literal
    var()
    // initializer syntax
    // these two strings are both empty, and are equivalent to each other

You can find out whether a String value is empty by
checking its Boolean isEmpty property:

    if {
        println)
    }
    // prints "Nothing to see here"

‌

### String Mutability 

You indicate whether a particular String can be modified
(or *mutated*) by assigning it to a variable (in which case it can be
modified), or to a constant (in which case it cannot be modified):

    var
    variableString
    // variableString is now "Horse and carriage"
     
    let
    constantString
    // this reports a compile-time error - a constant string cannot be modified

Note

This approach is different from string mutation in Objective-C and
Cocoa, where you choose between two classes (NSString and
NSMutableString) to indicate whether a string can be
mutated.

‌

### Strings Are Value Types 

Swift’s String type is a *value type*. If you create a
new String value is
*copied* when it is passed to a function or method, or when it is
assigned to a constant or variable. In each case, a new copy of the
existing String value is created, and the new copy is
passed or assigned, not the original version. Value types are described
in [Structures and Enumerations Are Value
Types](ClassesAndStructures.xhtml#TP40014097-CH13-XID_104).

Note

This behavior differs from that of NSString in Cocoa.
When you create an NSString instance in Cocoa, and pass
it to a function or method or assign it to a variable, you are always
passing or assigning a *reference* to the same single
NSString. No copying of the string takes place, unless
you specifically request it.

Swift’s copy-by-default String behavior ensures that when
a function or method passes you a String value, it is
clear that you own that exact String value, regardless of
where it came from. You can be confident that the string you are passed
will not be modified unless you modify it yourself.

Behind the scenes, Swift’s compiler optimizes string usage so that
actual copying takes place only when absolutely necessary. This means
you always get great performance when working with strings as value
types.

‌

### Working with Characters 

Swift’s String type represents a collection of
Character values in a specified order. Each
Character value represents a single Unicode character.
You can access the individual Character values in a
string by iterating over that string with a
for loop:

    for {
        println)
    }
    // D
    // o
    // g
    // !
    // 🐶

The for loop is described in [For
Loops](ControlFlow.xhtml#TP40014097-CH9-XID_154).

Alternatively, create a stand-alone Character constant or
variable from a single-character string literal by providing a
Character type annotation:

    let

‌

### Counting Characters 

To retrieve a count of the characters in a string, call the global
countElements function and pass in a string as the
function’s sole parameter:

    let =
    "Koala 🐨, Snail 🐌, Penguin 🐧, Dromedary 🐪"
    println)
    // prints "unusualMenagerie has 40 characters"

Note

Different Unicode characters and different representations of the same
Unicode character can require different amounts of memory to store.
Because of this, characters in Swift do not each take up the same amount
of memory within a string’s representation. As a result, the length of a
string cannot be calculated without iterating through the string to
consider each of its characters in turn. If you are working with
particularly long string values, be aware that the
countElements function must iterate over the characters
within a string in order to calculate an accurate character count for
that string.

Note also that the character count returned by
countElements is not always the same as the
length that
contains the same characters. The length of an NSString
is based on the number of 16-bit code units within the string’s UTF-16
representation and not the number of Unicode characters within the
string. To reflect this fact, the length property from
NSString when it is
accessed on a Swift String value.

‌

### Concatenating Strings and Characters 

String values can be added
together (or *concatenated*) with the addition operator
(+ value:

    let
    let
    let
    let
     
    let +
    character1
    let +
    string2
    let +
    string1
    let
    + character2

You can also append a String
value to an existing String variable with the addition
assignment operator (+=):

    var
    instruction
    // instruction now equals "look over there"
     
    var
    welcome
    // welcome now equals "good morning!"

Note

You can’t append a String to
an existing Character variable, because a
Character value must contain a single character only.

‌

### String Interpolation 

*String interpolation* is a way to construct a new String
value from a mix of constants, variables, literals, and expressions by
including their values inside a string literal. Each item that you
insert into the string literal is wrapped in a pair of parentheses,
prefixed by a backslash:

    let
    let =
    ")
    \* 2.5
    // message is "3 times 2.5 is 7.5"

In the example above, the value of multiplier is inserted
into a string literal as \(multiplier). This placeholder
is replaced with the actual value of multiplier when the
string interpolation is evaluated to create an actual string.

The value of multiplier is also part of a larger
expression later in the string. This expression calculates the value of
Double(multiplier) * 2.5 and inserts the result
(7.5) into the string. In this case, the expression is
written as \(Double(multiplier) * 2.5) when it is
included inside the string literal.

Note

The expressions you write inside parentheses within an interpolated
string cannot contain an unescaped double quote (") or
backslash (\), and cannot contain a carriage return or
line feed.

‌

### Comparing Strings 

Swift provides three ways to compare String values:
string equality, prefix equality, and suffix equality.

‌

### String Equality 

Two String values are considered equal if they contain
exactly the same characters in the same order:

    let =
    "We're a lot alike, you and I."
    let =
    "We're a lot alike, you and I."
    if {
        println)
    }
    // prints "These two strings are considered equal"

‌

### Prefix and Suffix Equality 

To check whether a string has a particular string prefix or suffix, call
the string’s hasPrefix
methods, both of which take a single argument of type
String and return a Boolean value. Both methods perform a
character-by-character comparison between the base string and the prefix
or suffix string.

The examples below consider an array of strings representing the scene
locations from the first two acts of Shakespeare’s *Romeo and Juliet*:

    let = [
        "Act 1 Scene 1: Verona, A public place",
        "Act 1 Scene 2: Capulet's mansion",
        "Act 1 Scene 3: A room in Capulet's mansion",
        "Act 1 Scene 4: A street outside Capulet's mansion",
        "Act 1 Scene 5: The Great Hall in Capulet's mansion",
        "Act 2 Scene 1: Outside Capulet's mansion",
        "Act 2 Scene 2: Capulet's orchard",
        "Act 2 Scene 3: Outside Friar Lawrence's cell",
        "Act 2 Scene 4: A street in Verona",
        "Act 2 Scene 5: Capulet's mansion",
        "Act 2 Scene 6: Friar Lawrence's cell"
    ]

You can use the hasPrefix method with the
romeoAndJuliet array to count the number of scenes in Act
1 of the play:

    var
    for {
        if)
    {
            ++act1SceneCount
        }
    }
    println)
    // prints "There are 5 scenes in Act 1"

Similarly, use the hasSuffix method to count the number
of scenes that take place in or around Capulet’s mansion and Friar
Lawrence’s cell:

    var
    var
    for {
        if
    scene) {
            ++mansionCount
        } else
    scene) {
            ++cellCount
        }
    }
    println)
    // prints "6 mansion scenes; 2 cell scenes"

‌

### Uppercase and Lowercase Strings 

You can access an uppercase or lowercase version of a string with its
uppercaseString
properties:

    let =
    "Could you help me, please?"
    let =
    normal
    // shouty is equal to "COULD YOU HELP ME, PLEASE?"
    let =
    normal
    // whispered is equal to "could you help me, please?"

‌

### Unicode 

*Unicode* is an international standard for encoding and representing
text. It enables you to represent almost any character from any language
in a standardized form, and to read and write those characters to and
from an external source such as a text file or web page.

Swift’s String types are
fully Unicode-compliant. They support a number of different Unicode
encodings, as described below.

‌

### Unicode Terminology 

Every character in Unicode can be represented by one or more *unicode
scalars*. A unicode scalar is a unique 21-bit number (and name) for a
character or modifier, such as U+0061 for
LOWERCASE LATIN LETTER A), or
U+1F425
("🐥").

When a Unicode string is written to a text file or some other storage,
these unicode scalars are encoded in one of several Unicode-defined
formats. Each format encodes the string in small chunks known as *code
units*. These include the UTF-8 format (which encodes a string as 8-bit
code units) and the UTF-16 format (which encodes a string as 16-bit code
units).

‌

### Unicode Representations of Strings 

Swift provides several different ways to access Unicode representations
of strings.

You can iterate over the string with a
for statement, to access its individual
Character values as Unicode characters. This process is
described in [Working with
Characters](StringsAndCharacters.xhtml#TP40014097-CH7-XID_376).

Alternatively, access a String value in one of three
other Unicode-compliant representations:

-   A collection of UTF-8 code units (accessed with the string’s
    utf8 property)

-   A collection of UTF-16 code units (accessed with the string’s
    utf16 property)

-   A collection of 21-bit Unicode scalar values (accessed with the
    string’s unicodeScalars property)

Each example below shows a different representation of the following
string, which is made up of the characters D,
o, and the 🐶
character (DOG FACE, or Unicode scalar
U+1F436):

    let

‌

### UTF-8 

You can access a UTF-8 representation of a String by
iterating over its utf8 property. This property is of
type UTF8View, which is a collection of unsigned 8-bit
(UInt8) values, one for each byte in the string’s UTF-8
representation:

    for
    dogString {
        print)
    }
    print)
    // 68 111 103 33 240 159 144 182

In the example above, the first four decimal codeUnit
values (68,
33,
o, whose UTF-8
representation is the same as their ASCII representation. The last four
codeUnit,
144) are a four-byte UTF-8
representation of the DOG FACE character.

‌

### UTF-16 

You can access a UTF-16 representation of a String by
iterating over its utf16 property. This property is of
type UTF16View, which is a collection of unsigned 16-bit
(UInt16) values, one for each 16-bit code unit in the
string’s UTF-16 representation:

    for
    dogString {
        print)
    }
    print)
    // 68 111 103 33 55357 56374

Again, the first four codeUnit,
111) represent the
characters D, and
!, whose UTF-16 code units have the same values as in the
string’s UTF-8 representation.

The fifth and sixth codeUnit
and 56374) are a UTF-16 surrogate pair representation of
the DOG FACE character. These values are a lead surrogate
value of U+D83D) and
a trail surrogate value of U+DC36 (decimal value
56374).

‌

### Unicode Scalars 

You can access a Unicode scalar representation of a
String value by iterating over its
unicodeScalars property. This property is of type
UnicodeScalarView, which is a collection of values of
type UnicodeScalar. A Unicode scalar is any 21-bit
Unicode code point that is not a lead surrogate or trail surrogate code
point.

Each UnicodeScalar property
that returns the scalar’s 21-bit value, represented within a
UInt32 value:

    for
    dogString {
        print)
    }
    print)
    // 68 111 103 33 128054

The value properties for the first four
UnicodeScalar,
111) once again
represent the characters D,
g
property of the fifth and final UnicodeScalar,
128054, is a decimal equivalent of the hexadecimal value
1F436, which is equivalent to the Unicode scalar
U+1F436 character.

As an alternative to querying their value properties,
each UnicodeScalar value can also be used to construct a
new String value, such as with string interpolation:

    for
    dogString {
        println)
    }
    // D
    // o
    // g
    // !
    // 🐶
