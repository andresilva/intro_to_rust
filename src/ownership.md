# Ownership

Variables are *moved* to new locations, preventing the previous location from using it

There is only every *one* owner of data!

## Problem

```c++
int main() {
    int *slot = malloc(sizeof(int));
    *slot = 3;
    helper(slot);
    helper(slot); // use after free!
}

void helper(int *slot) {
    printf("The number was: %d\n", *slot);
    free(slot);
}
```

```c++
a.out(62940,0x7fff7b9ea310) malloc: *** error for object 0x7fecb0c03b10:
pointer being freed was not allocated
*** set a breakpoint in malloc_error_break to debug
zsh: abort      ./a.out
```

## Solution

```rust
fn main() {
    let slot = Box::new(3);
    helper(slot); // moves the value!
    helper(slot); // error: use of moved value
}

fn helper(slot: Box<i32>) {
    println!("The number was: {}", slot);
}
```
