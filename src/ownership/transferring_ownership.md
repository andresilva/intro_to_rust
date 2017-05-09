# Transferring Ownership

```rust
fn helper() -> Box<i32> {
    let three = Box::new(3);
    return three; // transfer ownership
}

fn main() {
    // acquire ownership of return value
    let my_three = helper();

    println!("my_three: {}", my_three);
}
```
