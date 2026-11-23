# Le Dossier Complet

Divers · 500 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

C'est une épreuve de synthèse : il faut avoir résolu trois autres challenges et récupérer le premier segment de chaque flag,
celui qui précède le premier `_`. Ces trois mots sont `Hastad` (Diffusion Imprudente), `XXE` (Export XML) et `c4rv1ng`
(Fragments). La clé est le début du SHA-256 de ces trois mots reliés par des barres verticales.

```bash
python3 -c "import hashlib; print('CyberZerk{DOSSIER_c0mpl3t_'+hashlib.sha256(b'Hastad|XXE|c4rv1ng').hexdigest()[:12]+'}')"
```

**Flag :** `CyberZerk{DOSSIER_c0mpl3t_a2a34d87d580}`
