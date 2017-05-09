# Borrowing

Owned values can be *borrowed* in Rust to allow usage for a certain period of time.

```rust
// The `&` sigil means "borrowed reference"
fn helper(_slot: &Vec<i32>) { /* ... */ }

fn main() {
    let a = Vec::new();

    // doesn't move!
    helper(&a);
    helper(&a);
}
```

## Lifetimes

Borrowed values are only valid for a particular *lifetime*

```rust
fn main() {
    let a: &i32;
    {
        let b = 3;
        a = &b; // error! `b` does not live long enough
    }
}
```

```rust
fn main() {
    let b = 3;
    let _a: &i32;
    _a = &b; // ok, `b` has the same lifetime as `a`
}
```
