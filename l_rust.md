# creating project in rust 
```
cargo new rusty_cli
```

with above command main.rs file insidde src folder and other files related to rust project is created

main.rs is the entry point to rust program

```
# to run the main file in debugging mode 
cargo run
# to create an executable. This executable will be stored in target/debug 
cargo build
# to compile it with optimizations. This command will create an executable inside target/release instead of target/debug
cargo build --release 
```
# Variables
variable can create using let(immutable variable) and mut(mutable variable) keywords
```rust
fn main(){
    mut x = 1;
    let y = 1;
    println!("The value of x is: {}", x);
    println!("The value of y is: {}", y);
    x = 0; // error
    println!("The value of x is: {}", x);
    y = 2; // error        
}
```
# Data Types

**Integer     : i32 or i64**

| Length | Signed | Unsigned |
| --- | --- | --- |
| 8-bit  |   i8 | 	u8 |
| 16-bit | 	i16 | 	u16 |
| 32-bit | 	i32 | 	u32 |
| 64-bit | 	i64 | 	u64 |
| 128-bit | i128 | 	u128 |
| arch |    isize | usize |

signed i8 can store  -128 to 127 
unsigned  can store 0 to 255     

| Number literals | Example |
| --- | --- |
| Decimal | `98_222` |
| Hex | `0xff` |
| Octal | `0o77` |
| Binary | `0b1111_0000` |
| Byte (`u8` only) | `b'A'` |

**Integer Overflow**
```
Let’s say you have a variable of type u8 that can hold values between 0 and 255. If you try to change the variable to a value outside of that range, such as 256, integer overflow will occur. Rust has some interesting rules involving this behavior. When you’re compiling in debug mode, Rust includes checks for integer overflow that cause your program to panic at runtime if this behavior occurs. Rust uses the term panicking when a program exits with an error; we’ll discuss panics in more depth in the “Unrecoverable Errors with panic!” section in Chapter 9.

When you’re compiling in release mode with the --release flag, Rust does not include checks for integer overflow that cause panics. Instead, if overflow occurs, Rust performs two’s complement wrapping. In short, values greater than the maximum value the type can hold “wrap around” to the minimum of the values the type can hold. In the case of a u8, the value 256 becomes 0, the value 257 becomes 1, and so on. The program won’t panic, but the variable will have a value that probably isn’t what you were expecting it to have. Relying on integer overflow’s wrapping behavior is considered an error.

To explicitly handle the possibility of overflow, you can use these families of methods that the standard library provides on primitive numeric types:

Wrap in all modes with the wrapping_* methods, such as wrapping_add
Return the None value if there is overflow with the checked_* methods Return the value and a boolean indicating whether there was overflow with the overflowing_* methods Saturate at the value’s minimum or maximum values with saturating_* methods
```

```rust
fn main(){
    let a = 12u128;
    let age :f32 = 12.56;
    let aa = 14; //rust infers as i32
    println!("a is {} age is {} aa is {}", a,age, aa);
    let b:u128 = 123;
    let c :u64 = 324;
    println!("b+c {}", b+a); // error no implementation for `u128 + u64`
}
```

**Float       : f32,f64**  
Rust’s floating-point types are f32 and f64
**default type** is f64 because on modern CPUs it’s roughly the same speed as f32 but is capable of more precision.
```rust
fn main(){
    let a = 12u128;
    let age :u128 = 12;
    let aa = 14; //rust infers as i32
    println!("a is {} age is {} aa is {}", a,age, aa);
}
```

Boolean     : bool(true, false)
```rust
fn main(){
    let b = true;
    let b1 : bool = false;
    println!("b is {} b1 is {}", b, b1);
}
```
String      : string, &str, char
collections : tuple, array, vector, hash map

