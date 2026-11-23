# Badge d'Accès

Stéganographie · 125 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`badge_marc_v.png` est un vrai PNG. Le message est caché dans le bit de poids faible (LSB) du canal bleu, ligne par ligne, sous
la bande d'en-tête. `zsteg badge_marc_v.png` le sort directement. Sans zsteg :

```python
from PIL import Image
p = Image.open('badge_marc_v.png').convert('RGB').load()
bits = ''.join(str(p[x, y][2] & 1) for y in range(43, 300) for x in range(480))
print(bytes(int(bits[i:i+8], 2) for i in range(0, 400, 8)).split(b'\x00')[0].decode())
```

**Flag :** `CyberZerk{B4dg3_N0cturn3_H3ur3s_C4ch33s}`
