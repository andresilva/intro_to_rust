# Language Constructs

## Structs

```rust
struct Point {
    x: int,
    y: int,
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

### Enums With Data

```rust
enum Shape {
    Circle(Point, f64),
    Rectangle(Point, Point),
}

match shape {
    Circle(center, radius) => {
        draw_circle(center, radius)
    }
    Rectangle(ul, lr) => {
        draw_rectangle(ul, lr)
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

## Traits

```rust
trait Clone {
    // borrows the receiver,
    // returning the same type (Self)
    fn clone(&self) -> Self;
}

impl Clone for Point {
    fn clone(&self) -> Point {
        Point { x: self.x, y: self.y }
    }
}
```

### Traits in Generics

```rust
fn clone_vector<T: Clone>(v: &Vec<T>) -> Vec<T> {
    let mut other = Vec::new();
    for element in v.iter() {
        other.push(element.clone());
    }
    other
}
```

