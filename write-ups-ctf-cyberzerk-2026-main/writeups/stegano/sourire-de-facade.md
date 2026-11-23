# Sourire de façade

Stéganographie · 250 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`motivation.png` est en fait une image WebP, avec une archive ZIP collée à la fin du fichier (on voit la signature `PK\x03\x04`
après les données de l'image). Il suffit de l'ouvrir comme un zip :

```bash
unzip motivation.png
```

On récupère `journal_intime.txt`, qui contient le flag.

**Flag :** `CyberZerk{S0ur1r3_P0ur_C4ch3r_L3_Burn0ut}`
