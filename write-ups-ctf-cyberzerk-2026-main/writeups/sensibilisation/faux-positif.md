# Faux Positif

Sensibilisation · 125 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Il y a quatre mails et un seul est du phishing. On le reconnaît à ses en-têtes : `Received` depuis `cheap-bulk-mail.ru`,
`spf=fail dkim=none dmarc=fail`, et un lien vers un domaine qui imite le vrai (`secure-login[.]ru`). C'est aussi le seul dont
le `X-Tracking-Id` est du base64 lisible (les autres ont un identifiant sans sens).

```bash
echo '<X-Tracking-Id du mail 3>' | base64 -d
```

**Flag :** `CyberZerk{Un_B0n_R3fl3x3_Un_Cl1c_Ev1t3}`
