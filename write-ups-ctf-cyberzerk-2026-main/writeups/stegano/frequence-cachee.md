# Fréquence Cachée

Stéganographie · 150 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`message.wav` ne laisse rien entendre d'intelligible. Le texte n'est pas dans le son mais dans sa forme : il est dessiné dans
le spectrogramme, c'est-à-dire la représentation des fréquences au cours du temps.

```bash
sox message.wav -n spectrogram -o spectro.png
```

On peut aussi ouvrir le fichier dans Audacity ou Sonic Visualiser et passer en vue spectrogramme. Le flag se lit directement
sur l'image.

**Flag :** `CyberZerk{sp3ctr0_wav}`
