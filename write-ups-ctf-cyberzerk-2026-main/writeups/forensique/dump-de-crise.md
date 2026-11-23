# Dump de Crise

Forensique · 300 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Le secret a été « retiré du code » dans un commit plus récent, mais il est toujours dans l'historique git.

```bash
tar xzf depot_intranet.tgz && cd depot
git log --all -p | grep CyberZerk
```

Sinon on fait `git log`, on repère le commit qui supprime le secret et on le regarde avec `git show`.

**Flag :** `CyberZerk{G1t_N0ubl13_J4m41s_R13n_Du_P4ss3}`
