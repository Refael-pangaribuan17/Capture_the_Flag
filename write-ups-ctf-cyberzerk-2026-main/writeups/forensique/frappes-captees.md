# Frappes Captées

Forensique · 250 points · Créé par [@PercevalFox](https://github.com/PercevalFox)

`frappes.pcap` est une capture du bus USB d'un clavier. Chaque paquet transporte un rapport HID de 8 octets : le premier
octet indique les touches de modification (Maj), le troisième le code de la touche appuyée. Il suffit de rejouer la table
de correspondance du clavier pour chaque paquet.

```bash
tshark -r frappes.pcap -Y 'usb.transfer_type==1' -T fields -e usb.capdata > hid.txt
python3 - <<'PY'
m = {4:'a',5:'b',6:'c',7:'d',8:'e',9:'f',10:'g',11:'h',12:'i',13:'j',14:'k',15:'l',
     16:'m',17:'n',18:'o',19:'p',20:'q',21:'r',22:'s',23:'t',24:'u',25:'v',26:'w',27:'x',
     28:'y',29:'z',30:'1',31:'2',32:'3',33:'4',34:'5',35:'6',36:'7',37:'8',38:'9',39:'0'}
sh = {45:'_', 47:'{', 48:'}'}
out = ""
for l in open("hid.txt"):
    b = bytes.fromhex(l.strip().replace(':', ''))
    if len(b) < 3 or b[2] == 0:
        continue
    out += sh.get(b[2], m.get(b[2], '?').upper() if b[0] & 0x22 else m.get(b[2], '?'))
print(out)
PY
```

**Flag :** `CyberZerk{usb_h1d_k3yb0ard_r3p0rt_8_0ct3ts}`
