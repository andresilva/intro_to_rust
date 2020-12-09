# Algebraic Data Types

```rust
enum Option<T> {
  Some(T),
  None,
}

let my_vec = vec![0, 1, 2, 3, 4, 5];
let x = match my_vec.into_iter().find(|n| *n >= 2) {
    Some(2) => { 'a' },
    Some(n) if n > 10 => { 'b' },
    None => { 'c' },
};

println!("x: {}", x);
```

Fixed:

```rust
let my_vec = vec![0, 1, 2, 3, 4, 5];
let x = match my_vec.into_iter().find(|n| *n >= 2) {
    Some(2) => { 'a' },
    Some(n) if n > 10 => { 'b' },
    _ => { 'c' },
};

println!("x: {}", x);
```
