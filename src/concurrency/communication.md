# Communication

Threads can communicate with channels

```rust
use std::sync::mpsc;
use std::thread;
use std::time::Duration;

fn expensive_computation() -> i32 {
    thread::sleep(Duration::from_millis(500));
    123
}

fn main() {
    let (tx, rx) = mpsc::channel();

    thread::spawn(move || {
        tx.send(expensive_computation()).expect("Failed to send result");
    });

    // Do some work in the meantime

    let answer = rx.recv().expect("Failed to receive result");
    println!("answer: {}", answer);
}
```
