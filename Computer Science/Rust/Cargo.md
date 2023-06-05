Cargo is Rust’s build system and package manager

### create project with cargo

```
$ cargo new hello_cargo
```

Tis command creates a new directory and project called _hello_cargo_. We’ve named our project _hello_cargo_, and Cargo creates its files in a directory of the same name.

Go into the _hello_cargo_ directory and list the files. You’ll see that Cargo has generated two files and one directory for us: a _Cargo.toml_ file and a _src_ directory with a _main.rs_ file inside.

It has also initialized a new Git repository along with a _.gitignore_ file. Git files won’t be generated if you run `cargo new` within an existing Git repository; you can override this behavior by using `cargo new --vcs=git`.

![[TOML]]


Cargo expects your source files to live inside the _src_ directory. The top-level project directory is just for README files, license information, configuration files, and anything else not related to your code. Using Cargo helps you organize your projects. There’s a place for everything, and everything is in its place.

### Building and Running a Cargo Project

```
$ cargo build
```

This command creates an executable file in _target/debug/hello_cargo_

Running `cargo build` for the first time also causes Cargo to create a new file at the top level: _Cargo.lock_. This file keeps track of the exact versions of dependencies in your project

### Run the executable

```
$ ./target/debug/hello_cargo
$ cargo run
```


This command quickly checks your code to make sure it compiles but doesn’t produce an executable:

```
$ cargo check
```

### Building for release

```
cargo build --release
```

This command will create an executable in _target/release_ instead of _target/debug_.

It compile codes with optimizations.
The optimizations make your Rust code run faster, but turning them on lengthens the time it takes for your program to compile.

