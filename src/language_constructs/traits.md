# Traits

```rust
trait Mul {
    fn mul(self, other: Self) -> Self;
}

#[derive(Debug)]
struct Rational(usize, usize);

impl Mul for Rational {
    fn mul(self, other: Self) -> Self {
        Rational(self.0 * other.0, self.1 * other.1)
    }
}
```

## Traits in generics

```rust
#trait Mul {
#    fn mul(self, other: Self) -> Self;
#}
#
# #[derive(Debug)]
#struct Rational(usize, usize);
#
#impl Mul for Rational {
#    fn mul(self, other: Self) -> Self {
#        Rational(self.0 * other.0, self.1 * other.1)
#    }
#}
#
impl Mul for usize {
    fn mul(self, other: Self) -> Self {
        self * other
    }
}

fn mul<N: Mul>(n1: N, n2: N) -> N {
    n1.mul(n2)
}

println!("{:?}", mul(1, 2)); // => 2
println!("{:?}", mul(Rational(1, 2), Rational(1, 2))); // => Rational(1, 4)
```
