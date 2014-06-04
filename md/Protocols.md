‌‌

Protocols 
---------

A *protocol* defines a blueprint of methods, properties, and other
requirements that suit a particular task or piece of functionality. The
protocol doesn’t actually provide an implementation for any of these
requirements—it only describes what an implementation will look like.
The protocol can then be *adopted* by a class, structure, or enumeration
to provide an actual implementation of those requirements. Any type that
satisfies the requirements of a protocol is said to *conform* to that
protocol.

Protocols can require that conforming types have specific instance
properties, instance methods, type methods, operators, and subscripts.

‌

### Protocol Syntax 

You define protocols in a very similar way to classes, structures, and
enumerations:

    protocol {
        // protocol definition goes here
    }

Custom types state that they adopt a particular protocol by placing the
protocol’s name after the type’s name, separated by a colon, as part of
their definition. Multiple protocols can be listed, and are separated by
commas:

    struct,
    AnotherProtocol {
        // structure definition goes here
    }

If a class has a superclass, list the superclass name before any
protocols it adopts, followed by a comma:

    class,
    FirstProtocol {
        // class definition goes here
    }

‌

### Property Requirements 

A protocol can require any conforming type to provide an instance
property or type property with a particular name and type. The protocol
doesn’t specify whether the property should be a stored property or a
computed property—it only specifies the required property name and type.
The protocol also specifies whether each property must be gettable or
gettable *and* settable.

If a protocol requires a property to be gettable and settable, that
property requirement cannot be fulfilled by a constant stored property
or a read-only computed property. If the protocol only requires a
property to be gettable, the requirement can be satisfied by any kind of
property, and it is valid for it also to be settable if this is useful
for your own code.

Property requirements are always declared as variable properties,
prefixed with the var keyword. Gettable and settable
properties are indicated by writing  after
their type declaration, and gettable properties are indicated by writing
.

    protocol {
        var
    set
        var {
    get
    }

Always prefix type property requirements with the class
keyword when you define them in a protocol. This is true even though
type property requirements are prefixed with the static
keyword when implemented by a structure or enumeration:

    protocol {
        class:
    Int
    }

Here’s an example of a protocol with a single instance property
requirement:

    protocol {
        var
    }

The FullyNamed protocol defines any kind of thing that
has a fully-qualified name. It doesn’t specify what *kind* of thing it
must be—it only specifies that the thing must be able to provide a full
name for itself. It specifies this requirement by stating that any
FullyNamed type must have a gettable instance property
called fullName.

Here’s an example of a simple structure that adopts and conforms to the
FullyNamed protocol:

    struct {
        var
    }
    let:
    "John Appleseed")
    // john.fullName is "John Appleseed"

This example defines a structure called Person, which
represents a specific named person. It states that it adopts the
FullyNamed protocol as part of the first line of its
definition.

Each instance of Person has a single stored property
called fullName.
This matches the single requirement of the FullyNamed
protocol, and means that Person has correctly conformed
to the protocol. (Swift reports an error at compile-time if a protocol
requirement is not fulfilled.)

Here’s a more complex class, which also adopts and conforms to the
FullyNamed protocol:

    class {
        var?
        var
        init:
    String) {
            self
            self
        }
        var {
        return! +
    " "
        }
    }
    var:
    "Enterprise")
    // ncc1701.fullName is "USS Enterprise"

This class implements the fullName property requirement
as a computed read-only property for a starship. Each
Starship class instance stores a mandatory
name. The
fullName value if
it exists, and prepends it to the beginning of name to
create a full name for the starship.

‌

### Method Requirements 

Protocols can require specific instance methods and type methods to be
implemented by conforming types. These methods are written as part of
the protocol’s definition in exactly the same way as for normal instance
and type methods, but without curly braces or a method body. Variadic
parameters are allowed, subject to the same rules as for normal methods.

Note

Protocols use the same syntax as normal methods, but are not allowed to
specify default values for method parameters.

As with type property requirements, you always prefix type method
requirements with the class keyword when they are defined
in a protocol. This is true even though type method requirements are
prefixed with the static keyword when implemented by a
structure or enumeration:

    protocol {
        class()
    }

The following example defines a protocol with a single instance method
requirement:

    protocol {
        func
    }

This protocol, RandomNumberGenerator, requires any
conforming type to have an instance method called random,
which returns a Double value whenever it is called.
(Although it is not specified as part of the protocol, it is assumed
that this value will be a number between 0.0 and
1.0 inclusive.)

The RandomNumberGenerator protocol does not make any
assumptions about how each random number will be generated—it simply
requires the generator to provide a standard way to generate a new
random number.

Here’s an implementation of a class that adopts and conforms to the
RandomNumberGenerator protocol. This class implements a
pseudorandom number generator algorithm known as a *linear congruential
generator*:

    class:
    RandomNumberGenerator {
        var
        let
        let
        let
        func {
            lastRandom
    + c)
            return
        }
    }
    let =
    LinearCongruentialGenerator()
    println)
    // prints "Here's a random number: 0.37464991998171"
    println)
    // prints "And another one: 0.729023776863283"

‌

### Mutating Method Requirements 

It is sometimes necessary for a method to modify (or *mutate*) the
instance it belongs to. For instance methods on value types (that is,
structures and enumerations) you place the mutating
keyword before a method’s func keyword to indicate that
the method is allowed to modify the instance it belongs to and/or any
properties of that instance. This process is described in [Modifying
Value Types from Within Instance
Methods](Methods.xhtml#TP40014097-CH15-XID_305).

If you define a protocol instance method requirement that is intended to
mutate instances of any type that adopts the protocol, mark the method
with the mutating keyword as part of the protocol’s
definition. This enables structures and enumerations to adopt the
protocol and satisfy that method requirement.

Note

If you mark a protocol instance method requirement as
mutating, you do not need to write the
mutating keyword when writing an implementation of that
method for a class. The mutating keyword is only used by
structures and enumerations.

The example below defines a protocol called Togglable,
which defines a single instance method requirement called
toggle
method is intended to toggle or invert the state of any conforming type,
typically by modifying a property of that type.

The toggle method is marked with the
mutating
protocol definition, to indicate that the method is expected to mutate
the state of a conforming instance when it is called:

    protocol {
        mutating()
    }

If you implement the Togglable protocol for a structure
or enumeration, that structure or enumeration can conform to the
protocol by providing an implementation of the toggle
method that is also marked as mutating.

The example below defines an enumeration called
OnOffSwitch. This enumeration toggles between two states,
indicated by the enumeration cases On and
Off
implementation is marked as mutating, to match the
Togglable protocol’s requirements:

    enum {
        case
        mutating() {
            switch {
            case:
                self
            case:
                self
            }
        }
    }
    var =
    OnOffSwitch
    lightSwitch()
    // lightSwitch is now equal to .On

‌

### Protocols as Types 

Protocols do not actually implement any functionality themselves.
Nonetheless, any protocol you create will become a fully-fledged type
for use in your code.

Because it is a type, you can use a protocol in many places where other
types are allowed, including:

-   As a parameter type or return type in a function, method, or
    initializer

-   As the type of a constant, variable, or property

-   As the type of items in an array, dictionary, or other container

Note

Because protocols are types, begin their names with a capital letter
(such as FullyNamed and
RandomNumberGenerator) to match the names of other types
in Swift (such as Int, and
Double).

Here’s an example of a protocol used as a type:

    class {
        let
        let
        init:
    RandomNumberGenerator) {
            self
            self
        }
        func {
            return
    Int() \*
    Double
        }
    }

This example defines a new class called Dice, which
represents an *n*-sided dice for use in a board game.
Dice instances have an integer property called
sides, which represents how many sides they have, and a
property called generator, which provides a random number
generator from which to create dice roll values.

The generator property is of type
RandomNumberGenerator. Therefore, you can set it to an
instance of *any* type that adopts the
RandomNumberGenerator protocol. Nothing else is required
of the instance you assign to this property, except that the instance
must adopt the RandomNumberGenerator protocol.

Dice also has an initializer, to set up its initial
state. This initializer has a parameter called generator,
which is also of type RandomNumberGenerator. You can pass
a value of any conforming type in to this parameter when initializing a
new Dice instance.

Dice,
which returns an integer value between 1 and the number of sides on the
dice. This method calls the generator’s random method to
create a new random number between 0.0 and
1.0, and uses this random number to create a dice roll
value within the correct range. Because generator is
known to adopt RandomNumberGenerator, it is guaranteed to
have a random method to call.

Here’s how the Dice class can be used to create a
six-sided dice with a LinearCongruentialGenerator
instance as its random number generator:

    var,
    generator())
    for {
        println)
    }
    // Random dice roll is 3
    // Random dice roll is 5
    // Random dice roll is 4
    // Random dice roll is 5
    // Random dice roll is 4

‌

### Delegation 

*Delegation* is a design pattern that enables a class or structure to
hand off (or *delegate*) some of its responsibilities to an instance of
another type. This design pattern is implemented by defining a protocol
that encapsulates the delegated responsibilities, such that a conforming
type (known as a delegate) is guaranteed to provide the functionality
that has been delegated. Delegation can be used to respond to a
particular action, or to retrieve data from an external source without
needing to know the underlying type of that source.

The example below defines two protocols for use with dice-based board
games:

    protocol {
        var
        func()
    }
    protocol {
        func:
    DiceGame)
        func,
    didStartNewTurnWithDiceRoll)
        func:
    DiceGame)
    }

The DiceGame protocol is a protocol that can be adopted
by any game that involves dice. The DiceGameDelegate
protocol can be adopted by any type to track the progress of a
DiceGame.

Here’s a version of the *Snakes and Ladders* game originally introduced
in [Control Flow](ControlFlow.xhtml). This version is adapted to use a
Dice instance for its dice-rolls; to adopt the
DiceGame protocol; and to notify a
DiceGameDelegate about its progress:

    class {
        let
        let:
    6())
        var
        var[]
        init() {
            board:
    finalSquare)
            board;
    board] =
    +09
            board;
    board] =
    -02
        }
        var?
        func() {
            square
            delegate)
            gameLoop !=
    finalSquare {
                let =
    dice()
                delegate,
    didStartNewTurnWithDiceRoll)
                switch {
                case:
                    break
                case
    where:
                    continue
                default:
                    square
                    square]
                }
            }
            delegate)
        }
    }

For a description of the *Snakes and Ladders* gameplay, see the
[Break](ControlFlow.xhtml#TP40014097-CH9-XID_174) section of the
[Control Flow](ControlFlow.xhtml) chapter.

This version of the game is wrapped up as a class called
SnakesAndLadders, which adopts the
DiceGame protocol. It provides a gettable
dice method in order
to conform to the protocol. (The dice property is
declared as a constant property because it does not need to change after
initialization, and the protocol only requires that it is gettable.)

The *Snakes and Ladders* game board setup takes place within the class’s
init() initializer. All game logic is moved into the
protocol’s play method, which uses the protocol’s
required dice property to provide its dice roll values.

Note that the delegate property is defined as an
*optional* DiceGameDelegate, because a delegate isn’t
required in order to play the game. Because it is of an optional type,
the delegate property is automatically set to an initial
value of nil. Thereafter, the game instantiator has the
option to set the property to a suitable delegate.

DiceGameDelegate provides three methods for tracking the
progress of a game. These three methods have been incorporated into the
game logic within the play method above, and are called
when a new game starts, a new turn begins, or the game ends.

Because the delegate property is an *optional*
DiceGameDelegate method uses
optional chaining each time it calls a method on the delegate. If the
delegate property is nil, these delegate calls fail
gracefully and without error. If the delegate property is
non-nil, the delegate methods are called, and are passed the
SnakesAndLadders instance as a parameter.

This next example shows a class called DiceGameTracker,
which adopts the DiceGameDelegate protocol:

    class
    {
        var
        func:
    DiceGame) {
            numberOfTurns
            if
    SnakesAndLadders {
                println)
            }
            println)
        }
        func,
    didStartNewTurnWithDiceRoll) {
            ++numberOfTurns
            println)
        }
        func:
    DiceGame) {
            println)
        }
    }

DiceGameTracker implements all three methods required by
DiceGameDelegate. It uses these methods to keep track of
the number of turns a game has taken. It resets a
numberOfTurns property to zero when the game starts;
increments it each time a new turn begins; and prints out the total
number of turns once the game has ended.

The implementation of gameDidStart shown above uses the
game parameter to print some introductory information
about the game that is about to be played. The game
parameter has a type of DiceGame, not
SnakesAndLadders can
access and use only methods and properties that are implemented as part
of the DiceGame protocol. However, the method is still
able to use type casting to query the type of the underlying instance.
In this example, it checks whether game is actually an
instance of SnakesAndLadders behind the scenes, and
prints an appropriate message if so.

gameDidStart
property of the passed game parameter. Because
game
protocol, it is guaranteed to have a dice property, and
so the gameDidStart method is able to access and print
the dice’s sides property, regardless of what kind of
game is being played.

Here’s how DiceGameTracker looks in action:

    let()
    let()
    game
    game()
    // Started a new game of Snakes and Ladders
    // The game is using a 6-sided dice
    // Rolled a 3
    // Rolled a 5
    // Rolled a 4
    // Rolled a 5
    // The game lasted for 4 turns

‌

### Adding Protocol Conformance with an Extension 

You can extend an existing type to adopt and conform to a new protocol,
even if you do not have access to the source code for the existing type.
Extensions can add new properties, methods, and subscripts to an
existing type, and are therefore able to add any requirements that a
protocol may demand. For more about extensions, see
[Extensions](Extensions.xhtml).

Note

Existing instances of a type automatically adopt and conform to a
protocol when that conformance is added to the instance’s type in an
extension.

For example, this protocol, called TextRepresentable, can
be implemented by any type that has a way to be represented as text.
This might be a description of itself, or a text version of its current
state:

    protocol {
        func
    }

The Dice class from earlier can be extended to adopt and
conform to TextRepresentable:

    extension {
        func {
            return
    "A 
        }
    }

This extension adopts the new protocol in exactly the same way as if
Dice had provided it in its original implementation. The
protocol name is provided after the type name, separated by a colon, and
an implementation of all requirements of the protocol is provided within
the extension’s curly braces.

Any Dice instance can now be treated as
TextRepresentable:

    let,
    generator())
    println())
    // prints "A 12-sided dice"

Similarly, the SnakesAndLadders game class can be
extended to adopt and conform to the TextRepresentable
protocol:

    extension:
    TextRepresentable {
        func {
            return
    "A game of Snakes and Ladders with 
        }
    }
    println())
    // prints "A game of Snakes and Ladders with 25 squares"

‌

### Declaring Protocol Adoption with an Extension 

If a type already conforms to all of the requirements of a protocol, but
has not yet stated that it adopts that protocol, you can make it adopt
the protocol with an empty extension:

    struct {
        var
        func {
            return
    "A hamster named 
        }
    }
    extension

Instances of Hamster can now be used wherever
TextRepresentable is the required type:

    let =
    Hamster)
    let:
    TextRepresentable
    println())
    // prints "A hamster named Simon"

Note

Types do not automatically adopt a protocol just by satisfying its
requirements. They must always explicitly declare their adoption of the
protocol.

‌

### Collections of Protocol Types 

A protocol can be used as the type to be stored in a collection such as
an array or a dictionary, as mentioned in [Protocols as
Types](Protocols.xhtml#TP40014097-CH25-XID_352). This example creates an
array of TextRepresentable things:

    let[] =
    [game]

It is now possible to iterate over the items in the array, and print
each item’s textual representation:

    for {
        println())
    }
    // A game of Snakes and Ladders with 25 squares
    // A 12-sided dice
    // A hamster named Simon

Note that the thing constant is of type
TextRepresentable,
or DiceGame, even if the
actual instance behind the scenes is of one of those types. Nonetheless,
because it is of type TextRepresentable, and anything
that is TextRepresentable is known to have an
asText method, it is safe to call
thing.asText each time through the loop.

‌

### Protocol Inheritance 

A protocol can *inherit* one or more other protocols and can add further
requirements on top of the requirements it inherits. The syntax for
protocol inheritance is similar to the syntax for class inheritance, but
with the option to list multiple inherited protocols, separated by
commas:

    protocol:
    SomeProtocol {
        // protocol definition goes here
    }

Here’s an example of a protocol that inherits the
TextRepresentable protocol from above:

    protocol:
    TextRepresentable {
        func
    }

This example defines a new protocol,
PrettyTextRepresentable, which inherits from
TextRepresentable. Anything that adopts
PrettyTextRepresentable must satisfy all of the
requirements enforced by TextRepresentable, *plus* the
additional requirements enforced by
PrettyTextRepresentable. In this example,
PrettyTextRepresentable adds a single requirement to
provide an instance method called asPrettyText that
returns a String.

The SnakesAndLadders class can be extended to adopt and
conform to PrettyTextRepresentable:

    extension:
    PrettyTextRepresentable {
        func {
            var() +
    ":\n"
            for
    1 {
                switch] {
                case
    where:
                    output
                case
    snake:
                    output
                default:
                    output
                }
            }
            return
        }
    }

This extension states that it adopts the
PrettyTextRepresentable protocol and provides an
implementation of the asPrettyText method for the
SnakesAndLadders type. Anything that is
PrettyTextRepresentable must also be
TextRepresentable
implementation starts by calling the asText method from
the TextRepresentable protocol to begin an output string.
It appends a colon and a line break, and uses this as the start of its
pretty text representation. It then iterates through the array of board
squares, and appends an emoji representation for each square:

-   If the square’s value is greater than 0, it is the
    base of a ladder, and is represented by ▲.

-   If the square’s value is less than 0, it is the head
    of a snake, and is represented by ▼.

-   Otherwise, the square’s value is 0, and it is a
    “free” square, represented by ○.

The method implementation can now be used to print a pretty text
description of any SnakesAndLadders instance:

    println())
    // A game of Snakes and Ladders with 25 squares:
    // ○ ○ ▲ ○ ○ ▲ ○ ○ ▲ ▲ ○ ○ ○ ▼ ○ ○ ○ ○ ▼ ○ ○ ▼ ○ ▼ ○

‌

### Protocol Composition 

It can be useful to require a type to conform to multiple protocols at
once. You can combine multiple protocols into a single requirement with
a *protocol composition*. Protocol compositions have the form
protocol<SomeProtocol, AnotherProtocol>. You can list as
many protocols within the pair of angle brackets (<>) as
you need, separated by commas.

Here’s an example that combines two protocols called
Named into a single protocol
composition requirement on a function parameter:

    protocol {
        var
    }
    protocol {
        var
    }
    struct {
        var
        var
    }
    func:
    protocol\>) {
        println)
    }
    let =
    Person)
    wishHappyBirthday)
    // prints "Happy birthday Malcolm - you're 21!"

This example defines a protocol called Named, with a
single requirement for a gettable String property called
name. It also defines a protocol called
Aged, with a single requirement for a gettable
Int. Both of these
protocols are adopted by a structure called Person.

The example also defines a function called
wishHappyBirthday, which takes a single parameter called
celebrator. The type of this parameter is
protocol<Named, Aged>, which means “any type that
conforms to both the Named
protocols.” It doesn’t matter what specific type is passed to the
function, as long as it conforms to both of the required protocols.

The example then creates a new Person instance called
birthdayPerson and passes this new instance to the
wishHappyBirthday
conforms to both protocols, this is a valid call, and the
wishHappyBirthday function is able to print its birthday
greeting.

Note

Protocol compositions do not define a new, permanent protocol type.
Rather, they define a temporary local protocol that has the combined
requirements of all protocols in the composition.

‌

### Checking for Protocol Conformance 

You can use the is operators
described in [Type Casting](TypeCasting.xhtml) to check for protocol
conformance, and to cast to a specific protocol. Checking for and
casting to a protocol follows exactly the same syntax as checking for
and casting to a type:

-   The is if an
    instance conforms to a protocol and returns false if
    it does not.

-   The as? version of the downcast operator returns an
    optional value of the protocol’s type, and this value is
    nil if the instance does not conform to that
    protocol.

-   The as version of the downcast operator forces the
    downcast to the protocol type and triggers a runtime error if the
    downcast does not succeed.

This example defines a protocol called HasArea, with a
single property requirement of a gettable Double property
called area:

    @objc {
        var
    }

Note

You can check for protocol conformance only if your protocol is marked
with the @objc attribute, as seen for the
HasArea protocol above. This attribute indicates that the
protocol should be exposed to Objective-C code and is described in
*Using Swift with Cocoa and Objective-C*. Even if you are not
interoperating with Objective-C, you need to mark your protocols with
the @objc attribute if you want to be able to check for
protocol conformance.

Note also that @objc protocols can be adopted only by
classes, and not by structures or enumerations. If you mark your
protocol as @objc in order to check for conformance, you
will be able to apply that protocol only to class types.

Here are two classes, Circle,
both of which conform to the HasArea protocol:

    class {
        let
        var
        var
    pi
        init) {
    self
    }
    class {
        var
        init) {
    self
    }

The Circle
property requirement as a computed property, based on a stored
radius class
implements the area requirement directly as a stored
property. Both classes correctly conform to the HasArea
protocol.

Here’s a class called Animal, which does not conform to
the HasArea protocol:

    class {
        var
        init) {
    self
    }

The Circle and
Animal classes do not have a shared base class.
Nonetheless, they are all classes, and so instances of all three types
can be used to initialize an array that stores values of type
AnyObject:

    let[] = [
        Circle),
        Country),
        Animal)
    ]

The objects array is initialized with an array literal
containing a Circle instance with a radius of 2 units; a
Country instance initialized with the surface area of the
United Kingdom in square kilometers; and an Animal
instance with four legs.

The objects array can now be iterated, and each object in
the array can be checked to see if it conforms to the
HasArea protocol:

    for {
        if =
    object {
            println)
        } else {
            println)
        }
    }
    // Area is 12.5663708
    // Area is 243610.0
    // Something that doesn't have an area

Whenever an object in the array conforms to the HasArea
protocol, the optional value returned by the as? operator
is unwrapped with optional binding into a constant called
objectWithArea
constant is known to be of type HasArea, and so its
area property can be accessed and printed in a type-safe
way.

Note that the underlying objects are not changed by the casting process.
They continue to be a Circle
and an Animal. However, at the point that they are stored
in the objectWithArea constant, they are only known to be
of type HasArea
property can be accessed.

‌

### Optional Protocol Requirements 

You can define *optional requirements* for protocols, These requirements
do not have to be implemented by types that conform to the protocol.
Optional requirements are prefixed by the @optional
keyword as part of the protocol’s definition.

An optional protocol requirement can be called with optional chaining,
to account for the possibility that the requirement was not implemented
by a type that conforms to the protocol. For information on optional
chaining, see [Optional Chaining](OptionalChaining.xhtml).

You check for an implementation of an optional requirement by writing a
question mark after the name of the requirement when it is called, such
as someOptionalMethod?(someArgument). Optional property
requirements, and optional method requirements that return a value, will
always return an optional value of the appropriate type when they are
accessed or called, to reflect the fact that the optional requirement
may not have been implemented.

Note

Optional protocol requirements can only be specified if your protocol is
marked with the @objc attribute. Even if you are not
interoperating with Objective-C, you need to mark your protocols with
the @objc attribute if you want to specify optional
requirements.

Note also that @objc protocols can be adopted only by
classes, and not by structures or enumerations. If you mark your
protocol as @objc in order to specify optional
requirements, you will only be able to apply that protocol to class
types.

The following example defines an integer-counting class called
Counter, which uses an external data source to provide
its increment amount. This data source is defined by the
CounterDataSource protocol, which has two optional
requirements:

    @objc {
        @optional
    incrementForCount
        @optional:
    Int
    }

The CounterDataSource protocol defines an optional method
requirement called incrementForCount and an optional
property requirement called fixedIncrement. These
requirements define two different ways for data sources to provide an
appropriate increment amount for a Counter instance.

Note

Strictly speaking, you can write a custom class that conforms to
CounterDataSource without implementing *either* protocol
requirement. They are both optional, after all. Although technically
allowed, this wouldn’t make for a very good data source.

The Counter class, defined below, has an optional
dataSource property of type
CounterDataSource?:

    @objc {
        var
        var?
        func() {
            if =
    dataSource) {
                count
            } else =
    dataSource? {
                count
            }
        }
    }

The Counter class stores its current value in a variable
property called count class
also defines a method called increment, which increments
the count property every time the method is called.

The increment method first tries to retrieve an increment
amount by looking for an implementation of the
incrementForCount method on its data source. The
increment method uses optional chaining to try to call
incrementForCount, and passes the current
count value as the method’s single argument.

Note *two* levels of optional chaining at play here. Firstly, it is
possible that dataSource, and
so dataSource has a question mark after its name to
indicate that incrementForCount should only be called if
dataSource is non-nil. Secondly, even if
dataSource *does* exist, there is no guarantee that it
implements incrementForCount, because it is an optional
requirement. This is why incrementForCount is also
written with a question mark after its name.

Because the call to incrementForCount can fail for either
of these two reasons, the call returns an *optional* Int
value. This is true even though incrementForCount is
defined as returning a non-optional Int value in the
definition of CounterDataSource.

After calling incrementForCount, the optional
Int that it returns is unwrapped into a constant called
amount, using optional binding. If the optional
Int does contain a value—that is, if the delegate and
method both exist, and the method returned a value—the unwrapped
amount
property, and incrementation is complete.

If it is *not* possible to retrieve a value from the
incrementForCount method—either because
dataSource is nil, or because the data source does not
implement incrementForCount—then the
increment method tries to retrieve a value from the data
source’s fixedIncrement property instead. The
fixedIncrement property is also an optional requirement,
and so its name is also written using optional chaining with a question
mark on the end, to indicate that the attempt to access the property’s
value can fail. As before, the returned value is an optional
Int is
defined as a non-optional Int property as part of the
CounterDataSource protocol definition.

Here’s a simple CounterDataSource implementation where
the data source returns a constant value of 3 every time
it is queried. It does this by implementing the optional
fixedIncrement property requirement:

    class {
        let
    }

You can use an instance of ThreeSource as the data source
for a new Counter instance:

    var()
    counter()
    for {
        counter()
        println)
    }
    // 3
    // 6
    // 9
    // 12

The code above creates a new Counter instance; sets its
data source to be a new ThreeSource instance; and calls
the counter’s increment method four times. As expected,
the counter’s count property increases by three each time
increment is called.

Here’s a more complex data source called
TowardsZeroSource
instance count up or down towards zero from its current
count value:

    class:
    CounterDataSource {
        func:
    Int {
            if {
                return
            } else {
                return
            } else {
                return
            }
        }
    }

The TowardsZeroSource class implements the optional
incrementForCount method from the
CounterDataSource protocol and uses the
count argument value to work out which direction to count
in. If count is already zero, the method returns
0 to indicate that no further counting should take place.

You can use an instance of TowardsZeroSource with the
existing Counter
to zero. Once the counter reaches zero, no more counting takes place:

    counter
    counter =
    TowardsZeroSource()
    for {
        counter()
        println)
    }
    // -3
    // -2
    // -1
    // 0
    // 0
