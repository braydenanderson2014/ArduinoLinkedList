# BasicLinkedList for Arduino

`BasicLinkedList` is a lightweight templated singly linked list for Arduino sketches.

## Features

- Stores any copyable data type
- Supports append, prepend, indexed insert, indexed removal, value removal, lookup, and clear operations
- Returns pointers for direct access with `get()`
- Exposes `Optional<T>`-based helpers for safer reads with `getElement()`, `find()`, and `operator[]`

## Installation

### Arduino IDE

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
