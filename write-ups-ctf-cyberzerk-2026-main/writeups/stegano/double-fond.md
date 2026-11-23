# Double Fond

Stéganographie · 350 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Il y a deux niveaux. Un chunk PNG `tEXt` de mot-clé `cle` contient une clé en base64. Après le chunk `IEND`, des octets
supplémentaires sont collés au fichier : c'est le flag passé au XOR avec cette clé.

```python
d = open("affiche_crise.png", "rb").read()
import base64, re
k = base64.b64decode(re.search(rb"tEXtcle\x00([A-Za-z0-9+/=]+)", d).group(1))
tr = d[d.rfind(b"IEND")+8:]
print(bytes(tr[i] ^ k[i % len(k)] for i in range(len(tr))).decode())
```

On voit la clé avec `exiftool` ou `strings`, et les octets après `IEND` avec `binwalk` ou en lisant la fin du fichier.

**Flag :** `CyberZerk{St3g0_Pu1s_X0R_B13n_J0u3}`
