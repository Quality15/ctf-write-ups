# Cookie Monster Secret Recipe

| Field | Value |
| --- | --- |
| Platform | picoCTF 2025 |
| Category | Web Exploitation |
| Difficulty | Easy |
| Date | 2025-04-30 |

## Overview

Locate the recipe stored by the challenge website.

<details>
<summary>Original challenge description</summary>

Cookie Monster has hidden his top-secret cookie recipe somewhere on his website. As an aspiring cookie detective, your mission is to uncover this delectable secret. Can you outsmart Cookie Monster and find the hidden recipe? You can access the Cookie Monster [here](http://verbal-sleep.picoctf.net:60118/) and good luck

</details>

## Analysis

The flag was stored in a Base64-encoded HTTP cookie.

On the site there is a cookie value **secret_recipe**
Copy it and decode from **base64**

## Result

`picoCTF{c00k1e_m0nster_l0ves_c00kies_A964A134}`
