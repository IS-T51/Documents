## 2.5 Sviluppo API
In seguito descriveremo il funzionamento delle varie API sviluppate nel progetto.

Il routing viene generato a partire della specifica OpenAPI presente nel file *openapi.yaml* in *animati-server/src/api* grazie al modulo oas3-tools-cors di Nodejs. La logica delle API è definita nei file nella cartella *src/controllers*, che si occupano semplicemente dell'inoltro di richiesta e risposta tra i router e le funzioni di logica del sistema, e nei file nella cartella *src/service* che si occupano dell'effettiva elaborazione delle richieste.

Ogni API è progettata per restituire un messaggio di errore 500 in caso di errori interni al server o di comunicazione con MongoDB, tal volta realizzato mediante l'uso di try-catch, tal volta nel .catch delle Promises, o infine nella funzione di utility *writer.js*.

Il codice è reperibile nella repository github *https://github.com/IS-T51/animati-server*.


### API per la risorsa Utente
[...]

### API per la risorsa Attività
[...]

### API per la risorsa Lista
Di seguito descriviamo le API per gestire le varie azioni eseguibili sulla risorsa Lista, la loro logica si articola nel controller *src/controllers/Lista.js* e in *src/service/ListaService.js*.

Ognuna di queste API può essere eseguita solo specificando un token d’accesso come parametro nell’header, in quanto rappresenta una richiesta eseguibile solo da un utente autenticato. Per verificare l'autorizzazione dell'utente le API utilizzano l'API *getUtente* come middleware, quindi in caso di autenticazione non corretta restituiscono un messaggio di errore con codice 401.

#### API per l'inserimento di un'attività in una lista personale
L’API *aggiungiAttivitaALista* ha lo scopo di aggiungere un'attività all'elenco di attività di una specifica istanza della risorsa Lista e di salvare l'istanza modificata nel database nella collezione Liste.
Riceve in input l'id della lista in cui si desidera aggiungere l'attività (passato per percorso) e l'id dell'attività da aggiungere (passato come parametro di query).
Viene fornita in output la lista aggiornata se tutto è andato a buon fine. In caso contrario si restituisce un messaggio d’errore, ovvero nel caso in cui la richiesta non sia ben formulata o la lista sia già piena (errore 400), oppure in caso la lista sia inesistente (404) o in caso l'utente che effettua la richiesta non ne sia l'autore (403), oppure l'utente che effettua la richiesta non sia autenticato correttamente (401), oppure in caso si verifichi un errore interno al server o di comunicazione con MongoDB (500).

#### Creazione di una lista
L’API *aggiungiLista* ha lo scopo di creare una nuova istanza della risorsa Lista e di salvarla
nel database nella collezione Liste.
Riceve in input alla richiesta un body con il nome da assegnare della risorsa lista che viene creata.
Viene fornita in output la risorsa appena creata se tutto è andato a buon fine. In caso contrario si restituisce un messaggio d’errore, ovvero nel caso in cui la richiesta non sia ben formulata o l'utente abbia raggiunto il massimo numero di liste (errore 400), oppure in caso una lista con il nome fornito e l'utente come autore sia già esistente (400), oppure l'utente che effettua la richiesta non sia autenticato correttamente (401), oppure in caso si verifichi un errore interno al server o di comunicazione con MongoDB (500).

#### Eliminazione di una lista
L’API *eliminaLista* ha lo scopo di eliminare un’istanza della risorsa Lista dal database.
Riceve come unico parametro di input l'id della lista che si intende eliminare. Se tutto è an-
dato a buon fine non ritorna niente (messaggio di successo 204). In caso contrario si restituisce un messaggio d’errore, ovvero nel caso in cui la richiesta non sia ben formulata o l'utente stia cercando di eliminare la propria lista dei Preferiti (errore 400), oppure in caso la lista sia inesistente (404) o in caso l'utente che effettua la richiesta non ne sia l'autore (403), oppure l'utente che effettua la richiesta non sia autenticato correttamente (401), oppure in caso si verifichi un errore interno al server o di comunicazione con MongoDB (500).

#### Ricerca delle informazioni di una lista
L’API *getLista* ha lo scopo di ricercare una precisa lista nel database, dato il suo id passato
come unico parametro in input alla richiesta. Viene fornita in output la precisa risorsa richiesta se
presente con titolo ed elenco di attività in lista. In caso contrario si restituisce un messaggio d’errore, ovvero nel caso in cui la richiesta non sia ben formulata, oppure in caso la lista sia inesistente (404) o in caso l'utente che effettua la richiesta non ne sia l'autore (403), oppure l'utente che effettua la richiesta non sia autenticato correttamente (401), oppure in caso si verifichi un errore interno al server o di comunicazione con MongoDB (500).

#### Ricerca di tutte le proprie liste personali
L’API *getListe* ha lo scopo di ricercare ed elencare tutte le liste di uno specifico utente salvate nel database.
Non c’è niente in input alla richiesta, ma viene fornito in output l’elenco di tutte le liste dell'utente presenti, elenco che non sarà mai vuoto perché ogni utente deve avere in ogni momento la lista dei preferiti. In caso la richiesta non vada a buon fine si restituisce un messaggio d’errore, ovvero nel caso in cui la richiesta non sia ben formulata, oppure l'utente che effettua la richiesta non sia autenticato correttamente (401), oppure in caso si verifichi un errore interno al server o di comunicazione con MongoDB (500).

#### API per la rimozione di un'attività da una lista personale
L’API *rimuoviiAttivitaDaLista* ha lo scopo di rimuovere un'attività dall'elenco di attività di una specifica istanza della risorsa Lista e di salvare l'istanza modificata nel database nella collezione Liste.
Riceve in input l'id della lista in cui si desidera aggiungere l'attività (passato per percorso) e l'indice all'interno della lista dell'attività da rimuovere (passato come parametro di query).
Viene fornita in output la lista aggiornata se tutto è andato a buon fine. In caso contrario si restituisce un messaggio d’errore, ovvero nel caso in cui la richiesta non sia ben formulata (errore 400), oppure in caso la lista sia inesistente (404) o in caso l'utente che effettua la richiesta non ne sia l'autore (403), oppure l'utente che effettua la richiesta non sia autenticato correttamente (401), oppure in caso si verifichi un errore interno al server o di comunicazione con MongoDB (500).




### API per la risorsa Etichetta
Di seguito descriviamo le API per gestire le varie azioni eseguibili sulla risorsa Etichetta, la loro logica si articola nel controller *src/controllers/Etichette.js* e in *src/service/EtichetteService.js*.

#### Creazione di un etichetta
L’API *aggiungiEtichetta* ha lo scopo di creare una nuova istanza della risorsa Etichetta e di salvarla
nel database nella collezione Etichette.
Riceve in input alla richiesta un body con i vari attributi della risorsa etichetta che viene creata.
Viene fornita in output la risorsa appena creata se tutto è andato a buon fine. In caso contrario si restituisce un messaggio d’errore (nel caso in cui la richiesta non sia ben formulata oppure l'utente che effettua la richiesta non sia autenticato correttamente o non abbia i privilegi di amministartore oppure in caso si verifichi un errore interno al server o di comunicazione con MongoDB).
Nel caso in cui il nome dell'etichetta da creare coincida con il nome di un'etichetta già presente nel database, l'istanza presente sarà aggiornata.
Quest’API può essere eseguita solo specificando un token d’accesso come parametro nell’header, in quanto rappresenta una richiesta eseguibile solo da un utente autenticato e con i privilegi di amministratore. Per verificare l'autorizzazione dell'utente l'API utilizza l'API *getUtente* come middleware.

#### Ricerca di tutte le etichette
L’API *ottieniEtichette* ha lo scopo di ricercare ed elencare tutte le etichette salvate nel database.
Non c’è niente in input alla richiesta, ma viene fornito in output l’elenco di tutte le etichette presenti, una risposta con codice 204 se nessuna etichetta è salvata nel database, oppure un messaggio di errore in caso di errori interni al server o di comunicazione con MongoDB.
Per utilizzare questa API non è necessaria autenticazione.



### API di default

Il controller *Default.js* e il file di business logic *DefaultService.js* definiscono il funzionamento dell'API di default, ideata per verificare la connessione del client con il server. Qualora il server sia funzionante, la funzione *ping* di *DefaultService.js* restituirà una Promise che può solo avere successo, il messaggio di successo sarà inserito nella risposta da fornire al richiedente dalla funzione *ping* del controller, quindi il metodo GET presso l'endpoint /ping restituirà sempre un messaggio 200 di successo.

<div class="page-break"></div>