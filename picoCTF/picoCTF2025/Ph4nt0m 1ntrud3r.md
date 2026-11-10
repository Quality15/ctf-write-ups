# Ph4nt0m 1ntrud3r

| Field | Value |
| --- | --- |
| Platform | picoCTF 2025 |
| Category | Forensics |
| Difficulty | Easy |
| Date | 2025-04-30 |

## Overview

Reconstruct the flag from the supplied packet capture.

<details>
<summary>Original challenge description</summary>

A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag. To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder! Find the PCAP file here [Network Traffic PCAP file](https://challenge-files.picoctf.net/c_verbal_sleep/3fe089c41615b9413666bedca922e07bf6ad8894a3dabd2737735143ad2396cf/myNetworkTraffic.pcap) and try to get the flag.

</details>

## Analysis

The recorded analysis uses packet ordering and payload decoding to recover the flag.

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

## Result

`picoCTF{1t_w4snt_th4t_34sy_tbh_4r_966d0bfb}`
