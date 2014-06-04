‌‌

Lexical Structure 
-----------------

The *lexical structure* of Swift describes what sequence of characters
form valid tokens of the language. These valid tokens form the
lowest-level building blocks of the language and are used to describe
the rest of the language in subsequent chapters.

In most cases, tokens are generated from the characters of a Swift
source file by considering the longest possible substring from the input
text, within the constraints of the grammar that are specified below.
This behavior is referred to as *longest match* or *maximal munch*.

‌

### Whitespace and Comments 

Whitespace has two uses: to separate tokens in the source file and to
help determine whether an operator is a prefix or postfix (see
[Operators](LexicalStructure.xhtml#TP40014097-CH30-XID_871)), but is
otherwise ignored. The following characters are considered whitespace:
space (U+0020), line feed (U+000A), carriage return (U+000D), horizontal
tab (U+0009), vertical tab (U+000B), form feed (U+000C) and null
(U+0000).

Comments are treated as whitespace by the compiler. Single line comments
begin with *//* and continue until the end of the line. Multiline
comments begin with /*.
Nesting is allowed, but the comment markers must be balanced.

‌

### Identifiers 

*Identifiers* begin with an upper case or lower case letter A through Z,
an underscore (_), a noncombining alphanumeric Unicode
character in the Basic Multilingual Plane, or a character outside the
Basic Multilingual Plan that isn’t in a Private Use Area. After the
first character, digits and combining Unicode characters are also
allowed.

To use a reserved word as an identifier, put a backtick
(  ) before and after it. For example,
class is not a valid identifier, but
 class  is valid. The backticks are not considered
part of the identifier;  x  have
the same meaning.

Inside a closure with no explicit parameter names, the parameters are
implicitly named $0,
$2, and so on. These names are valid identifiers within
the scope of the closure.

Grammar of an identifier

‌ identifier →
[identifier-head](LexicalStructure.xhtml#identifier-head)[identifier-characters](LexicalStructure.xhtml#identifier-characters)~opt~

‌ identifier →
  

‌ identifier →
[implicit-parameter-name](LexicalStructure.xhtml#implicit-parameter-name)

‌ identifier-list → [identifier](LexicalStructure.xhtml#identifier)
[identifier](LexicalStructure.xhtml#identifier),[identifier-list](LexicalStructure.xhtml#identifier-list)

‌ identifier-head → Upper- or lowercase letter A through Z

‌ identifier-head → U+00A8, U+00AA, U+00AD, U+00AF, U+00B2–U+00B5, or
U+00B7–U+00BA

‌ identifier-head → U+00BC–U+00BE, U+00C0–U+00D6, U+00D8–U+00F6, or
U+00F8–U+00FF

‌ identifier-head → U+0100–U+02FF, U+0370–U+167F, U+1681–U+180D, or
U+180F–U+1DBF

‌ identifier-head → U+1E00–U+1FFF

‌ identifier-head → U+200B–U+200D, U+202A–U+202E, U+203F–U+2040, U+2054,
or U+2060–U+206F

‌ identifier-head → U+2070–U+20CF, U+2100–U+218F, U+2460–U+24FF, or
U+2776–U+2793

‌ identifier-head → U+2C00–U+2DFF or U+2E80–U+2FFF

‌ identifier-head → U+3004–U+3007, U+3021–U+302F, U+3031–U+303F, or
U+3040–U+D7FF

‌ identifier-head → U+F900–U+FD3D, U+FD40–U+FDCF, U+FDF0–U+FE1F, or
U+FE30–U+FE44

‌ identifier-head → U+FE47–U+FFFD

‌ identifier-head → U+10000–U+1FFFD, U+20000–U+2FFFD, U+30000–U+3FFFD,
or U+40000–U+4FFFD

‌ identifier-head → U+50000–U+5FFFD, U+60000–U+6FFFD, U+70000–U+7FFFD,
or U+80000–U+8FFFD

‌ identifier-head → U+90000–U+9FFFD, U+A0000–U+AFFFD, U+B0000–U+BFFFD,
or U+C0000–U+CFFFD

‌ identifier-head → U+D0000–U+DFFFD or U+E0000–U+EFFFD

‌ identifier-character → Digit 0 through 9

‌ identifier-character → U+0300–U+036F, U+1DC0–U+1DFF, U+20D0–U+20FF, or
U+FE20–U+FE2F

‌ identifier-character →
[identifier-head](LexicalStructure.xhtml#identifier-head)

‌ identifier-characters →
[identifier-character](LexicalStructure.xhtml#identifier-character)[identifier-characters](LexicalStructure.xhtml#identifier-characters)~opt~

‌ implicit-parameter-name →
$[decimal-digits](LexicalStructure.xhtml#decimal-digits)

‌

### Keywords 

The following keywords are reserved and may not be used as identifiers,
unless they’re escaped with backticks, as described above in
[Identifiers](LexicalStructure.xhtml#TP40014097-CH30-XID_796).

-   Keywords used in declarations: class,
    deinit,
    extension,
    import,
    protocol,
    struct,
    typealias.

-   Keywords used in statements: break,
    case,
    default,
    fallthrough,
    for,
    where.

-   Keywords used in expressions and types: as,
    dynamicType,
    super,
    Type,
    __FILE__, and
    __LINE__.

-   Keywords reserved in particular contexts:
    associativity,
    get,
    left,
    nonmutating,
    override,
    precedence,
    right,
    unowned(safe),
    weak. Outside the context
    in which they appear in the grammar, they can be used as
    identifiers.

‌

### Literals 

A *literal* is the source code representation of a value of an integer,
floating-point number, or string type. The following are examples of
literals:

    42
    3.14159
    "Hello, world!"

Grammar of a literal

‌ literal → [integer-literal](LexicalStructure.xhtml#integer-literal)
[floating-point-literal](LexicalStructure.xhtml#floating-point-literal)
[string-literal](LexicalStructure.xhtml#string-literal)

‌

### Integer Literals 

*Integer literals* represent integer values of unspecified precision. By
default, integer literals are expressed in decimal; you can specify an
alternate base using a prefix. Binary literals begin with
0b, and
hexadecimal literals begin with 0x.

Decimal literals contain the digits 0 through
9 and
1 through
7
through 9 through
F in upper- or lowercase.

Negative integers literals are expressed by prepending a minus sign
(-.

Underscores (_) are allowed between digits for
readability, but are ignored and therefore don’t affect the value of the
literal. Integer literals can begin with leading zeros
(0), but are likewise ignored and don’t affect the base
or value of the literal.

Unless otherwise specified, the default type of an integer literal is
the Swift standard library type Int. The Swift standard
library also defines types for various sizes of signed and unsigned
integers, as described in
[Integers](TheBasics.xhtml#TP40014097-CH5-XID_411).

Grammar of an integer literal

‌ integer-literal →
[binary-literal](LexicalStructure.xhtml#binary-literal)

‌ integer-literal →
[octal-literal](LexicalStructure.xhtml#octal-literal)

‌ integer-literal →
[decimal-literal](LexicalStructure.xhtml#decimal-literal)

‌ integer-literal →
[hexadecimal-literal](LexicalStructure.xhtml#hexadecimal-literal)

‌ binary-literal →
0b[binary-digit](LexicalStructure.xhtml#binary-digit)[binary-literal-characters](LexicalStructure.xhtml#binary-literal-characters)~opt~

‌ binary-digit → Digit 0 or 1

‌ binary-literal-character →
[binary-digit](LexicalStructure.xhtml#binary-digit) _

‌ binary-literal-characters →
[binary-literal-character](LexicalStructure.xhtml#binary-literal-character)[binary-literal-characters](LexicalStructure.xhtml#binary-literal-characters)~opt~

‌ octal-literal →
0o[octal-digit](LexicalStructure.xhtml#octal-digit)[octal-literal-characters](LexicalStructure.xhtml#octal-literal-characters)~opt~

‌ octal-digit → Digit 0 through 7

‌ octal-literal-character →
[octal-digit](LexicalStructure.xhtml#octal-digit) _

‌ octal-literal-characters →
[octal-literal-character](LexicalStructure.xhtml#octal-literal-character)[octal-literal-characters](LexicalStructure.xhtml#octal-literal-characters)~opt~

‌ decimal-literal →
[decimal-digit](LexicalStructure.xhtml#decimal-digit)[decimal-literal-characters](LexicalStructure.xhtml#decimal-literal-characters)~opt~

‌ decimal-digit → Digit 0 through 9

‌ decimal-digits →
[decimal-digit](LexicalStructure.xhtml#decimal-digit)[decimal-digits](LexicalStructure.xhtml#decimal-digits)~opt~

‌ decimal-literal-character →
[decimal-digit](LexicalStructure.xhtml#decimal-digit) _

‌ decimal-literal-characters →
[decimal-literal-character](LexicalStructure.xhtml#decimal-literal-character)[decimal-literal-characters](LexicalStructure.xhtml#decimal-literal-characters)~opt~

‌ hexadecimal-literal →
0x[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-literal-characters](LexicalStructure.xhtml#hexadecimal-literal-characters)~opt~

‌ hexadecimal-digit → Digit 0 through 9, a through f, or A through F

‌ hexadecimal-literal-character →
[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)
_

‌ hexadecimal-literal-characters →
[hexadecimal-literal-character](LexicalStructure.xhtml#hexadecimal-literal-character)[hexadecimal-literal-characters](LexicalStructure.xhtml#hexadecimal-literal-characters)~opt~

‌

### Floating-Point Literals 

*Floating-point literals* represent floating-point values of unspecified
precision.

By default, floating-point literals are expressed in decimal (with no
prefix), but they can also be expressed in hexadecimal (with a
0x prefix).

Decimal floating-point literals consist of a sequence of decimal digits
followed by either a decimal fraction, a decimal exponent, or both. The
decimal fraction consists of a decimal point (.) followed
by a sequence of decimal digits. The exponent consists of an upper- or
lowercase e prefix followed by sequence of decimal digits
that indicates what power of 10 the value preceding the e
is multiplied by. For example, 1.25e2 represents 1.25 ⨉
10^2^, which evaluates to 125.0. Similarly,
1.25e-2 represents 1.25 ⨉ 10^-2^, which evaluates to
0.0125.

Hexadecimal floating-point literals consist of a 0x
prefix, followed by an optional hexadecimal fraction, followed by a
hexadecimal exponent. The hexadecimal fraction consists of a decimal
point followed by a sequence of hexadecimal digits. The exponent
consists of an upper- or lowercase p prefix followed by
sequence of decimal digits that indicates what power of 2 the value
preceding the p is multiplied by. For example,
0xFp2 represents 15 ⨉ 2^2^, which evaluates to
60 represents 15 ⨉
2^-2^, which evaluates to 3.75.

Unlike with integer literals, negative floating-point numbers are
expressed by applying the unary minus operator (-) to a
floating-point literal, as in -42.0. The result is an
expression, not a floating-point integer literal.

Underscores (_) are allowed between digits for
readability, but are ignored and therefore don’t affect the value of the
literal. Floating-point literals can begin with leading zeros
(0), but are likewise ignored and don’t affect the base
or value of the literal.

Unless otherwise specified, the default type of a floating-point literal
is the Swift standard library type Double, which
represents a 64-bit floating-point number. The Swift standard library
also defines a Float type, which represents a 32-bit
floating-point number.

Grammar of a floating-point literal

‌ floating-point-literal →
[decimal-literal](LexicalStructure.xhtml#decimal-literal)[decimal-fraction](LexicalStructure.xhtml#decimal-fraction)~opt~[decimal-exponent](LexicalStructure.xhtml#decimal-exponent)~opt~

‌ floating-point-literal →
[hexadecimal-literal](LexicalStructure.xhtml#hexadecimal-literal)[hexadecimal-fraction](LexicalStructure.xhtml#hexadecimal-fraction)~opt~[hexadecimal-exponent](LexicalStructure.xhtml#hexadecimal-exponent)

‌ decimal-fraction →
.[decimal-literal](LexicalStructure.xhtml#decimal-literal)

‌ decimal-exponent →
[floating-point-e](LexicalStructure.xhtml#floating-point-e)[sign](LexicalStructure.xhtml#sign)~opt~[decimal-literal](LexicalStructure.xhtml#decimal-literal)

‌ hexadecimal-fraction →
.[hexadecimal-literal](LexicalStructure.xhtml#hexadecimal-literal)~opt~

‌ hexadecimal-exponent →
[floating-point-p](LexicalStructure.xhtml#floating-point-p)[sign](LexicalStructure.xhtml#sign)~opt~[hexadecimal-literal](LexicalStructure.xhtml#hexadecimal-literal)

‌ floating-point-e → e

‌ floating-point-p → p

‌ sign → +

‌

### String Literals 

A string literal is a sequence of characters surrounded by double
quotes, with the following form:

-   ~~~~ 
    "characters"
    ~~~~

String literals cannot contain an unescaped double quote
("), a
carriage return, or a line feed.

Special characters can be included in string literals using the
following escape sequences:

-   Null Character (\0)

-   Backslash (\\)

-   Horizontal Tab (\t)

-   Line Feed (\n)

-   Carriage Return (\r)

-   Double Quote (\")

-   Single Quote (\')

Characters can also be expressed by \x followed by two
hexadecimal digits, \u followed by four hexadecimal
digits, or \U followed by eight hexadecimal digits. The
digits in these escape sequences identify a Unicode codepoint.

The value of an expression can be inserted into a string literal by
placing the expression in parentheses after a backslash
(\). The interpolated expression must not contain an
unescaped double quote ("), an unescaped backslash
(\), a carriage return, or a line feed. The expression
must evaluate to a value of a type that the String class
has an initializer for.

For example, all the following string literals have the same value:

    "1 2 3"
    "1 2 
    "1 2 
    var;
    "1 2 

The default type of a string literal is String. The
characters that make up a string are of type Character.
For more information about the String and
Character types, see [Strings and
Characters](StringsAndCharacters.xhtml).

Grammar of a string literal

‌ string-literal →
"

‌ quoted-text →
[quoted-text-item](LexicalStructure.xhtml#quoted-text-item)[quoted-text](LexicalStructure.xhtml#quoted-text)~opt~

‌ quoted-text-item →
[escaped-character](LexicalStructure.xhtml#escaped-character)

‌ quoted-text-item →
\(

‌ quoted-text-item → Any Unicode extended grapheme cluster except
", U+000A, or U+000D

‌ escaped-character → \0
\n

‌ escaped-character →
\x[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)

‌ escaped-character →
\u[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)

‌ escaped-character →
\U[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)

‌

### Operators 

The Swift standard library defines a number of operators for your use,
many of which are discussed in [Basic Operators](BasicOperators.xhtml)
and [Advanced Operators](AdvancedOperators.xhtml). The present section
describes which characters can be used as operators.

Operators are made up of one or more of the following characters:
/,
!,
>,
~. That said, the tokens
=,
/*, and the unary
prefix operator & are reserved. These tokens can’t be
overloaded, nor can they be used to define custom operators.

The whitespace around an operator is used to determine whether an
operator is used as a prefix operator, a postfix operator, or a binary
operator. This behavior is summarized in the following rules:

-   If an operator has whitespace around both sides or around neither
    side, it is treated as a binary operator. As an example, the
    + and
    a + b is treated as a binary operator.

-   If an operator has whitespace on the left side only, it is treated
    as a prefix unary operator. As an example, the ++
    operator in a ++b is treated as a prefix unary
    operator.

-   If an operator has whitespace on the right side only, it is treated
    as a postfix unary operator. As an example, the ++
    operator in a++ b is treated as a postfix unary
    operator.

-   If an operator has no whitespace on the left but is followed
    immediately by a dot (.), it is treated as a postfix
    unary operator. As an example, the ++ operator in
    a++.b is treated as a postfix unary operator
    (a++ . b).

For the purposes of these rules, the characters (,
[ before an operator, the
characters )
after an operator, and the characters ,,
; are also considered whitespace.

There is one caveat to the rules above. If the ! or
? operator has no whitespace on the left, it is treated
as a postfix operator, regardless of whether it has whitespace on the
right. To use the ? operator as syntactic sugar for the
Optional type, it must not have whitespace on the left.
To use it in the conditional (? :) operator, it must have
whitespace around both sides.

In certain constructs, operators with a leading < or
> may be split into two or more tokens. The remainder is
treated the same way and may be split again. As a result, there is no
need to use whitespace to disambiguate between the closing
> characters in constructs like
Dictionary<String, Array<Int>>. In this example, the
closing > characters are not treated as a single token
that may then be misinterpreted as a bit shift >>
operator.

To learn how to define new, custom operators, see [Custom
Operators](AdvancedOperators.xhtml#TP40014097-CH27-XID_48) and [Operator
Declaration](Declarations.xhtml#TP40014097-CH34-XID_644). To learn how
to overload existing operators, see [Operator
Functions](AdvancedOperators.xhtml#TP40014097-CH27-XID_43).

Grammar of operators

‌ operator →
[operator-character](LexicalStructure.xhtml#operator-character)[operator](LexicalStructure.xhtml#operator)~opt~

‌ operator-character → /
+
>
.

‌ binary-operator → [operator](LexicalStructure.xhtml#operator)

‌ prefix-operator → [operator](LexicalStructure.xhtml#operator)

‌ postfix-operator → [operator](LexicalStructure.xhtml#operator)
