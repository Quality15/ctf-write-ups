# Flag Hunters

| Field | Value |
| --- | --- |
| Platform | picoCTF 2025 |
| Category | Reverse Engineering |
| Difficulty | Easy |
| Date | 2025-04-29 |

## Overview

Determine why the lyric reader omits a hidden refrain.

<details>
<summary>Original challenge description</summary>

Lyrics jump from verses to the refrain kind of like a subroutine call. There's a hidden refrain this program doesn't print by default. Can you get it to print it? There might be something in it for you. The program's source code can be downloaded [here](https://challenge-files.picoctf.net/c_verbal_sleep/7ece2015c227ce98f450f0199b953b8ecba02748c09557e95645acf045e1f96f/lyric-reader.py). Connect to the program with netcat: `$ nc verbal-sleep.picoctf.net 59014`

</details>

## Analysis

The Python lyric reader interprets control directives that change the position from which it reads the lyrics.

To get flag we need to use `RETURN 0` in our response, but because line in spliting with `;` we should enter `some_text;RETURN 0`

## Result

`picoCTF{70637h3r_f0r3v3r_05182f4f}`
