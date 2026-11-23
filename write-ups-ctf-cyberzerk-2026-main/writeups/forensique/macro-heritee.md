# Macro Héritée

Forensique · 250 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`macro.vba` reconstruit une chaîne morceau par morceau avec des `Chr(n)`, la décode en base64, puis la renverse avec
`StrReverse`. L'obfuscation n'est là que pour ralentir la lecture : il suffit de refaire les trois mêmes étapes.

```bash
python3 - <<'PY'
import re, base64
v = open("macro.vba").read()
b64 = "".join(chr(int(x)) for x in re.findall(r"Chr\((\d+)\)", v))
print(base64.b64decode(b64).decode()[::-1])
PY
```

Rappel au passage : on n'active jamais les macros d'un document venu de l'extérieur.

**Flag :** `CyberZerk{vba_d3s0bfusc4t10n_ch4in3_chr_b64_r3v3rs3}`
