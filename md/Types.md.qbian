‌‌

Types 
-----

In Swift, there are two kinds of types: named types and compound types.
A *named type* is a type that can be given a particular name when it is
defined. Named types include classes, structures, enumerations, and
protocols. For example, instances of a user-defined class named
MyClass. In addition
to user-defined named types, the Swift standard library defines many
commonly used named types, including those that represent arrays,
dictionaries, and optional values.

Data types that are normally considered basic or primitive in other
languages—such as types that represent numbers, characters, and
strings—are actually named types, defined and implemented in the Swift
standard library using structures. Because they are named types, you can
extend their behavior to suit the needs of your program, using an
extension declaration, discussed in [Extensions](Extensions.xhtml) and
[Extension Declaration](Declarations.xhtml#TP40014097-CH34-XID_633).

A *compound type* is a type without a name, defined in the Swift
language itself. There are two compound types: function types and tuple
types. A compound type may contain named types and other compound types.
For instance, the tuple type (Int, (Int, Int)) contains
two elements: The first is the named type Int, and the
second is another compound type (Int, Int).

This chapter discusses the types defined in the Swift language itself
and describes the type inference behavior of Swift.

Grammar of a type

‌ type → [array-type](Types.xhtml#array-type)
[function-type](Types.xhtml#function-type)
[type-identifier](Types.xhtml#type-identifier)
[tuple-type](Types.xhtml#tuple-type)
[optional-type](Types.xhtml#optional-type)
[implicitly-unwrapped-optional-type](Types.xhtml#implicitly-unwrapped-optional-type)
[protocol-composition-type](Types.xhtml#protocol-composition-type)
[metatype-type](Types.xhtml#metatype-type)

‌

### Type Annotation 

A *type annotation* explicitly specifies the type of a variable or
expression. Type annotations begin with a colon (:) and
end with a type, as the following examples show:

    let) =
    (3.14159)
    func) {
    /* ... */

In the first example, the expression someTuple is
specified to have the tuple type (Double, Double). In the
second example, the parameter a to the function
someFunction is specified to have the type
Int.

Type annotations can contain an optional list of type attributes before
the type.

Grammar of a type annotation

‌ type-annotation →
:[attributes](Attributes.xhtml#attributes)~opt~[type](Types.xhtml#type)

‌

### Type Identifier 

A type identifier refers to either a named type or a type alias of a
named or compound type.

Most of the time, a type identifier directly refers to a named type with
the same name as the identifier. For example, Int is a
type identifier that directly refers to the named type
Int, and the type identifier
Dictionary<String, Int> directly refers to the named type
Dictionary<String, Int>.

There are two cases in which a type identifier does not refer to a type
with the same name. In the first case, a type identifier refers to a
type alias of a named or compound type. For instance, in the example
below, the use of Point in the type annotation refers to
the tuple type (Int, Int).

    typealias)
    let)

In the second case, a type identifier uses dot (.) syntax
to refer to named types declared in other modules or nested within other
types. For example, the type identifier in the following code references
the named type MyType that is declared in the
ExampleModule module.

    var:
    ExampleModule

Grammar of a type identifier

‌ type-identifier →
[type-name](Types.xhtml#type-name)[generic-argument-clause](GenericParametersAndArguments.xhtml#generic-argument-clause)~opt~
[type-name](Types.xhtml#type-name)[generic-argument-clause](GenericParametersAndArguments.xhtml#generic-argument-clause)~opt~.[type-identifier](Types.xhtml#type-identifier)

‌ type-name → [identifier](LexicalStructure.xhtml#identifier)

‌

### Tuple Type 

A tuple type is a comma-separated list of zero or more types, enclosed
in parentheses.

You can use a tuple type as the return type of a function to enable the
function to return a single tuple containing multiple values. You can
also name the elements of a tuple type and use those names to refer to
the values of the individual elements. An element name consists of an
identifier followed immediately by a colon (:). For an example that
demonstrates both of these features, see [Functions with Multiple Return
Values](Functions.xhtml#TP40014097-CH10-XID_212).

Void is a typealias for the the empty tuple type,
(). If there is only one element inside the parentheses,
the type is simply the type of that element. For example, the type of
(Int). As
a result, you can label a tuple element only when the tuple type has two
or more elements.

Grammar of a tuple type

‌ tuple-type →
(

‌ tuple-type-body →
[tuple-type-element-list](Types.xhtml#tuple-type-element-list)...~opt~

‌ tuple-type-element-list →
[tuple-type-element](Types.xhtml#tuple-type-element)
[tuple-type-element](Types.xhtml#tuple-type-element),[tuple-type-element-list](Types.xhtml#tuple-type-element-list)

‌ tuple-type-element →
[attributes](Attributes.xhtml#attributes)~opt~inout~opt~[type](Types.xhtml#type)
inout~opt~[element-name](Types.xhtml#element-name)[type-annotation](Types.xhtml#type-annotation)

‌ element-name → [identifier](LexicalStructure.xhtml#identifier)

‌

### Function Type 

A function type represents the type of a function, method, or closure
and consists of a parameter and return type separated by an arrow
(->):

-   ~~~~ 
    parameter type -> return type
    ~~~~

Because the *parameter type* and the *return type* can be a tuple type,
function types support functions and methods that take multiple
paramaters and return multiple values.

You can apply the auto_closure attribute to a function
type that has a parameter type of () and that returns the
type of an expression (see [Type
Attributes](Attributes.xhtml#TP40014097-CH35-XID_463)). An autoclosure
function captures an implicit closure over the specified expression,
instead of the expression itself. The following example uses the
auto_closure attribute in defining a very simple assert
function:

    func:
    @auto_closure:
    String) {
        if() {
            println)
        }
    }
    let
    simpleAssert,
    "testNumber isn't an even number.")
    // prints "testNumber isn't an even number."

A function type can have a variadic parameter as the last parameter in
its *parameter type*. Syntactically, a variadic parameter consists of a
base type name followed immediately by three dots (...),
as in Int.... A variadic parameter is treated as an array
that contains elements of the base type name. For instance, the variadic
parameter Int.... For
an example that uses a variadic parameter, see [Variadic
Parameters](Functions.xhtml#TP40014097-CH10-XID_222).

To specify an in-out parameter, prefix the parameter type with the
inout keyword. You can’t mark a variadic parameter or a
return type with the inout keyword. In-out parameters are
discussed in [In-Out
Parameters](Functions.xhtml#TP40014097-CH10-XID_226).

The type of a curried function is equivalent to a nested function type.
For example, the type of the curried function
addTwoNumbers()() below is
Int -> Int -> Int:

    func:
    Int {
        return
    }
    addTwoNumbers

The function types of a curried function are grouped from right to left.
For instance, the function type Int -> Int -> Int is
understood as Int -> (Int -> Int)—that is, a function
that takes an Int and returns another function that takes
and return an Int. For example, you can rewrite the
curried function addTwoNumbers()() as the following
nested function:

    func) -\>
    (Int) {
        func:
    Int {
            return
        }
        return
    }
    addTwoNumbers

Grammar of a function type

‌ function-type →
[type](Types.xhtml#type)->[type](Types.xhtml#type)

‌

### Array Type 

The Swift language uses square brackets ([]) immediately
after the name of a type as syntactic sugar for the named type
Array<T>, which is defined in the Swift standard library.
In other words, the following two declarations are equivalent:

    let,
    "Brian"]
    let\> =
    ["Alex"]

In both cases, the constant someArray is declared as an
array of strings. The elements of an array can be accessed using square
brackets as well: someArray[0] refers to the element at
index 0, "Alex".

As the above example also shows, you can use square brackets to create
an array using an array literal. Empty array literals are written using
an empty pair of square brackets and can be used to create an empty
array of a specified type.

    var[] = []

You can create multidimensional arrays by chaining multiple sets of
square brackets to the name of the base type of the elements. For
example, you can create a three-dimensional array of integers using
three sets of square brackets:

    var,
    2,
    8]]]

When accessing the elements in a multidimensional array, the left-most
subscript index refers to the element at that index in the outermost
array. The next subscript index to the right refers to the element at
that index in the array that’s nested one level in. And so on. This
means that in the example above, array3D[0] refers to
[[1, 2], [3, 4]] refers to
[3, 4] refers to the
value 4.

For a detailed discussion of the Swift standard library
Array type, see
[Arrays](CollectionTypes.xhtml#TP40014097-CH8-XID_135).

Grammar of an array type

‌ array-type → [type](Types.xhtml#type)[
[array-type](Types.xhtml#array-type)[

‌

### Optional Type 

The Swift language defines the postfix ? as syntactic
sugar for the named type Optional<T>, which is defined in
the Swift standard library. In other words, the following two
declarations are equivalent:

    var?
    var:
    Optional\>

In both cases, the variable optionalInteger is declared
to have the type of an optional integer. Note that no whitespace may
appear between the type and the ?.

The type Optional<T> is an enumeration with two cases,
None, which are used to
represent values that may or may not be present. Any type can be
explicitly declared to be (or implicitly converted to) an optional type.
When declaring an optional type, be sure to use parentheses to properly
scope the ? operator. As an example, to declare an
optional array of integers, write the type annotation as
(Int[])? produces an
error.

If you don’t provide an initial value when you declare an optional
variable or property, its value automatically defaults to
nil.

Optionals conform to the LogicValue protocol and
therefore may occur in a Boolean context. In that context, if an
instance of an optional type T? contains any value of
type T (that is, it’s value is
Optional.Some(T)), the optional type evaluates to
true.

If an instance of an optional type contains a value, you can access that
value using the postfix operator !, as shown below:

    optionalInteger
    optionalInteger

Using the ! operator to unwrap an optional that has a
value of nil results in a runtime error.

You can also use optional chaining and optional binding to conditionally
perform an operation on an optional expression. If the value is
nil, no operation is performed and therefore no runtime
error is produced.

For more information and to see examples that show how to use optional
types, see [Optionals](TheBasics.xhtml#TP40014097-CH5-XID_428).

Grammar of an optional type

‌ optional-type → [type](Types.xhtml#type)?

‌

### Implicitly Unwrapped Optional Type 

The Swift language defines the postfix ! as syntactic
sugar for the named type ImplicitlyUnwrappedOptional<T>,
which is defined in the Swift standard library. In other words, the
following two declarations are equivalent:

    var!
    var:
    ImplicitlyUnwrappedOptional\>

In both cases, the variable implicitlyUnwrappedString is
declared to have the type of an implicitly unwrapped optional string.
Note that no whitespace may appear between the type and the
!.

You can use implicitly unwrapped optionals in all the same places in
your code that you can use optionals. For instance, you can assign
values of implicitly unwrapped optionals to variables, constants, and
properties of optionals, and vice versa.

As with optionals, if you don’t provide an initial value when you
declare an implicitly unwrapped optional variable or property, it’s
value automatically defaults to nil.

Because the value of an implicitly unwrapped optional is automatically
unwrapped when you use it, there’s no need to use the !
operator to unwrap it. That said, if you try to use an implicitly
unwrapped optional that has a value of nil, you’ll get a
runtime error.

Use optional chaining to conditionally perform an operation on an
implicitly unwrapped optional expression. If the value is
nil, no operation is performed and therefore no runtime
error is produced.

For more information about implicitly unwrapped optional types, see
[Implicitly Unwrapped
Optionals](TheBasics.xhtml#TP40014097-CH5-XID_436).

Grammar of an implicitly unwrapped optional type

‌ implicitly-unwrapped-optional-type →
[type](Types.xhtml#type)!

‌

### Protocol Composition Type 

A protocol composition type describes a type that conforms to each
protocol in a list of specified protocols. Protocol composition types
may be used in type annotations and in generic parameters.

Protocol composition types have the following form:

-   ~~~~ 
    protocol<Protocol 1, Protocol 2>
    ~~~~

A protocol composition type allows you to specify a value whose type
conforms to the requirements of multiple protocols without having to
explicitly define a new, named protocol that inherits from each protocol
you want the type to conform to. For example, specifying a protocol
composition type
protocol<ProtocolA, ProtocolB, ProtocolC> is effectively
the same as defining a new protocol ProtocolD that
inherits from ProtocolA, and
ProtocolC, but without having to introduce a new name.

Each item in a protocol composition list must be either the name of
protocol or a type alias of a protocol composition type. If the list is
empty, it specifies the empty protocol composition type, which every
type conforms to.

Grammar of a protocol composition type

‌ protocol-composition-type →
protocol

‌ protocol-identifier-list →
[protocol-identifier](Types.xhtml#protocol-identifier)
[protocol-identifier](Types.xhtml#protocol-identifier),[protocol-identifier-list](Types.xhtml#protocol-identifier-list)

‌ protocol-identifier → [type-identifier](Types.xhtml#type-identifier)

‌

### Metatype Type 

A metatype type refers to the type of any type, including class types,
structure types, enumeration types, and protocol types.

The metatype of a class, structure, or enumeration type is the name of
that type followed by .Type. The metatype of a protocol
type—not the concrete type that conforms to the protocol at runtime—is
the name of that protocol followed by .Protocol. For
example, the metatype of the class type SomeClass is
SomeClass.Type and the metatype of the protocol
SomeProtocol.

You can use the postfix self expression to access a type
as a value. For example, SomeClass.self returns
SomeClass itself, not an instance of
SomeClass returns
SomeProtocol itself, not an instance of a type that
conforms to SomeProtocol at runtime. You can use a
dynamicType expression with an instance of a type to
access that instance’s runtime type as a value, as the following example
shows:

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

Grammar of a metatype type

‌ metatype-type → [type](Types.xhtml#type).
[type](Types.xhtml#type).

‌

### Type Inheritance Clause 

A type inheritance clause is used to specify which class a named type
inherits from and which protocols a named type conforms to. A type
inheritance clause begins with a colon (:), followed by a
comma-separated list of type identifiers.

Class types may inherit from a single superclass and conform to any
number of protocols. When defining a class, the name of the superclass
must appear first in the list of type identifiers, followed by any
number of protocols the class must conform to. If the class does not
inherit from another class, the list may begin with a protocol instead.
For an extended discussion and several examples of class inheritance,
see [Inheritance](Inheritance.xhtml).

Other named types may only inherit from or conform to a list of
protocols. Protocol types may inherit from any number of other
protocols. When a protocol type inherits from other protocols, the set
of requirements from those other protocols are aggregated together, and
any type that inherits from the current protocol must conform to all of
those requirements.

A type inheritance clause in an enumeration definition may be either a
list of protocols, or in the case of an enumeration that assigns raw
values to its cases, a single, named type that specifies the type of
those raw values. For an example of an enumeration definition that uses
a type inheritance clause to specify the type of its raw values, see
[Raw Values](Enumerations.xhtml#TP40014097-CH12-XID_190).

Grammar of a type inheritance clause

‌ type-inheritance-clause →
:[type-inheritance-list](Types.xhtml#type-inheritance-list)

‌ type-inheritance-list → [type-identifier](Types.xhtml#type-identifier)
[type-identifier](Types.xhtml#type-identifier),[type-inheritance-list](Types.xhtml#type-inheritance-list)

‌

### Type Inference 

Swift uses type inference extensively, allowing you to omit the type or
part of the type of many variables and expressions in your code. For
example, instead of writing var x: Int = 0, you can omit
the type completely and simply write var x = 0—the
compiler correctly infers that x names a value of type
Int. Similarly, you can omit part of a type when the full
type can be inferred from context. For instance, if you write
let dict: Dictionary = ["A": 1], the compiler infers that
dict.

In both of the examples above, the type information is passed up from
the leaves of the expression tree to its root. That is, the type of
x is inferred by first
checking the type of 0 and then passing this type
information up to the root (the variable x).

In Swift, type information can also flow in the opposite direction—from
the root down to the leaves. In the following example, for instance, the
explicit type annotation (: Float) on the constant
eFloat
to have type Float.

    let
    // The type of e is inferred to be Double.
    let
    // The type of eFloat is Float.

Type inference in Swift operates at the level of a single expression or
statement. This means that all of the information needed to infer an
omitted type or part of a type in an expression must be accessible from
type-checking the expression or one of its subexpressions.
