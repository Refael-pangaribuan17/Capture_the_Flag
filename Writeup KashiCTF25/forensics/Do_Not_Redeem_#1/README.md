# Do Not Redeem #1

**Final Points:** 319


## Description
Uh oh, we're in trouble again. Kitler's Amazon Pay wallet got emptied by some scammer. Can you figure out the OTP sent to kitler right before that happened, as well as the time (unix timestamp in milliseconds) at which kitler received that OTP?

Flag format: `KashiCTF{OTP_TIMESTAMP}`, i.e. `KashiCTF{XXXXXX_XXXXXXXXXXXXX}`

## Attachments 
Download kitler's-phone.tar.gz

Mirrors:

   1. [https://gofile.io/d/edmDCj](https://gofile.io/d/edmDCj)
   2. [https://storage.googleapis.com/chall-storage/kitler's-phone.tar.gz](https://storage.googleapis.com/chall-storage/kitler's-phone.tar.gz)
   3. [GDrive](https://limewire.com/d/10d200d2-f55c-446e-9f2b-82bb81f38a84#w-sotKaYWiawMRljM_R78scaItljuNBK88sz90NWpZU)
   4. [https://limewire.com/d/10d200d2-f55c-446e-9f2b-82bb81f38a84#w-sotKaYWiawMRljM_R78scaItljuNBK88sz90NWpZU](https://limewire.com/d/10d200d2-f55c-446e-9f2b-82bb81f38a84#w-sotKaYWiawMRljM_R78scaItljuNBK88sz90NWpZU)

Verify the checksum

```
$ sha256sum kitler\'s-phone.tar.gz

5ce7e5047c54ce6ec145508ed6a4aecc237c41b86ea61e7e2991e9a8ed05142a  kitler's-phone.tar.gz
```

---
## Writeup

After downloading the files I searched for the OTP using the below command as it must have been from Amazon Pay.
``` bash
$ grep -ra "Amazon Pay" .
```

And there was the OTP **839216** and also the location of where it was *./data_mirror/data_ce/null/0/com.google.android.apps.messaging/databases/bugle_db* was a hint to where I can find the timestamp. I immediately used *sqlite* to search through the database, see all the tables and in the messages tables were some 13-digit numbers which I assumed to be the unix-timestamp. I tried the flag using these numbers one by one and Success!
```
$ sqlite3 ./data_mirror/data_ce/null/0/com.google.android.apps.messaging/databases/bugle_db

sqlite> .tables
sqlite> SELECT * FROM messages;
```

---
## Flag

```
KashiCTF{839216_1740251608654}
```                 