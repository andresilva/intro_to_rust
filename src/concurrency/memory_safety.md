# Memory Safety

Safety is achieve by requiring that a `closure` owns captured variables.

```rust
let mut a = Vec::new();

// spawn a thread and move ownership of 'a' into it
::std::thread::spawn(move || {
    a.push("foo");
});

a.push("bar"); // error!
```

## Sharing Memory

Tasks can also share memory:

```rust
use std::collections::HashMap;
use std::sync::Arc;
use std::thread;

fn main() {
    let mut map = HashMap::new();
    map.insert("tomato", "red");
    map.insert("celery", "green");
    map.insert("carrot", "orange");

    let arc1 = Arc::new(map);
    let arc2 = arc1.clone();

    let t1 = thread::spawn(move || println!("Celery is `{}`", arc1["celery"]));
    let t2 = thread::spawn(move || println!("Carrots are `{}`", arc2["carrot"]));

    t1.join().unwrap();
    t2.join().unwrap();
}
```
