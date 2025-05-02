# Ph4nt0m 1ntrud3r
|Date|Category|Difficulty|
|--|--|--|
|2025-04-30|Forensics|Easy|
## Task description
A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag. To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder! Find the PCAP file here [Network Traffic PCAP file](https://challenge-files.picoctf.net/c_verbal_sleep/3fe089c41615b9413666bedca922e07bf6ad8894a3dabd2737735143ad2396cf/myNetworkTraffic.pcap) and try to get the flag.
## Solution 
Open file with **Wireshark**
Sort all traffic by time, from lower to upper
From the response #15 (time: 0.003102) we see that text section of request contains some *base64* code.
Collect all these parts of encoded flag and the decode it
```
cGljb0NURg==
ezF0X3c0cw==
bnRfdGg0dA==
XzM0c3lfdA==
YmhfNHJfOQ==
NjZkMGJmYg==
fQ==
```
## Flag
`picoCTF{1t_w4snt_th4t_34sy_tbh_4r_966d0bfb}`
