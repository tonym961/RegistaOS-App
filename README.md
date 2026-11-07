# RegistaOS — app Android

Questo repository contiene gli APK firmati di RegistaOS e il manifest che l'app
legge per sapere se c'e' una versione nuova. Il codice sta altrove.

## Installare e tenere aggiornata l'app

Con [Obtainium](https://github.com/ImranR98/Obtainium): aggiungi come app
l'indirizzo di questo repository

    https://github.com/tonym961/RegistaOS-App

e Obtainium legge le Release, riconosce le versioni e avvisa da solo.

Oppure a mano, dalla [pagina delle release](../../releases/latest).

## Com'e' organizzato

| Dove | Cosa |
|---|---|
| **Release** (tag `v<versione>-<code>`) | l'APK firmato, come allegato |
| `latest.json` sul ramo | manifest del canale produzione: versione + indirizzo dell'APK |
| `latest-beta.json` sul ramo | manifest del canale beta |

Gli APK stanno negli **allegati delle Release** e non fra i file del ramo: un
allegato non entra nella storia di git, e committare 55 MB a ogni rilascio
gonfierebbe il repository per sempre, perche' la storia non si pota.

## Due cose da sapere

Il repository **deve restare pubblico**: l'app scarica senza autenticazione
(`Config.ghToken` e' vuoto per scelta). Se diventa privato, l'aggiornamento non
parte e l'app non riesce a spiegare perche'.

Gli APK sono firmati con la chiave di release di RegistaOS, impronta SHA-256
`85:56:9A:04:95:6F:27:8A:25:D5:AD:23:24:F1:93:B6:41:24:09:AD:21:DB:87:69:3A:D6:3D:FE:CE:ED:31:6C`.
Un APK firmato con una chiave diversa **non si installa sopra** quello
esistente: va disinstallato a mano, perdendo i dati locali.
