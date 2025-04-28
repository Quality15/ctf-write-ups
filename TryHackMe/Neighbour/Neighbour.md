# Neighbour
Write-Up by **Mttttt** *2024-06-09*
## Room Description

Check out our new cloud service, Authentication Anywhere -- log in from anywhere you would like! Users can enter their username and password, for a totally secure login process! You definitely wouldn't be able to find any secrets that other people have in their profile, right?

**Access this challenge** by deploying both the vulnerable machine by pressing the green "Start Machine" button located within this task, and the TryHackMe AttackBox by pressing the  "Start AttackBox" button located at the top-right of the page.

Navigate to the following URL using the AttackBox: [http://10.10.146.220](http://10.10.146.220)[](http://10.10.146.220)

  

Check out similar content on TryHackMe:

- [IDOR](https://tryhackme.com/room/idor)

## Solution

Go to the site with our IP:
http://10.10.146.220/

See login page
Lets take a look at source code:
```html
... other code
<!-- use guest:guest credentials until registration is fixed -->
...
```

Use this credentials to login

That is our URL after logging in

http://10.10.146.220/profile.php?user=guest

Lets change HTTP parameter to `admin`

http://10.10.146.220/profile.php?user=admin

And see our flag on site

## Questions

1. *Question #1*. Find the flag on your neighbor's logged in page!
   *Answer*: **flag{66be95c478473d91a5358f2440c7af1f}**
