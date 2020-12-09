# Testing and Documentation

Built-in testing support and docs.

```rust
#[test]
fn it_works() {
  assert_eq!(one_more(1), 2);
}

/// Returns one more than its argument.
///
/// ```
/// assert_eq!(one_more(42), 43);
/// ```
pub fn one_more(n: i32) -> i32 {
  n + 1
}
```
