# Vidage de Mémoire

Forensique · 450 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Le flag n'est pas en clair dans `heap.dump`, un `strings | grep` ne donne rien. Il faut repérer la structure qui le contient.
Juste après le marqueur `AUTHBLK` viennent un octet de clé XOR, deux octets de longueur (en petit-boutiste), puis le jeton
XORé avec cette clé.

```bash
python3 - <<'PY'
raw = open("heap.dump", "rb").read()
i = raw.find(b"AUTHBLK\x00") + 8
cle = raw[i]
ln = int.from_bytes(raw[i+1:i+3], "little")
print(bytes(b ^ cle for b in raw[i+3:i+3+ln]).decode())
PY
```

**Flag :** `CyberZerk{c0r3_dump_struct_x0r_auth_bl0ck}`
