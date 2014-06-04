‌‌

Generics 
--------

*Generic code* enables you to write flexible, reusable functions and
types that can work with any type, subject to requirements that you
define. You can write code that avoids duplication and expresses its
intent in a clear, abstracted manner.

Generics are one of the most powerful features of Swift, and much of the
Swift standard library is built with generic code. In fact, you’ve been
using generics throughout this Language Guide, even if you didn’t
realize it. For example, Swift’s Array and
Dictionary types are both generic collections. You can
create an array that holds Int values, or an array that
holds String values, or indeed an array for any other
type that can be created in Swift. Similarly, you can create a
dictionary to store values of any specified type, and there are no
limitations on what that type can be.

‌

### The Problem That Generics Solve 

Here’s a standard, non-generic function called
swapTwoInts values:

    func:
    Int) {
        let
        a
        b
    }

This function makes use of in-out parameters to swap the values of
a, as described in [In-Out
Parameters](Functions.xhtml#TP40014097-CH10-XID_226).

The swapTwoInts function swaps the original value of
b, and the original value of
a. You can call this function to
swap the values in two Int variables:

    var
    var
    swapTwoInts)
    println)
    // prints "someInt is now 107, and anotherInt is now 3"

The swapTwoInts function is useful, but it can only be
used with Int values. If you want to swap two
String values, you
have to write more functions, such as the swapTwoStrings
and swapTwoDoubles functions shown below:

    func:
    String) {
        let
        a
        b
    }
     
    func:
    Double) {
        let
        a
        b
    }

You may have noticed that the bodies of the swapTwoInts,
swapTwoStrings
functions are identical. The only difference is the type of the values
that they accept (Int, and
Double).

It would be much more useful, and considerably more flexible, to write a
single function that could swap two values of *any* type. This is the
kind of problem that generic code can solve. (A generic version of these
functions is defined below.)

Note

In all three functions, it is important that the types of
a are defined to be the same as each
other. If a were not of the same
type, it would not be possible to swap their values. Swift is a
type-safe language, and does not allow (for example) a variable of type
String to
swap values with each other. Attempting to do so would be reported as a
compile-time error.

‌

### Generic Functions 

*Generic functions* can work with any type. Here’s a generic version of
the swapTwoInts function from above, called
swapTwoValues:

    func
    a) {
        let
        a
        b
    }

The body of the swapTwoValues function is identical to
the body of the swapTwoInts function. However, the first
line of swapTwoValues is slightly different from
swapTwoInts. Here’s how the first lines compare:

    func:
    Int)
    func
    a)

The generic version of the function uses a *placeholder* type name
(called T, in this case) instead of an *actual* type name
(such as Int, or
Double). The placeholder type name doesn’t say anything
about what T must be, but it *does* say that both
a must be of the same type
T represents. The actual type
to use in place of T will be determined each time the
swapTwoValues function is called.

The other difference is that the generic function’s name
(swapTwoValues) is followed by the placeholder type name
(T). The
brackets tell Swift that T is a placeholder type name
within the swapTwoValues function definition. Because
T is a placeholder, Swift does not look for an actual
type called T.

The swapTwoValues function can now be called in the same
way as swapTwoInts, except that it can be passed two
values of *any* type, as long as both of those values are of the same
type as each other. Each time swapTwoValues is called,
the type to use for T is inferred from the types of
values passed to the function.

In the two examples below, T is inferred to be
Int respectively:

    var
    var
    swapTwoValues)
    // someInt is now 107, and anotherInt is now 3
     
    var
    var
    swapTwoValues,
    &anotherString)
    // someString is now "world", and anotherString is now "hello"

Note

The swapTwoValues function defined above is inspired by a
generic function called swap, which is part of the Swift
standard library, and is automatically made available for you to use in
your apps. If you need the behavior of the swapTwoValues
function in your own code, you can use Swift’s existing
swap function rather than providing your own
implementation.

‌

### Type Parameters 

In the swapTwoValues example above, the placeholder type
T is an example of a *type parameter*. Type parameters
specify and name a placeholder type, and are written immediately after
the function’s name, between a pair of matching angle brackets (such as
<T>).

Once specified, a type parameter can be used to define the type of a
function’s parameters (such as the a
parameters of the swapTwoValues function); or as the
function’s return type; or as a type annotation within the body of the
function. In each case, the placeholder type represented by the type
parameter is replaced with an *actual* type whenever the function is
called. (In the swapTwoValues example above,
T the first time the
function was called, and was replaced with String the
second time it was called.)

You can provide more than one type parameter by writing multiple type
parameter names within the angle brackets, separated by commas.

‌

### Naming Type Parameters 

In simple cases where a generic function or generic type needs to refer
to a single placeholder type (such as the swapTwoValues
generic function above, or a generic collection that stores a single
type, such as Array), it is traditional to use the
single-character name T for the type parameter. However,
you are can use any valid identifier as the type parameter name.

If you are defining more complex generic functions, or generic types
with multiple parameters, it can be useful to provide more descriptive
type parameter names. For example, Swift’s Dictionary
type has two type parameters—one for its keys and one for its values. If
you were writing Dictionary yourself, you might name
these two type parameters KeyType and
ValueType to remind you of their purpose as you use them
within your generic code.

Note

Always give type parameters UpperCamelCase names (such as
T) to indicate that they are a
placeholder for a *type*, not a value.

‌

### Generic Types 

In addition to generic functions, Swift enables you to define your own
*generic types*. These are custom classes, structures, and enumerations
that can work with *any* type, in a similar way to Array
and Dictionary.

This section shows you how to write a generic collection type called
Stack. A stack is an ordered set of values, similar to an
array, but with a more restricted set of operations than Swift’s
Array type. An array allows new items to be inserted and
removed at any location in the array. A stack, however, allows new items
to be appended only to the end of the collection (known as *pushing* a
new value on to the stack). Similarly, a stack allows items to be
removed only from the end of the collection (known as *popping* a value
off the stack).

Note

The concept of a stack is used by the
UINavigationController class to model the view
controllers in its navigation hierarchy. You call the
UINavigationController class
pushViewController:animated: method to add (or push) a
view controller on to the navigation stack, and its
popViewControllerAnimated: method to remove (or pop) a
view controller from the navigation stack. A stack is a useful
collection model whenever you need a strict “last in, first out”
approach to managing a collection.

The illustration below shows the push / pop behavior for a stack:

![image: ../Art/stackPushPop\_2x.png](Art/stackPushPop_2x.png)

1.  There are currently three values on the stack.

2.  A fourth value is “pushed” on to the top of the stack.

3.  The stack now holds four values, with the most recent one at the
    top.

4.  The top item in the stack is removed, or “popped”.

5.  After popping a value, the stack once again holds three values.

Here’s how to write a non-generic version of a stack, in this case for a
stack of Int values:

    struct {
        var[]()
        mutating:
    Int) {
            items)
        }
        mutating {
            return()
        }
    }

This structure uses an Array property called
items to store the values in the stack.
Stack and
pop, to push and pop values on and off the stack. These
methods are marked as mutating, because they need to
modify (or *mutate*) the structure’s items array.

The IntStack type shown above can only be used with
Int values, however. It would be much more useful to
define a *generic* Stack class, that can manage a stack
of *any* type of value.

Here’s a generic version of the same code:

    struct\> {
        var[]()
        mutating:
    T) {
            items)
        }
        mutating {
            return()
        }
    }

Note how the generic version of Stack is essentially the
same as the non-generic version, but with a placeholder type parameter
called T.
This type parameter is written within a pair of angle brackets
(<T>) immediately after the structure’s name.

T defines a placeholder name for “some type
T” to be provided later on. This future type can be
referred to as “T” anywhere within the structure’s
definition. In this case, T is used as a placeholder in
three places:

-   To create a property called items, which is
    initialized with an empty array of values of type T

-   To specify that the push method has a single
    parameter called item, which must be of type
    T

-   To specify that the value returned by the pop method
    will be a value of type T

You create instances of Stack in a similar way to
Array, by writing the
actual type to be used for this specific stack within angle brackets
after the type name when creating a new instance with initializer
syntax:

    var =
    Stack\>()
    stackOfStrings)
    stackOfStrings)
    stackOfStrings)
    stackOfStrings)
    // the stack now contains 4 strings

Here’s how stackOfStrings looks after pushing these four
values on to the stack:

![image:
../Art/stackPushedFourStrings\_2x.png](Art/stackPushedFourStrings_2x.png)

Popping a value from the stack returns and removes the top value,
"cuatro":

    let =
    stackOfStrings()
    // fromTheTop is equal to "cuatro", and the stack now contains 3 strings

Here’s how the stack looks after popping its top value:

![image:
../Art/stackPoppedOneString\_2x.png](Art/stackPoppedOneString_2x.png)

Because it is a generic type, Stack can be used to create
a stack of *any* valid type in Swift, in a similar manner to
Array.

‌

### Type Constraints 

The swapTwoValues
type can work with any type. However, it is sometimes useful to enforce
certain *type constraints* on the types that can be used with generic
functions and generic types. Type constraints specify that a type
parameter must inherit from a specific class, or conform to a particular
protocol or protocol composition.

For example, Swift’s Dictionary type places a limitation
on the types that can be used as keys for a dictionary. As described in
[Dictionaries](CollectionTypes.xhtml#TP40014097-CH8-XID_143), the type
of a dictionary’s keys must be *hashable*. That is, it must provide a
way to make itself uniquely representable. Dictionary
needs its keys to be hashable so that it can check whether it already
contains a value for a particular key. Without this requirement,
Dictionary could not tell whether it should insert or
replace a value for a particular key, nor would it be able to find a
value for a given key that is already in the dictionary.

This requirement is enforced by a type constraint on the key type for
Dictionary, which specifies that the key type must
conform to the Hashable protocol, a special protocol
defined in the Swift standard library. All of Swift’s basic types (such
as String, and
Bool) are hashable by default.

You can define your own type constraints when creating custom generic
types, and these constraints provide much of the power of generic
programming. Abstract concepts like Hashable characterize
types in terms of their conceptual characteristics, rather than their
explicit type.

‌

### Type Constraint Syntax 

You write type constraints by placing a single class or protocol
constraint after a type parameter’s name, separated by a colon, as part
of the type parameter list. The basic syntax for type constraints on a
generic function is shown below (although the syntax is the same for
generic types):

    func,
    U:
    U) {
        // function body goes here
    }

The hypothetical function above has two type parameters. The first type
parameter, T, has a type constraint that requires
T. The
second type parameter, U, has a type constraint that
requires U to conform to the protocol
SomeProtocol.

‌

### Type Constraints in Action 

Here’s a non-generic function called findStringIndex,
which is given a String value to find and an array of
String values within which to find it. The
findStringIndex function returns an optional
Int value, which will be the index of the first matching
string in the array if it is found, or nil if the string
cannot be found:

    func:
    String? {
        for
    enumerate) {
            if {
                return
            }
        }
        return
    }

The findStringIndex function can be used to find a string
value in an array of strings:

    let,
    "llama"]
    if =
    findStringIndex) {
        println)
    }
    // prints "The index of llama is 2"

The principle of finding the index of a value in an array isn’t useful
only for strings, however. You can write the same functionality as a
generic function called findIndex, by replacing any
mention of strings with values of some type T instead.

Here’s how you might expect a generic version of
findStringIndex, to be
written. Note that the return type of this function is still
Int?, because the function returns an optional index
number, not an optional value from the array. Be warned, though—this
function does not compile, for reasons explained after the example:

    func:
    T? {
        for
    enumerate) {
            if {
                return
            }
        }
        return
    }

This function does not compile as written above. The problem lies with
the equality check, “if value == valueToFind”. Not every
type in Swift can be compared with the equal to operator
(==). If you create your own class or structure to
represent a complex data model, for example, then the meaning of “equal
to” for that class or structure is not something that Swift can guess
for you. Because of this, it is not possible to guarantee that this code
will work for *every* possible type T, and an appropriate
error is reported when you try to compile the code.

All is not lost, however. The Swift standard library defines a protocol
called Equatable, which requires any conforming type to
implement the equal to operator (==) and the not equal to
operator (!=) to compare any two values of that type. All
of Swift’s standard types automatically support the
Equatable protocol.

Any type that is Equatable can be used safely with the
findIndex function, because it is guaranteed to support
the equal to operator. To express this fact, you write a type constraint
of Equatable as part of the type parameter’s definition
when you define the function:

    func:
    Equatable:
    T? {
        for
    enumerate) {
            if {
                return
            }
        }
        return
    }

The single type parameter for findIndex is written as
T: Equatable that
conforms to the Equatable protocol.”

The findIndex function now compiles successfully and can
be used with any type that is Equatable, such as
Double:

    let =
    findIndex)
    // doubleIndex is an optional Int with no value, because 9.3 is not in the array
    let =
    findIndex],
    "Andrea")
    // stringIndex is an optional Int containing a value of 2

‌

### Associated Types 

When defining a protocol, it is sometimes useful to declare one or more
*associated types* as part of the protocol’s definition. An associated
type gives a placeholder name (or *alias*) to a type that is used as
part of the protocol. The actual type to use for that associated type is
not specified until the protocol is adopted. Associated types are
specified with the typealias keyword.

‌

### Associated Types in Action 

Here’s an example of a protocol called Container, which
declares an associated type called ItemType:

    protocol {
        typealias
        mutating:
    ItemType)
        var
        subscript
    
    }

The Container protocol defines three required
capabilities that any container must provide:

-   It must be possible to add a new item to the container with an
    append method.

-   It must be possible to access a count of the items in the container
    through a count property that returns an
    Int value.

-   It must be possible to retrieve each item in the container with a
    subscript that takes an Int index value.

This protocol doesn’t specify how the items in the container should be
stored or what type they are allowed to be. The protocol only specifies
the three bits of functionality that any type must provide in order to
be considered a Container. A conforming type can provide
additional functionality, as long as it satisfies these three
requirements.

Any type that conforms to the Container protocol must be
able to specify the type of values it stores. Specifically, it must
ensure that only items of the right type are added to the container, and
it must be clear about the type of the items returned by its subscript.

To define these requirements, the Container protocol
needs a way to refer to the type of the elements that a container will
hold, without knowing what that type is for a specific container. The
Container protocol needs to specify that any value passed
to the append method must have the same type as the
container’s element type, and that the value returned by the container’s
subscript will be of the same type as the container’s element type.

To achieve this, the Container protocol declares an
associated type called ItemType, written as
typealias ItemType. The protocol does not define what
ItemType is an alias *for*—that information is left for
any conforming type to provide. Nonetheless, the ItemType
alias provides a way to refer to the type of the items in a
Container, and to define a type for use with the
append method and subscript, to ensure that the expected
behavior of any Container is enforced.

Here’s a version of the non-generic IntStack type from
earlier, adapted to conform to the Container protocol:

    struct {
        // original IntStack implementation
        var[]()
        mutating:
    Int) {
            items)
        }
        mutating {
            return()
        }
        // conformance to the Container protocol
        typealias
        mutating:
    Int) {
            self)
        }
        var {
        return
        }
        subscript {
            return]
        }
    }

The IntStack type implements all three of the
Container protocol’s requirements, and in each case wraps
part of the IntStack type’s existing functionality to
satisfy these requirements.

Moreover, IntStack specifies that for this implementation
of Container to
use is a type of Int. The definition of
typealias ItemType = Int turns the abstract type of
ItemType for
this implementation of the Container protocol.

Thanks to Swift’s type inference, you don’t actually need to declare a
concrete ItemType as part of the
definition of IntStack
conforms to all of the requirements of the Container
protocol, Swift can infer the appropriate ItemType to
use, simply by looking at the type of the append method’s
item parameter and the return type of the subscript.
Indeed, if you delete the typealias ItemType = Int line
from the code above, everything still works, because it is clear what
type should be used for ItemType.

You can also make the generic Stack type conform to the
Container protocol:

    struct {
        // original Stack<T> implementation
        var[]()
        mutating:
    T) {
            items)
        }
        mutating {
            return()
        }
        // conformance to the Container protocol
        mutating:
    T) {
            self)
        }
        var {
        return
        }
        subscript {
            return]
        }
    }

This time, the placeholder type parameter T is used as
the type of the append
parameter and the return type of the subscript. Swift can therefore
infer that T is the appropriate type to use as the
ItemType for this particular container.

‌

### Extending an Existing Type to Specify an Associated Type 

You can extend an existing type to add conformance to a protocol, as
described in [Adding Protocol Conformance with an
Extension](Protocols.xhtml#TP40014097-CH25-XID_355). This includes a
protocol with an associated type.

Swift’s Array type already provides an
append property, and a
subscript with an Int index to retrieve its elements.
These three capabilities match the requirements of the
Container protocol. This means that you can extend
Array protocol
simply by declaring that Array adopts the protocol. You
do this with an empty extension, as described in [Declaring Protocol
Adoption with an Extension](Protocols.xhtml#TP40014097-CH25-XID_357):

    extension

Array’s existing append method and subscript enable Swift
to infer the appropriate type to use for ItemType, just
as for the generic Stack type above. After defining this
extension, you can use any Array as a
Container.

‌

### Where Clauses 

Type constraints, as described in [Type
Constraints](Generics.xhtml#TP40014097-CH26-XID_244), enable you to
define requirements on the type parameters associated with a generic
function or type.

It can also be useful to define requirements for associated types. You
do this by defining *where clauses* as part of a type parameter list. A
where clause enables you to require that an associated type conforms to
a certain protocol, and/or that certain type parameters and associated
types be the same. You write a where clause by placing the
where keyword immediately after the list of type
parameters, followed by one or more constraints for associated types,
and/or one or more equality relationships between types and associated
types.

The example below defines a generic function called
allItemsMatch, which checks to see if two
Container instances contain the same items in the same
order. The function returns a Boolean value of true if
all items match and a value of false if they do not.

The two containers to be checked do not have to be the same type of
container (although they can be), but they do have to hold the same type
of items. This requirement is expressed through a combination of type
constraints and where clauses:

    func\<
        C1
        where ==
    C2:
    Equatable\>
        (someContainer,
    anotherContainer {
            
            // check that both containers contain the same number of items
            if !=
    anotherContainer {
                return
            }
            
            // check each pair of items to see if they are equivalent
            for
    0 {
                if] !=
    anotherContainer] {
                    return
                }
            }
            
            // all items match, so return true
            return
            
    }

This function takes two arguments called someContainer
and anotherContainer
argument is of type C1, and the
anotherContainer.
Both C1 are placeholder type
parameters for two container types to be determined when the function is
called.

The function’s type parameter list places the following requirements on
the two type parameters:

    C1
    protocol (written as C1: Container).

    C2
    protocol (written as C2: Container).

-   The ItemType must be the same
    as the ItemType (written as
    C1.ItemType == C2.ItemType).

-   The ItemType must conform to
    the Equatable protocol (written as
    C1.ItemType: Equatable).

The third and fourth requirements are defined as part of a where clause,
and are written after the where keyword as part of the
function’s type parameter list.

These requirements mean:

    someContainer is a container of type
    C1.

    anotherContainer is a container of type
    C2.

    someContainer
    contain the same type of items.

-   The items in someContainer can be checked with the
    not equal operator (!=) to see if they are different
    from each other.

The third and fourth requirements combine to mean that the items in
anotherContainer can *also* be checked with the
!= operator, because they are exactly the same type as
the items in someContainer.

These requirements enable the allItemsMatch function to
compare the two containers, even if they are of a different container
type.

The allItemsMatch function starts by checking that both
containers contain the same number of items. If they contain a different
number of items, there is no way that they can match, and the function
returns false.

After making this check, the function iterates over all of the items in
someContainer
loop and the half-closed range operator (..). For each
item, the function checks whether the item from
someContainer is not equal to the corresponding item in
anotherContainer. If the two items are not equal, then
the two containers do not match, and the function returns
false.

If the loop finishes without finding a mismatch, the two containers
match, and the function returns true.

Here’s how the allItemsMatch function looks in action:

    var =
    Stack\>()
    stackOfStrings)
    stackOfStrings)
    stackOfStrings)
     
    var,
    "dos"]
     
    if,
    arrayOfStrings) {
        println)
    } else {
        println)
    }
    // prints "All items match."

The example above creates a Stack instance to store
String values, and pushes three strings onto the stack.
The example also creates an Array instance initialized
with an array literal containing the same three strings as the stack.
Even though the stack and the array are of a different type, they both
conform to the Container protocol, and both contain the
same type of values. You can therefore call the
allItemsMatch function with these two containers as its
arguments. In the example above, the allItemsMatch
function correctly reports that all of the items in the two containers
match.
