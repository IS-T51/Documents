
# 3. Analisi del contesto
Nel presente capitolo viene discusso il contesto del funzionamento del sistema, fornendo una descrizione testuale e un diagramma di contesto.

## 3.1 Utenti e sistemi esterni
In questa sezione vengono presentati gli utenti e i sistemi esterni con cui l’applicazione Animati si interfaccerà.

### Utente
Attore, l'utente è il destinatario finale dell'applicazione, colui che utilizza l'app per consultare il catalogo delle attività, come specificato da **O1**, e avvalersi di ulteriori strumenti di supporto all'animazione, come specificato da **O2**. Gli utenti sono divisi, come da **O3** e **O4**, in tre categorie:
- utenti anonimi, ovvero i "visitatori" che accedono all'applicazione unicamente per consultare il catalogo e utilizzare gli strumenti. Per questi utenti si applicano gli **RF** da **1** a **6**.
- utenti autenticati, ovvero gli "animatori" che intendono usare l'app per lasciare contributi utili agli altri utenti (valutazioni, segnalazioni e proposte di attività) e organizzare le attività del catalogo in liste personali. Per questi utenti si applicano gli **RF** da **1** a **4** e da **7** a **17**.
- amministratori, ovvero coloro che si occupano di gestire il catalogo e la community di utenti (modificando il catalogo delle attività, modificando il ruolo di altri utenti e gestendo le segnalazioni ad attività). Per questi utenti si applicano gli **RF** da **1** a **4**, da **7** a **12**, da **16** a **22**.
### Google APIs
Sistema subordinato, le API di Google vengono utilizzate dal sistema per autenticare gli utenti all'interno dell'applicazione, come da **O3**, usando lo standard OAuth 2.0. Google permette agli utenti di effettuare l'accesso su una pagina di Google con le proprie credenziali Google, per poi restituire all'applicazione un codice con il quale si possono ottenere informazioni sull'account Google dell'utente, o agire (limitatamente alle autorizzazioni concesse dall'utente) in sua vece presso i server di Google. Le API di Google saranno interpellate esclusivamente per la realizzazione di **RF5**.
### MongoDB
Sistema subordinato, MongoDB è un database management system di tipo non relazionale con cui il sistema si interfaccerà per l'immagazzinamento e il recupero di dati relativi al catalogo delle attività, agli utenti e alle liste personali degli utenti. MongoDB sarà quindi usato per la realizzazione degli **RF** da **1** a **3**, da **6** a **15** e da **17** a **22**.
Inoltre per le funzionalità "in presenza di connessione" il sistema si interfaccerà con il servizio MongoDB Atlas, un servizio di cloud computing che fornisce un Database-as-a-Service. Quest'ultimo sarà utilizzato per la realizzazione degli **RF** da **1** a **3**, **5**, da **7** a **15** e da **17** a **22**, qualora il dispositivo dell'utente sia connesso a Internet.
### IndexedDB
Sistema subordinato, IndexedDB è un API Javascript che fornisce un database management system di tipo non relazionale con cui il sistema si interfaccerà per l'immagazzinamento e il recupero di dati strutturati lato client, ovvero sul browser dell'utente, relativi al catalogo delle attività, agli utenti e alle liste personali degli utenti, come da **O5**. IndexedDB sarà quindi usato, sui dispositivi che lo consentono, per la realizzazione dell'**RF1** (aggiornamento catalogo locale), per garantire le funzionalità "in assenza di connessione" comprendenti l'uso di dati strutturati, ovvero **RF3**, **RF6**, **RF17**.


## 3.2 Diagramma di contesto

<center><img alt="Diagramma di Contesto" src="D2/img/CXD/context-diagram_v3.png" width="100%"/></center>

La figura mostra le principali interazioni tra attori o sistemi esterni e l’applicazione Animati. Segue una descrizione delle interazioni evidenziate dal diagramma.


### Flussi di informazione tra utente e sistema:
- L'utente anonimo può effettuare l'accesso tramite account Google (**RF5**), mentre l'utente autenticato (amministratore compreso) può effettuare il logout dal sistema (**RF16**).
Qualsiasi utente può selezionare dei filtri (**RF3**) e richiedere di consultare il catalogo (**RF2**), anche senza aver disposto filtri. Il sistema mostrerà all'utente il risultato della ricerca.
- L'utente può selezionare un'attività e il sistema mostrerà i dettagli dell'attività all'utente, l'utente autenticato potrà allora lasciare una valutazione all'attività (**RF12**) o una segnalazione (**RF13**).
- L'amministratore può chiedere di visualizzare l'elenco delle segnalazioni e il sistema mostrerà all'amministratore tale elenco (**RF22**), l'amministratore a quel punto può selezionare una specifica attività segnala e il sistema gli mostrerà le segnalazioni inerenti ad essa.
- L'amministratore può chiedere di visualizzare l'elenco degli utenti autenticati e il sistema mostrerà all'amministratore tale elenco (**RF20**), l'amministratore a quel punto può chiedere di modificare il ruolo di un utente (**RF21**).
- L'utente autenticato può aggiungere una proposta di attività al catalogo o può aggiungere direttamente un'attività se è un amministratore (**RF14** e **RF18**), o modificare una propria proposta di attività se autenticato o una qualsiasi attività del catalogo se amministratore (**RF15** e **RF19**). Qualora un'attività o proposta con titolo uguale a quello scelto dall'utente sia già presente in catalogo, il sistema notificherà l'utente.
- L'utente autenticato può chiedere di visualizzare l'elenco delle proprie liste personali di attività e il sistema risponderà mostrando tale elenco (**RF11**), a quel punto può selezionare una lista e il sistema gli mostrerà le attività presenti nella relativa lista, può creare una nuova lista specificandone il nome (**RF7**), eliminare una lista (**RF8**), aggiungere un'attività a una lista (**RF9**) o rimuovere un'attività da una lista (**RF10**).
- L'utente può un tool da utilizzare (**RF4**).
- Selezionando il fischietto o il timer l'utente può, rispettivamente, inviare un suono e attiva fischietto (**RF29** e **RF30**), o inviare un suono, selezionare il tempo di partenza, avviare, fermare o riavviare timer (**RF26**), e in entrambi i casi il sistema riprodurrà il suono selezionato al momento desiderato (**RF31**).
- Selezionando il cronometro l'utente può avviare, fermare, salvare un tempo parziale, o riprendere il cronometraggio (**RF27** e **RF38**) e il sistema mostrerà il tempo trascorso dall'avvio del cronometro.
- Selezionando i dadi o lo strumento di creazione squadre l'utente può impostare i parametri desiderati per l'estrazione (**RF23** e **RF25**) o della squadra (**RF** da **34** a **38**) e richiedere un'estrazione (**RF24** e **RF39**), il sistema risponderà mostrando l'elemento estratto.
- Selezionando il segna-punti l'utente può scegliere i nomi dei segnapunti e incrementarne o decrementarne i punteggi (**RF32** e **RF33**), e il sistema terrà traccia dei punteggi dei segna-punti e li mostrerà all'utente.


### Flussi di informazione tra MongoDB e sistema:
- In concomitanza all'operazione di login di un utente, il sistema interroga MongoDB per recuperare i dati dell'utente in caso sia già registrato o aggiungere l'utente al database in occasione del primo accesso (**RF5**), e MongoDB fornisce al sistema i dati sull'utente e in caso registra il nuovo utente.
- In concomitanza al primo accesso dell'utente sull'applicazione o in concomitanza a richieste di consultare o filtrare il catalogo da parte dell'utente (**RF** da **1** a **3**), il sistema richiede (se primo accesso)/può richiedere (negli altri casi) a MongoDB le attività del catalogo che rispettano i filtri impostati (eventualmente nessuno), e MongoDB fornisce le attività filtrate al sistema.
- Superati 30 minuti dall'ultimo aggiornamento del catalogo locale sul dispositivo di un utente che lo permette o in concomitanza di un suo nuovo accesso all'applicazione o dopo un'operazione che comprende la modifica di dati personali o del catalogo (**RF1**), il sistema richiede a MongoDB una lista ordinata di modifiche avvenute ai database di interesse dell'utente, e MongoDB la fornisce.
- In concomitanza all'invio di una valutazione o segnalazione ad un'attività da parte di un utente autenticato (**RF12** e **RF13**), il sistema inoltrerà tali informazioni a MongoDB.
- In concomitanza alle richieste di visualizzazione degli elenchi delle segnalazioni ad attività o degli utenti da parte di un amministratore (**RF22** e **RF20**), il sistema inoltrerà a MongoDB tali richieste e MongoDB fornirà gli elenchi al sistema, e in concomitanza alla richiesta di modifica del ruolo di un utente da parte di un amministratore (**RF21**), il sistema inoltrerà tale richiesta a MongoDB.
- In concomitanza alle richieste di modifica dei campi attività o proposta di attività, o di creazione di una nuova attività o proposta di attività, da parte di un utente autenticato o di un amministratore (**RF11-15** e **RF18-19**), il sistema inoltrerà tale richiesta a MongoDB; oltre a ciò, nel caso particolare di richieste di creazione, qualora l'attività o proposta sia già presente nel catalogo, MongoDB informerà di ciò il sistema (che potrà usare l'informazione per notificare l'utente).
- In concomitanza alle richieste di visualizzazione dell'elenco delle proprie liste di attività da parte di un utente autenticato (**RF11**), il sistema può inoltrare a MongoDB tale richiesta e MongoDB fornirà l'elenco al sistema; in concomitanza a qualsiasi richiesta di manipolazione delle proprie liste di attività da parte di un utente autenticato (**RF** da **7** a **10**), il sistema inoltrerà tali richieste a MongoDB, oltre a ciò, nel caso particolare di richiesta di creazione di una nuova lista di attività, qualora la lista sia già presente tra le liste personali dell'utente, MongoDB informerà di ciò il sistema (che potrà usare l'informazione per notificare l'utente).
- In concomitanza alle richieste di visualizzazione delle informazioni di un'attività da parte di un utente, il sistema può inoltrare tale richiesta a MongoDB, che risponderà fornendo i dettagli dell'attività.

### Flussi di informazione tra IndexedDB e sistema:
- In concomitanza alle richieste di visualizzazione delle informazioni di un'attività da parte di un utente, il sistema può inoltrare tale richiesta a IndexedDB, che risponderà fornendo i dettagli dell'attività.
- In concomitanza a richieste di consultare o filtrare il catalogo da parte dell'utente (**RF2** e **RF3**), il sistema può richiedere a IndexedDB le attività del catalogo che rispettano i filtri impostati (eventualmente nessuno), e IndexedDB fornirà le attività filtrate al sistema.
- In concomitanza alle richieste di visualizzazione dell'elenco delle proprie liste di attività da parte di un utente autenticato (**RF11**), il sistema può inoltrare a IndexedDB tale richiesta e IndexedDB fornirà l'elenco al sistema
- Superati 30 minuti dall'ultimo aggiornamento del catalogo locale sul dispositivo di un utente che lo permette o in concomitanza di un suo nuovo accesso all'applicazione o dopo un'operazione che comprende la modifica di dati personali o del catalogo (**RF1**), il sistema aggiorna i dati presenti nei database locali.

### Flussi di informazione tra Google APIs e sistema:
- In concomitanza all'operazione di login di un utente (**RF5**), il sistema reindirizzerà l'utente su una pagina di accesso Google con una richiesta di permessi per l'utente, Google dopo aver raccolto l'informazione richiesta reindirizzerà l'utente sull'applicazione fornendo un codice autorizzativo, il sistema utilizzerà il codice autorizzativo per richiedere un token a Google, Google infine invierà al sistema il token richiesto contenente le informazioni sull'account Google dell'utente necessarie al sistema.



<div class="page-break"></div>
