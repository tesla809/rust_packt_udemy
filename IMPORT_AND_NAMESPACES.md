Back to main
[README](README.md)

#Import and Namespaces

**Overview**:
1. How Rust code is organized
2. Some more types
3. Build some more bigger programs

## How Rust code is organized
Rust code is organized into crates. 

Crates are further organized into modules. So, crates are built up from modules.

One crates can rely on another crate.

![Crates relying on one another](/images/crate-organization-overview.png)
*Crates relying on one another*

**How to import things into the namespace?**
The keyword ```use```.

```rust 

```

```std``` is the standard library in Rust.

```collections``` is a module within the standard library ```std```.

```::``` plucks out an item from a group.

**Import explained**
```use std::collections::LinkedList``` means, here is a cargo package, ```std``` and we are plucking out the collections module. From that we will pluck out the LinkedList item.

**Usage explained**
```let mut ll == LinkedList::new();``` means declare a mutable binding (aka variable) called ```ll```. Remember that bindings are immutable by default. ```LinkedList::new()``` plucks out the method ```new()``` from ```LinkedList```. That method is assigned to ```ll```.











## Some more types

## Build some more bigger programs







