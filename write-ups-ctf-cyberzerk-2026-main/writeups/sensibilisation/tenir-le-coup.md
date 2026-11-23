# Tenir le Coup

Sensibilisation · 150 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Le récit adressé à Marc_V cache un acrostiche : la première lettre de chaque ligne, lues de haut en bas, forment le message.

```bash
awk '{printf substr($0,1,1)}' recit.txt; echo
```

Le message qu'on obtient est aussi le flag. Si tu traverses une période difficile, parles-en à quelqu'un : un collègue, un
proche, un médecin. Demander de l'aide n'est pas une faiblesse.

**Flag :** `CyberZerk{TUNESPASSEUL}`
