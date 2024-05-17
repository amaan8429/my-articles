---
title: "The Simple stuff - Rust Series Part 3"
datePublished: Fri May 17 2024 11:07:31 GMT+0000 (Coordinated Universal Time)
cuid: clwaks7jy000509leents2ofo
slug: the-simple-stuff-rust-series-part-3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1715943998811/b2cd7f3b-6d77-4bc3-84b3-e14bbd96fb02.png
tags: rust, rust-lang, rust-programming

---

In Rust, variables are declared using the `let` keyword, followed by the variable name and an optional type annotation. Here's an example of declaring a simple variable:

```rust
let x = 5; // x is an immutable variable of type i32 (integer)
```

If you don't specify a type, Rust will infer the type based on the value assigned to the variable.

You can also explicitly annotate the type of a variable:

```rust
let y: i64 = 42; // y is an immutable variable of type i64 (64-bit integer)
```

By default, variables in Rust are immutable, meaning their value cannot be changed after initialization. However, you can declare a mutable variable using the `mut` keyword:

```rust
let mut count = 0; // count is a mutable variable
count = 1; // This is allowed because count is mutable
```

Here are a few more examples of different types of variables in Rust:

```rust
// Boolean
let is_active = true;
let is_admin: bool = false;

// Character
let grade = 'A';

// String
let message = "Hello, Rust!";
let hello: String = String::from("Hello, World!");

// Float
let pi = 3.14159;
let tau: f64 = 6.28318; // f64 is 64-bit floating-point

// Tuple (a fixed-size collection of different types)
let point: (i32, i32, i32) = (10, 20, 30);

// Array (a fixed-size collection of the same type)
let bytes: [u8; 3] = [1, 2, 3]; // u8 is an unsigned 8-bit integer
```

You can also perform operations on variables:

```rust
let mut x = 5;
x = x + 1; // x is now 6

let y = 10;
let sum = x + y; // sum is 16
```

Note that when you reassign a value to a mutable variable, the old value is dropped (deallocated), and the new value takes its place. This is a key aspect of Rust's memory management and ownership rules, which help prevent common issues like null pointer dereferences and data races.

In summary, Rust variables are declared with the `let` keyword, can be immutable or mutable, and can be of various types, including primitives (like integers, floats, and booleans), strings, tuples, and arrays. Rust also provides type inference, so you don't always need to explicitly annotate the type of a variable.

## Let's Understand some more concepts using this code :

```rust
fn main() {
    //main is the entry point of the program. you don't have to call main unlike in C or C++ or Java
    let sentence: String = String::from("Hello, World!");
    // String::from() is used to create a new String
    let first_word: String = get_first_word(sentence);
    println!("{}", first_word);
    looping_numbers();
}

// Function to get the first word of a sentence
fn get_first_word(sentence: String) -> String {
    //every variable in Rust is immutable by default. To make it mutable, you have to use the mut keyword
    let mut ans = String::new(); // String::new() is used to create a new empty String
    for char in sentence.chars() {
        ans.push_str(char.to_string().as_str());
        if char == ' ' {
            break;
        }
    }
    return ans;
}

// Function to loop through numbers
fn looping_numbers() {
    let _i = 4; // putting _ in front of a variable name will suppress the warning of unused variable
    for i in 0..10 {
        println!("{}", i);
    }
}
```

1. **Entry Point**: The `main` function serves as the entry point of a Rust program.
    
2. **String Handling**: We've seen different ways to create and manipulate strings in Rust, including `String::from()`, `String::new()`, iterating over characters using `str.chars()`, converting a single character to a `String` using [`char.to`](http://char.to)`_string()`, and appending a string to another string using `string.push_str()`.
    
3. **Function Definition and Calling**: We've defined two custom functions, `get_first_word` and `looping_numbers`, and demonstrated how to call them from the `main` function.
    
4. **Return Values**: The `get_first_word` function shows how to return a value from a function in Rust.
    
5. **Variable Mutability**: We've demonstrated that variables in Rust are immutable by default and how to make a variable mutable using the `mut` keyword.
    
6. **Loops**: We've shown two different ways to loop in Rust: using a `for` loop with an iterator (`for char in sentence.chars()`) and using a range-based `for` loop (`for i in 0..10`).
    
7. **Unused Variable Handling**: We've shown how to suppress the warning for an unused variable by prefixing it with an underscore (`let _i = 4;`).
    
8. **Printing to Console**: We've used the `println!` macro to print values to the console.
    

Through this code example, we've explored some fundamental concepts in Rust, including variable declaration, string manipulation, function definition and calling, loops, and printing to the console. This serves as a good starting point for understanding the basics of Rust programming.