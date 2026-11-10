# bytemancy 1

| Field | Value |
| --- | --- |
| Platform | picoCTF 2026 |
| Category | General Skills |
| Difficulty | Easy |
| Date | 2026-04-29 16:36 |

## Overview

Determine the byte sequence accepted by the supplied program.

<details>
<summary>Original challenge description</summary>

Can you conjure the right bytes? 
The program's source code can be downloaded [here](https://challenge-files.picoctf.net/c_foggy_cliff/89d4e001a32151c23b9ad54e9f12939e30d20903b113433cbd5e65df11ffabf7/app.py). 
Connect to the program with netcat:
`$ nc <ip> <port>`

</details>

## Analysis

The program compared the input with a fixed sequence of repeated bytes.

### Step 1
First, download source code and analyze it a bit

There are some lines we interested in:
```python
if user_input == "\x65"*1751:  
     print(open("./flag.txt", "r").read())  
     break
```
This code checks if we entered symbol **"\x65"** for 1751 times
### Step 2
Lets make this program think that we entered those symbols
We can do it using pipeline:
```bash
$ python3 -c 'print("\x65"*1751)' | nc foggy-cliff.picoctf.net 64973 # change ip and port on those u have personally got in the task
```

It works in the way that second command (`nc`) gets an input of what first command outputs

## Result

`picoCTF{h0w_m4ny_e's???_7dbc095c}`
