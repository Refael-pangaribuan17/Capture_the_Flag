# Restructuration

Web · 350 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Le générateur d'aperçus va chercher côté serveur l'URL qu'on lui donne : c'est une SSRF. Le coffre `interne.php` ne répond
qu'aux requêtes qui viennent de la machine elle-même (boucle locale). Le site bloque bien `127.0.0.1` et `localhost`, mais
seulement en comparant des chaînes, donc les autres écritures de la même adresse passent (`0.0.0.0`, IP en décimal...).

```
?url=http://0.0.0.0:8080/interne.php
?url=http://2130706433:8080/interne.php
```

Attention au port : il faut mettre `:8080`, c'est le port du conteneur. Sans lui la requête part sur le port 80 où rien
n'écoute et on obtient « Impossible de récupérer cette URL ».

Le serveur interroge alors `interne.php` depuis lui-même et le flag s'affiche.

**Flag :** `CyberZerk{SSRF_V3rs_L3_C0ffr3_Int3rn3}`
