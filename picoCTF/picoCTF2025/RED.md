# RED

| Field | Value |
| --- | --- |
| Platform | picoCTF 2025 |
| Category | Forensics |
| Difficulty | Easy |
| Date | 2025-04-30 |

## Overview

Recover concealed data from the supplied image.

## Analysis

A metadata comment pointed to the least significant bits, which contained Base64-encoded data.

First, check metadata (3rd hint told us to do this)
There is a comment `Crimson heart, vibrant and bold,.Hearts flutter at your sight..Evenings glow softly red,.Cherries burst with sweet life..Kisses linger with your warmth..Love deep as merlot..Scarlet leaves falling softly,.Bold in every stroke`
Lets combine capital letters: `C H E C K L S B` => `CHECK LSB`
Now we would use `zsteg` tool to see **LSB** *(Least Significant Bit)*
```sh
zsteg red.png lsb
```

And there would be our flag, encoded with **Base64**
```
cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX  
2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==
```

Decode it with any tool or site you want (or in terminal with `echo "<base64 text>" | base64 -d`)

## Result

`picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}`
