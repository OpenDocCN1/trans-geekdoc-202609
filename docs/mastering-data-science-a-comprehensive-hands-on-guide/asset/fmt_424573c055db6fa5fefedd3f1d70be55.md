
## 3.3.2 Tuple

A tuple is an ordered, immutable collection of items. It is ideal for storing fixed data that should not change.

### Key Features

- Ordered: Elements have a defined sequence.
- Immutable: Cannot be modified after creation.
- Supports heterogeneous data types.

### Syntax

`my_tuple = (1, 2, 3, "apple", True)`

### Common Operations

#### Accessing Elements

```python
my_tuple = (1, 2, 3, "apple", True)
print(my_tuple[0])  # Output: 1
```

#### Slicing

```python
print(my_tuple[1:3])  # Outputs (2, 3)
```

#### Iterating

```python
for item in my_tuple:
    print(item)
```

#### Unpacking

```python
a, b, c, d, e = my_tuple
print(a, b)  # Output: 1 2
```

### Immutability

Cannot modify, add, or remove elements after creation.

### When to Use Tuples

When the data should remain constant (e.g., coordinates, configuration settings).

## 3.3.3 Dictionaries

A dictionary is an unordered, mutable collection of key-value pairs. It is ideal for associating unique keys with specific values.

### Key Features

- Unordered: Elements have no defined sequence (ordered since Python 3.7+).
- Mutable: Can add, remove, or update key-value pairs.
- Keys must be unique and immutable (e.g., strings, numbers, or tuples).

### Syntax

`my_dict = {"name": "Alice", "age": 25, "city": "New York"}`

### Common Operations

#### Accessing Values

```python
print(my_dict["name"])  # Output: Alice
```

#### Adding/Updating Values

```python
my_dict["job"] = "Engineer"  # Adds a new key-value pair
my_dict["age"] = 26  # Updates the value of "age"
```

#### Removing Key-Value Pairs

```python
del my_dict["city"]  # Removes the "city" key
my_dict.pop("age")  # Removes and returns the value of "age"
```

#### Iterating

```python
for key, value in my_dict.items():
    print(key, value)
```

#### Checking for Keys

```python
print("name" in my_dict)  # Output: True
```

### When to Use Dictionaries

When data needs to be accessed by unique keys (e.g., user profiles, lookup tables).

## 3.3.4 Sets

A set is an unordered, mutable collection of unique elements. It is ideal for storing items without duplicates and performing set operations.

### Key Features

- Unordered: Elements have no defined sequence.
- Mutable: Can add or remove elements.
- Unique: Does not allow duplicate values.

### Syntax

`my_set = {1, 2, 3, 4}`

### Common Operations

#### Adding Elements

```python
my_set = {1, 2, 3, 4}
my_set.add(5)  # Adds 5 to the set
```

#### Removing Elements

```python
my_set.remove(2)  # Removes 2 (throws an error if not present)
my_set.discard(10)  # Removes 10 (does not throw an error if not present)
```

#### Set Operations

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
print(set1.union(set2))  # {1, 2, 3, 4, 5}
print(set1.intersection(set2))  # {3}
print(set1.difference(set2))  # {1, 2}
```

#### Checking Membership

```python
print(3 in my_set)  # Output: True
```

### When to Use Sets

When duplicate values are not allowed (e.g., storing unique IDs, removing duplicates from a list).

## 3.3.5 Comparison of Python Data Structures

| Feature | List | Tuple | Dictionary | Set |
| --- | --- | --- | --- | --- |
| Ordered | Yes | Yes | No (Ordered since 3.7+) | No |
| Mutable | Yes | No | Yes | Yes |
| Allows Duplicates | Yes | Yes | Keys: No, Values: Yes | No |
| Access Method | Indexing | Indexing | Keys | Unordered |
| Best For | Sequential Data | Fixed Data | Key-Value Associations | Unique, Unordered Data |

## 3.3.6 Choosing the Right Data Structure

Use a `list`: When you need an ordered, mutable collection of items.

Use a `tuple`: When you need an ordered, immutable collection of items.

Use a `dict`: When you need to store data as key-value pairs.

Use a `set`: When you need a collection of unique elements.

In addition, Python has very strong built-in data structures: `list`, `tuple`, `dict`, and `set`. Choosing the right structure based on your requirements will ensure efficient, clean code—be it regarding immutability, uniqueness, or key-value mapping. Mastering these data structures is a necessity for effective Python programming.

# 3.4 File Handling: Reading and Writing Files

File handling is a very useful skill in Python; it basically allows one to create, read, write, and manipulate files. Python provides a very simple and efficient way of interacting with files using built-in functions and methods.

## 3.4.1 File Handling Modes

Python supports different modes for file handling:

| Mode | Description |
| --- | --- |
| 'r' | Read mode (default). Opens a file for reading; raises an error if the file does not exist. |
| 'w' | Write mode. Opens a file for writing; creates the file if it does not exist or overwrites the file if it exists. |
| 'a' | Append mode. Opens a file for appending; creates the file if it does not exist. |
| 'r+' | Read and write mode. Opens a file for both reading and writing. |
| 'w+' | Write and read mode. Creates the file if it doesn’t exist or overwrites it if it does. |
| 'a+' | Append and read mode. Opens a file for both appending and reading. |
| 'b' | Binary mode. Used with other modes (e.g., 'rb' or 'wb') for binary files like images or videos. |

## 3.4.2 Reading Files

### Reading the Entire File

Use the `read()` method to read the entire contents of a file.

Example:

```python
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)
```

Ensure that the `example.txt` file is present in the current directory before running this program. Below is an example of the content for a sample `example.txt` file:

This is line 1
This is line 2
This is line 3

### Reading Line by Line

Use the `readline()` method to read one line at a time.

Example:

```python
with open('example.txt', 'r') as file:
    line = file.readline()
    while line:
        print(line.strip())  # Removes the newline character
        line = file.readline()
```

### Reading All Lines as a List

Use the `readlines()` method to read all lines into a list.

Example:

```python
with open('example.txt', 'r') as file:
    lines = file.readlines()
    print(lines)
```

## 3.4.3 Writing Files

### Writing Text to a File

Use the `write()` method to write a string to a file.

Example:

```python
with open('example.txt', 'w') as file:
    file.write("Hello, World!\n")
    file.write("This is a new line.")
```

### Writing Multiple Lines

Use the `writelines()` method to write a list of strings to a file.

Example:

```python
lines = ["First line\n", "Second line\n", "Third line\n"]
with open('example.txt', 'w') as file:
    file.writelines(lines)
```

### Appending to a File

Use the 'a' mode to append content to an existing file.

Example:

```python
with open('example.txt', 'a') as file:
    file.write("\nAppended line.")
```

## 3.4.4 Working with Binary Files

Binary files, such as images or videos, require the 'b' mode.

### Reading Binary Files

```python
with open('image.jpg', 'rb') as file:
    data = file.read()
    print(data[:10])  # Prints the first 10 bytes
```

Make sure the file `image.jpg` exists in the current directory in order to run this code block.

### Writing Binary Files

```python
with open('output.jpg', 'wb') as file:
    file.write(data)
```

## 3.4.5 File Pointer Operations

Python provides methods to manipulate the file pointer:

`tell()`: Returns the current position of the file pointer.

`seek(offset, whence)`: Moves the file pointer to a specific position.

Example:

```python
with open('example.txt', 'r') as file:
    print(file.tell())  # Outputs: 0 (beginning of the file)
    file.read(5)  # Reads the first 5 characters
    print(file.tell())  # Outputs: 5
    file.seek(0)  # Moves the pointer back to the start
```

## 3.4.6 Exception Handling in File Operations

Use try-except blocks to handle potential errors during file operations.

Example:

```python
try:
    with open('nonexistent.txt', 'r') as file:
        content = file.read()
except FileNotFoundError:
    print("The file does not exist.")
```

## 3.4.7 Using the with Statement

The `with` statement is the preferred way to handle files as it automatically closes the file after the block is executed. It prevents resource leaks and simplifies code.

Example:

```python
with open('example.txt', 'r') as file:
```
