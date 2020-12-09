# Nesting

Borrows can be nested:

* Someone can borrow something you are borrowing.
* Someone can borrow part of the thing you are borrowing.

```rust
struct MyStruct { inner: i32 }

fn do_print(value: &i32) {
    println!("value: {}", *value);
}

fn print(s: &MyStruct) {
    do_print(&s.inner);
}

fn main() {
    let s = MyStruct { inner: 3 };
    print(&s);
}
```

```rust
struct MyStruct { inner: i32 }

fn get(s: &MyStruct) -> &i32 {
    &s.inner
}

fn main() {
    let s = MyStruct { inner: 3 };
    let inner = get(&s); // same lifetime as `s`
    println!("inner: {}", inner);

    // essentially the same as
    let inner = &s.inner;
    println!("inner: {}", inner);
}
```
