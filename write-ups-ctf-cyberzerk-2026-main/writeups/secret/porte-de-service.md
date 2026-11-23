# La Porte de Service

Divers · 350 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Challenge non listé. On fournit la capture d'une réponse du service de maintenance (`reponse_http.txt`). Le corps du message
ne dit rien d'utile, mais il faut lire tous les en-têtes, pas seulement le texte. L'un d'eux, `X-Service-Door`, porte le flag
en base64.

```bash
grep -i '^X-Service-Door:' reponse_http.txt | awk '{print $2}' | base64 -d; echo
```

Les serveurs en disent souvent long par leurs en-têtes de réponse ; c'est la première chose à regarder.

**Flag :** `CyberZerk{p0rt3_d3_s3rv1c3_cach33_dans_un_3nt3t3}`
