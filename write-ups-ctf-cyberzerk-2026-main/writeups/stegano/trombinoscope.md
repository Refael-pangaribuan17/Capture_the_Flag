# Trombinoscope

Stéganographie · 175 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Le flag n'est pas dans les pixels mais dans les métadonnées EXIF du JPEG, champ `UserComment`.

```bash
exiftool trombi_marc_v.jpg
```

Sans exiftool : `python3 -c "import piexif;print(piexif.load('trombi_marc_v.jpg')['Exif'][37510])"`.

**Flag :** `CyberZerk{M3t4d0nn33s_EXIF_B4v4rd3s}`
