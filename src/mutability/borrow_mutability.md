# Borrow Mutability

Borrowed pointers may coerce:

```rust
let a = &mut 1;
let b: &int = a; // ok
let c: &mut int = b; // error!
```

Values can be *frozen* by borrowing

```rust
let mut a = Vec::new();
{
    let b = &a; // freezes `a`
    a.push(1);  // error!
}
a.push(2); // ok
```
