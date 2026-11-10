# head-dump

| Field | Value |
| --- | --- |
| Platform | picoCTF 2025 |
| Category | Web Exploitation |
| Difficulty | Easy |
| Date | 2025-04-29 |

## Overview

Determine whether the application's diagnostic interface exposes process memory.

<details>
<summary>Original challenge description</summary>

Welcome to the challenge! In this challenge, you will explore a web application and find an endpoint that exposes a file containing a hidden flag. The application is a simple blog website where you can read articles about various topics, including an article about API Documentation. Your goal is to explore the application and find the endpoint that generates files holding the server’s memory, where a secret flag is hidden. The website is running [picoCTF News](http://verbal-sleep.picoctf.net:53749/).

</details>

## Analysis

The application exposed a heap dump containing the flag.

Just go to documentation page and scroll down to the `/heapdump`
**Try Out** this API callout and download heapdump file
Then search for `picoCTF{` and find our flag

## Result

`picoCTF{Pat!3nt_15_Th3_K3y_388d10f7}`
