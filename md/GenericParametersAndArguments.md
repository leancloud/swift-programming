‌‌

Generic Parameters and Arguments 
--------------------------------

This chapter describes parameters and arguments for generic types,
functions, and initializers. When you declare a generic type, function,
or initializer, you specify the type parameters that the generic type,
function, or initializer can work with. These type parameters act as
placeholders that are replaced by actual concrete type arguments when an
instance of a generic type is created or a generic function or
initializer is called.

For an overview of generics in Swift, see [Generics](Generics.xhtml).

‌

### Generic Parameter Clause 

A *generic parameter clause* specifies the type parameters of a generic
type or function, along with any associated constraints and requirements
on those parameters. A generic parameter clause is enclosed in angle
brackets (\<\>) and has one of the following forms:

-   ~~~~ 
    <generic parameter list>
    ~~~~

-   ~~~~ 
    <generic parameter list where requirements>
    ~~~~

The *generic parameter list* is a comma-separated list of generic
parameters, each of which has the following form:

-   ~~~~ 
    type parameter: constraint
    ~~~~

A generic parameter consists of a *type parameter* followed by an
optional *constraint*. A *type parameter* is simply the name of a
placeholder type (for instance, T,
V, and
so on). You have access to the type parameters (and any of their
associated types) in the rest of the type, function, or initializer
declaration, including in the signature of the function or initializer.

The *constraint* specifies that a type parameter inherits from a
specific class or conforms to a protocol or protocol composition. For
instance, in the generic function below, the generic parameter
T: Comparable indicates that any type argument
substituted for the type parameter T must conform to the
Comparable protocol.

    func:
    Comparable) -\>
    T {
        if {
            return
        }
        return
    }

Because Int, for example, both
conform to the Comparable protocol, this function accepts
arguments of either type. In contrast with generic types, you don’t
specify a generic argument clause when you use a generic function or
initializer. The type arguments are instead inferred from the type of
the arguments passed to the function or initializer.

    simpleMin)
    // T is inferred to be Int
    simpleMin)
    // T is inferred to be Double

‌

### Where Clauses 

You can specify additional requirements on type parameters and their
associated types by including a where clause after the
*generic parameter list*. A where clause consists of the
keyword where, followed by a comma-separated list of one
or more *requirements*.

The *requirements* in a where clause specify that a type
parameter inherits from a class or conforms to a protocol or protocol
composition. Although the where clause provides syntactic
sugar for expressing simple constraints on type parameters (for
instance, T: Comparable is equivalent to
T where T: Comparable and so on), you can use it to
provide more complex constraints on type parameters and their associated
types. For instance, you can express the constraints that a generic type
T and conforms to
a protocol P.

As mentioned above, you can constrain the associated types of type
parameters to conform to protocols. For example, the generic parameter
clause <T: Generator where T.Element: Equatable>
specifies that T
protocol and the associated type of T,
T.Element
protocol (T has the associated type
Element declares
Element conforms to
Generator).

You can also specify the requirement that two types be identical, using
the == operator. For example, the generic parameter
clause
<T: Generator, U: Generator where T.Element == U.Element>
expresses the constraints that T
conform to the Generator protocol and that their
associated types must be identical.

Any type argument substituted for a type parameter must meet all the
constraints and requirements placed on the type parameter.

You can overload a generic function or initializer by providing
different constraints, requirements, or both on the type parameters in
the generic parameter clause. When you call an overloaded generic
function or initializer, the compiler uses these constraints to resolve
which overloaded function or initializer to invoke.

You can subclass a generic class, but the subclass must also be a
generic class.

Grammar of a generic parameter clause

‌ generic-parameter-clause →
<

‌ generic-parameter-list →
[generic-parameter](GenericParametersAndArguments.xhtml#generic-parameter)
[generic-parameter](GenericParametersAndArguments.xhtml#generic-parameter),[generic-parameter-list](GenericParametersAndArguments.xhtml#generic-parameter-list)

‌ generic-parameter → [type-name](Types.xhtml#type-name)

‌ generic-parameter →
[type-name](Types.xhtml#type-name):[type-identifier](Types.xhtml#type-identifier)

‌ generic-parameter →
[type-name](Types.xhtml#type-name):[protocol-composition-type](Types.xhtml#protocol-composition-type)

‌ requirement-clause →
where[requirement-list](GenericParametersAndArguments.xhtml#requirement-list)

‌ requirement-list →
[requirement](GenericParametersAndArguments.xhtml#requirement)
[requirement](GenericParametersAndArguments.xhtml#requirement),[requirement-list](GenericParametersAndArguments.xhtml#requirement-list)

‌ requirement →
[conformance-requirement](GenericParametersAndArguments.xhtml#conformance-requirement)
[same-type-requirement](GenericParametersAndArguments.xhtml#same-type-requirement)

‌ conformance-requirement →
[type-identifier](Types.xhtml#type-identifier):[type-identifier](Types.xhtml#type-identifier)

‌ conformance-requirement →
[type-identifier](Types.xhtml#type-identifier):[protocol-composition-type](Types.xhtml#protocol-composition-type)

‌ same-type-requirement →
[type-identifier](Types.xhtml#type-identifier)==[type-identifier](Types.xhtml#type-identifier)

‌

### Generic Argument Clause 

A *generic argument clause* specifies the type arguments of a generic
type. A generic argument clause is enclosed in angle brackets (\<\>) and
has the following form:

-   ~~~~ 
    <generic argument list>
    ~~~~

The *generic argument list* is a comma-separated list of type arguments.
A *type argument* is the name of an actual concrete type that replaces a
corresponding type parameter in the generic parameter clause of a
generic type. The result is a specialized version of that generic type.
As an example, the Swift standard library defines a generic dictionary
type as:

    struct:
    Hashable,
    DictionaryLiteralConvertible {
        /* ... */
    }

The specialized version of the generic Dictionary type,
Dictionary<String, Int> is formed by replacing the
generic parameters KeyType: Hashable and
ValueType with the concrete type arguments
String. Each type argument must
satisfy all the constraints of the generic parameter it replaces,
including any additional requirements specified in a
where clause. In the example above, the
KeyType type parameter is constrained to conform to the
Hashable
must also conform to the Hashable protocol.

You can also replace a type parameter with a type argument that is
itself a specialized version of a generic type (provided it satisfies
the appropriate constraints and requirements). For example, you can
replace the type parameter T
with a specialized version of an array, Array<Int>, to
form an array whose elements are themselves arrays of integers.

    let:
    Array,
    3]]

As mentioned in [Generic Parameter
Clause](GenericParametersAndArguments.xhtml#TP40014097-CH37-XID_775),
you don’t use a generic argument clause to specify the type arguments of
a generic function or initializer.

Grammar of a generic argument clause

‌ generic-argument-clause →
<

‌ generic-argument-list →
[generic-argument](GenericParametersAndArguments.xhtml#generic-argument)
[generic-argument](GenericParametersAndArguments.xhtml#generic-argument),[generic-argument-list](GenericParametersAndArguments.xhtml#generic-argument-list)

‌ generic-argument → [type](Types.xhtml#type)
