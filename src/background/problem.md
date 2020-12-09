# Problem

![](../img/chromium.png)

> “Around 70% of our high severity security bugs are memory unsafety problems
> (that is, mistakes with C/C++ pointers). Half of those are use-after-free
> bugs.” - [Chromium project](https://www.chromium.org/Home/chromium-security/memory-safety)

```c
typedef struct Dummy { int a; int b; } Dummy;

void foo(void) {
    Dummy *ptr = (Dummy *) malloc(sizeof(struct Dummy));
    Dummy *alias = ptr;
    free(ptr);
    int a = alias.a; // use after free
    free(alias); // double free
}
```

## Solved by managed languages

### Java, Python, Ruby, C#, Scala, Go...
- Restrict direct access to memory
- Run-time management of memory via periodic garbage collection
- No explicit malloc and free, no memory corruption issues
- But...
  - Overhead of tracking object references
  - Program behavior unpredictable due to GC (bad for real-time systems)
  - Limited concurrency (global interpreter lock typical)
  - Larger code size
  - VM must often be included
  - Needs more memory and CPU power (i.e. not baremetal)

### Requirements for system programs
- Must be fast and have minimal runtime overhead
- Should support direct memory access, but be memory-safe
