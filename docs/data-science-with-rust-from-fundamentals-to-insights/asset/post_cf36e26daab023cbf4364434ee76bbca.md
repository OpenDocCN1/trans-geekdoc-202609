
## Data Structures in Rust

### Vectors

Vectors, akin to dynamic arrays, are one of the most commonly used data structures in Rust. They provide a way to store a collection of elements that can grow or shrink in size.

#### Creating and Using Vectors:

```rust
fn main() {
    let mut vec: Vec = Vec::new();
    vec.push(1);
    vec.push(2);
    vec.push(3);

    for elem in &vec {
        println!("{}", elem);
    }
}
```

- Vec::new(): Creates a new, empty vector.
- vec.push(1): Adds an element to the end of the vector.
- for elem in &vec: Iterates over the elements of the vector.

Vectors can also be created with the vec! macro, allowing for a more concise initialization.

#### Using the vec! Macro:

```rust
fn main() {
    let vec = vec![1, 2, 3, 4, 5];
    for elem in &vec {
        println!("{}", elem);
    }
}
```

### Strings

Strings in Rust are a bit more complex due to Rust's ownership system, which ensures memory safety. There are two main types of strings: String and &str (string slice).

#### Creating and Manipulating Strings:

```rust
fn main() {
    let mut s = String::from("Hello");
    s.push_str(", world!");
    println!("{}", s);
}
```

- String::from("Hello"): Creates a new String from a string literal.
- s.push_str(", world!"): Appends a string slice to the String.

### HashMaps

HashMaps are collections that store key-value pairs, enabling efficient retrieval of values based on their keys. They are particularly useful for scenarios where you need to associate unique keys with specific values.

#### Creating and Using HashMaps:

```rust
use std::collections::HashMap;

fn main() {
    let mut scores = HashMap::new();
    scores.insert(String::from("Blue"), 10);
    scores.insert(String::from("Yellow"), 50);

    let team_name = String::from("Blue");
    let score = scores.get(&team_name);

    match score {
        Some(s) => println!("The score of {} is {}", team_name, s),
        None => println!("No score found for {}", team_name)
    }
}
```

- HashMap::new(): Creates a new, empty HashMap.
- scores.insert(...): Inserts a key-value pair into the HashMap.
- scores.get(&team_name): Retrieves the value associated with team_name.

### HashSets

A HashSet is a collection of unique values, useful when you need to ensure that no duplicates exist in your dataset. HashSet is built on top of HashMap, providing unique elements without associated values.

#### Creating and Using HashSets:

```rust
use std::collections::HashSet;

fn main() {
    let mut books = HashSet::new();
    books.insert("Rust Programming".to_string());
    books.insert("Data Science with Rust".to_string());
    books.insert("Rust Programming".to_string()); // Duplicate entry, will be ignored

    for book in &books {
        println!("{}", book);
    }
}
```

- HashSet::new(): Creates a new, empty HashSet.
- books.insert(...): Inserts a value into the HashSet.

### Linked Lists

While Rust does not include a standard library implementation for linked lists, creating custom linked lists can be a valuable exercise for understanding pointers and ownership. A linked list consists of nodes where each node contains data and a reference to the next node in the sequence.

#### Implementing a Simple Linked List:

```rust
enum List {
    Cons(i32, Box<List>),
    Nil,
}

use List::{Cons, Nil};

fn main() {
    let list = Cons(1, Box::new(Cons(2, Box::new(Cons(3, Box::new(Nil))))));
    println!("Created a simple linked list!");
}
```

- enum List: Defines a recursive data structure for the linked list.
- Box<List>: Allocates memory on the heap, allowing Rust to manage the recursive nature of the list.

### Binary Trees

Binary trees are essential for many algorithms and data structures, such as binary search trees and heaps. They provide fast lookup, insertion, and deletion operations.

#### Implementing a Simple Binary Tree:

```rust
enum BinaryTree {
    Node(i32, Box<BinaryTree>, Box<BinaryTree>),
    Empty,
}

use BinaryTree::{Node, Empty};

fn main() {
    let tree = Node(10, Box::new(Node(5, Box::new(Empty), Box::new(Empty))),
        Box::new(Node(15, Box::new(Empty), Box::new(Empty))));
    println!("Created a simple binary tree!");
}
```

- enum BinaryTree: Defines a recursive structure for the binary tree.
- Box<BinaryTree>: Uses heap allocation to manage the recursive structure.

## Error Handling in Rust

### Rust's Error Handling Philosophy

Rust distinguishes between two types of errors: recoverable and unrecoverable. Recoverable errors are those from which your program can recover, such as a file not being found. Unrecoverable errors, on the other hand, are those that indicate bugs in your program, such as an out-of-bounds array access. Rust provides distinct mechanisms to handle each type:

- **Recoverable Errors**: Managed using the Result<T, E> type.
- **Unrecoverable Errors**: Managed using the panic! macro.

### Using Result for Recoverable Errors

The Result enum is a powerful tool in Rust's error handling arsenal. It is defined as:

```rust
enum Result<T, E> {
    Ok(T),
    Err(E),
}
```

The Result type signifies that an operation can either succeed (Ok) and yield a value of type T, or fail (Err) and yield an error of type E. This allows errors to be propagated up the call stack, compelling the programmer to handle them explicitly.

#### Example: Reading a File

```rust
use std::fs::File;
use std::io::{self, Read};

fn read_file(file_path: &str) -> Result<String, io::Error> {
    let mut file = File::open(file_path)?;
    let mut contents = String::new();
    file.read_to_string(&mut contents)?;

    Ok(contents)
}

fn main() {
    match read_file("data.txt") {
        Ok(contents) => println!("File contents: {}", contents),
        Err(e) => println!("Error reading file: {}", e),
    }
}
```

In this example:

- File::open(file_path) returns a Result<File, io::Error>.
- The ? operator is used to propagate errors. If File::open returns an Err, the function will return early with that error.
- The main function matches on the result, handling both the Ok and Err cases.

### Chaining Results with the ? Operator

The ? operator simplifies error propagation by eliminating the need for explicit match statements. This operator automatically converts the error type to match the return type of the function, promoting cleaner and more readable code.

#### Example: Connecting Multiple Results

```rust
fn read_and_print_file(file_path: &str) -> Result<(), io::Error> {
    let contents = read_file(file_path)?;
    println!("File contents: {}", contents);
    Ok(())
}

fn main() {
    if let Err(e) = read_and_print_file("data.txt") {
        println!("Application error: {}", e);
    }
}
```

Here, the read_and_print_file function reads the file and prints its contents. The ? operator is used to propagate any errors encountered during the file reading process.

### Custom Error Types

Rust's error handling becomes even more powerful when you define your own custom errors. This involves implementing the std::error::Error trait, which provides compatibility with Rust's error handling ecosystem.

#### Example: Creating Custom Error Types

```rust
use std::fmt;

#[derive(Debug)]
enum DataError {
    NotFound,
    ParseError,
}

impl fmt::Display for DataError {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        match *self {
            DataError::NotFound => write!(f, "Data not found"),
            DataError::ParseError => write!(f, "Error parsing data"),
        }
    }
}

impl std::error::Error for DataError {}
```

With this custom error type, you can handle specific error conditions more effectively:

```rust
use std::fs::File;
use std::io::{self, Read};
use std::num::ParseIntError;

fn read_and_parse_file(file_path: &str) -> Result<i32, Box<dyn std::error::Error>> {
    let mut file = File::open(file_path)?;
    let mut contents = String::new();
    file.read_to_string(&mut contents)?;

    // Simulate a parsing function
    let num: i32 = contents.trim().parse().map_err(|_e| DataError::ParseError)?;
    Ok(num)
}

fn main() {
    match read_and_parse_file("data.txt") {
        Ok(num) => println!("Parsed number: {}", num),
        Err(e) => println!("Application error: {}", e),
    }
}
```

In this example:

- Box<dyn std::error::Error> is used to return a type that implements the Error trait.
- The custom error DataError::ParseError is used to handle parsing errors specifically.

### panic! for Unrecoverable Errors

The panic! macro is used for unrecoverable errors, which force the program to terminate immediately. This should be reserved for truly exceptional situations where continuing execution is impossible or would lead to incorrect results.

#### Example: Using panic!
