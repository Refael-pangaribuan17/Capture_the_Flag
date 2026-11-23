# Solde de Congés

Web · 350 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Le solde d'un compte est de 1 jour. Quand on réserve, le serveur vérifie que le solde est positif, attend un court instant,
puis retire un jour. Entre la vérification et le retrait il n'y a aucun verrou. Si on envoie plusieurs réservations en même
temps, plusieurs passent la vérification avant que la première ait retiré son jour, et le solde finit négatif. La route
`/flag` n'affiche le flag que dans ce cas.

```bash
B=https://solde-conges.cyberzerk.fr
curl -s -c j -X POST $B/start
seq 12 | xargs -P12 -I_ curl -s -b j -X POST $B/book > /dev/null
curl -s -b j $B/flag
```

Le flag est propre à chaque session : sa fin (10 caractères hexadécimaux) change d'un joueur à l'autre. Il faut coller le
flag qu'on reçoit soi-même.

**Flag :** `CyberZerk{r4c3_c0nd1t10n_s0ld3_n3g4t1f_<10 caractères hexadécimaux propres à ta session>}`
