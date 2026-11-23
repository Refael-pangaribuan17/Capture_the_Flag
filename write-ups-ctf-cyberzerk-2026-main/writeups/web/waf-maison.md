# Waf Maison (3 tours)

Web · 500 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Les trois tours racontent la même histoire. Didier a écrit un portail de connexion vulnérable à l'injection SQL. À chaque fois
qu'on le contourne, il ajoute un filtre (une regex) devant le paramètre `id`.

Flags :

- Tour 1 : `CyberZerk{N3_J4m4iS_Re1nv3nTEr_l4_R0uE}`
- Tour 2 : `CyberZerk{W4f_M41s0n_TjRs_P4s_f0ncT1oNneL}`
- Tour 3 : `CyberZerk{l3_W4f_UlT1m3_eT_1nvI0l4bl3_n0n?}`

Le paramètre `pass` passe par `mysql_real_escape_string`, ce n'est donc pas lui le point d'entrée. C'est toujours `id` qui reste
injectable. Chaque filtre est une liste noire (mots-clés SQL, espaces, guillemets, antislash...), et à chaque tour il existe une
écriture différente qui donne le même effet SQL sans déclencher la regex.

On ne publie pas ici les charges exactes. Les solutions de la communauté sont les bienvenues pour ce challenge, voir
[CONTRIBUTING.md](../../CONTRIBUTING.md).

Ce qu'il faut retenir : une liste noire ne remplace pas une requête préparée, et un correctif fait dans l'urgence en laisse
souvent d'autres ouverts.
