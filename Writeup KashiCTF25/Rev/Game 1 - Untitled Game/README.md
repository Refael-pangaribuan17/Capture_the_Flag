# Game 1 - Untitled Game 🎮

**Final Points:** 100


## Description
We made a game.


Flag format: `KashiCTF{your_flag_here};`

## Link -
 [Drive Link](https://drive.google.com/file/d/1bf4WnxE81YIizN2e77x5PrkqGPwllgki/view?usp=drive_link) {Download the game from here} ==> `Challgame.exe`

----
## Writeup

On downloading the files, I ran the command 
```
grep -r "KashiCTF{"
```
Which showed that this string existed inside the binary `Challgame.exe`

so I ran 
```
grep -a "KashiCTF{" Challgame.exe
```

Which gave the flag.
<img src="images/sol.png" alt="solution">

---
## The Game

I ran it using wine.
 
<img src="images/wine.png" alt="wine">

It was a simple same where the objective was to escape the trap.

<img src="images/game.png" alt="game">

on clicking let's begin
<img src="images/ingame.png" alt="game">

---
## Flag

```
KashiCTF{N07_1N_7H3_G4M3}
```                 

