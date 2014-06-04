‌‌

Methods 
-------

*Methods* are functions that are associated with a particular type.
Classes, structures, and enumerations can all define instance methods,
which encapsulate specific tasks and functionality for working with an
instance of a given type. Classes, structures, and enumerations can also
define type methods, which are associated with the type itself. Type
methods are similar to class methods in Objective-C.

The fact that structures and enumerations can define methods in Swift is
a major difference from C and Objective-C. In Objective-C, classes are
the only types that can define methods. In Swift, you can choose whether
to define a class, structure, or enumeration, and still have the
flexibility to define methods on the type you create.

‌

### Instance Methods 

*Instance methods* are functions that belong to instances of a
particular class, structure, or enumeration. They support the
functionality of those instances, either by providing ways to access and
modify instance properties, or by providing functionality related to the
instance’s purpose. Instance methods have exactly the same syntax as
functions, as described in [Functions](Functions.xhtml).

You write an instance method within the opening and closing braces of
the type it belongs to. An instance method has implicit access to all
other instance methods and properties of that type. An instance method
can be called only on a specific instance of the type it belongs to. It
cannot be called in isolation without an existing instance.

Here’s an example that defines a simple Counter class,
which can be used to count the number of times an action occurs:


class {
    var
    func() {
            count++
        }
        func)
    {
            count
        }
        func() {
            count
        }
    }
｀｀｀

The Counter class defines three instance methods:

    increment.

    incrementBy(amount: Int) increments the counter by an
    specified integer amount.

    reset resets the counter to zero.

The Counter class also declares a variable property,
count, to keep track of the current counter value.

You call instance methods with the same dot syntax as properties:


let()
// the initial counter value is 0
counter()
// the counter's value is now 1
 counter)
    // the counter's value is now 6
    counter()
    // the counter's value is now 0

‌

### Local and External Parameter Names for Methods 

Function parameters can have both a local name (for use within the
function’s body) and an external name (for use when calling the
function), as described in [External Parameter
Names](Functions.xhtml#TP40014097-CH10-XID_214). The same is true for
method parameters, because methods are just functions that are
associated with a type. However, the default behavior of local names and
external names is different for functions and methods.

Methods in Swift are very similar to their counterparts in Objective-C.
As in Objective-C, the name of a method in Swift typically refers to the
method’s first parameter using a preposition such as
with, as seen
in the incrementBy method from the preceding
Counter class example. The use of a preposition enables
the method to be read as a sentence when it is called. Swift makes this
established method naming convention easy to write by using a different
default approach for method parameters than it uses for function
parameters.

Specifically, Swift gives the *first* parameter name in a method a local
parameter name by default, and gives the second and subsequent parameter
names both local *and* external parameter names by default. This
convention matches the typical naming and calling convention you will be
familiar with from writing Objective-C methods, and makes for expressive
method calls without the need to qualify your parameter names.

Consider this alternative version of the Counter class,
which defines a more complex form of the incrementBy
method:

    class {
        var
        func,
    numberOfTimes) {
            count \*
    numberOfTimes
        }
    }

This incrementBy method has two
parameters—amount. By
default, Swift treats amount as a local name only, but
treats numberOfTimes as both a local *and* an external
name. You call the method as follows:

    let()
    counter,
    numberOfTimes)
    // counter value is now 15

You don’t need to define an external parameter name for the first
argument value, because its purpose is clear from the function name
incrementBy. The second argument, however, is qualified
by an external parameter name to make its purpose clear when the method
is called.

This default behavior effectively treats the method as if you had
written a hash symbol (#) before the
numberOfTimes parameter:

    func,
    \#numberOfTimes) {
        count
    }

The default behavior described above mean that method definitions in
Swift are written with the same grammatical style as Objective-C, and
are called in a natural, expressive way.

‌

### Modifying External Parameter Name Behavior for Methods 

Sometimes it’s useful to provide an external parameter name for a
method’s first parameter, even though this is not the default behavior.
You can either add an explicit external name yourself, or you can prefix
the first parameter’s name with a hash symbol to use the local name as
an external name too.

Conversely, if you do not want to provide an external name for the
second or subsequent parameter of a method, override the default
behavior by using an underscore character (_) as an
explicit external parameter name for that parameter.

‌

### The self Property 

Every instance of a type has an implicit property called
self, which is exactly equivalent to the instance itself.
You use this implicit self property to refer to the
current instance within its own instance methods.

The increment method in the example above could have been
written like this:

    func() {
        self++
    }

In practice, you don’t need to write self in your code
very often. If you don’t explicitly write self, Swift
assumes that you are referring to a property or method of the current
instance whenever you use a known property or method name within a
method. This assumption is demonstrated by the use of
count) inside the
three instance methods for Counter.

The main exception to this rule occurs when a parameter name for an
instance method has the same name as a property of that instance. In
this situation, the parameter name takes precedence, and it becomes
necessary to refer to the property in a more qualified way. You use the
implicit self property to distinguish between the
parameter name and the property name.

Here, self disambiguates between a method parameter
called x and an instance property that is also called
x:

    struct {
        var
        func:
    Double {
            return
        }
    }
    let:
    4.0)
    if)
    {
        println)
    }
    // prints "This point is to the right of the line where x == 1.0"

Without the self prefix, Swift would assume that both
uses of x referred to the method parameter called
x.

‌

### Modifying Value Types from Within Instance Methods 

Structures and enumerations are *value types*. By default, the
properties of a value type cannot be modified from within its instance
methods.

However, if you need to modify the properties of your structure or
enumeration within a particular method, you can opt in to *mutating*
behavior for that method. The method can then mutate (that is, change)
its properties from within the method, and any changes that it makes are
written back to the original structure when the method ends. The method
can also assign a completely new instance to its implicit
self property, and this new instance will replace the
existing one when the method ends.

You can opt in to this behavior by placing the mutating
keyword before the func keyword for that method:

    struct {
        var
        mutating
    moveByX:
    Double) {
            x
            y
        }
    }
    var:
    1.0)
    somePoint:
    3.0)
    println)
    // prints "The point is now at (3.0, 4.0)"

The Point structure above defines a mutating
moveByX
instance by a certain amount. Instead of returning a new point, this
method actually modifies the point on which it is called. The
mutating keyword is added to its definition to enable it
to modify its properties.

Note that you cannot call a mutating method on a constant of structure
type, because its properties cannot be changed, even if they are
variable properties, as described in [Stored Properties of Constant
Structure Instances](Properties.xhtml#TP40014097-CH14-XID_325):

    let:
    3.0)
    fixedPoint:
    3.0)
    // this will report an error

‌

### Assigning to self Within a Mutating Method 

Mutating methods can assign an entirely new instance to the implicit
self example shown
above could have been written in the following way instead:

    struct {
        var
        mutating
    moveByX:
    Double) {
            self +
    deltaX)
        }
    }

This version of the mutating moveByX method creates a
brand new structure whose x values
are set to the target location. The end result of calling this
alternative version of the method will be exactly the same as for
calling the earlier version.

Mutating methods for enumerations can set the implicit
self parameter to be a different member from the same
enumeration:

    enum {
        case
        mutating() {
            switch {
            case:
                self
            case:
                self
            case:
                self
            }
        }
    }
    var =
    TriStateSwitch
    ovenLight()
    // ovenLight is now equal to .High
    ovenLight()
    // ovenLight is now equal to .Off

This example defines an enumeration for a three-state switch. The switch
cycles between three different power states (Off,
Low) every time its
next method is called.

‌

### Type Methods 

Instance methods, as described above, are methods that are called on an
instance of a particular type. You can also define methods that are
called on the type itself. These kinds of methods are called *type
methods*. You indicate type methods for classes by writing the keyword
class keyword,
and type methods for structures and enumerations by writing the keyword
static keyword.

Note

In Objective-C, you can define type-level methods only for Objective-C
classes. In Swift, you can define type-level methods for all classes,
structures, and enumerations. Each type method is explicitly scoped to
the type it supports.

Type methods are called with dot syntax, like instance methods. However,
you call type methods on the type, not on an instance of that type.
Here’s how you call a type method on a class called
SomeClass:

    class {
        class() {
            // type method implementation goes here
        }
    }
    SomeClass()

Within the body of a type method, the implicit self
property refers to the type itself, rather than an instance of that
type. For structures and enumerations, this means that you can use
self to disambiguate between static properties and static
method parameters, just as you do for instance properties and instance
method parameters.

More generally, any unqualified method and property names that you use
within the body of a type method will refer to other type-level methods
and properties. A type method can call another type method with the
other method’s name, without needing to prefix it with the type name.
Similarly, type methods on structures and enumerations can access static
properties by using the static property’s name without a type name
prefix.

The example below defines a structure called
LevelTracker, which tracks a player’s progress through
the different levels or stages of a game. It is a single-player game,
but can store information for multiple players on a single device.

All of the game’s levels (apart from level one) are locked when the game
is first played. Every time a player finishes a level, that level is
unlocked for all players on the device. The LevelTracker
structure uses static properties and methods to keep track of which
levels of the game have been unlocked. It also tracks the current level
for an individual player.

    struct {
        static =
    1
        static
    unlockLevel) {
            if \>
    highestUnlockedLevel =
    level
        }
        static
    levelIsUnlocked {
            return \<=
    highestUnlockedLevel
        }
        var
        mutating
    advanceToLevel {
            if
    LevelTracker) {
                currentLevel
                return
            } else {
                return
            }
        }
    }

The LevelTracker structure keeps track of the highest
level that any player has unlocked. This value is stored in a static
property called highestUnlockedLevel.

LevelTracker also defines two type functions to work with
the highestUnlockedLevel property. The first is a type
function called unlockLevel, which updates the value of
highestUnlockedLevel whenever a new level is unlocked.
The second is a convenience type function called
levelIsUnlocked if a
particular level number is already unlocked. (Note that these type
methods can access the highestUnlockedLevel static
property without your needing to write it as
LevelTracker.highestUnlockedLevel.)

In addition to its static property and type methods,
LevelTracker tracks an individual player’s progress
through the game. It uses an instance property called
currentLevel to track the level that a player is
currently playing.

To help manage the currentLevel property,
LevelTracker defines an instance method called
advanceToLevel. Before updating
currentLevel, this method checks whether the requested
new level is already unlocked. The advanceToLevel method
returns a Boolean value to indicate whether or not it was actually able
to set currentLevel.

The LevelTracker structure is used with the
Player class, shown below, to track and update the
progress of an individual player:

    class {
        var()
        let
        func:
    Int) {
            LevelTracker
    + 1)
            tracker +
    1)
        }
        init) {
            playerName
        }
    }

The Player class creates a new instance of
LevelTracker to track that player’s progress. It also
provides a method called completedLevel, which is called
whenever a player completes a particular level. This method unlocks the
next level for all players and updates the player’s progress to move
them to the next level. (The Boolean return value of
advanceToLevel is ignored, because the level is known to
have been unlocked by the call to
LevelTracker.unlockLevel on the previous line.)

You can create a instance of the Player class for a new
player, and see what happens when the player completes level one:

    var:
    "Argyrios")
    player)
    println)
    // prints "highest unlocked level is now 2"

If you create a second player, whom you try to move to a level that is
not yet unlocked by any player in the game, the attempt to set the
player’s current level fails:

    player)
    if
    player) {
        println)
    } else {
        println)
    }
    // prints "level 6 has not yet been unlocked"
