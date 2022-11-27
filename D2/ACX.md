
# Analisi del contesto
Nel presente capitolo viene discusso il contesto del funzionamento del sistema, fornendo una descrizione testuale e un diagramma di contesto.

## Utenti e sistemi esterni
In questa sezione vengono presentati gli utenti e i sistemi esterni con cui l’applicazione Animati si interfaccerà.

### Utente
Attore, l'utente è il destinatario finale dell'applicazione, colui che utilizza l'app per consultare il catalogo delle attività, come specificato da **O1**, e avvalersi di ulteriori strumenti di supporto all'animazione, come specificato da **O2**. Gli utenti sono divisi, come da **O3** e **O4**, in tre categorie:
- utenti anonimi, ovvero i "visitatori" che accedono all'applicazione unicamente per consultare il catalogo e utilizzare gli strumenti. Per questi utenti si applicano gli **RF** da **1** a **6**.
- utenti autenticati, ovvero gli "animatori" che intendono usare l'app per lasciare contributi utili agli altri utenti (valutazioni, segnalazioni e proposte di attività) e organizzare le attività del catalogo in liste personali. Per questi utenti si applicano gli **RF** da **1** a **4** e da **7** a **17**.
- amministratori, ovvero coloro che si occupano di gestire il catalogo e la community di utenti (modificando il catalogo delle attività, modificando il ruolo di altri utenti e gestendo le segnalazioni ad attività). Per questi utenti si applicano gli **RF** da **1** a **4**, da **7** a **12**, da **16** a **22**.
### Google APIs
Sistema subordinato, le API di Google vengono utilizzate dal sistema per autenticare gli utenti all'interno dell'applicazione, come da **O3**, usando lo standard OAuth 2.0. Google permette agli utenti di effettuare l'accesso su una pagina di Google con le proprie credenziali Google, per poi restituire all'applicazione un codice con il quale si possono ottenere informazioni sull'account Google dell'utente, o agire (limitatamente alle autorizzazioni concesse dall'utente) in sua vece presso i server di Google. Le API di Google saranno interpellate esclusivamente per la realizzazione di **RF5**.
### MongoDB
Sistema subordinato, MongoDB è un database management system di tipo non relazionale con cui il sistema si interfaccerà per l'immagazzinamento e il recupero di dati relativi al catalogo delle attività, gli utenti e le liste degli utenti. MongoDB sarà quindi usato per la realizzazione degli **RF** da **1** a **3**, da **6** a **15** e da **17** a **22**.
Inoltre per le funzionalità "in presenza di connessione" il sistema si interfaccerà con il servizio MongoDB Atlas, un servizio di cloud computing che fornisce un Database-as-a-Service. Quest'ultimo sarà utilizzato per la realizzazione degli **RF** da **1** a **3**, **5**, da **7** a **15** e da **17** a **22**, qualora il dispositivo dell'utente sia connesso a Internet.


## Diagramma di contesto

<center><img alt="Diagramma di Contesto" src="D2/img/CXD/context-diagram_v2.png" width="100%"/></center>

La figura mostra le principali interazioni tra attori o sistemi esterni e l’applicazione Animati. Segue una descrizione delle interazioni evidenziate dal diagramma.

L'utente può visionare il catalogo (RF[...]), le attività (RF[...]), le liste di attività (RF[...], RF[...]), le attività presenti in una lista (RF[...]), le segnalazioni ricevute (RF[...]), la singola segnalazione (RF[...]), <br>[...]






<div class="page-break"></div>
