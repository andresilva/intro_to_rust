# No hidden states

```rust
enum Option<T> {
  Some(T),
  None,
}

enum Result<T, E> {
  Ok(T),
  Err(E),
}

# let mut my_vec = vec![1, 2, 3, 42].into_iter();

// v is Option<&T>, not &T -- cannot use without checking for None
let v = my_vec.find(|t| *t >= 42);

if let Some(v) = v {
    println!("v: {:?}", v);
}

// n is Result<i32, ParseIntError> -- cannot use without checking for Err
let n = "42a".parse::<i32>();

match n {
    Ok(n) => println!("n: {}", n),
    Err(err) => println!("failed with error: {:?}", err),
}
```
