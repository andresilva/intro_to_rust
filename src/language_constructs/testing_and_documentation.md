# Testing and Documentation

Built-in testing support and docs.

### Tests

```rust
#[test]
fn test_pop_empty_stack() {
    let stack = Vec::<u32>::new();
    assert!(stack.pop() == None);
}
```

```
running 1 test
test test_pop_empty_stack … ok

test result: ok. 1 passed; 0 failed; 0 ignored; 0 measured
```

```rust
#[test]
fn test_pop_empty_stack() {
    let mut stack = Vec::<u32>::new();
    stack.push(3);
    assert!(stack.pop() == None);
}
```

```
running 1 test
test test_pop_empty_stack … FAILED

--- test_pop_empty_stack stdout ---
          thread ‘test_pop_empty_stack’ panicked at ‘assertion failed: stack.pop() == None’, test.rs: 4

failures:
     test_pop_empty_stack

test result: FAILED. 0 passed; 1 failed; 0 ignored; 0 measured

```

### Documentation (with tests!)

```rust
/// Removes the last element from a vector and returns it, or None if it is empty.
///
/// # Examples
///
/// ```
/// let stack = Vec::<u32>::new();
/// assert!(stack.pop() == None);
/// ```
fn pop(&mut self) -> Option<Box<T>> {
    // ...
}
```

```
running 1 test
test test_pop_empty_stack_0 … ok

test result: ok. 1 passed; 0 failed; 0 ignored; 0 measured
```
