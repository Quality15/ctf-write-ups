# Scan Surprise

| Field | Value |
| --- | --- |
| Platform | picoCTF 2024 |
| Category | Forensics |
| Difficulty | Easy |
| Date | 2024-05-29 |
| Author | Mttttt |

## Overview

Recover the flag from the image supplied in the challenge archive.

<details>
<summary>Original challenge description</summary>

I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead? You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/13/challenge.zip)

- *Category*: **Forensics**
- *Difficulty*: **Easy**

</details>

## Analysis

The image contained a QR code that decoded to the flag.

Download file and unzip it
There is file `flag.png`
This is a QR Code

Decode it with any QRCode Decoder

Get the flag

## Result

`picoCTF{p33k_@_b00_d4ca652e}`
