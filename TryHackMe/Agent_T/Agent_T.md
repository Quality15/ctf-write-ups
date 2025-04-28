# Agent T
Write-Up by **Mttttt** *2024-05-30*

## Room Description
Agent T uncovered this website, which looks innocent enough, but something seems off about how the server responds...

After deploying the vulnerable machine attached to this task, please wait a couple of minutes for it to respond.
#### Hint:
Look closely at the HTTP headers when you request the first page...

## Solution
**IP of machine:** `10.10.169.226`

Do a simple nmap scanning
`nmap -sC -sV 10.10.169.226 -oN nmap.log`
Result:
```
Starting Nmap 7.95 ( https://nmap.org ) at 2024-05-30 20:04 EEST  
Nmap scan report for 10.10.169.226  
Host is up (0.080s latency).  
Not shown: 998 closed tcp ports (conn-refused)  
PORT      STATE    SERVICE VERSION  
80/tcp    open     http    PHP cli server 5.5 or later (PHP 8.1.0-dev)  
|_http-title:  Admin Dashboard  
10617/tcp filtered unknown  
  
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .  
Nmap done: 1 IP address (1 host up) scanned in 19.97 seconds
```
Start **dirsearch**
`dirsearch -u 10.10.169.226 -o dirseach.log`
Result:
```
200   199B   http://10.10.169.226/.travis.yml
200    22KB  http://10.10.169.226/404.html
200     4KB  http://10.10.169.226/gulpfile.js
200     1KB  http://10.10.169.226/package.json
200   627KB  http://10.10.169.226/package-lock.json
```

In the google i found this [backdoor](https://www.exploit-db.com/exploits/49933)

Download it and run
We get a reverse shell

Let's find all *.txt* files
`find / -iname "*.txt"`
Output:
```
/usr/share/doc/libdb5.3/build_signature_amd64.txt  
/usr/share/doc/mount/mount.txt  
/usr/share/doc/util-linux/howto-build-sys.txt  
/usr/share/doc/util-linux/blkid.txt  
/usr/share/doc/util-linux/PAM-configuration.txt  
/usr/share/doc/util-linux/mount.txt  
/usr/share/doc/util-linux/howto-tests.txt  
/usr/share/doc/util-linux/hwclock.txt  
/usr/share/doc/util-linux/pg.txt  
/usr/share/doc/util-linux/getopt.txt  
/usr/share/doc/util-linux/howto-compilation.txt  
/usr/share/doc/util-linux/cal.txt  
/usr/share/doc/util-linux/modems-with-agetty.txt  
/usr/share/doc/util-linux/deprecated.txt  
/usr/share/doc/util-linux/howto-debug.txt  
/usr/share/doc/util-linux/getopt_changelog.txt  
/usr/share/doc/util-linux/release-schedule.txt  
/usr/share/doc/util-linux/00-about-docs.txt  
/usr/share/doc/util-linux/col.txt  
/var/www/html/vendor/fontawesome-free/LICENSE.txt  
/flag.txt
```

See our **flag.txt** file

Read it
`cat /flag.txt`

## Questions
1. *Question #1*. **What is the flag?**
   *Answer*: `flag{4127d0530abf16d6d23973e3df8dbecb}`
