# Language Constructs

## Primitives

- **Booleans**: are true and false
- **Integers**: are both signed and unsigned. u8/i8, u16/i16, u32/i32, u64/i64, and u128/i128.
- **Floating point numbers**: f32 and f64
- **Tuples**: are for grouping different types together (i32, f64, i8)
- **Arrays**: that are fixed size [u32; 3] is the type of [1, 2, 3]
- **References**: like pointers but safer. &i32 is the type of &5
- **Slices**: refer to parts of an array &[u8]
- **char**: is a single Unicode Scalar Value, and uses single quotes '🦀'
- **&str**: is an immutable UTF-8 string "this is a crab: 🦀"

## Structs

```rust
struct Point {
    x: usize,
    y: usize,
}

fn main() {
    let p = Point { x: 1, y: 2 };
}
```

## Tuples

```rust
fn main() {
    let pair = (2, 3);
    let (first, second) = pair;
    println!("pair: {:?}", pair);
    println!("first: {:?}, second: {:?}", first, second);
}
```

## Enums

```rust
enum Shape {
    Circle,
    Square
}

fn test(shape: Shape) {
    match shape {
        Circle => { /* ... */ }
        Square => { /* ... */ }
    }
}
```

## "&Pointers"

```rust
let value = 1;
let a: &i32 = &value;               // never null!
let b: Option<&i32> = Some(&value); // may be null

// represented as a null pointer
let c: Option<&i32> = None;
```

Any `&mut` pointer is the *only* pointer to its data

```rust
let mut a = 1;

let b = &mut a; // ok
let c = &mut a; // error!
```
