# heap 0

| Field | Value |
| --- | --- |
| Platform | picoCTF 2024 |
| Category | Binary Exploitation |
| Difficulty | Easy |
| Date | 2024-06-25 |
| Author | Mttttt |

## Overview

Examine how the program handles writes to a heap-allocated buffer.

<details>
<summary>Original challenge description</summary>

Are overflows just a stack concern? Download the binary [here](https://artifacts.picoctf.net/c_tethys/28/chall). Download the source [here](https://artifacts.picoctf.net/c_tethys/28/chall.c)Connect with the challenge instance here:
`nc tethys.picoctf.net 50970`


- *Category*: **Binary Exploitation**
- *Difficulty*: **Easy**

</details>

## Analysis

An unchecked write could modify adjacent heap data.

Connect to `nc tethys.picoctf.net 50970`

Choose option 2 (Write buffer)
And do simple Buffer Overflow by writing a log of characters

Then, choose option 4 (See flag)

And get the answer

## Result

`picoCTF{my_first_heap_overflow_76775c7c}`
