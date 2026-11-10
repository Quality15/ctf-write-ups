# Blame Game

| Field | Value |
| --- | --- |
| Platform | picoCTF 2024 |
| Category | General Skills |
| Difficulty | Easy |
| Date | 2024-05-29 |
| Author | Mttttt |

## Overview

Locate the flag in the Git history associated with a project file.

## Analysis

The flag appeared in the author field of a commit affecting the file.

```bash
git log message.py
```
```
commit 0351e0474493168ca76441c24630c17554fd09ca  
Author: picoCTF{@sk_th3_1nt3rn_d2d29f22} <ops@picoctf.com>  
Date:   Tue Mar 12 00:07:01 2024 +0000  
  
   optimize file size of prod code  
  
commit c9e851509190f5887e91339ee18087e3e77ebfda  
Author: picoCTF <ops@picoctf.com>  
Date:   Tue Mar 12 00:07:01 2024 +0000  
  
   create top secret project
```

## Result

`picoCTF{@sk_th3_1nt3rn_d2d29f22}`
