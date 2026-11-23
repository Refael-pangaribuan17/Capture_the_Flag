# Ingénierie Sociale

Sensibilisation · 250 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`messages_internes.zip` contient trois fichiers : un mail, une note du standard et un chat. Chacun cache un morceau du flag,
et chaque morceau est encodé différemment. Rien n'indique l'encodage ni l'ordre, il faut les trouver.

**L'ordre.** Les numéros ne servent à rien ici, les fichiers ont des horodatages : le mail est de 09:12, la note du standard
de 11:47 et le chat de 16:03. Les morceaux se lisent dans l'ordre de l'attaque : mail, standard, chat.

**Le mail.** `Q3liZXJaZXJre0NoNDFu` finit par `u` et a la tête d'un base64 (lettres, chiffres, 20 caractères). Décodé :
`CyberZerk{Ch41n`.

**La note du standard.** `3_1at3a13e13_F0` ne ressemble à rien de lisible, mais les chiffres sont à leur place et seules les
lettres sont décalées. Un ROT13 donne `3_1ng3n13r13_S0`.

**Le chat.** `6331346c335f4272317333337d` n'a que des chiffres et des lettres de a à f, c'est de l'hexadécimal. Décodé :
`c14l3_Br1s33}`.

```bash
echo Q3liZXJaZXJre0NoNDFu | base64 -d
echo '3_1at3a13e13_F0' | tr 'A-Za-z' 'N-ZA-Mn-za-m'
echo 6331346c335f4272317333337d | xxd -r -p
```

Bout à bout : `CyberZerk{Ch41n3_1ng3n13r13_S0c14l3_Br1s33}`.

**Flag :** `CyberZerk{Ch41n3_1ng3n13r13_S0c14l3_Br1s33}`
