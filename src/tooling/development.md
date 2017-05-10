# Development

## Meta

[Rustup](https://www.rustup.rs/) is the version manager for different Rust versions. This lets you easily switch between `stable`, `beta`, and `nightly` versions of Rust, as well as update each version.

## Cargo

Rust comes bundled with a tool called `cargo`, which handles project generation, building, and dependency management. It also manages 3rd party commands (download, build, run).

## Code Formatting

[Rustfmt](https://github.com/rust-lang-nursery/rustfmt) provides autoformatting for code, so it makes it easy to both report and enforce a coding style.

## Dependency Management

A published Rust library is called a crate, and the global repository for published crates is [crates.io](https://crates.io/).

Dependencies are specified in a `Cargo.toml` file, and resolved dependency versions are recorded in `Cargo.lock`.

```toml
[package]
name = "my_lib"
version = "0.1.0"
authors = ["Azriel Hoh"]

[dependencies]
uuid = "0.5.0"

[dev-dependencies]
time = "0.1.37"
```

## IDE

There is basic IDE support for a number of editors:

* Eclipse
* Visual Studio
* IntelliJ IDEA
* GNOME Builder

Editor plugins:

* Emacs
* Vim
* Sublime Text
* Atom
* Visual Studio Code

These when linked up with the compiler and `racer` (quick-and-dirty completion), provide:

* Inline warning and error highlighting
* Some form of autocompletion (limited)

The current status of IDE support can be seen at [areweideyet.com](https://areweideyet.com/).
