# Rust fixme 3

| Field | Value |
| --- | --- |
| Platform | picoCTF 2025 |
| Category | General Skills |
| Difficulty | Easy |
| Date | 2025-04-30 |

## Overview

Correct the supplied Rust program so that it prints the flag.

<details>
<summary>Original challenge description</summary>

Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag! Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/dcdaf491b35c1d0f5075e9583edbbb7aaea1dffb6ad32bc000e4d87b5200ff7b/fixme3.tar.gz).

</details>

## Analysis

The source inspection identified a commented-out function relevant to the program's output.

Look at the source code of `main.rs`
There is commented function, lets uncomment it
And now run this program with `cargo run main.rs`

## Result

`picoCTF{n0w_y0uv3_f1x3d_1h3m_411}`
