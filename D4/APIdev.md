## 2.5 Sviluppo API
In seguito descriveremo il funzionamento delle varie API sviluppate nel progetto.

Il routing viene generato a partire della specifica OpenAPI presente nel file *openapi.yaml* in *animati-server/src/api* grazie al modulo oas3-tools-cors di Nodejs. La logica delle API è definita nei file nella cartella *src/controllers*, che si occupano semplicemente dell'inoltro di richiesta e risposta tra i router e le funzioni di logica del sistema, e nei file nella cartella *src/service* che si occupano dell'effettiva elaborazione delle richieste.

Ogni API è progettata per restituire un messaggio di errore 500 in caso di errori interni al server o di comunicazione con MongoDB, tal volta realizzato mediante l'uso di try-catch, tal volta nel .catch delle Promises, o infine nella funzione di utility *writer.js*.



### API per la risorsa Etichetta
Di seguito descriviamo le API per gestire le varie azioni eseguibili sulla risorsa Etichetta, la loro logica si articola nel controller *src/controllers/Etichette.js* e in *src/service/EtichetteService.js*.

#### Creazione di un etichetta
L’API *aggiungiEtichetta* ha lo scopo di creare una nuova istanza della risorsa Etichetta e di salvarla
nel database nella collezione Etichette.
Riceve in input alla richiesta un body con i vari attributi della risorsa etichetta che viene creata.
Viene fornita in output la risorsa appena creata se tutto è andato a buon fine. In caso contrario si
restituisce un messaggio d’errore (nel caso in cui la richiesta non sia ben formulata oppure l'utente che effettua la richiesta non sia autenticato correttamente o non abbia i privilegi di amministartore oppure in caso si verifichi un errore interno al server o di comunicazione con MongoDB).
Nel caso in cui il nome dell'etichetta da creare coincida con il nome di un'etichetta già presente nel database, l'istanza presente sarà aggiornata.
Quest’API può essere eseguita solo specificando un token d’accesso come parametro
nell’header, in quanto rappresenta una richiesta eseguibile solo da un utente autenticato e con i privilegi di amministratore. Per verificare l'autorizzazione dell'utente l'API utilizza l'API *getUtente* come middleware.

#### Ricerca di tutte le etichette
L’API *ottieniEtichette* ha lo scopo di ricercare ed elencare tutte le etichette salvate nel database.
Non c’è niente in input alla richiesta, ma viene fornito in output l’elenco di tutte le etichette presenti, una risposta con codice 204 se nessuna etichetta è salvata nel database, oppure un messaggio di errore in caso di errori interni al server o di comunicazione con MongoDB.
Per utilizzare questa API non è necessaria autenticazione.



### API di default

Il controller *Default.js* e il file di business logic *DefaultService.js* definiscono il funzionamento dell'API di default, ideata per verificare la connessione del client con il server. Qualora il server sia funzionante, la funzione *ping* di *DefaultService.js* restituirà una Promise che può solo avere successo, il messaggio di successo sarà inserito nella risposta da fornire al richiedente dalla funzione *ping* del controller, quindi il metodo GET presso l'endpoint /ping restituirà sempre un messaggio 200 di successo.

<div class="page-break"></div>