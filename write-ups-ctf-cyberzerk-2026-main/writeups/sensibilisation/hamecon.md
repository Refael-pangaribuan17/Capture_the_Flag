# Hameçon

Sensibilisation · 150 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`courriel.eml` ressemble à un message interne, mais c'est du phishing. Le nom affiché de l'expéditeur ne correspond pas au
vrai domaine du `Return-Path` (en `.xyz`), et le texte du lien ne mène pas là où il dit. Dans le vrai `href`, le paramètre
`id` est le flag encodé en base64url.

```bash
python3 - <<'PY'
import re, base64, email
m = email.message_from_file(open("courriel.eml"))
corps = m.get_payload(decode=True).decode()
href = re.search(r'href="([^"]+)"', corps).group(1)
p = re.search(r"id=([A-Za-z0-9_\-]+)", href).group(1)
print(base64.urlsafe_b64decode(p + "=" * (-len(p) % 4)).decode())
PY
```

Avant de cliquer sur un lien, on regarde toujours sa vraie adresse et l'en-tête du message.

**Flag :** `CyberZerk{n3_cl1qu3z_pas_1nsp3ct3z_l3_l13n}`
