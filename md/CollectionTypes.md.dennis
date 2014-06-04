‌‌

Collection Types 
----------------

Swift provides two *collection types*, known as arrays and dictionaries,
for storing collections of values. Arrays store ordered lists of values
of the same type. Dictionaries store unordered collections of values of
the same type, which can be referenced and looked up through a unique
identifier (also known as a key).

Arrays and dictionaries in Swift are always clear about the types of
values and keys that they can store. This means that you cannot insert a
value of the wrong type into an array or dictionary by mistake. It also
means you can be confident about the types of values you will retrieve
from an array or dictionary. Swift’s use of explicitly typed collections
ensures that your code is always clear about the types of values it can
work with and enables you to catch any type mismatches early in your
code’s development.

Note

Swift’s Array type exhibits different behavior to other
types when assigned to a constant or variable, or when passed to a
function or method. For more information, see [Mutability of
Collections](CollectionTypes.xhtml#TP40014097-CH8-XID_151) and
[Assignment and Copy Behavior for Collection
Types](ClassesAndStructures.xhtml#TP40014097-CH13-XID_109).

‌

### Arrays 

An *array* stores multiple values of the same type in an ordered list.
The same value can appear in an array multiple times at different
positions.

Swift arrays are specific about the kinds of values they can store. They
differ from Objective-C’s NSArray and
NSMutableArray classes, which can store any kind of
object and do not provide any information about the nature of the
objects they return. In Swift, the type of values that a particular
array can store is always made clear, either through an explicit type
annotation, or through type inference, and does not have to be a class
type. If you create an array of Int values, for example,
you can’t insert any value other than Int values into
that array. Swift arrays are type safe, and are always clear about what
they may contain.

‌

### Array Type Shorthand Syntax 

The type of a Swift array is written in full as
Array<SomeType> is the
type that the array is allowed to store. You can also write the type of
an array in shorthand form as SomeType[]. Although the
two forms are functionally identical, the shorthand form is preferred,
and is used throughout this guide when referring to the type of an
array.

‌

### Array Literals 

You can initialize an array with an *array literal*, which is a
shorthand way to write one or more values as an array collection. An
array literal is written as a list of values, separated by commas,
surrounded by a pair of square brackets:

-   ~~~~ 
    [value 1, value 2, value 3]
    ~~~~

The example below creates an array called shoppingList to
store String values:

    var[] =
    ["Eggs"]
    // shoppingList has been initialized with two initial items

The shoppingList variable is declared as “an array of
String.
Because this particular array has specified a value type of
String, it is *only* allowed to store
String
array is initialized with two String values
("Eggs"), written within an
array literal.

Note

The shoppingList array is declared as a variable (with
the var introducer) and not a constant (with the
let introducer) because more items are added to the
shopping list in the examples below.

In this case, the array literal contains two String
values and nothing else. This matches the type of the
shoppingList variable’s declaration (an array that can
only contain String values), and so the assignment of the
array literal is permitted as a way to initialize
shoppingList with two initial items.

Thanks to Swift’s type inference, you don’t have to write the type of
the array if you’re initializing it with an array literal containing
values of the same type. The initialization of
shoppingList could have been written in a shorter form
instead:

    var,
    "Milk"]

Because all values in the array literal are of the same type, Swift can
infer that String[] is the correct type to use for the
shoppingList variable.

‌

### Accessing and Modifying an Array 

You access and modify an array through its methods and properties, or by
using subscript syntax.

To find out the number of items in an array, check its read-only
count property:

    println)
    // prints "The shopping list contains 2 items."

Use the Boolean isEmpty property as a shortcut for
checking whether the count property is equal to
0:

    if {
        println)
    } else {
        println)
    }
    // prints "The shopping list is not empty."

You can add a new item to the end of an array by calling the array’s
append method:

    shoppingList)
    // shoppingList now contains 3 items, and someone is making pancakes

Alternatively, add a new item to the end of an array with the addition
assignment operator (+=):

    shoppingList
    // shoppingList now contains 4 items

You can also append an array of compatible items with the addition
assignment operator (+=):

    shoppingList,
    "Cheese"]
    // shoppingList now contains 7 items

Retrieve a value from the array by using *subscript syntax*, passing the
index of the value you want to retrieve within square brackets
immediately after the name of the array:

    var]
    // firstItem is equal to "Eggs"

Note that the first item in the array has an index of 0,
not 1. Arrays in Swift are always zero-indexed.

You can use subscript syntax to change an existing value at a given
index:

    shoppingList
    // the first item in the list is now equal to "Six eggs" rather than "Eggs"

You can also use subscript syntax to change a range of values at once,
even if the replacement set of values has a different length than the
range you are replacing. The following example replaces
"Chocolate Spread", and
"Butter" and
"Apples":

    shoppingList,
    "Apples"]
    // shoppingList now contains 6 items

Note

You can’t use subscript syntax to append a new item to the end of an
array. If you try to use subscript syntax to retrieve or set a value for
an index that is outside of an array’s existing bounds, you will trigger
a runtime error. However, you can check that an index is valid before
using it, by comparing it to the array’s count property.
Except when count (meaning the array
is empty), the largest valid index in an array will always be
count - 1, because arrays are indexed from zero.

To insert an item into the array at a specified index, call the array’s
insert(atIndex:) method:

    shoppingList,
    atIndex)
    // shoppingList now contains 7 items
    // "Maple Syrup" is now the first item in the list

This call to the insert method inserts a new item with a
value of "Maple Syrup" at the very beginning of the
shopping list, indicated by an index of 0.

Similarly, you remove an item from the array with the
removeAtIndex method. This method removes the item at the
specified index and returns the removed item (although you can ignore
the returned value if you do not need it):

    let =
    shoppingList)
    // the item that was at index 0 has just been removed
    // shoppingList now contains 6 items, and no Maple Syrup
    // the mapleSyrup constant is now equal to the removed "Maple Syrup" string

Any gaps in an array are closed when an item is removed, and so the
value at index 0 is once again equal to
"Six eggs":

    firstItem]
    // firstItem is now equal to "Six eggs"

If you want to remove the final item from an array, use the
removeLast method rather than the
removeAtIndex method to avoid the need to query the
array’s count property. Like the
removeAtIndex returns
the removed item:

    let =
    shoppingList()
    // the last item in the array has just been removed
    // shoppingList now contains 5 items, and no cheese
    // the apples constant is now equal to the removed "Apples" string

‌

### Iterating Over an Array 

You can iterate over the entire set of values in an array with the
for loop:

    for {
        println)
    }
    // Six eggs
    // Milk
    // Flour
    // Baking Powder
    // Bananas

If you need the integer index of each item as well as its value, use the
global enumerate function to iterate over the array
instead. The enumerate function returns a tuple for each
item in the array composed of the index and the value for that item. You
can decompose the tuple into temporary constants or variables as part of
the iteration:

    for
    enumerate) {
        println +
    1)
    }
    // Item 1: Six eggs
    // Item 2: Milk
    // Item 3: Flour
    // Item 4: Baking Powder
    // Item 5: Bananas

For more about the for loop, see [For
Loops](ControlFlow.xhtml#TP40014097-CH9-XID_154).

‌

### Creating and Initializing an Array 

You can create an empty array of a certain type (without setting any
initial values) using initializer syntax:

    var[]()
    println)
    // prints "someInts is of type Int[] with 0 items."

Note that the type of the someInts variable is inferred
to be Int[], because it is set to the output of an
Int[] initializer.

Alternatively, if the context already provides type information, such as
a function argument or an already-typed variable or constant, you can
create an empty array with an empty array literal, which is written as
[] (an empty pair of square brackets):

    someInts)
    // someInts now contains 1 value of type Int
    someInts = []
    // someInts is now an empty array, but is still of type Int[]

Swift’s Array type also provides an initializer for
creating an array of a certain size with all of its values set to a
provided default value. You pass this initializer the number of items to
be added to the new array (called count) and a default
value of the appropriate type (called repeatedValue):

    var =
    Double:
    0.0)
    // threeDoubles is of type Double[], and equals [0.0, 0.0, 0.0]

Thanks to type inference, you don’t need to specify the type to be
stored in the array when using this initializer, because it can be
inferred from the default value:

    var =
    Array)
    // anotherThreeDoubles is inferred as Double[], and equals [2.5, 2.5, 2.5]

Finally, you can create a new array by adding together two existing
arrays of compatible type with the addition operator (+).
The new array’s type is inferred from the type of the two arrays you add
together:

    var +
    anotherThreeDoubles
    // sixDoubles is inferred as Double[], and equals [0.0, 0.0, 0.0, 2.5, 2.5, 2.5]

‌

### Dictionaries 

A *dictionary* is a container that stores multiple values of the same
type. Each value is associated with a unique *key*, which acts as an
identifier for that value within the dictionary. Unlike items in an
array, items in a dictionary do not have a specified order. You use a
dictionary when you need to look up values based on their identifier, in
much the same way that a real-world dictionary is used to look up the
definition for a particular word.

Swift dictionaries are specific about the types of keys and values they
can store. They differ from Objective-C’s NSDictionary
and NSMutableDictionary classes, which can use any kind
of object as their keys and values and do not provide any information
about the nature of these objects. In Swift, the type of keys and values
that a particular dictionary can store is always made clear, either
through an explicit type annotation or through type inference.

Swift’s dictionary type is written as
Dictionary<KeyType, ValueType>, where
KeyType is the type of value that can be used as a
dictionary key, and ValueType is the type of value that
the dictionary stores for those keys.

The only restriction is that KeyType must be
*hashable*—that is, it must provide a way to make itself uniquely
representable. All of Swift’s basic types (such as
String, and
Bool) are hashable by default, and all of these types can
be used as the keys of a dictionary. Enumeration member values without
associated values (as described in [Enumerations](Enumerations.xhtml))
are also hashable by default.

‌

### Dictionary Literals 

You can initialize a dictionary with with a *dictionary literal*, which
has a similar syntax to the array literal seen earlier. A dictionary
literal is a shorthand way to write one or more key-value pairs as a
Dictionary collection.

A *key-value pair* is a combination of a key and a value. In a
dictionary literal, the key and value in each key-value pair are
separated by a colon. The key-value pairs are written as a list,
separated by commas, surrounded by a pair of square brackets:

-   ~~~~ 
    [key 1: value 1, key 2: value 2, key 3: value 3]
    ~~~~

The example below creates a dictionary to store the names of
international airports. In this dictionary, the keys are three-letter
International Air Transport Association codes, and the values are
airport names:

    var,
    String:
    "Dublin"]

The airports dictionary is declared as having a type of
Dictionary<String, String>, which means “a
Dictionary,
and whose values are also of type String”.

Note

The airports dictionary is declared as a variable (with
the var introducer), and not a constant (with the
let introducer), because more airports will be added to
the dictionary in the examples below.

The airports dictionary is initialized with a dictionary
literal containing two key-value pairs. The first pair has a key of
"TYO". The second
pair has a key of "DUB" and a value of
"Dublin".

This dictionary literal contains two String: String
pairs. This matches the type of the airports variable
declaration (a dictionary with only String keys, and only
String values) and so the assignment of the dictionary
literal is permitted as a way to initialize the airports
dictionary with two initial items.

As with arrays, you don’t have to write the type of the dictionary if
you’re initializing it with a dictionary literal whose keys and values
have consistent types. The initialization of airports
could have been be written in a shorter form instead:

    var,
    "DUB"]

Because all keys in the literal are of the same type as each other, and
likewise all values are of the same type as each other, Swift can infer
that Dictionary<String, String> is the correct type to
use for the airports dictionary.

‌

### Accessing and Modifying a Dictionary 

You access and modify a dictionary through its methods and properties,
or by using subscript syntax. As with an array, you can find out the
number of items in a Dictionary by checking its read-only
count property:

    println)
    // prints "The dictionary of airports contains 2 items."

You can add a new item to a dictionary with subscript syntax. Use a new
key of the appropriate type as the subscript index, and assign a new
value of the appropriate type:

    airports
    // the airports dictionary now contains 3 items

You can also use subscript syntax to change the value associated with a
particular key:

    airports
    // the value for "LHR" has been changed to "London Heathrow"

As an alternative to subscripting, use a dictionary’s
updateValue(forKey:) method to set or update the value
for a particular key. Like the subscript examples above, the
updateValue(forKey:) method sets a value for a key if
none exists, or updates the value if that key already exists. Unlike a
subscript, however, the updateValue(forKey:) method
returns the *old* value after performing an update. This enables you to
check whether or not an update took place.

The updateValue(forKey:) method returns an optional value
of the dictionary’s value type. For a dictionary that stores
String values, for example, the method returns a value of
type String?”. This
optional value contains the old value for that key if one existed before
the update, or nil if no value existed:

    if =
    airports,
    forKey) {
        println)
    }
    // prints "The old value for DUB was Dublin."

You can also use subscript syntax to retrieve a value from the
dictionary for a particular key. Because it is possible to request a key
for which no value exists, a dictionary’s subscript returns an optional
value of the dictionary’s value type. If the dictionary contains a value
for the requested key, the subscript returns an optional value
containing the existing value for that key. Otherwise, the subscript
returns nil:

    if =
    airports] {
        println)
    } else {
        println)
    }
    // prints "The name of the airport is Dublin International."

You can use subscript syntax to remove a key-value pair from a
dictionary by assigning a value of nil for that key:

    airports
    // "Apple International" is not the real airport for APL, so delete it
    airports
    // APL has now been removed from the dictionary

Alternatively, remove a key-value pair from a dictionary with the
removeValueForKey method. This method removes the
key-value pair if it exists and returns the removed value, or returns
nil if no value existed:

    if =
    airports) {
        println)
    } else {
        println)
    }
    // prints "The removed airport's name is Dublin International."

‌

### Iterating Over a Dictionary 

You can iterate over the key-value pairs in a dictionary with a
for loop. Each item in the dictionary
is returned as a (key, value) tuple, and you can
decompose the tuple’s members into temporary constants or variables as
part of the iteration:

    for)
    in {
        println)
    }
    // TYO: Tokyo
    // LHR: London Heathrow

For more about the for loop, see [For
Loops](ControlFlow.xhtml#TP40014097-CH9-XID_154).

You can also retrieve an iteratable collection of a dictionary’s keys or
values by accessing its keys
properties:

    for
    airports {
        println)
    }
    // Airport code: TYO
    // Airport code: LHR
     
    for
    airports {
        println)
    }
    // Airport name: Tokyo
    // Airport name: London Heathrow

If you need to use a dictionary’s keys or values with an API that takes
an Array instance, initialize a new array with the
keys property:

    let =
    Array)
    // airportCodes is ["TYO", "LHR"]
     
    let =
    Array)
    // airportNames is ["Tokyo", "London Heathrow"]

Note

Swift’s Dictionary type is an unordered collection. The
order in which keys, values, and key-value pairs are retrieved when
iterating over a dictionary is not specified.

‌

### Creating an Empty Dictionary 

As with arrays, you can create an empty Dictionary of a
certain type by using initializer syntax:

    var =
    Dictionary\>()
    // namesOfIntegers is an empty Dictionary<Int, String>

This example creates an empty dictionary of type Int,
String to store human-readable names of integer values.
Its keys are of type Int, and its values are of type
String.

If the context already provides type information, create an empty
dictionary with an empty dictionary literal, which is written as
[:] (a colon inside a pair of square brackets):

    namesOfIntegers
    // namesOfIntegers now contains 1 key-value pair
    namesOfIntegers = [:]
    // namesOfIntegers is once again an empty dictionary of type Int, String

Note

Behind the scenes, Swift’s array and dictionary types are implemented as
*generic collections*. For more on generic types and collections, see
[Generics](Generics.xhtml).

‌

### Mutability of Collections 

Arrays and dictionaries store multiple values together in a single
collection. If you create an array or a dictionary and assign it to a
variable, the collection that is created will be *mutable*. This means
that you can change (or *mutate*) the size of the collection after it is
created by adding more items to the collection, or by removing existing
items from the ones it already contains. Conversely, if you assign an
array or a dictionary to a constant, that array or dictionary is
*immutable*, and its size cannot be changed.

For dictionaries, immutability also means that you cannot replace the
value for an existing key in the dictionary. An immutable dictionary’s
contents cannot be changed once they are set.

Immutability has a slightly different meaning for arrays, however. You
are still not allowed to perform any action that has the potential to
change the size of an immutable array, but you *are* allowed to set a
new value for an existing index in the array. This enables Swift’s
Array type to provide optimal performance for array
operations when the size of an array is fixed.

The mutability behavior of Swift’s Array type also
affects how array instances are assigned and modified. For more
information, see [Assignment and Copy Behavior for Collection
Types](ClassesAndStructures.xhtml#TP40014097-CH13-XID_109).

Note

It is good practice to create immutable collections in all cases where
the collection’s size does not need to change. Doing so enables the
Swift compiler to optimize the performance of the collections you
create.
