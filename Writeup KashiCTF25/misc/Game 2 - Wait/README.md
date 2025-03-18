# Game 1 - Wait ⏰
**Final Points:** 195


## Description
We made a game.


Flag format: `KashiCTF{your_flag_here};`

## Link -
 [Drive Link](https://drive.google.com/file/d/1GDYmOiW54pPLFxfQaBOOS5IPEAoplFPy/view?usp=drive_link) {Download the game from here} ==> `wait.exe`

----
## Writeup

On downloading the game file,

![game here](images/sus.png)

The logo of the game was `sus`. 😆😆

I ran the command 
```
grep -r "KashiCTF{"
```
but got nothing from it.

![grep won't work here kiddo](images/nogrep.png)

Then I ran it using wine.

![game start](images/waiting.png)

It was a simple game, and its objective was to wait for `48 hours` or `172800 Seconds` for the flag to be revealed.

I could have waited for the flag to be revealed automatically after 2 days but the CTF competition was for 24 hours only in itself.

So, now I could have used a tool like [Cheat Engine](https://www.cheatengine.org/) or just try changing the Date of my system to see if it works.

![before the date change](images/bef.png)

and after changing the date to 2 days later, I got

![After the date change](images/af.png)

the flag !!!

It was very easy after all.

We could have also used Cheat engine to change the time_remaining attribute 

---
## Flag

```
KashiCTF{Ch4kr4_Vyuh}
```                 

