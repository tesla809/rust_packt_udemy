Back to main
[README](README.md)

##Bindings aka variables:
**Bindings: Rust's name for variables.**

**They are IMMUTABLE by DEFAULT**.
This helps catch errors in code like unintended state mutations.

The Rust compiler gives very good error message descriptions. They also contain very good documentation on how to fix these issues.

Syntax is similar to C or JavaScript.

Example:
```rust
let sample_variable = "value";
```

Bindings aka variables are **immutable by default** so the following code won't compile.

```rust
// code won't compi;e
let sample_variable = "value";
sample_variable = "other value";
```

**Mutable bindings allowed**
Unlike some purely functional languages however, Rust does support mutable binding aka mutable variables.
You must opt in to mutable variables.

Using the ```mut``` keyword allows us to mutate the bindings aka varibale's state.

```rust
// code will compile
let mut counter = 0;
counter = counter + 1;
counter = counter + 10;
```


**Rust compiler will prevent you from uninitalized variables.**

This is a source of bugs in other low-level languages.

Uninitialized variables usuallly contain garbage values. Using them will probably create bugs.

```rust
// code will compile
let mut whatever;  // uninitalized. compiler will throw an error.
do_something(whatever);
```

