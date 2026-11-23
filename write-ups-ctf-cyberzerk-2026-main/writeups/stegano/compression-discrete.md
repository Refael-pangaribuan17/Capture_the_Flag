# Compression Discrète

Stéganographie · 400 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Le message n'est pas dans les pixels de `photo.jpg` mais dans les coefficients DCT, ceux que le JPEG utilise pour compresser.
C'est la méthode jsteg : elle cache un bit dans le bit de poids faible de chaque coefficient AC, en laissant de côté les
coefficients valant 0 ou 1. Un outil LSB sur les pixels ne voit rien.

```bash
jsteg reveal photo.jpg -
```

À défaut de l'outil `jsteg`, `stegoveritas photo.jpg` explore aussi cette piste.

**Flag :** `CyberZerk{jst3g_lsb_d3s_c03ff1c13nts_dct_jp3g}`
