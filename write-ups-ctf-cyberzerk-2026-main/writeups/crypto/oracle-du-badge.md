# L'Oracle du Badge

Cryptographie · 400 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Le service chiffre `PREFIXE || ta saisie || SECRET` en AES-128-ECB et te renvoie le résultat en hexadécimal. Le défaut d'ECB,
c'est que deux blocs de 16 octets identiques donnent deux blocs chiffrés identiques. Comme tu choisis une partie du clair,
tu peux deviner le secret un octet à la fois.

D'abord il faut trouver la longueur du préfixe (13 ici). On envoie des `A` en nombre croissant, et dès que deux blocs chiffrés
consécutifs sont égaux, on sait que le bourrage a aligné nos `A` sur des blocs complets. Ensuite on cale le secret pour qu'il
ne reste qu'un seul octet inconnu à la fin d'un bloc, on compare avec les 256 valeurs possibles, et on recommence pour l'octet
suivant.

```python
import requests
BS = 16
U = "https://oracle-badge.cyberzerk.fr/?data="
enc = lambda b: bytes.fromhex(requests.get(U + b.hex()).text.strip())
blk = lambda c: [c[i:i+BS] for i in range(0, len(c), BS)]

def longueur_prefixe():
    for p in range(BS):
        b = blk(enc(b"A" * (p + 2*BS)))
        for i in range(len(b) - 1):
            if b[i] == b[i+1]:
                return i*BS - p

P = longueur_prefixe()
align = (BS - P % BS) % BS
base = P + align
connu = b""
while not connu.endswith(b"}"):
    pad = b"A" * (align + (BS - 1 - len(connu) % BS))
    bloc = (base + (len(connu) // BS) * BS) // BS
    ref = blk(enc(pad))[bloc]
    for x in range(256):
        if blk(enc(pad + connu + bytes([x])))[bloc] == ref:
            connu += bytes([x])
            break
print(connu.decode())
```

**Flag :** `CyberZerk{EcB_r3v3l3_1_0ct3t_a_la_f0is_m3m3_av3c_pr3f1x3}`
