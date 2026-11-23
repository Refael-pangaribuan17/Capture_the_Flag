# Pointeuse Fantôme

Web · 100 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Le site pose un cookie `profil`. C'est du base64 qui cache un JSON du genre `{"employe":"...","role":"employe"}`, et rien
n'est signé. On le décode, on remplace le rôle par `manager`, on réencode en base64 et on recharge la page. La vue manager
affiche le vrai registre des heures sup, avec le flag.

```bash
echo -n '{"role":"manager"}' | base64   # eyJyb2xlIjoibWFuYWdlciJ9
```

On remplace ensuite le cookie `profil` par cette valeur (outils de développement du navigateur, onglet Stockage ou Application).

**Flag :** `CyberZerk{P0int3us3_Qu1_0ubl13_L3s_H3ur3s_Sup}`
