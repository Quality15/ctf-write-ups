# endianness
Write-Up by **Mttttt** *2024-05-31*

## Task description
Know of little and big endian? [Source](https://artifacts.picoctf.net/c_titan/78/flag.c)

- *Category*: **General Skills**
- *Difficulty*: **Easy**

## Solution
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

## Answer
`picoCTF{3ndi4n_sw4p_su33ess_cfe38ef0}`
