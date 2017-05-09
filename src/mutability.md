# Mutability

Values are *immutable* by default in Rust, and must be tagged as being *mutable*.

```rust
let a = 4;
a = 5; // error!
```

```rust
let mut a = 4;
a = 5; // ok
```

Mutability is also a part of the type of a borrowed pointer.

```rust
fn inc(i: &i32) {
    *i += 1; // error!
}
```

```rust
fn inc(i: &mut i32) {
    *i += 1; // ok
}
```