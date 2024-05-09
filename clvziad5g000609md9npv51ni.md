---
title: "Why Rust and Why Not Node.js or Python? - Rust Series Part 1"
datePublished: Thu May 09 2024 17:12:11 GMT+0000 (Coordinated Universal Time)
cuid: clvziad5g000609md9npv51ni
slug: why-rust-and-why-not-nodejs-or-python-rust-series-part-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1715274659274/a1294616-a65d-49d4-a1f8-905085f1ff9b.png
tags: rust, rust-lang

---

## Ease of Writing

Generally, it's recommended to use Node.js or Python as your first language because they're easier to write. The reason is that they don't have type safety, meaning they don't enforce types anywhere. For example, in JavaScript, you can assign a variable as a number and then change it to a string in the next line without any errors.

```javascript
let x = 1; // x is a number
x = "hello"; // x is now a string, no error
```

However, this is not considered good practice as it can lead to bugs. Ideally, you should have strict types, or at least explicitly define that a variable can be a number or a string. TypeScript and Python (with type hints) address this issue by introducing type safety.

## Systems Language

Rust is a systems language, which means it allows you to have access to low-level resources on the machine, such as memory (RAM). In Rust, you can directly interact with memory by putting variables there, removing them, and creating references. This level of control is necessary for tasks like building compilers, operating systems, file systems, and other low-level software.

## Performance

Rust is incredibly fast compared to JavaScript. Even if you can build a use case in JavaScript, for performance-critical applications like web real-time communication (WebRTC) servers, trading applications, or exchanges, you would typically use faster languages like Rust, C, Go, or Zig.

Many projects expose a high-level JavaScript API but use a lower-level language like Rust or C++ for the core functionality due to performance reasons.

## Concurrency

Rust, like Java and Go, supports concurrency, which means running multiple threads on a single machine. In contrast, Node.js is single-threaded by default, meaning it can only run on one core of your machine, even if you have a multi-core CPU. You can achieve multi-threading in Node.js, but it's not the standard approach.

In Rust, you can spawn threads that can independently run on different cores, sharing resources and data more easily than in Node.js, where you would need to use inter-process communication (IPC).

## Memory Safety

One of the key advantages of Rust over languages like C is its memory safety. C allows manual memory allocation and deallocation, which can lead to issues like dangling pointers and null pointer exceptions if not handled correctly. Rust, on the other hand, has a different approach to memory management that makes it more memory-safe, reducing the chances of such errors.

We'll discuss memory management and memory safety in more detail when we cover that topic.

In summary, while Node.js and Python are great for getting started, Rust offers advantages in performance, concurrency, and memory safety, making it suitable for systems programming, low-level tasks, and performance-critical applications.