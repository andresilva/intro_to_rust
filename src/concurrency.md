# Concurrency

Using ownership to prevent data races.

Parallelism is achieved at the granularity of an OS thread.

```rust
use std::thread;
use std::time::Duration;

fn expensive_computation() {
    println!("expensive start");
    thread::sleep(Duration::from_millis(500));
    println!("expensive end");
}

fn other_expensive_computation() {
    println!("other_expensive start");
    thread::sleep(Duration::from_millis(500));
    println!("other_expensive end");
}

fn main() {
    // Spawn a child thread to be run in parallel
    thread::spawn(|| {
        expensive_computation();
    });

    other_expensive_computation();
}
```
