# Plan de Charge

Stéganographie · 350 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Le message est caché dans les bits de poids faible du canal bleu de `plan_de_charge.png`, mais pas dans l'ordre des pixels.
Les positions suivent une permutation pseudo-aléatoire dont la graine (1337) est donnée avec le challenge. Un outil LSB
séquentiel comme `zsteg` ne trouve donc rien, il faut rejouer la même permutation.

```bash
python3 - <<'PY'
import numpy as np
from PIL import Image
flat = np.array(Image.open("plan_de_charge.png"))[:, :, 2].flatten()
ordre = np.random.default_rng(1337).permutation(len(flat))[:47*8]
bits = [flat[p] & 1 for p in ordre]
print(bytes(int("".join(map(str, bits[i:i+8])), 2) for i in range(0, len(bits), 8)).decode())
PY
```

**Flag :** `CyberZerk{lsb_d1sp3rs3_p4r_prng_pas_s3qu3nt13l}`
