...

# Loops:

Rust supports several kinds of loops: loop, while, and for.

# Infinite Loop:

```
```rust
let mut count = 0;
loop {
    count += 1;
    if count == 5 {
        break;
    }
}
```
```

# While Loop:

```
```rust
let mut number = 3;
while number != 0 {
    println!("{}!", number);
    number -= 1;
}
println!("Liftoff!");
```
```

# For Loop:

```
```rust
let array = [10, 20, 30, 40, 50];
for element in array.iter() {
    println!("The value is: {}", element);
}
```
```