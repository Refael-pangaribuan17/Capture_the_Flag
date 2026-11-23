# Note de Frais

Cryptographie · 150 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`note_chiffree.txt` est du base64. Une fois décodé, on obtient un texte où seules les lettres sont brouillées
(accolades et chiffres intacts), du Vigenère donc.

Pour trouver la clé, on sait que le flag commence par `CyberZerk{`. En comparant ces 9 lettres avec le début du
texte chiffré, on lit la clé : elle se répète tous les 6 caractères, c'est `FOLACE`. Il reste à déchiffrer le reste.

```bash
base64 -d note_chiffree.txt    # HmmetDjfv{...}
```

**Flag :** `CyberZerk{Pr1m3s_CODIR_P3nd4nt_L3s_R3fus_D3_C0ng3s}`
