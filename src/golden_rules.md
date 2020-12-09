# Golden Rules

## The holy grail of Rust

Learn these rules, and they will serve you well.

- You can't keep borrowing something after it stops existing
- One object may have many immutable references to it (`&T`)
- **OR** exactly one mutable reference (`&mut T`) (not both)
- That's it!

![](./img/holy_grail.jpg)

- TLDR: Aliasing **XOR** Mutability
