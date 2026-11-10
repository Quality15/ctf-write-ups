# PIE TIME

| Field | Value |
| --- | --- |
| Platform | picoCTF 2025 |
| Category | Binary Exploitation |
| Difficulty | Easy |
| Date | 2025-04-29 |

## Overview

Examine the role of position-independent execution in the supplied binary.

<details>
<summary>Original challenge description</summary>

Can you try to get the flag? Beware we have PIE! Connect to the program with netcat:

```sh
$ nc rescued-float.picoctf.net 63047
```

The program's source code can be downloaded [here](https://challenge-files.picoctf.net/c_rescued_float/2757d7751ddf1be98450094c20e981031e6c654474ddeb8f646f6d98e3832c15/vuln.c). The binary can be downloaded [here](https://challenge-files.picoctf.net/c_rescued_float/2757d7751ddf1be98450094c20e981031e6c654474ddeb8f646f6d98e3832c15/vuln).

</details>

## Analysis

The original notes record the recovered flag without documenting the procedure.

## Result

`picoCTF{b4s1c_p051t10n_1nd3p3nd3nc3_93dd5fcb}`
