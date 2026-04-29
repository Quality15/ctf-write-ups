---
created at: 2026-04-29 || 16:44
category: General Skills
tags:
  - picoCTF_2026
difficulty: Easy
---
## Task description
Oops! Someone accidentally sent an important file to a network printer—can you retrieve it from the print server?
## Solution
In the first hint, tasks said us that printer works with a SMB server
Let's check what we can see in SMB:
```bash
$ smbclient -L //mysterious-sea.picoctf.net -p 53888 -N # put ur ip and port

        Sharename       Type      Comment  
        ---------       ----      -------  
        shares          Disk      Public Share With Guests  
        IPC$            IPC       IPC Service (Samba 4.19.5-Ubuntu)  
SMB1 disabled -- no workgroup available
```

We see directory named **shares**
Now connect to that directory:
```bash
$ smbclient -L //mysterious-sea.picoctf.net/shares -p 53888 -N

smb: \> ls
dummy.txt  
flag.txt
smb: \> get flag.txt
smb: \> exit
```

Now we have flag:
```bash
cat flag.txt
```
## Flag
`picoCTF{5mbpr1nter5h4re57a400ec3}`