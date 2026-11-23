# Second Facteur

Sensibilisation · 150 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

L'énoncé donne un secret en base32 et un instant précis (en temps Unix). Il faut calculer le code TOTP valable à cet
instant : c'est le même calcul que les applications d'authentification à deux facteurs, avec SHA-1, un pas de 30 secondes et
6 chiffres.

```bash
oathtool --totp -b "JBSWY3DPEHPK3PXP" --now='@1762900000'
```

Le code obtenu complète le flag.

**Flag :** `CyberZerk{2fa_053377}`
