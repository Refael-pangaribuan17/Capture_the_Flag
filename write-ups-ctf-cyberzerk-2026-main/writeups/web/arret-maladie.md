# Arrêt Maladie

Web · 100 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

C'est une IDOR. La page charge le dossier avec `?dossier_id=1042` sans vérifier que ce dossier est bien le tien.
Le collègue en arrêt est « juste avant le vôtre » : en passant à `?dossier_id=1041`, on tombe sur son arrêt et sur le flag.

**Flag :** `CyberZerk{ID0R_M4n4g3m3nt_T0x1qu3}`
