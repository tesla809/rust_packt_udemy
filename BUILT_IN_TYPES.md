Back to main
[README](README.md)

#Built-In types:

We'll examine the built-in types provided by Rust, using the Rust playground, a web based Rust development environment.

Rust playground: play.rust-lang.org

We will write a simple "Hello, World!" app.

```rust
fn main() {
  println!("Hello, world");
}
```

**Keyword Descriptions**
```fn```
Keyword for function

```main()```
Special function that runs first in Rust

```println!()```
Rust's print function. The ! at the end of println!() is called a macro.

**Macros**
The compiler does a bit of work before compiling code to generate some more code. 

It will figure out what types of values it is meant to format into the string at compile time without being told.

This allows us to avoid the clunky syntax of C's printf() without the runtime costs of Python's "reflection based format".

**Reflection**: In computer science, is the ability of a process to examine, introspect and modify its own structure and behavior.

**Longer program**
We can make the code more composable by creating a seperate function with our Hello, world! code inside of it.

```rust
fn main() {
    say_hello();
    math_operations();
}

fn say_hello(){
    println!("Hello, world");
}

fn math_operations() {
    let a = 1;  // immutable binding aka variable (by default)
    let b = 2;
    println!("{} + {} is {}", a, b, a + b);  // string interpolation
}
```

**String interpolation**
```println!("{} + {} is {}", a, b, a + b);```
The first argument is the string itself. ```{}``` are used as placeholders. The next three arguments will be inserted into the placeholders sequentially.

**Type system described**
![Type System Description](https://octodex.github.com/images/yaktocat.png)
