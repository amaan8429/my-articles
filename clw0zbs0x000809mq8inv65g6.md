---
title: "Setting up rust locally - Rust Series Part 2"
datePublished: Fri May 10 2024 17:56:56 GMT+0000 (Coordinated Universal Time)
cuid: clw0zbs0x000809mq8inv65g6
slug: setting-up-rust-locally-rust-series-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1715363756379/c253d754-2b91-4248-863b-1d1a28fcb801.png
tags: rust, rust-lang, rust-programming

---

Here is a reformatted version of the text with proper structure and formatting:

# Installing Rust

## Try Rust Online (Optional)

You can try Rust online in the [Rust Playground](https://play.rust-lang.org/) without installing anything on your computer.

## Rustup: The Rust Installer and Version Management Tool

The primary way to install Rust is through a tool called `rustup`, which is a Rust installer and version management tool.

### Installation on macOS, Linux, or Other Unix-like OS

If you're running macOS, Linux, or another Unix-like OS, run the following command in your terminal and follow the on-screen instructions:

```plaintext
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Now type `cargo` in your terminal -

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1715268012025/3e392b29-9c6d-480d-91ed-d6e4792a817c.png align="center")

### Updating Rust

Rust updates very frequently. If you have installed Rustup some time ago, chances are your Rust version is out of date. Get the latest version of Rust by running:

```plaintext
rustup update
```

## Cargo: The Rust Build Tool and Package Manager

When you install Rustup, you'll also get the latest stable version of the Rust build tool and package manager, known as Cargo. Cargo enables you to:

* Build your project with `cargo build`
    
* Run your project with `cargo run`
    
* Test your project with `cargo test`
    
* Build documentation for your project with `cargo doc`
    
* Publish a library to [crates.io](http://crates.io) with `cargo publish`
    

To test that you have Rust and Cargo installed, run this in your terminal:

```plaintext
cargo --version
```

## Setting up Vs Code to work with Rust

Install this extension to work efficiently with rust in VS code

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1715268081345/13493c21-ae93-4cf9-8b21-3bec535a0220.png align="center")

## Generating a New Project

To create a new Rust project, use Cargo:

```plaintext
cargo new hello-rust
```

This will generate a new directory called `hello-rust` with the following files:

```plaintext
hello-rust
|- Cargo.toml
|- src
  |- main.rs
```

* `Cargo.toml` is the manifest file for Rust, where you keep metadata for your project and dependencies.
    
* `src/`[`main.rs`](http://main.rs) is where you'll write your application code.
    

To run the "Hello, world!" program, navigate to the new directory and run:

```plaintext
cargo run
```

## Adding Dependencies

You can add dependencies to your project from [crates.io](http://crates.io), the package registry for Rust. In this example, we'll add the `ferris-says` crate.

In `Cargo.toml`, add the following under the `[dependencies]` section:

```toml
[dependencies]
ferris-says = "0.3.1"
```

Or, you can run:

```plaintext
cargo add ferris-says
```

Then, run:

```plaintext
cargo build
```

Cargo will install the dependency for you. You'll notice a new file, `Cargo.lock`, which is a log of the exact versions of the dependencies you're using locally.

## A Small Rust Application

To make a small program in rust , open [`main.rs`](http://main.rs), remove everything, and add the following code:

```rust
fn main() {
    println!("Hello, world!");
}
```

Save the file and run:

```plaintext
cargo run
```

Assuming everything went well, you should see your application print a message with `Hello World!`

## Congratulations, you're a Rustacean now!