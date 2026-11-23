# Appels à l'aide

Forensique · 100 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

On ouvre la capture réseau dans Wireshark, clic droit sur un paquet HTTP, *Follow > HTTP Stream*. On y voit un
`POST /adieu.php` vers un serveur inconnu, et son corps contient le flag. `strings capture.pcap` marche aussi.

**Flag :** `CyberZerk{Exf1ltr4t10n_HTTP_D3s3sp01r}`
