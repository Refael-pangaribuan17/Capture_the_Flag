# Nuit du 13

Forensique · 150 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Dans `access.log`, au milieu du bruit, une seule requête part vers un export sensible et aboutit : code 200, grosse taille de
réponse, IP externe, User-Agent `curl`. Le flag est la valeur du paramètre `token` de cette requête, encodée dans l'URL.

```bash
grep "/export.php" access.log | grep '" 200 '
```

Il reste à décoder la valeur de `token=` (CyberChef, *URL Decode*).

**Flag :** `CyberZerk{L0g_4n4lys3_Exf1l_C0nf1rm33}`
