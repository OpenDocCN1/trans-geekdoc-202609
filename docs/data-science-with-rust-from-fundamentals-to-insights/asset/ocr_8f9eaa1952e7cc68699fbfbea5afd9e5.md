# Error Handling in Rust

# Rust's Error Handling Philosophy

Rust distinguishes between two types of errors: recoverable and unrecoverable. Recoverable errors are those from which your program can recover, such as a file not being found. Unrecoverable errors, on the other hand, are those that indicate bugs in your program, such as an out-of-bounds array access. Rust provides distinct mechanisms to handle each type:

+   - **Recoverable Errors**: Managed using the Result<T, E> type.
+   - **Unrecoverable Errors**: Managed using the panic! macro.

# Using Result for Recoverable Errors

The Result enum is a powerful tool in Rust's error handling arsenal. It is defined as:

```
```rust
enum Result { Ok(T), Err(E), }
```
```

The Result type signifies that an operation can either succeed (Ok) and yield a value of type T, or fail (Err) and yield an error of type E. This allows errors to be propagated up the call stack, compelling the programmer to handle them explicitly.

# Example: Reading a File

```
```rust
use std::fs::File; use std::io::{self, Read};

fn read_file(file_path: &str) -> Result<String, io::Error> {
    let mut file = File::open(file_path)?;
    let mut contents = String::new();
    file.read_to_string(&mut contents)?;
```