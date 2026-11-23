# Fragments

Forensique · 300 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`secteur.raw` est un secteur brut, sans système de fichiers. Un PNG y est noyé au milieu d'autres octets. On le retrouve à
sa signature de début (`89 50 4E 47`) et à sa fin (`IEND`), on découpe entre les deux, puis on lit son chunk de texte.

```bash
python3 - <<'PY'
raw = open("secteur.raw", "rb").read()
s = raw.find(b"\x89PNG\r\n\x1a\n")
e = raw.find(b"IEND", s) + 8
open("out.png", "wb").write(raw[s:e])
PY
exiftool out.png | grep -i flag
```

`binwalk -e secteur.raw` fait le même découpage automatiquement.

**Flag :** `CyberZerk{c4rv1ng_l3_PNG_surv1t_a_l_3ff4c3m3nt}`
