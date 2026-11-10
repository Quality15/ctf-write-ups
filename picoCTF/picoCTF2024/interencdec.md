# interencdec

| Field | Value |
| --- | --- |
| Platform | picoCTF 2024 |
| Category | Cryptography |
| Difficulty | Easy |
| Date | 2024-05-28 |
| Author | Mttttt |

## Overview

Recover the flag from the encoded challenge file.

<details>
<summary>Original challenge description</summary>

Can you get the real meaning from this file. Download the file [here](https://artifacts.picoctf.net/c_titan/109/enc_flag).

- *Category*: **Cryptography**
- *Difficulty*: **Easy**

</details>

## Analysis

The file combined two layers of Base64 encoding with a Caesar cipher.

Downloaded file content:
```
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyMHdNakV5TnpVNGZRPT0nCg==
```

Lets send it to CyberChef
After Base64 decoding we got this:
```
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX20wMjEyNzU4fQ=='
```

It seems to be bytes literal string
Just remove `b'` at the beginning and `'` at the end

Then decode it from Base64:

```bash
echo "d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX20wMjEyNzU4fQ==" | base64 -d
```
Output:
`wpjvJAM{jhlzhy_k3jy9wa3k_m0212758}`

It can be assumed, that it is **Caesar Cipher**

After sending our string to CyberChef, choose **ROT13 Decode**

As is **Caesar Cipher** just move letters on some numbers left or right, we need to pick up that one number

![[Caesar Cipher.png]]

The correct number was **19**

![[picoCTF_interencedec_solution.png]]

## Result

`picoCTF{caesar_d3cr9pt3d_f0212758}`
