# Mail du DRH

Forensique · 150 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

On ouvre `note_du_drh.eml` et on lit les en-têtes. Le `From` annonce `drh@tricatel-cyber.fr`, mais le `Received` vient de
`mail-cheap-relay.ru`, avec `Received-SPF: fail`, `dmarc=fail` et un `Reply-To` qui pointe vers l'attaquant. Le mail est usurpé.

La pièce jointe `note_interne_rh.txt` est en base64 (`Content-Transfer-Encoding: base64`). Décodée, elle contient l'ordre de
surveillance des arrêts maladie et le flag.

**Flag :** `CyberZerk{M4il_Sp00f3_P0ur_Surv31ll3r_L3s_Arr3ts}`
