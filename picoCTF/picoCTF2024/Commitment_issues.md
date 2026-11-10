# Commitment issues

| Field | Value |
| --- | --- |
| Platform | picoCTF 2024 |
| Category | General Skills |
| Difficulty | Easy |
| Date | 2024-06-25 |
| Author | Mttttt |

## Overview

Recover a deleted flag from the history of the supplied repository.

<details>
<summary>Original challenge description</summary>

I accidentally wrote the flag down. Good thing I deleted it! You download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/138/challenge.zip)

- *Category*: **General Skills**
- *Difficulty*: **Easy**

</details>

## Analysis

The commit diff retained the content removed from the working copy.

First of all, we need to unzip the file
All we got is `message.txt`
If use command `ls -lah`, we can see `.git` directory
From the task name and hints we can find out that answer is somewhere in git commit

Let's see Git logs for `message.txt`:
```bash
git log ./message.txt
```
Output:
```
commit 42942c9c605b30100f5d859ef6e172027447c0db (HEAD -> master)  
Author: picoCTF <ops@picoctf.com>  
Date:   Tue Mar 12 00:06:23 2024 +0000  
  
   remove sensitive info  
  
commit b562f0b425907789d11d2fe2793e67592dc6be93  
Author: picoCTF <ops@picoctf.com>  
Date:   Tue Mar 12 00:06:23 2024 +0000  
  
   create flag
```

It can be assumed that flag is in file `message.txt` under commit `b562..be93`

Let's see file under this commit:
```bash
git show b562f0b425907789d11d2fe2793e67592dc6be93:./message.txt
```

Output is our flag

## Result

`picoCTF{s@n1t1z3_c785c319}`
