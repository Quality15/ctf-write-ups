---
created at: 2026-04-29 || 16:21
category: General Skills
tags:
  - picoCTF_2026
difficulty: Easy
---
## Task description
I have built my own Git server with my own rules! You can clone the challenge repo using the command below. 
`git clone ssh://git@<unique-ip>:<port>/git/challenge.git` 
Here's the password: `d9df7038` 
Check the README to get your flag!
## Solution
### Step 1
Clone repository with command given:
`git clone ssh://git@<unique-ip>:<port>/git/challenge.git`
Using password given in the task
### Step 2
Check the **README.md** file:
```text
# MyGit  
  
### If you want the flag, make sure to push the flag!  
  
Only flag.txt pushed by ```root:root@picoctf``` will be updated with the flag.  
  
GOOD LUCK!
```
### Step 3
We need to specify our Git username and email:
`git config user.name "root`
`git config user.email "root@picoctf"`
### Step 4
Now, let's change our flag and push to the git server:
```bash
$ echo "something" > flag.txt # or any another way to change file context
$ git add . # or git add flag.txt
$ git commit -m "flag.txt changed"
$ git push origin master
```

After this we can finally get our flag:
*(output after last command)*
```bash
git@foggy-cliff.picoctf.net's password:   
Enumerating objects: 4, done.  
Counting objects: 100% (4/4), done.  
Delta compression using up to 4 threads  
Compressing objects: 100% (2/2), done.  
Writing objects: 100% (3/3), 283 bytes | 283.00 KiB/s, done.  
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0  
remote: Author matched and flag.txt found in commit...  
remote: Congratulations! You have successfully impersonated the root user  
remote: Here's your flag: picoCTF{1mp3rs0n4t4_g17_345y_220a9833}  
To ssh://foggy-cliff.picoctf.net:59249/git/challenge.git  
   0dcb7df..afbdf1f  master -> master
```
## Flag
`picoCTF{1mp3rs0n4t4g17345y220a9833}`