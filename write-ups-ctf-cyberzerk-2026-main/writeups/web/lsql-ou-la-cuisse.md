# L'SQL ou la cuisse ?

Web · 100 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Injection SQL classique sur le formulaire de connexion :

```
username: admin'--
password: (ce que tu veux)
```

Le `'` ferme la chaîne dans la requête, `--` commente tout ce qui suit, donc le mot de passe n'est jamais vérifié.
On arrive connecté en admin, avec la note du PDG et le flag.

**Flag :** `CyberZerk{SQL_1nj3ct10n_C4us3d_By_Burn0ut}`
