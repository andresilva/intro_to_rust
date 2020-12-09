# Compatibility

Rust uses LLVM, normal calling conventions, no runtime, DWARF, so:
 - Works with all traditional tools.
    - gdb/lldb works
    - valgrind works
    - LLVM sanitizers work
    - Linux: perf works
    - macOS: Instruments works
    - Windows: Whatever's used, it probably works (maybe!)

