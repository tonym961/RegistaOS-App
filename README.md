# RegistaOS — APK

Questo repository contiene **solo** gli APK firmati di RegistaOS e il manifest
che l'app legge per sapere se c'e' una versione nuova. Il codice sta altrove.

- `registaos-latest.apk` / `latest.json` — canale di produzione
- `registaos-beta.apk` / `latest-beta.json` — canale beta

Il repository **deve restare pubblico**: l'app scarica da
`raw.githubusercontent.com` senza autenticazione (`Config.ghToken` e' vuoto per
scelta). Se diventa privato, l'aggiornamento non parte e l'app non lo spiega.

Gli APK sono firmati con la chiave di release di RegistaOS. Un APK firmato con
una chiave diversa **non si installa sopra** quello esistente: va disinstallato
a mano, perdendo i dati locali.
