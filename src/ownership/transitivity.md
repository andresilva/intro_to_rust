# Transitivity

Ownership is a *deep* property of a type

```rust
struct A { b: B }
struct B { c: Box<i32> }

fn main() {
    let a: A = A { b: B { c: Box::new(2) } };
    let c = a.b.c;

    let b: B = a.b; // error! (moved by `c`)
}
```
