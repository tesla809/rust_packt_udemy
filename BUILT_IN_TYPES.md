Back to main
[README](README.md)

#Built-In types:

We'll examine the built-in types provided by Rust, using the Rust playground, a web based Rust development environment.

Rust playground: play.rust-lang.org


##**Our First Rust Program**
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

###**Type system described**
Rust has a strong, static type system. It is also a compiled language, which means you have to run it through a build step and compile the code an executable.

**Strong** means that it doesn't automatically turn one type into another.

**Static** means that it knows what type of things are before running the program. This is where most of Rust's power comes from.

You will have to explicitly have to tell it to do so. 

![Type System Description](/images/type-system-language-comparisons.png)
*Rust in comparison to other languages.*

###**Built-in Types**
**Overview**:
-Booleans
-Characters
-Integers (whole numbers)
-Floating point (decimals)
-Arrays
-Slices
-Tuples
-Function (pointers)

####**Booleans**
One can declare booleans explicitly, or the compiler can infer them.
```rust
let x = true;  // inferred by compiler
let x: bool = true;  // explictly declared type
```
Both of the statements are equivalant! Again, the compiler can infer a binding's type most of the time.

To declare a binding's type, use the colon (```:```) after the variable, like above.

```rust

let x: bool = true;
```

Remember, a binding is Rust's name for a variable.

What will this print?
```rust
let x = false;
let y = x && true;
println!("y is {}", y);  // false
```
False!

####**Characters**
Rust characters are not 8-bit unsigned ints like C.

They are unicode scalars made out of 4-bits. This means that Rust fully supports unicode by default.
```rust
let c: char = 'A';
let d char = '💕'; // supports unicode
```

####**Integer Types**
Rust has several integer types.
They are grouped based on size and signed-ness.

So, you have 8, 16, 32, 64 bit integers and signed/unsigned integers. 

```rust
let a: i8 = -15;
let b: u8 = 25;
let c: i16 = -356;
let d: u16 = 1029;
let e: i32 = -31337;
let f: u32 = 42949672;
let g: i64 = -4294967295;
let h: u64 = 18336744073709551615;
```
*Grouped based on size and signeness*

There are also architecture sized types. These are 32 bits on 32-bit machines and 64 bit on 64-bit machines, and so on.

In coming Rust releases, there will be 128-bit support.

**Architecture sized types**: These are signed ```isize``` or unsigned ```usize``` types that are either 32 or 64 bit size, depending on the machine in question. 

```rust
let i: isize = -1;
let j: usize = 1;
```
*Architecture sized types*

####**Floating point numbers (Decimals)**
Rust supports single and double floating point precision. 

**Single point** precision requires 32-bits. 
**Double point** precision requires 64-bits.

Quoting Webopedia: 
>"The term double precision is something of a misnomer because the precision is not really double.
>
> The word double derives from the fact that a double-precision number uses twice as many bits as a regular floating-point number.
>
>For example, if a single-precision number requires 32 bits, its double-precision counterpart will be 64 bits long.
>The extra bits increase not only the precision but also the range of magnitudes that can be represented.
>
>The exact amount by which the precision and range of magnitudes are increased depends on what format the program is using to represent floating-point values.
>
>Most computers use a standard format known as the IEEE floating-point format"
[From Webopedia](https://www.webopedia.com/TERM/D/double_precision.html)

```rust
let single: f32 = 1.1225 * 10.0
let double: f64 = 1.2e-15; 
```

*[Stack overflow description of single and double floating point precision](https://stackoverflow.com/questions/801117/whats-the-difference-between-a-single-precision-and-double-precision-floating-p)*

Floating point numbers can be written with decimal place or in scientific notation.

####Homogeneous and Heterogeneous Containers: Arrays and Tuples
Rust has arrays where are homogeneous and heterogeneous.

**Homogeneous**: only takes the same type.

**Heterogeneous**: can accept multiple types.

####**Arrays**
Arrays are **Homogeneous**, taking only takes the same type.


```rust
let array: [i8; 3] = [1, 4, 7];
println!("{}", array[1]);  // access element 1 in array
// prints 4
```
In our initialization of our array binding, we are creating an array of three 8-bit signed integers. We use the ```i8``` integer type.

**How to access**:
Arrays are accessed with brackets.

####**Tuples**
Tuples are **Heterogeneous**, can accept multiple types.

```rust
let tuple: (i32, char) = (21, 'x');
println!("{}", tuple.1);  // access element 1 in tuple
// prints 4
```
In our initialization of our tuple binding, we are creating a tuple of two elements, a  32-bit signed integers and a character. We use the ```i32``` integer and char type.

**How to access**:
Tuples are accessed with dot notation.


####**Functions**
You can store functions them as variables.
```rust 
fn main() {
    let i1 = 1;
    let i2 = 2;
    println!("{} + {} = {}", i1, i2, add(i1, i2));
}

fn add(a: i32, b: i32) -> i32 {
    return a + b;
}
```

**Main Function**
The ```main()``` function always is needed and runs first in every Rust program.

**Parameters**
```a: i32``` means a is a binding of type i32 aka a 32 bit signed integer.

**Return types**
```-> i32``` means that the return type is of type i32.

```fn add(a: i32, b: i32) -> i32```
Function signature reads as function add taking two i32s and returning an i32.

**Returning values**
```return a + b;``` is equal to ```a + b```.
This has to do with how Rust evaluates expressions.

You can return by omitting the return keyword and semi-colon to the last expression in the statement.

**Printing formatted strings with functions**
The Rust compiler expects the number of placeholders to equal the number of variables that follow. If not, the rust compiler will throw an error.

```println!()``` also expects double quotes ```""``` not single qoutes ```''```. If not, the compiler will throw an error.

```println!("{} + {} = {}", i1, i2, add(i1, i2));```


**Mixing integer types in functions**
```rust
fn main() {
  let i1 = 1;
  let i2 = 2;
  println!("{} + {} = {}", i1, i2, add(i1, i2));
}

fn add(a: i32, b: i64) -> i32 {
  return a + b;
}
```
The function signature will throw an error. One cannot return a type lower than the ones used. So adding ```i32```bit integer and a ```i64``` bit integer will throw an error. It will be a ```mismatched types``` error.

![Mismatched types error](/images/mismatched-types-error-rust.png)
*Mismatched types error*

The compiler is SUPER helpful in finding and suggesting documentation to solve the issue.

**Casting to fix mixing integer types in functions**
```rust
fn main() {
  let i1 = 1;
  let i2 = 2;
  println!("{} + {} = {}", i1, i2, add(i1, i2));
}

fn add(a: i32, b: i64) -> i32 {
  return a + (b as i32);  // casts i64 to i32 type 
}
```

```return a + (b as i32);``` casts i64 to i32 type. 

The parentheses are there for clarity. We could write it as
```return a + b as i32;``` 









