# Rallonge

Cryptographie · 400 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Le jeton est signé avec `SHA256(secret || message)`, un secret de 16 octets. SHA-256 travaille par blocs et son résultat n'est
rien d'autre que son état interne à la fin du dernier bloc. On peut donc repartir de la signature, sans connaître le secret,
et continuer à hacher : on obtient la signature valide de `secret || message || bourrage || &role=admin`. Le digest forgé
sert de clé AES pour `cipher.bin`. Le module `sha256ext.py` fourni avec le challenge fait la reprise du calcul.

```python
import re
from Crypto.Cipher import AES
from sha256ext import extend

t = open("token.txt").read()
msg = re.search(r"message = (.+)", t).group(1).encode()
tag = bytes.fromhex(re.search(r"tag\s+= ([0-9a-f]+)", t).group(1))
lg = int(re.search(r"longueur_secret = (\d+)", t).group(1))

forge = extend(tag, lg + len(msg), b"&role=admin")
pt = AES.new(forge, AES.MODE_ECB).decrypt(open("cipher.bin", "rb").read())
print(pt[:-pt[-1]].decode())
```

L'outil `hashpumpy` fait la même chose si tu préfères ne pas utiliser le module fourni.

**Flag :** `CyberZerk{l3ngth_3xt3ns10n_f0rg3_l4_s1gn4tur3_du_c00k13}`
