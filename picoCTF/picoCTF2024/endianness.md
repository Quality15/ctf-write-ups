# endianness

| Field | Value |
| --- | --- |
| Platform | picoCTF 2024 |
| Category | General Skills |
| Difficulty | Easy |
| Date | 2024-05-31 |
| Author | Mttttt |

## Overview

Determine the big-endian and little-endian representations requested by the challenge service.

<details>
<summary>Original challenge description</summary>

Know of little and big endian? [Source](https://artifacts.picoctf.net/c_titan/78/flag.c)

- *Category*: **General Skills**
- *Difficulty*: **Easy**

</details>

## Analysis

The supplied C code defined how the service interpreted the order of the input bytes.

Download file and open it with **vim**

We see source code of netcat server

Server asks us to put Little Endiana word and Big Endiana word

Lets modify source code of server, leave only functions to convert Big and Little Endiana words

```c
char *find_little_endian(const char *word)  
{  
... 
}  
  
char *find_big_endian(const char *word)  
{  
...
}  
  
int main()  
{  
   char* challenge_word = ""; // <- here will be word that server asks
  
   char *little_endian = find_little_endian(challenge_word);  
  
   char *big_endian = find_big_endian(challenge_word);  
  
   puts(little_endian);  
   puts(big_endian);  
  
   return 0;  
}
```

Connect to netcat and see whats word it will ask
Put this word to out program

Compile and run
Output will be Little and Big words

## Result

`picoCTF{3ndi4n_sw4p_su33ess_cfe38ef0}`
