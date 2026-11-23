# Diffusion Imprudente

Cryptographie · 250 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`broadcast.txt` contient trois chiffrés RSA du même message pour trois destinataires, avec le même exposant `e = 3` et trois
modules différents. Sans bourrage aléatoire, chaque chiffré vaut `m³ mod n_i`. Le théorème des restes chinois recolle les
trois en un seul `m³ mod (n1·n2·n3)`, et comme `m³` est plus petit que ce produit, il suffit d'une racine cubique entière pour
retrouver `m`. C'est l'attaque de Håstad.

```python
import re
from functools import reduce
from gmpy2 import mpz, iroot

d = open("broadcast.txt").read()
n = [mpz(x) for x in re.findall(r"n\d+ = (\d+)", d)]
c = [mpz(x) for x in re.findall(r"c\d+ = (\d+)", d)]

N = reduce(lambda a, b: a * b, n)
x = mpz(0)
for ci, ni in zip(c, n):
    Ni = N // ni
    x += ci * Ni * pow(Ni, -1, ni)

m, _ = iroot(x % N, 3)
m = int(m)
print(m.to_bytes((m.bit_length() + 7) // 8, "big").decode())
```

**Flag :** `CyberZerk{Hastad_br0adcast_3_d3st1nat41r3s_1_m3ss4g3}`
