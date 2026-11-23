# Clés en Main

Cryptographie · 350 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Le fichier `cle_publique_et_message.txt` donne `n`, `e` et `c` (RSA). Le point faible est que les deux nombres premiers
qui forment `n` sont très proches l'un de l'autre. Dans ce cas la factorisation de Fermat marche tout de suite : on cherche
`a` tel que `a² − n` soit un carré parfait, alors `p = a − b` et `q = a + b`.

```python
import math, re, sys

# lit n, e et c dans le fichier passé en argument
texte = open(sys.argv[1]).read()
n, e, c = (int(re.search(rf"^{v}\s*=\s*(\d+)", texte, re.M).group(1)) for v in "nec")

a = math.isqrt(n) + 1
while True:
    b2 = a*a - n; b = math.isqrt(b2)
    if b*b == b2:
        p, q = a-b, a+b
        break
    a += 1
d = pow(e, -1, (p-1)*(q-1))
m = pow(c, d, n)
print(m.to_bytes((m.bit_length()+7)//8, "big").decode())
```

On le lance avec `python3 cle_pub.py cle_publique_et_message.txt`.

**Flag :** `CyberZerk{F3rm4t_C4ss3_L3s_Pr3m13rs_Tr0p_Pr0ch3s}`
