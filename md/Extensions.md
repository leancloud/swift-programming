‌‌

Extensions 
----------

*Extensions* add new functionality to an existing class, structure, or
enumeration type. This includes the ability to extend types for which
you do not have access to the original source code (known as
*retroactive modeling*). Extensions are similar to categories in
Objective-C. (Unlike Objective-C categories, Swift extensions do not
have names.)

Extensions in Swift can:

-   Add computed properties and computed static properties

-   Define instance methods and type methods

-   Provide new initializers

-   Define subscripts

-   Define and use new nested types

-   Make an existing type conform to a protocol

Note

If you define an extension to add new functionality to an existing type,
the new functionality will be available on all existing instances of
that type, even if they were created before the extension was defined.

‌

### Extension Syntax 

Declare extensions with the extension keyword:

    extension {
        // new functionality to add to SomeType goes here
    }

An extension can extend an existing type to make it adopt one or more
protocols. Where this is the case, the protocol names are written in
exactly the same way as for a class or structure:

    extension,
    AnotherProtocol {
        // implementation of protocol requirements goes here
    }

Adding protocol conformance in this way is described in [Adding Protocol
Conformance with an Extension](Protocols.xhtml#TP40014097-CH25-XID_355).

‌

### Computed Properties 

Extensions can add computed instance properties and computed type
properties to existing types. This example adds five computed instance
properties to Swift’s built-in Double type, to provide
basic support for working with distance units:

    extension {
        var
    self
        var
    self
        var
    self
        var
    self
        var
    self
    }
    let
    println)
    // prints "One inch is 0.0254 meters"
    let
    println)
    // prints "Three feet is 0.914399970739201 meters"

These computed properties express that a Double value
should be considered as a certain unit of length. Although they are
implemented as computed properties, the names of these properties can be
appended to a floating-point literal value with dot syntax, as a way to
use that literal value to perform distance conversions.

In this example, a Double is
considered to represent “one meter”. This is why the m
computed property returns self—the expression
1.m
value of 1.0.

Other units require some conversion to be expressed as a value measured
in meters. One kilometer is the same as 1,000 meters, so the
km computed property multiplies the value by
1_000.00 to convert into a number expressed in meters.
Similarly, there are 3.28024 feet in a meter, and so the
ft computed property divides the underlying
Double, to convert it
from feet to meters.

These properties are read-only computed properties, and so they are
expressed without the get keyword, for brevity. Their
return value is of type Double, and can be used within
mathematical calculations wherever a Double is accepted:

    let +
    195
    println)
    // prints "A marathon is 42195.0 meters long"

Note

Extensions can add new computed properties, but they cannot add stored
properties, or add property observers to existing properties.

‌

### Initializers 

Extensions can add new initializers to existing types. This enables you
to extend other types to accept your own custom types as initializer
parameters, or to provide additional initialization options that were
not included as part of the type’s original implementation.

Extensions can add new convenience initializers to a class, but they
cannot add new designated initializers or deinitializers to a class.
Designated initializers and deinitializers must always be provided by
the original class implementation.

Note

If you use an extension to add an initializer to a value type that
provides default values for all of its stored properties and does not
define any custom initializers, you can call the default initializer and
memberwise initializer for that value type from within your extension’s
initializer.

This would not be the case if you had written the initializer as part of
the value type’s original implementation, as described in [Initializer
Delegation for Value
Types](Initialization.xhtml#TP40014097-CH18-XID_281).

The example below defines a custom Rect structure to
represent a geometric rectangle. The example also defines two supporting
structures called Size, both of
which provide default values of 0.0 for all of their
properties:

    struct {
        var =
    0.0
    }
    struct {
        var
    }
    struct {
        var()
        var()
    }

Because the Rect structure provides default values for
all of its properties, it receives a default initializer and a
memberwise initializer automatically, as described in [Default
Initializers](Initialization.xhtml#TP40014097-CH18-XID_279). These
initializers can be used to create new Rect instances:

    let()
    let =
    Rect,
    y),
        size,
    height))

You can extend the Rect structure to provide an
additional initializer that takes a specific center point and size:

    extension {
        init:
    Size) {
            let -
    (size)
            let -
    (size)
            self:
    Point),
    size)
        }
    }

This new initializer starts by calculating an appropriate origin point
based on the provided center point and
size value. The initializer then calls the structure’s
automatic memberwise initializer init(origin:size:),
which stores the new origin and size values in the appropriate
properties:

    let:
    Point),
        size,
    height))
    // centerRect's origin is (2.5, 2.5) and its size is (3.0, 3.0)

Note

If you provide a new initializer with an extension, you are still
responsible for making sure that each instance is fully initialized once
the initializer completes.

‌

### Methods 

Extensions can add new instance methods and type methods to existing
types. The following example adds a new instance method called
repetitions type:

    extension {
        func: () -\> ()) {
            for {
                task()
            }
        }
    }

The repetitions method takes a single argument of type
() -> (), which indicates a function that has no
parameters and does not return a value.

After defining this extension, you can call the
repetitions method on any integer number to perform a
task that many number of times:

    3({
        println)
        })
    // Hello!
    // Hello!
    // Hello!

Use trailing closure syntax to make the call more succinct:

    3 {
        println)
    }
    // Goodbye!
    // Goodbye!
    // Goodbye!

‌

### Mutating Instance Methods 

Instance methods added with an extension can also modify (or *mutate*)
the instance itself. Structure and enumeration methods that modify
self or its properties must mark the instance method as
mutating, just like mutating methods from an original
implementation.

The example below adds a new mutating method called
square type, which squares
the original value:

    extension {
        mutating() {
            self
        }
    }
    var
    someInt()
    // someInt is now 9

‌

### Subscripts 

Extensions can add new subscripts to an existing type. This example adds
an integer subscript to Swift’s built-in Int type. This
subscript [n]
places in from the right of the number:

    123456789[0]

    123456789[1]

…and so on:

    extension {
        subscript) -\>
    Int {
            var
                for
    1 {
                    decimalBase
                }
                return)
    % 10
        }
    }
    746381295]
    // returns 5
    746381295]
    // returns 9
    746381295]
    // returns 2
    746381295]
    // returns 7

If the Int value does not have enough digits for the
requested index, the subscript implementation returns 0,
as if the number had been padded with zeroes to the left:

    746381295]
    // returns 0, as if you had requested:
    0746381295]

‌

### Nested Types 

Extensions can add new nested types to existing classes, structures and
enumerations:

    extension {
        enum {
            case,
    Other
        }
        var {
        switch
    String {
        case,
    "u":
            return
        case,
    "g",
        "n",
    "t":
            return
        default:
            return
            }
        }
    }

This example adds a new nested enumeration to Character.
This enumeration, called Kind, expresses the kind of
letter that a particular character represents. Specifically, it
expresses whether the character is a vowel or a consonant in a standard
Latin script (without taking into account accents or regional
variations), or whether it is another kind of character.

This example also adds a new computed instance property to
Character, which returns the
appropriate Kind enumeration member for that character.

The nested enumeration can now be used with Character
values:

    func:
    String) {
        println)
        for {
            switch {
            case:
                print)
            case:
                print)
            case:
                print)
            }
        }
        print)
    }
    printLetterKinds)
    // 'Hello' is made up of the following kinds of letters:
    // consonant vowel consonant consonant vowel

This function, printLetterKinds, takes an input
String value and iterates over its characters. For each
character, it considers the kind computed property for
that character, and prints an appropriate description of that kind. The
printLetterKinds function can then be called to print the
kinds of letters in an entire word, as shown here for the word
"Hello".

Note

character.kind is already known to be of type
Character.Kind. Because of this, all of the
Character.Kind member values can be written in shorthand
form inside the switch statement, such as
.Vowel.
