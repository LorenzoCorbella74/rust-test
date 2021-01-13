[back](../README.md)

# Standard Library

## Prelude
Come si può accedere a Vec or Box da ogni file senza usare *use* . E' grazie al module prelude della standard library.

Know that in the Rust standard library anything that is exported in std::prelude::* is automatically available to every part of Rust. That is the case for Vec and Box but others as well (Option, Copy, etc.).

Because of standard library's prelude, it's common for your libary to have its own prelude module as a starting point for where users should import all of the most common data structures for using your library (e.g use my_library::prelude::*). It doesn't automatically get used in programs/libraries that use your crate, but it's a good convention to follow so people know where to start.

# Links
+ [Official page](https://doc.rust-lang.org/std/)
+ [Rust API Guideline](https://rust-lang.github.io/api-guidelines/)