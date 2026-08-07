# BasicLinkedList for Arduino


<!-- HEALTH_BADGES_START -->
[![Health: Unsure](https://img.shields.io/badge/Health-Unsure-9e9e9e?style=flat-square)](https://github.com/braydenanderson2014/ArduinoLinkedList)
[![Testing: Unmanaged](https://img.shields.io/badge/Testing-Unmanaged-9e9e9e?style=flat-square)](https://github.com/braydenanderson2014/ArduinoLinkedList)
<!-- HEALTH_BADGES_END -->

A simple, templated linked list implementation for Arduino projects. This class allows you to create and manage a linked list of any data type.
`BasicLinkedList` is a lightweight templated singly linked list for Arduino sketches.

## Features

- Stores any copyable data type
- Supports append, prepend, indexed insert, indexed removal, value removal, lookup, and clear operations
- Returns pointers for direct access with `get()`
- Exposes `Optional<T>`-based helpers for safer reads with `getElement()`, `find()`, and `operator[]`

## Installation

To use `LinkedList` in your Arduino sketch:

1. Copy the `LinkedList` class code to your project's directory.
2. Include `LinkedList.h` at the top of your sketch.

# Arduino:
## Change Log
### Version 1.0.0
* Initial Release
### Version 1.0.1
* Fixed an issue with the getElement() Function. The function will return the item if its found, or it will return a default constructed T() in the event an item is not found.



1. Download or clone this repository.
2. Place it in your Arduino `libraries` directory.
3. Restart the Arduino IDE if it is already open.

### PlatformIO

Add the repository to your `lib_deps` list or install it manually in your project.

## Include

```cpp
#include <BasicLinkedList.h>
```

## Quick Start

```cpp
#include <BasicLinkedList.h>

LinkedList<int> numbers;

void setup() {
    Serial.begin(9600);

    numbers.append(1);
    numbers.append(2);
    numbers.prepend(0);
    numbers.add(3);

    int* value = numbers.get(1);
    if (value != nullptr) {
        Serial.println(*value);
    }

    numbers.remove(0);
    numbers.removeElement(3);
}
```

## API Overview

### Creating a list

```cpp
LinkedList<int> values;
```

### Adding items

```cpp
values.add(10);
values.append(20);
values.prepend(5);
values.insert(15);
values.insert(25, 3);
```

### Reading items

```cpp
int* pointerValue = values.get(0);
Optional<int> elementValue = values.getElement(0);
Optional<int> indexedValue = values[0];
String textValue = values.getAsString(0);
Optional<size_t> foundIndex = values.find(20);
```

### Checking list state

```cpp
size_t count = values.size();
bool empty = values.isEmpty();
bool hasTwenty = values.contains(20);
```

### Removing items

```cpp
values.remove(0);        // remove by index
values.removeElement(5); // remove by value
values.clear();
```

## Important Notes

- `get()` returns a pointer and returns `nullptr` when an index cannot be resolved.
- `remove()` removes by index.
- `removeElement()` removes by value.
- `getElement()`, `find()`, and `operator[]` return `Optional<T>`-style values.

## Example Sketch

See `examples/Example/Example.ino` for a full sketch example.

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for release history.

## Repository Sync

This mirror repository is kept aligned with the library stored in `braydenanderson2014/C-Arduino-Libraries`.
