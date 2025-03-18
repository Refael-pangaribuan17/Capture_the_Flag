# Lost Frequencies 
**Final Points:** 100 

## Description 
Zeroes, ones, dots, and dashes 
Data streams in bright flashes 

```
111 0000 10 111 1000 00 10 01 010 1011 11 111 010 000 0
```

**Note:** Wrap the capitalized flag in `KashiCTF{}`. 

---

## Writeup 

The key clues in the challenge were: 
- *Zeroes and ones*: Suggesting **binary** encoding. 
- *Dots and dashes*: Indicating **Morse code**. 

### Step 1: Convert Binary to Morse Code 
Interpreting the given binary sequence with `1` as a dash (`-`), `0` as a dot (`.`), and spaces separating characters: 

```
--- .... -. --- -... .. -. .- .-. -.-- -- --- .-. ... .
```

### Step 2: Decode Morse Code
Using [dcode.fr Morse Decoder](https://www.dcode.fr/morse-code)

> **OHNOBINARYMORSE**

---

## Flag 
```
KashiCTF{OHNOBINARYMORSE}
```
