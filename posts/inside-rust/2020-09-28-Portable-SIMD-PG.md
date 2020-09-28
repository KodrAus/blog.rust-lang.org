---
layout: post
title: "Announcing the Portable SIMD Project Group"
author: Jubilee, Lokathor, Ashley Mannix, and Caleb Zulawski
description: "Announcing the Portable SIMD Project Group"
team: the library team <https://www.rust-lang.org/governance/teams/library>
---

We're announcing the start of the _Portable SIMD Project Group_ within the Libs team. This group is dedicated to making a portable SIMD API available to stable Rust users.

The Portable SIMD Project Group is being lead by [@calebzulawski](https://github.com/calebzulawski), [@Lokathor](https://github.com/Lokathor), and [@workingjubilee](https://github.com/workingjubilee).

### What are project groups?

Rust uses [project groups](https://rust-lang.github.io/rfcs/2856-project-groups.html) to help coordinate work. They're a place for people to get involved in helping shape the parts of Rust that matter to them.

### What is portable SIMD?

SIMD (Single Instruction, Multiple Data) instructions can apply the same operation to multiple values _simultaneously_.
We say these instructions are _vectorized_ because they operate on a "vector" of values instead of a single value (it's similar to an array, but not to be confused with Rust's `Vec` type).
Different chip vendors offer different hardware intrinsics for achieving vectorization.
Rust's standard library has exposed some of these intrinsics to users directly through the [`std::arch` module](https://doc.rust-lang.org/core/arch/index.html) since [`1.27.0`](https://blog.rust-lang.org/2018/06/21/Rust-1.27.html) shipped back in mid 2018.

You _can_ build vectorized algorithms on `std::arch` directly, but that could mean sacrificing portability, or having to maintain a different implementation for each CPU you want to support.
They can also just be noisy to work with directly.

The goal of the Portable SIMD project group is to provide a high-level API in a new `std::simd` module that abstracts these platform-specific intrinsics away.
You just pick a vector type with the right size, like `f32x4`, and perform operations on them, like addition, and the appropriate intrinsics will be used behind the scenes.

There are still reasons to want to choose intrinsics in `std::arch` directly though.
`std::simd` cannot mirror the details of every possible vendor API.
`std::simd` is Rust's explicit, _portable_ vectorization story.

### How can I get involved?

If you'd like to get on board and help make portable SIMD a reality you can visit our [GitHub repository](https://github.com/rust-lang/project-portable-simd) or reach out on [Zulip](https://rust-lang.zulipchat.com/#narrow/stream/257879-project-portable-simd) and say hi! :wave:
