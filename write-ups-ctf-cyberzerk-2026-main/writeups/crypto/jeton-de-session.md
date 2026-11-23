# Le Jeton de Session

Cryptographie · 350 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Les 624 jetons fournis sont 624 sorties consécutives du générateur aléatoire de Python (un Mersenne Twister). C'est exactement
la taille de son état interne. Chaque sortie est l'état « mélangé » par une suite de décalages et de masques, et cette
opération est réversible. En l'inversant sur les 624 valeurs, on reconstruit le générateur, et on peut alors prédire ce qu'il
a sorti ensuite : ce sont les octets qui ont servi de clé XOR pour `secret.bin`.

```python
import random, struct

def untemper(y):
    y ^= y >> 18
    y ^= (y << 15) & 0xEFC60000
    for _ in range(7):
        y ^= (y << 7) & 0x9D2C5680
    y ^= (y >> 11) ^ (y >> 22)
    return y & 0xFFFFFFFF

fuite = [int(x) for x in open("tokens.txt").read().split()]
etat = tuple(untemper(v) for v in fuite[:624])
r = random.Random()
r.setstate((3, etat + (624,), None))

c = open("secret.bin", "rb").read()
cle = b""
while len(cle) < len(c):
    cle += struct.pack(">I", r.getrandbits(32))
print(bytes(a ^ b for a, b in zip(c, cle)).decode())
```

**Flag :** `CyberZerk{MT19937_s3_cl0n3_av3c_624_s0rt13s_untemper}`
