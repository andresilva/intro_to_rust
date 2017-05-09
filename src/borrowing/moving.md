# Moving

Borrowing prevents *moving*

```rust
fn work_with(_slot: Vec<i32>) { /* ... */ }

fn main() {
    let a = vec![1];
    let b = &a;

    work_with(a); // error! borrowed by 'b'
}
```


```rust
fn work_with(_slot: Vec<i32>) { /* ... */ }

fn main() {
    let a = Vec::new();
    {
        let _b = &a;
    }
    work_with(a); // ok
}
```

## Problem

A common mistake in C:

```c
*int helper() {
    int a = 3;
    return &a;
}

int main(int argc, char const *argv[]) {
    printf("%d\n", *helper());
    return 0;
}
```

Rust's way of representing this:

```rust
fn main() {
    println!("Your number was: {}", *helper());
}

fn helper<'a>() -> &'a i32 {
    let a = 3;
    return &a;
}
```

```rust
fn main() {
    println!("Your number was: {}", *helper(&3));
}

fn helper<'a>(value: &'a i32) -> &'a i32 {
    return value;
}
```
