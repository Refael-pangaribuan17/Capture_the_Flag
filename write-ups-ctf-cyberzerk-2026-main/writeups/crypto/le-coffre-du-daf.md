# Le Coffre du DAF

Cryptographie · 200 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`coffre_chiffre.hex` est un message passé au XOR avec une clé qui se répète. Même astuce que pour la note de frais :
le flag commence par `CyberZerk{`, donc `chiffré XOR début connu` donne directement la clé (`TRICATEL`, 8 octets).

```python
data = bytes.fromhex(open("coffre_chiffre.hex").read().strip())
cle = bytes(data[i] ^ b"CyberZerk{"[i] for i in range(8))
print(bytes(data[i] ^ cle[i % 8] for i in range(len(data))).decode())
```

**Flag :** `CyberZerk{X0R_R3p3t3_C_3st_P4s_S3cur1s3}`
