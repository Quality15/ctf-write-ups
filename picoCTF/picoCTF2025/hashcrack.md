# hashcrack

| Field | Value |
| --- | --- |
| Platform | picoCTF 2025 |
| Category | Cryptography |
| Difficulty | Easy |
| Date | 2025-04-29 |

## Overview

Recover the passwords represented by the challenge hashes.

<details>
<summary>Original challenge description</summary>

A company stored a secret message on a server which got breached due to the admin using weakly hashed passwords. Can you gain access to the secret stored within the server? Access the server using `nc verbal-sleep.picoctf.net 61522`

</details>

## Analysis

A hash lookup service identified plaintext matches for the supplied values.

To solve this challenge we would use [CrackStation](https://crackstation.net/)
Just paste all hashes from terminal to it

| Hash                                                             | Password    | Hash Type |
| ---------------------------------------------------------------- | ----------- | --------- |
| 482c811da5d5b4bc6d497ffa98491e38                                 | password123 | md5       |
| b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3                         | letmein     | sha1      |
| 916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745 | qwerty098   | sha256    |

## Result

`picoCTF{UseStr0nG_h@shEs_&PaSswDs!_36a1cf73}`
