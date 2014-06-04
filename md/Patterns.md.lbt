‌‌

Patterns 
--------

A *pattern* represents the structure of a single value or a composite
value. For example, the structure of a tuple (1, 2) is a
comma-separated list of two elements. Because patterns represent the
structure of a value rather than any one particular value, you can match
them with a variety of values. For instance, the pattern
(x, y) and any
other two-element tuple. In addition matching a pattern with a value,
you can extract part or all of a composite value and bind each part to a
constant or variable name.

In Swift, patterns occur in variable and constant declarations (on their
left-hand side), in for statements, and
in switch statements (in their case labels). Although any
pattern can occur in the case labels of a switch
statement, in the other contexts, only wildcard patterns, identifier
patterns, and patterns containing those two patterns can occur.

You can specify a type annotation for a wildcard pattern, an identifier
pattern, and a tuple pattern to constraint the pattern to match only
values of a certain type.

Grammar of a pattern

‌ pattern →
[wildcard-pattern](Patterns.xhtml#wildcard-pattern)[type-annotation](Types.xhtml#type-annotation)~opt~

‌ pattern →
[identifier-pattern](Patterns.xhtml#identifier-pattern)[type-annotation](Types.xhtml#type-annotation)~opt~

‌ pattern →
[value-binding-pattern](Patterns.xhtml#value-binding-pattern)

‌ pattern →
[tuple-pattern](Patterns.xhtml#tuple-pattern)[type-annotation](Types.xhtml#type-annotation)~opt~

‌ pattern → [enum-case-pattern](Patterns.xhtml#enum-case-pattern)

‌ pattern → [type-casting-pattern](Patterns.xhtml#type-casting-pattern)

‌ pattern → [expression-pattern](Patterns.xhtml#expression-pattern)

‌

### Wildcard Pattern 

A *wildcard pattern* matches and ignores any value and consists of an
underscore (_). Use a wildcard pattern when you don’t
care about the values being matched against. For example, the following
code iterates through the closed range 1..3, ignoring the
current value of the range on each iteration of the loop:

    for {
        // Do something three times.
    }

Grammar of a wildcard pattern

‌ wildcard-pattern → _

‌

### Identifier Pattern 

An *identifier pattern* matches any value and binds the matched value to
a variable or constant name. For example, in the following constant
declaration, someValue is an identifier pattern that
matches the value 42:

    let

When the match succeeds, the value 42 is bound (assigned)
to the constant name someValue.

When the pattern on the left-hand side of a variable or constant
declaration is an identifier pattern, the identifier pattern is
implicitly a subpattern of a value-binding pattern.

Grammar of an identifier pattern

‌ identifier-pattern → [identifier](LexicalStructure.xhtml#identifier)

‌

### Value-Binding Pattern 

A *value-binding pattern* binds matched values to variable or constant
names. Value-binding patterns that bind a matched value to the name of a
constant begin with the keyword let; those that bind to
the name of variable begin with the keyword var.

Identifiers patterns within a value-binding pattern bind new named
variables or constants to their matching values. For example, you can
decompose the elements of a tuple and bind the value of each element to
a corresponding identifier pattern.

    let)
    switch {
        // Bind x and y to the elements of point.
    case):
        println)
    }
    // prints "The point is at (3, 2)."

In the example above, let distributes to each identifier
pattern in the tuple pattern (x, y). Because of this
behavior, the switch cases
case let (x, y):
match the same values.

Grammar of a value-binding pattern

‌ value-binding-pattern →
var[pattern](Patterns.xhtml#pattern)
let[pattern](Patterns.xhtml#pattern)

‌

### Tuple Pattern 

A *tuple pattern* is a comma-separated list of zero or more patterns,
enclosed in parentheses. Tuple patterns match values of corresponding
tuple types.

You can constrain a tuple pattern to match certain kinds of tuple types
by using type annotations. For example, the tuple pattern
(x, y): (Int, Int) in the constant declaration
let (x, y): (Int, Int) = (1, 2) matches only tuple types
in which both elements are of type Int. To constrain only
some elements of a tuple pattern, provide type annotations directly to
those individual elements. For example, the tuple pattern in
let (x: String, y) matches any two-element tuple type, as
long as the first element is of type String.

When a tuple pattern is used as the pattern in a
for statement or in a variable or
constant declaration, it can contain only wildcard patterns, identifier
patterns, or other tuple patterns that contain those. For example, the
following code isn’t valid because the element 0 in the
tuple pattern (x, 0) is an expression pattern:

    let,
    0,
    1)]
    // This code isn't valid.
    for {
        /* ... */
    }

The parentheses around a tuple pattern that contains a single element
have no effect. The pattern matches values of that single element’s
type. For example, the following are equivalent:

    let
    let
    let
    // a: Int = 2

Grammar of a tuple pattern

‌ tuple-pattern →
(

‌ tuple-pattern-element-list →
[tuple-pattern-element](Patterns.xhtml#tuple-pattern-element)
[tuple-pattern-element](Patterns.xhtml#tuple-pattern-element),[tuple-pattern-element-list](Patterns.xhtml#tuple-pattern-element-list)

‌ tuple-pattern-element → [pattern](Patterns.xhtml#pattern)

‌

### Enumeration Case Pattern 

An *enumeration case pattern* matches a case of an existing enumeration
type. Enumeration case patterns appear only in switch
statement case labels.

If the enumeration case you’re trying to match has any associated
values, the corresponding enumeration case pattern must specify a tuple
pattern that contains one element for each associated value. For an
example that uses a switch statement to match enumeration
cases containing associated values, see [Associated
Values](Enumerations.xhtml#TP40014097-CH12-XID_189).

Grammar of an enumeration case pattern

‌ enum-case-pattern →
[type-identifier](Types.xhtml#type-identifier)~opt~.[enum-case-name](Declarations.xhtml#enum-case-name)[tuple-pattern](Patterns.xhtml#tuple-pattern)~opt~

‌

### Type-Casting Patterns 

There are two type-casting patterns, the is pattern and
the as pattern. Both type-casting patterns appear only in
switch and
as patterns have the following form:

-   ~~~~ 
    is type
    ~~~~

-   ~~~~ 
    pattern as type
    ~~~~

The is pattern matches a value if the type of that value
at runtime is the same as the type specified in the right-hand side of
the is pattern—or a subclass of that type. The
is operator in
that they both perform a type cast but discard the returned type.

The as pattern matches a value if the type of that value
at runtime is the same as the type specified in the right-hand side of
the as pattern—or a subclass of that type. If the match
succeeds, the type of the matched value is cast to the *pattern*
specified in the left-hand side of the as pattern.

For an example that uses a switch statement to match
values with is patterns, see [Type
Casting for Any and
AnyObject](TypeCasting.xhtml#TP40014097-CH22-XID_448).

Grammar of a type casting pattern

‌ type-casting-pattern → [is-pattern](Patterns.xhtml#is-pattern)
[as-pattern](Patterns.xhtml#as-pattern)

‌ is-pattern → is[type](Types.xhtml#type)

‌ as-pattern →
[pattern](Patterns.xhtml#pattern)as[type](Types.xhtml#type)

‌

### Expression Pattern 

An *expression pattern* represents the value of an expression.
Expression patterns appear only in switch statement case
labels.

The expression represented by the expression pattern is compared with
the value of an input expression using the Swift standard library
~= operator. The matches succeeds if the
~=. By default, the
~= operator compares two values of the same type using
the == operator. It can also match an integer value with
a range of integers in an Range object, as the following
example shows:

    let)
    switch {
    case):
        println)
    case):
        println)
    default:
        println)
    }
    // prints "(1, 2) is near the origin."

You can overload the ~= operator to provide custom
expression matching behavior. For example, you can rewrite the above
example to compare the point expression with a string
representations of points.

    // Overload the ~= operator to match a string with an integer
    func:
    Int {
        return ==
    "
    }
    switch {
    case):
        println)
    case):
        println)
    default:
        println)
    }
    // prints "(1, 2) is near the origin."

Grammar of an expression pattern

‌ expression-pattern → [expression](Expressions.xhtml#expression)
