# Generics

```rust
struct MyVec<T> { /* */ }

impl<T> MyVec<T> {
  pub fn find<P>(&self, predicate: P) -> Option<&T>
    where P: Fn(&T) -> bool
  {
    for v in self {
      if predicate(v) {
        return Some(v);
      }
    }
    None
  }
}
```
