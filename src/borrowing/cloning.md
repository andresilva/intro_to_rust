# Cloning

Borrowed values can become owned values through *cloning*.

Cloning is to make a deep duplicate of the memory of the borrowed value.

```rust
fn clone_vector(v: &Vec<i32>) -> Vec<i32> {
    v.clone()
}

fn main() {
    let mut v1 = vec![1, 2, 3];
    let v2 = clone_vector(&v1);

    v1[0] = 0;

    println!("v1: {:?}", v1);
    println!("v2: {:?}", v2);
}
```
