# What you get out of it

## Iterator invalidation

- Iterator invalidation due to mutating a collection you're iterating over;
- This pattern can be written in C, C++, Java, Python, Javascript...
  - But may result in, e.g, `ConcurrentModificationException` (at runtime!)
  
```rust
let mut vs = vec![1, 2, 3, 4];
for v in &vs {
    vs.pop();
    // ERROR: cannot borrow `vs` as mutable because
    // it is also borrowed as immutable
}
```

## Use-after-free

- Valid in C/C++ and a common source of errors.

```rust
let y: &i32;
{
    let x = 5;
    y = &x; // error: `x` does not live long enough
}
println!("{}", *y);
```

## Resource leak

- Never forget to close a file or a socket ever again.

```rust
use std::fs::File;
use std::io::prelude::*;

fn main() -> std::io::Result<()> {
    {
        let mut file = File::create("foo.txt")?;
        file.write_all(b"Hello, world!")?;
        // file is automatically closed here
    } 
    
    Ok(())
}
```
