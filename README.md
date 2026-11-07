# RegistaOS — app Android

Questo repository contiene gli APK firmati di RegistaOS e il manifest che l'app
legge per sapere se c'e' una versione nuova. Il codice sta altrove.

## Installare e tenere aggiornata l'app

Con [Obtainium](https://github.com/ImranR98/Obtainium): *Add App*, e come
indirizzo

    https://github.com/tonym961/RegistaOS-App

Niente altro da impostare: Obtainium legge le Release, ricava la versione dal
tag e avvisa da solo quando ne esce una nuova.

Dal telefono si puo' anche aprire questo indirizzo nel browser, che apre
Obtainium con il campo gia' compilato (non e' cliccabile qui perche' GitHub
mostra solo i collegamenti `http`):

    obtainium://add/https://github.com/tonym961/RegistaOS-App

Senza Obtainium: si scarica a mano dalla
[pagina delle release](../../releases/latest).

## Com'e' organizzato

| Dove | Cosa |
|---|---|
| **Release** (tag `v<versione>`) | l'APK firmato, come allegato |
| `latest.json` sul ramo | manifest del canale produzione: versione + indirizzo dell'APK |
| `latest-beta.json` sul ramo | manifest del canale beta |

Il tag e' **esattamente** la versione dell'app (`v0.12.172` per la versione
`0.12.172`), e di APK nella release ce n'e' **uno solo**. Sono i due requisiti
di Obtainium: la versione la prende dal tag e la confronta anche come stringa
con quella installata, quindi un tag che porti dentro altro — il numero di
build, per esempio — terrebbe l'app «da aggiornare» per sempre; e con due APK
allegati non saprebbe quale prendere.

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
