# Journal Fantôme

Forensique · 250 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`pointeuse.sqlite` est une base SQLite où une ligne a été supprimée. Un `DELETE` dans SQLite retire la ligne de l'index,
mais sans `VACUUM`, les octets restent dans le fichier jusqu'à ce qu'une nouvelle ligne les écrase.

```bash
sqlite3 pointeuse.sqlite .recover | grep CyberZerk
```

En dépannage, un simple `strings` sur le fichier brut retrouve aussi le texte.

```bash
strings pointeuse.sqlite | grep CyberZerk
```

**Flag :** `CyberZerk{sql1t3_d3l3t3_n3_v1d3_pas_l3s_p4g3s}`
