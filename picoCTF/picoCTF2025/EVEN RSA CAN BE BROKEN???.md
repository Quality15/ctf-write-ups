# EVEN RSA CAN BE BROKEN???

| Field | Value |
| --- | --- |
| Platform | picoCTF 2025 |
| Category | Cryptography |
| Difficulty | Easy |
| Date | 2025-04-29 |

## Overview

Recover the plaintext from the supplied RSA parameters and ciphertext.

<details>
<summary>Original challenge description</summary>

This service provides you an encrypted flag. Can you decrypt it with just N & e? Connect to the program with netcat: `$ nc verbal-sleep.picoctf.net 51434` The program's source code can be downloaded [here](https://challenge-files.picoctf.net/c_verbal_sleep/19dc994c3573239de3934a5fd5a89282385e1d6cc9fc01666db38f439d64499d/encrypt.py).

</details>

## Analysis

The challenge used an even RSA modulus, which exposed a factor of two.

Go to [this](https://www.dcode.fr/rsa-cipher) site and enter the N, e and the cyphertext

## Result

`picoCTF{tw0_1$_pr!m381772be5}`
