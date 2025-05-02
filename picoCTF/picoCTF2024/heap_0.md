# heap 0
Write-Up by **Mttttt** *2024-06-25*

## Task description
Are overflows just a stack concern? Download the binary [here](https://artifacts.picoctf.net/c_tethys/28/chall). Download the source [here](https://artifacts.picoctf.net/c_tethys/28/chall.c)Connect with the challenge instance here:
`nc tethys.picoctf.net 50970`


- *Category*: **Binary Exploitation**
- *Difficulty*: **Easy**

## Solution
Connect to `nc tethys.picoctf.net 50970`

Choose option 2 (Write buffer)
And do simple Buffer Overflow by writing a log of characters

Then, choose option 4 (See flag)

And get the answer

## Answer
`picoCTF{my_first_heap_overflow_76775c7c}`
