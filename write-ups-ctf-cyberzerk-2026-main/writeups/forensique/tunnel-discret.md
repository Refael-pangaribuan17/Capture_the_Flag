# Tunnel Discret

Forensique · 350 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`capture.pcap` montre un processus qui fait sortir des données par des requêtes DNS, un canal que peu de pare-feux
surveillent. Chaque sous-domaine demandé a la forme `NN.<hex>.exfil-…`, où `NN` est le numéro d'ordre du morceau. Il suffit
de trier les requêtes par ce numéro et de recoller les morceaux hexadécimaux.

```bash
tshark -r capture.pcap -Y 'dns.flags.response==0' -T fields -e dns.qry.name \
  | grep exfil | sort -t. -k1 -n \
  | awk -F. '{print $2}' | tr -d '\n' | xxd -r -p
```

**Flag :** `CyberZerk{dns_3xf1ltr4t10n_r34ss3mbl3_l3s_s0us_d0m41n3s}`
