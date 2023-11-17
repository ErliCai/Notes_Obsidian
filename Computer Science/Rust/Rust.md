Rust is an ahead-of-time compiled_language, meaning you can compile a program and give the executable to someone else, and they can run it even without having Rust installed

### standard library & prelude

By default, Rust has a set of items defined in the standard library that it brings into the scope of every program. This set is called the _prelude_, and you can see everything in it [in the standard library documentation](https://doc.rust-lang.org/stable/std/prelude/index.html).

If a type you want to use isn’t in the prelude, you have to bring that type into scope explicitly with a `use` statement.



