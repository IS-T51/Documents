
# Requisiti non funzionali del progetto
Nel presente capitolo vengono riportati i requisiti non funzionali (RNF) del sistema.

---

## Efficienza e prestazioni
I seguenti requisiti assumono che l'utente disponga di una connessione a Internet con una velocità di trasmissione di almeno 20Mbps, per velocità inferiori non sono offerte garanzie di prestazione per quanto riguarda le funzionalità online dell'app.

> #### RNF1.
> Il sistema risponde a richieste di consultazione e filtraggio del catalogo ([RF2.](#rf2) ed [RF3.](#rf3)) e consultazione delle proprie liste ([RF11.](#rf11)) da parte dell'utente in meno di 1 secondo.

> #### RNF2.
> Il sistema risponde a richieste di modifica dati da parte dell'utente (da [RF8.](#rf8) a [RF20.](#rf21) escluso [RF11.](#rf11)) in meno di 1 secondo grazie a meccanismi di aggiornamento sequenziale.

> #### RNF3.
> Qualora il dispositivo utilizzato dall'utente lo permetta (si veda Portabilità), una copia locale del catalogo delle attività sarà creata sul dispositivo dell'utente ([RF1.](#rf1)) al primo utilizzo dell'app o qualvolta l'utente elimini tali dati, ed essa sarà successivamente aggiornata con frequenza di massimo 30 minuti od ogni volta che l'utente avvierà l'app e sarà connesso ad Internet.

> #### RNF4.
> La creazione della copia locale del catalogo impiegherà fino a 10 secondi, l'aggiornamento fino a 1 secondo, e nessuna delle due operazioni impedirà o interromperà la navigazione all'interno dell'app da parte dell'utente.

> #### RNF5.
> Per ogni operazione concernente le funzionalità dei tools ([RF4.](#rf4)) il sistema avrà un tempo di risposta inferiore a 1 secondo.

> #### RNF6.
> Il tempo di risposta da parte del sistema nell'operazione di login ([RF5.](#rf5)) (oltre al tempo impiegato dall'utente per inserire i propri dati quando si trova sull'interfaccia di Google) sarà inferiore a 10 secondi.

> #### RNF7.
> Qualora il dispositivo utilizzato dall'utente lo permetta, le funzionalità di consultazione e filtraggio del catalogo ([RF2.](#rf2) ed [RF3.](#rf3)), utilizzo dei tools ([RF4.](#rf4)) e consultazione delle proprie liste ([RF11.](#rf11)) saranno garantite anche in assenza di connessione ad Internet e con tempi di risposta da parte del sistema inferiori a 1 secondo.

> #### RNF8.
> Il tempo di risposta da parte del sistema nell'operazione di logout ([RF16.](#rf16)) sarà inferiore a 100ms.

> #### RNF9.
> L'aplicazione richiederà un consumo da parte del dispositivo dell'utente inferiore a 20MB di dati Internet mediamente in settimana, con un'aggiunta inferiore a 20MB in occasione della creazione della copia locale del catalogo.


Nota: il tempo di visualizzazione dei risultati delle richieste al sistema da parte dell'utente dipende, oltre che dal tempo di risposta del sistema, anche dal tempo di che caricamento del browser, che non è di competenza dell'applicazione.

## Memorizzazione dati
> #### RNF10.
> I dati salvati sul dispositivo dell'utente occuperanno fino a un massimo di 20MB di spazio.

> #### RNF11.
> Dati salvati per utenti anonimi.
>> ##### RNF11.1.
>> Non saranno salvati dati lato server.
>
>> ##### RNF11.2.
>> Qualora il browser dell'utente lo permetta, dopo che questi avrà visualizzato il contenuto di un tutorial o di determinati messaggi di errore, gli verrà chiesta conferma di non volerlo più visualizzare in futuro; inoltre, qualora il browser dell'utente lo permetta, all'utente verrà chiesto il consenso di memorizzare dati sul browser in stato persistente. Tali scelte saranno memorizzate sotto forma di cookie tecnici nel browser dell'utente stesso, sotto previo consenso.
>
>> ##### RNF11.3.
>> Qualora il browser dell'utente lo permetta, una copia del catalogo sarà memorizzata nel suo browser.

> #### RNF12.
> Dati salvati per utenti autenticati.
>> [RNF11.2.](#rnf92)
>> [RNF11.3.](#rnf93)
>> ##### RNF12.1.
>> Lato server saranno raccolte le seguenti informazioni sugli utenti autenticati: mail, valutazioni lasciate alle attività, proposte di nuovi giochi, liste di attività, segnalazioni inviate, presenza o meno di privilegi di amministratore.
>
>> ##### RNF12.2.
>> Qualora il dispositivo dell'utente lo permetta, le informazioni menzionate in RNF12.1 saranno memorizzate sul dispositivo dell'utente.

## Privacy e security
> #### RNF13.
> Ogni connessione riguardante il sistema avverrà tramite protocollo HTTPS per garantire sicurezza e protezione dei dati trasmessi.

> #### RNF14.
> Visibilità dei dati.
>> ##### RNF14.1.
>> I dati di cui al punto RNF9.2 saranno visibili esclusivamente dall'utente direttamente interessato e solo su richiesta di accesso.
>
>> ##### RNF14.2.
>> I dati delle liste di attività create da un utente autenticato saranno visibili esclusivamente dall'utente stesso.
>
>> ##### RNF14.3.
>> I dati relativi alle valutazioni lasciate da un utente alle attività e alle sue proposte sono visibli all'utente stesso e, in forma anonimizzata, a tutti gli altri utenti.
>
>> ##### RNF14.4.
>> I dati relativi a mail, id identificativo e segnalazioni di un utente sono visibili dall'utente stesso e da tutti gli utenti con privilegi di amministratore.

> #### RNF15.
> Il trattamento dei dati degli utenti sarà conforme alla normativa vigente espressa dal GDPR. In particolare:
>> ##### RNF15.1.
>> Per il trattamento dei dati sarà richiesto agli utenti il consenso preventivo ed esplicito, che l'utente potrà negare in qualsiasi momento tranne che per i cookie tecnici (RNF9.1), di cui comunque sarà informato.
>
>> ##### RNF15.2.
>> Agli utenti verrà garantito il diritto all'oblio: su esplicita richiesta di un utente saranno cancellati tutti i dati che lo riguardano dal sistema, eccetto per le valutazioni lasciate ad attività, le attività proposte e le segnalazioni di attività, che saranno conservati in forma anonima.

## Portabilità
> #### RNF16.
> Le funzionalità online (sezioni "in presenza di connessione" negli RF) dell'app saranno garantite su qualsiasi browser che supporti HTML5.

> #### RNF17.
> Le funzionalità offline (sezioni "in assenza di connessione" negli RF) dell'app che non richiedono memorizzazione di dati strutturati saranno garantite su qualsiasi browser che supporti service workers, nello specifico:
> 1. Chrome da versione 40
> 2. Edge da versione 17
> 3. Firefox da versione 44
> 4. Opera da versione 27
> 5. Safari da versione 11.1
> 6. Chrome Android da versione 40
> 7. Firefox for Android da versione 44
> 8. Opera Android da versione 27
> 9. Safari on iOS da versione 11.3
> 10. Samsung Internet da versione 4.0
> 11. WebView Android da versione 40

> #### RNF18.
> Le funzionalità offline (sezioni "in assenza di connessione" negli RF) dell'app che richiedono memorizzazione di dati strutturati saranno garantite su qualsiasi browser che supporti sia service workers sia IndexedDB API, nello specifico saranno sicuramente garantite su:
> 1. Chrome da versione 83
> 2. Edge da versione 83
> 3. Firefox non garantito, ma è consigliata almeno la versione 58
> 4. Opera da versione 70
> 5. Safari non garantito, ma è consigliata almeno la versione 15
> 6. Chrome Android da versione 83
> 7. Firefox for Android non garantito, ma è consigliata almeno la versione 58
> 8. Opera Android da versione 59
> 9. Safari on iOS non garantito, ma è consigliata almeno la  versione 15
> 10. Samsung Internet da versione 13.0
> 11. WebView Android da versione 83

## Usabilità
> #### RNF19.
> Le principali funzionalità dell'app avranno delle schermate di spiegazione che ne faciliterà la comprensione all'utente.

> #### RNF20.
> Tempi di addestramento.
>> ##### RNF20.1.
>> Dopo 10 minuti di navigazione nell'app l'utente avrà compreso come utilizzare tutte le funzionalità offerte agli utenti anonimi.
>
>> ##### RNF20.2.
>> Dopo ulteriori 20 minuti di navigazione nell'app l'utente avrà compreso come utilizzare tutte le funzionalità offerte agli utenti autenticati.
>
>> ##### RNF20.3.
>> Dopo ulteriori 15 minuti di navigazione nell'app l'utente avrà compreso come utilizzare tutte le funzionalità offerte agli amministratori.

> #### RNF21.
> Dopo questo addestramento, gli utenti esperti non dovrebbero superare, in media, i 2 errori al giorno.

> #### RNF22.
> L'aspetto, il funzionamento e lo sviluppo del sistema rispetteranno i principali aspetti dello [standard di ux design](https://www.interaction-design.org/literature/article/user-interface-design-guidelines-10-rules-of-thumb), ad esempio:
>> ##### RNF22.1.
>>  L'utente è avvisato visivamente e chiaramente dello stato attuale del sistema (anonimo/autenticato/admin, account con cui è loggato, offline/online/errore) tramite un banner nel menù.
>
>> ##### RNF22.2.
>> Qualora il dispositivo dell'utente lo permetta, in caso di malfunzionamento invece di generici errori del browser verranno mostrati messaggi di errore specifici, per garantire una migliore comprensione da parte dell'utente.
>
>> ##### RNF22.3
>> L'attività di testing e validazione verrà effettuata con la presenza di 50 veri animatori ed educatori.

## Affidabilità e robustezza
> #### RNF23.
> Il sistema sarà disponibile mediamente per almeno 20 giorni al mese nel primo anno dal deployment.

> #### RNF24.
> Il tempo medio di malfunzionamento del sistema sarà di 3 giorni in presenza di segnalazioni di malfunzionamento da parte degli utenti.

> #### RNF25.
> Nel caso in cui si dovesse verificare un malfunzionamento del sistema mentre un utente è connesso ad esso via Internet, è garantito che i dati che l'utente ha memorizzato sul suo account fino a 10 secondi prima del malfunzionamento saranno preservati.

> #### RNF26.
> Nel caso in cui il server del sistema non fosse raggiungibile a causa di un malfunzionamento, è garantito, qualora il dispositivo dell'utente lo permetta, il funzionamento delle funzionalità offline (sezioni "in assenza di connessione" negli RF).

## Sicurezza
> #### RNF27.
> Qualora un utente rilevi un contenuto inappropriato in una delle attività nel catalogo avrà la possibilità di segnalarlo agli amministratori del sistema.

> #### RNF28.
> È garantito che le segnalazioni sulle attività vengano controllate dagli amministratori con una frequenza minima di 4 ore nella fascia oraria tra le 8:00 del mattino e le 00:00 (mezzanotte).

> #### RNF29.
> Il funzionamento dell'app deve garantire che per lo svolgimento delle attività di animazione sia sufficiente che solo un dispositivo (quello dell'organizzatore) sia connesso all'app e che i partecipanti all'attività usino l'app per un tempo limitato a meno di 10 secondi, in modo che non debbano passare troppo tempo davanti allo schermo e che non debbano necessariamente possedere un dispositivo proprio per poter partecipare.

## Interoperabilità
> #### RNF30.
> Il sistema interagirà con un servizio in cloud di database non relazionale offerto da MongoDB per memorizzare dati e rispondere alle richieste degli utenti online.

> #### RNF31.
> Il sistema userà l'API di Google con il protocollo OAuth 2.0 per identificare gli utenti.

> #### RNF32.
> Il sistema esporrà API per la consultazione e il filtraggio del catalogo online.

> #### RNF33.
> Il sistema esporrà API per la creazione ed esportazione di liste di attività.

> #### RNF34.
> Sotto previo consenso da parte dell'utente e qualora il dispositivo dell'utente lo permetta, il sistema interagirà con un sistema di gestione di database non relazionale fornito dalle API di IndexedDB per memorizzare dati in locale e rispondere alle richieste degli utenti offline.

## Scalabilità
> #### RNF35.
> Il sistema potrà supportare fino a 10.000 utenti autenticati registrati contemporaneamente nel sistema senza perdita di prestazioni grazie alla possibilità di gestire le richieste degli utenti, qualora i loro dispositivi lo permettano, anche offline, rimuovendo quindi lavoro dal server.

> #### RNF36.
> Il sistema potrà supportare fino a 10.000 attività presenti contemporaneamente nel catalogo senza senza perdita di prestazione negli aggiornamenti alle copie locali degli utenti sfruttando la tecnica di aggiornamento sequenziale.

> #### RNF37.
> Il sistema potrà gestire fino a 10.000 richieste per unità di tempo senza perdita di prestazioni grazie alla possibilità di gestire le richieste degli utenti, qualora i loro dispositivi lo permettano, anche offline, rimuovendo quindi lavoro dal server.

## Accessibilità
> #### RNF38.
> Il funzionamento del sistema adotterà provvedimenti per facilitarne l'uso da parte di persone con disabilità ispirati da [Web Content Accessibility Guidelines (WCAG) 2.2](https://www.w3.org/TR/WCAG22/), ad esempio:
>> ##### RNF38.1.
>> lo stile del sistema prevederà colori ad alto contrasto per facilitare la navigazione di ipovedenti;
>
>> ##### RNF38.2.
>> la web app sarà completamente navigabile da tastiera per facilitare persone con mobilità limitata e non vedenti, in particolare:
>> 1. ogni elemento interagibile tramite posizionamento del click del mouse sarà raggiungibile per chi naviga tramite tastiera (usando frecce e tab) spostando il "focus" su di esso, per facilitare la navigazione per persone con capacità motorie o visive ridotte;
>> 2. l'ordine con cui viene messo il "focus" sugli elementi all'interno di una pagina rispetterà il flow logico della stessa, per facilitare la navigazione per persone con capacità motorie o visive ridotte;
>> 3. ogni elemento quando il focus viene messo su di esso farà comparire un riquadro con breve suggerimento o spiegazione riguardo l'elemento stesso in modo che questo possa essere letto da eventuali sistemi di screen-reader o VoiceOver, per facilitare la navigazione per persone con capacità visive o di processo del linguaggio scritto ridotte.

## Lingua
> #### RNF39.
> Il sistema sarà distribuito in lingua italiana.

## Distribuzione
> #### RNF40.
> Il codice sorgente dell'applicativo sarà distribuito sotto licenza GPL3.0.

## Progressive Web App
> #### RNF41.
> Il sistema sarà distribuito come Progressive Web App, pertanto dovrà rispettare i seguenti vincoli:
>> [RNF13.](#rnf13)
>> ##### RNF41.1.
>> Qualora il dispositivo dell'utente lo permetta, parte dell'app può essere caricata ed eseguita anche mentre il dispositivo dell'utente è offline.
>
>> ##### RNF41.2.
>> L'app deve avere un Web App Manifest di riferimento con almeno quattro proprietà chiave: name, short_name, start_url, e display.
>
>> ##### RNF41.3.
>> L'app deve avere una icona grande almeno 144×144 pixel in formato png.

<div class="page-break"></div>
