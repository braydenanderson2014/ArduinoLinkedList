# LinkedList for Arduino

A simple, templated linked list implementation for Arduino projects. This class allows you to create and manage a linked list of any data type.

## Features

- Templated class: Can store any data type.
- Dynamic resizing: Automatically manages memory as elements are added or removed.
- Basic operations: `append`, `prepend`, `insert`, `remove`, `get`, `contains`, `getSize`, `isEmpty`, `clear`.

## WARNING: This Library Utilizes POINTERS *. This is due to the Libraries ability to utilize any return type. (Bool, String, int, float, etc)

## Installation

To use `LinkedList` in your Arduino sketch:

1. Copy the `LinkedList` class code to your project's directory.
2. Include `LinkedList.h` at the top of your sketch.

## Change Log
### Version 1.0.0
* Initial Release
### Version 1.0.1
* Fixed Issues Related to Library Not Building.
* Syntax Errors that were not discovered originally when Library was update have not been rectified. Library Should now work as intended.
### Version 1.0.2
* Update to README
* Added [LINKED LIST]: to the Serial Print Statements to make it easier to debug
* Added Overloaded Insert Function() to insert a value at a specific index
* Added Insert Function to insert a value randomly into the list
* Adjusted size Variable to be capitalized as Size. That way the compiler will not get confused with the size() function
* Added an Iterator to the LinkedList. This will allow you to iterate through the list
* This Library Has been partially tested. Please report any bugs to the Author
### Version 1.0.3
* Added a boolean variable to the LinkedList Constructor to determine if the LinkedList should print to the Serial Monitor or not.
* Added a setDebug() function to set the debug variable to true or false
* Added a getDebug() function to get the debug variable
### Version 1.0.4
* Added a new function called getAsString() to return the LinkedList element as a String
* Deprecated the keyExists() and valueExists() functions. They will be removed in the next release.. (Use contains() instead)
* Removed debug statements from the library, this is to save memory. A duplicate Library will be created with debug statements in it.
* Added Function Comments to the Library
### Version 1.0.5 
* REMOVING Two Deprecated Functions -> Use contains()
* Renamed the remove function to more closely correlate to what it does.
* Added new remove function that takes in an index to remove to match other List Libraries.
* Added getElement Function that returns the element instead of the pointer to the element.
### Version 1.0.6 [Current-Release]
* Renaming Linked List Files (including src File) to BasicLinkedList. This is due to Arduino Library Manager Requiring Library Headers to Match Library Names. And since you cannot Duplicate Library Names, The library will be Listed the same as PlatformIO. (BasicLinkedList)


## Currently Tested Functions
`cpp
    insert(1 parameter version)
    prepend()
    append()
    size()
    get()
`
prepend, and append were used automatically by the insert function

## Usage

To create a linked list, simply declare an instance of `LinkedList` with the desired type:

```cpp
#include <LinkedList.h>

LinkedList<int> myList;
```
## Adding Elements
### Append an element to the end of the list:

```cpp
myList.append(1);
```
### Prepend an element to the beginning of the list:

```cpp
myList.prepend(0);
```
### Insert an element at a specific position:

```cpp
myList.insert(2, 1);  // Insert '2' at position '1'
```

```cpp
myList.insert(1); //Insert '1' anywhere in the List.
```
## Accessing Elements
### Retrieve an element at a specific position:

```cpp
int value = myList.get(1);
```
## Removing Elements
### Remove an element by value:

```cpp
myList.remove(1);
```
## Utility Functions
### Check if the list contains a specific value:

```cpp
if (myList.contains(2)) {
    // Element is in the list
}
```
## Get the size of the list:

```cpp
size_t size = myList.size();
```
### Check if the list is empty:

```cpp
if (myList.isEmpty()) {
    // List is empty
}
```
### Clear the list:

```cpp
myList.clear();
```
## Example
```cpp
LinkedList<int> myList;
myList.append(1);
myList.append(2);
myList.prepend(0);
myList.insert(3, 3);

for (size_t i = 0; i < myList.size(); i++) {
    Serial.print("Element at position ");
    Serial.print(i);
    Serial.print(": ");
    Serial.println(myList.get(i));
}

myList.remove(2);
myList.clear();
```
