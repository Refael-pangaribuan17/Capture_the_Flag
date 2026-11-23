# Signature Unique

Cryptographie · 550 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`signatures.json` contient deux signatures ECDSA (courbe secp256k1) de deux messages différents, et le `r` est le même dans
les deux. Ça veut dire que le même nonce `k` a servi deux fois. À partir de là c'est de l'algèbre modulo l'ordre `n` de la
courbe : `k = (z1 − z2) / (s1 − s2)`, puis la clé privée `d = (s1·k − z1) / r`, où `z` est le SHA-256 du message. La clé AES
de `vault.bin` est le SHA-256 de `d` écrit en décimal.

```python
import json, hashlib
from Crypto.Cipher import AES

n = 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFEBAAEDCE6AF48A03BBFD25E8CD0364141
inv = lambda a: pow(a % n, -1, n)
h = lambda m: int.from_bytes(hashlib.sha256(m.encode()).digest(), "big") % n

d = json.load(open("signatures.json"))
r, s1, s2 = d["r1"], d["s1"], d["s2"]
k = (h(d["msg1"]) - h(d["msg2"])) * inv(s1 - s2) % n
priv = (s1 * k - h(d["msg1"])) * inv(r) % n

cle = hashlib.sha256(str(priv).encode()).digest()
pt = AES.new(cle, AES.MODE_ECB).decrypt(open("vault.bin", "rb").read())
print(pt[:-pt[-1]].decode())
```

**Flag :** `CyberZerk{ECDSA_m3m3_n0nc3_d0nn3_la_cl3_pr1v33}`
