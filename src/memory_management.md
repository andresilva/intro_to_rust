# Memory Management

Rust has fine-grained memory management, but is automatically managed once created.

Each variable has a *scope* it is valid for, and it is automatically deallocated when it goes out of scope.

```rust
fn main() {
    // `slot` is an *owned* value
    let slot = Box::new(3);
    // The slot goes out of scope here, it is free'd
}
```

## Reference Counting

Reference counting is another way of managing memory.

```rust
use std::rc::Rc;

fn main() {
    let data = Rc::new(3);          // reference count of 1
    {
        let data2 = data.clone();   // reference count of 2
        work_with(data2);           // transfer ownership of `data2`
    }                               // reference count of 1
    work_with(data);                // transfer ownership of `data`
}                                   // reference count of 0, memory deallocated

fn work_with(data: Rc<i32>) {}
```

This allows multiple structs to *own* a reference to the same chunk of memory. This is useful for sharing a 'context' object between processors, for example &mdash; one processor may add information to the context which allows other processors to reason over it.
