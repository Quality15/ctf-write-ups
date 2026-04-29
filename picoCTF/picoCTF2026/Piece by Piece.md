---
created at: 2026-04-29 || 17:08
category: General Skills
tags:
  - picoCTF_2026
difficulty: Easy
---
## Task description
After logging in, you will find multiple file parts in your home directory. These parts need to be combined and extracted to reveal the flag.
## Solution
### Step 1
Login with SSH:
```bash
ssh ctf-player@<ip> -p <port>
```

Then, check what is in this home directory
```bash
$ ls
instructions.txt  part_aa  part_ab  part_ac  part_ad  part_ae
$ cat instructions.txt
Hint:  
  
- The flag is split into multiple parts as a zipped file.  
- Use Linux commands to combine the parts into one file.  
- The zip file is password protected. Use this "supersecret" password to extract the zip file.  
- After unzipping, check the extracted text file for the flag.
```
### Step 3
Now, we need to combine all this parts in one file
We can do it by simply write all their context in one file like this:
```bash
ctf-player@pico-chall$ cat part_a* > test.zip  
ctf-player@pico-chall$ unzip -P supersecret test.zip    
Archive:  test.zip  
extracting: flag.txt                   
ctf-player@pico-chall$ cat flag.txt    
picoCTF{z1p_and_spl1t_f1l3s_4r3_fun_28d309dc}
```
## Flag
`picoCTF{z1p_and_spl1t_f1l3s_4r3_fun_28d309dc}`