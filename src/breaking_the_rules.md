# Breaking The Rules

## `unsafe` Blocks

```rust
fn main() {
    let a = 3;

    // Turn off some compiler checks,
    // "I know what I'm doing"
    unsafe {
        let b = &a as *const i32 as *mut i32;
        *b = 4;
    }

    println!("{}", a); // prints 4
}
```

## Transmuting

Transforming the mutability of a variable.

```rust
unsafe fn transmute<T, U>(t: T) -> U {
    /* ... */
}
```

```rust
// Invalid promotion to a mutable pointer
let a: &usize = &3;
let b: &mut usize = unsafe { std::mem::transmute(a) };
```

## Foreign Function Interface (FFI)

*All* FFI is unsafe

```rust
extern {
    fn write(fd: i32, data: *const u8, len: usize) -> i32;
}

fn main() {
    let data = b"Hello, world!\n";

    unsafe {
        write(1, &data[0], data.len());
    }
}
```

### Fast FFI

```asm
main:
  ...
  xorl    %edi, %edi
  leaq    _str1365(%rip), %rsi
  movl    $0xd, %edx
  callq   0x100000eb2 ## symbol stub for: _write
```
