‌‌

Type Casting 
------------

*Type casting* is a way to check the type of an instance, and/or to
treat that instance as if it is a different superclass or subclass from
somewhere else in its own class hierarchy.

Type casting in Swift is implemented with the is and
as operators. These two operators provide a simple and
expressive way to check the type of a value or cast a value to a
different type.

You can also use type casting to check whether a type conforms to a
protocol, as described in [Checking for Protocol
Conformance](Protocols.xhtml#TP40014097-CH25-XID_363).

‌

### Defining a Class Hierarchy for Type Casting 

You can use type casting with a hierarchy of classes and subclasses to
check the type of a particular class instance and to cast that instance
to another class within the same hierarchy. The three code snippets
below define a hierarchy of classes and an array containing instances of
those classes, for use in an example of type casting.

The first snippet defines a new base class called
MediaItem. This class provides basic functionality for
any kind of item that appears in a digital media library. Specifically,
it declares a name property of type
String initializer. (It
is assumed that all media items, including all movies and songs, will
have a name.)

    class {
        var
        init) {
            self
        }
    }

The next snippet defines two subclasses of MediaItem. The
first subclass, Movie, encapsulates additional
information about a movie or film. It adds a director
property on top of the base MediaItem class, with a
corresponding initializer. The second subclass, Song,
adds an artist property and initializer on top of the
base class:

    class {
        var
        init:
    String) {
            self
            super)
        }
    }
     
    class {
        var
        init:
    String) {
            self
            super)
        }
    }

The final snippet creates a constant array called
library
instances and three Song instances. The type of the
library array is inferred by initializing it with the
contents of an array literal. Swift’s type checker is able to deduce
that Movie have a common
superclass of MediaItem, and so it infers a type of
MediaItem[] array:

    let = [
        Movie,
    director),
        Song,
    artist),
        Movie,
    director),
        Song,
    artist),
        Song:
    "Never Gonna Give You Up")
    ]
    // the type of "library" is inferred to be MediaItem[]

The items stored in library are still
Movie instances behind the
scenes. However, if you iterate over the contents of this array, the
items you receive back are typed as MediaItem, and not as
Movie. In order to work with them
as their native type, you need to *check* their type, or *downcast* them
to a different type, as described below.

‌

### Checking Type 

Use the *type check operator* (is) to check whether an
instance is of a certain subclass type. The type check operator returns
true if the instance is of that subclass type and
false if it is not.

The example below defines two variables, movieCount and
songCount
and Song array:

    var
    var
     
    for {
        if {
            ++movieCount
        } else
    {
            ++songCount
        }
    }
     
    println)
    // prints "Media library contains 2 movies and 3 songs"

This example iterates through all items in the library
array. On each pass, the for loop sets
the item in
the array.

item is Movie if the current
MediaItem instance and
false if it is not. Similarly,
item is Song checks whether the item is a
Song instance. At the end of the
for loop, the values of
movieCount contain a count
of how many MediaItem instances were found of each type.

‌

### Downcasting 

A constant or variable of a certain class type may actually refer to an
instance of a subclass behind the scenes. Where you believe this is the
case, you can try to *downcast* to the subclass type with the *type cast
operator* (as).

Because downcasting can fail, the type cast operator comes in two
different forms. The optional form, as?, returns an
optional value of the type you are trying to downcast to. The forced
form, as, attempts the downcast and force-unwraps the
result as a single compound action.

Use the optional form of the type cast operator (as?)
when you are not sure if the downcast will succeed. This form of the
operator will always return an optional value, and the value will be
nil if the downcast was not possible. This enables you to
check for a successful downcast.

Use the forced form of the type cast operator (as) only
when you are sure that the downcast will always succeed. This form of
the operator will trigger a runtime error if you try to downcast to an
incorrect class type.

The example below iterates over each MediaItem in
library, and prints an appropriate description for each
item. To do this, it needs to access each item as a true
Movie, and not just as a
MediaItem. This is necessary in order for it to be able
to access the director property
of a Movie for use in the
description.

In this example, each item in the array might be a Movie,
or it might be a Song. You don’t know in advance which
actual class to use for each item, and so it is appropriate to use the
optional form of the type cast operator (as?) to check
the downcast each time through the loop:

    for {
        if
    as {
            println)
        } else =
    item {
            println)
        }
    }
     
    // Movie: 'Casablanca', dir. Michael Curtiz
    // Song: 'Blue Suede Shoes', by Elvis Presley
    // Movie: 'Citizen Kane', dir. Orson Welles
    // Song: 'The One And Only', by Chesney Hawkes
    // Song: 'Never Gonna Give You Up', by Rick Astley

The example starts by trying to downcast the current item
as a Movie is a
MediaItem instance, it’s possible that it *might* be a
Movie; equally, it’s also possible that it might a
Song.
Because of this uncertainty, the as? form of the type
cast operator returns an *optional* value when attempting to downcast to
a subclass type. The result of item as Movie is of type
Movie?”.

Downcasting to Movie fails when applied to the two
Song instances in the library array. To cope with this,
the example above uses optional binding to check whether the optional
Movie actually contains a value (that is, to find out
whether the downcast succeeded.) This optional binding is written
“if let movie = item as? Movie”, which can be read as:

“Try to access item. If this is
successful, set a new temporary constant called movie to
the value stored in the returned optional Movie.”

If the downcasting succeeds, the properties of movie are
then used to print a description for that Movie instance,
including the name of its director. A similar principle
is used to check for Song instances, and to print an
appropriate description (including artist name) whenever
a Song is found in the library.

Note

Casting does not actually modify the instance or change its values. The
underlying instance remains the same; it is simply treated and accessed
as an instance of the type to which it has been cast.

‌

### Type Casting for Any and AnyObject 

Swift provides two special type aliases for working with non-specific
types:

    AnyObject can represent an instance of any class
    type.

    Any can represent an instance of any type at all,
    apart from function types.

Note

Use Any only when you
explicitly need the behavior and capabilities they provide. It is always
better to be specific about the types you expect to work with in your
code.

‌

### AnyObject 

When working with Cocoa APIs, it is common to receive an array with a
type of AnyObject[], or “an array of values of any object
type”. This is because Objective-C does not have explicitly typed
arrays. However, you can often be confident about the type of objects
contained in such an array just from the information you know about the
API that provided the array.

In these situations, you can use the forced version of the type cast
operator (as) to downcast each item in the array to a
more specific class type than AnyObject, without the need
for optional unwrapping.

The example below defines an array of type AnyObject[]
and populates this array with three instances of the
Movie class:

    let[] = [
        Movie,
    director),
        Movie:
    "Duncan Jones"),
        Movie,
    director)
    ]

Because this array is known to contain only Movie
instances, you can downcast and unwrap directly to a non-optional
Movie with the forced version of the type cast operator
(as):

    for {
        let
    Movie
        println)
    }
    // Movie: '2001: A Space Odyssey', dir. Stanley Kubrick
    // Movie: 'Moon', dir. Duncan Jones
    // Movie: 'Alien', dir. Ridley Scott

For an even shorter form of this loop, downcast the
someObjects
instead of downcasting each item:

    for
    as[] {
        println)
    }
    // Movie: '2001: A Space Odyssey', dir. Stanley Kubrick
    // Movie: 'Moon', dir. Duncan Jones
    // Movie: 'Alien', dir. Ridley Scott

‌

### Any 

Here’s an example of using Any to work with a mix of
different types, including non-class types. The example creates an array
called things, which can store values of type
Any:

    var[]()
     
    things)
    things)
    things)
    things)
    things)
    things))
    things:
    "Ghostbusters"))

The things values,
two Double value, a tuple
of type (Double, Double), and the movie “Ghostbusters”,
directed by Ivan Reitman.

You can use the is operators in a
switch statement’s cases to discover the specific type of
a constant or variable that is known only to be of type
Any. The example below
iterates over the items in the things array and queries
the type of each item with a switch statement. Several of
the switch statement’s cases bind their matched value to
a constant of the specified type to enable its value to be printed:

    for {
        switch {
        case:
            println)
        case:
            println)
        case
    Int:
            println)
        case
    Double:
            println)
        case:
            println)
        case
    String:
            println)
        case
    (Double):
            println)
        case
    Movie:
            println)
        default:
            println)
        }
    }
     
    // zero as an Int
    // zero as a Double
    // an integer value of 42
    // a positive double value of 3.14159
    // a string value of "hello"
    // an (x, y) point at 3.0, 5.0
    // a movie called 'Ghostbusters', dir. Ivan Reitman

Note

The cases of a switch statement use the forced version of
the type cast operator (as) to
check and cast to a specific type. This check is always safe within the
context of a switch case statement.
