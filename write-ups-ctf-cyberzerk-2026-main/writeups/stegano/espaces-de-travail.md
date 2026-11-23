# Espaces de Travail

Stéganographie · 200 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`note.txt` paraît anodin, mais il pèse plus lourd que son texte visible. Entre les caractères se cachent des espaces de
largeur nulle, invisibles à l'écran : un caractère (U+200B) joue le rôle du 0, l'autre (U+200C) celui du 1. Mis bout à bout,
ces bits forment des octets.

```bash
python3 - <<'PY'
t = open("note.txt", encoding="utf-8").read()
bits = "".join("0" if c == "​" else "1" for c in t if c in "​‌")
print("".join(chr(int(bits[i:i+8], 2)) for i in range(0, len(bits) - 7, 8)))
PY
```

**Flag :** `CyberZerk{z3r0_w1dth_c_3st_pas_vis1bl3}`
