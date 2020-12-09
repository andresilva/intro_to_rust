# Owned Mutability

Mutability propagates deeply into owned types

```rust
struct A { b: B }

struct B { c: usize }

fn main() {
    let mut a = A { b: B { c: 2 } };
    a.b.c = 3;
    a.b = B { c: 4 };
    a = A { b: B { c: 5 } };

    let frozen = a;
    frozen.b.c = 4; // error!
}
```
