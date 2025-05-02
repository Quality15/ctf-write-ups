# Time Machine
Write-Up by **Mttttt** *2024-05-28*

## Task description
What was I last working on? I remember writing a note to help me remember... You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/163/challenge.zip)

- *Category*: **General Skills**
- *Difficulty*: **Easy**

## Solution
Download the file and unzip it. Go to directory `drop-in`

There is only one file - `message.txt`

Lets see his Git History by following command:
```bash
git show ./message.txt
```
Output:
```
commit e65fedb3a72a16c577f4b17023b63997134b307d (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:29 2024 +0000

    picoCTF{t1m3m@ch1n3_88c35e3b}

diff --git a/message.txt b/message.txt
new file mode 100644
index 0000000..4324621
--- /dev/null
+++ b/message.txt
@@ -0,0 +1 @@
+This is what I was working on, but I'd need to look at my commit history to know why...

```

And we the flag in commit `e65f..b307d`

## Answer
`picoCTF{t1m3m@ch1n3_88c35e3b}`
