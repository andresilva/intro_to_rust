# Concurrency

## What is concurrency

- One program with multiple threads of execution running at the same time
- Threads can share data without communication overhead
  - (networking, inter-process communication channels, etc)
- Threads are more lightweight than individual processes
  - No large OS context switch when switching between threads

## Why is concurrency hard

```rust
/* thread 1 */ let mut y = &mut x;
/* thread 1 */ *y = 1;
/* thread 1 */ println!("{}", *y); // foo expects 1
               // => 1
/* thread 2 */ let mut z = &mut x;
/* thread 2 */ *z = 2;
/* thread 2 */ println!("{}", *z); // bar expects 2
               // => 2
```

- Sharing data: What if two threads try to write to the same piece of data at
  the same time?
- Data races: The behavior of the same piece of code might change depending on
  when exactly it executes
- Synchronization: How can I be sure all of my threads see the correct world
  view?
- Deadlock: How can you safely share resources across threads and ensure threads
  don't lock each other out of data access?
