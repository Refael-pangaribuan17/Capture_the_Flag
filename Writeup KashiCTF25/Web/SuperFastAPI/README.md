# SuperFastAPI ⚡

**Final Points:** 100


## Description
Made my very first API!

However, I have to still integrate it with a Frontend so can't do much at this point lol.


Flag format: `KashiCTF{your_flag_here};`

## Instance
``http://kashictf.iitbhucybersec.in:port/``

----
## Writeup

On analyzing the website it was a simple api app with no frontend

<img src="images/website.png" alt="web_api">

Then I changed the URL to search for `/robots.txt` or `/.git/` for some hidden instructions, as I got nothing from the sources and application tab on developer tools or even from burp suite. 

 This made me use a Fuzzer like `gobuster` or an [Online URL fuzzer](https://pentest-tools.com/website-vulnerability-scanning/discover-hidden-directories-and-files) 

where I found:
<img src="images/fuzzer.png" alt="fuzz">

On digging deeper I reached ``http://kashictf.iitbhucybersec.in:port/docs/``
Which had OpenAPI service.

<img src="images/super.png" alt="super">

<img src="images/creat.png" alt="create_user">
There on trying multiple things, I found that 
The flag was only visible to the ``admin``

But no user named admin existed.

I then created a user `admin`

<img src="images/admin_cret.png" alt="creation">

but he was also denied the permission to get the flag,

And then I saw an update user tab

and thought of changing the attributes of admin user and also assign role to him.
```json
{
  "fname": "Admin",
  "lname": "_Admin",
  "email": "admin@admin.com",
  "gender": "male",
  "role": "admin"
}
```
<img src="images/admin_up.png" alt="admin_update">

Then I tried getting the flag from flag tab using `admin'

which was successful and gave 
```
        Requested URL
              http://kashictf.iitbhucybersec.in:port/flag/admin
```

<img src="images/flag_on_web.png" alt="got_flag">


on reaching there I got the flag.

<img src="images/theflag.png" alt="flag">



---
## Flag

```
KashiCTF{your_flag_here}
```                 
