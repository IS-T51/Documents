
# 1. Casi d'uso
Nel presente capitolo vengono riportati i requisiti funzionali (RF) del sistema utilizzando il linguaggio naturale e Use Case Diagram (UCD) scritti in UML.

## 1.1 Diagramma dei casi d'uso

<center><img alt="D2/Diagramma strategico" src="D2/img/UCD/alto_livello.png" width="100%"/></center>

La prima figura mostra i principali casi d'uso dell’applicazione Animati, raggruppati per omogeneità, e gli attori coinvolti.

<center><img alt="D2/Diagramma dettagliato" src="D2/img/UCD/basso_livello.png" width="100%"/></center>

La seconda figura mostra in dettaglio i principali casi d'uso dell’applicazione Animati e gli attori coinvolti. Segue una descrizione dei casi d'uso.


## 1.2 Descrizione dei casi d'uso
![Effettuare l'accesso](D2/img/UCD/1.png)
> #### **Titolo:**
>> Effettuare l'accesso
> #### **Riassunto:**
>> Questo use case descrive come l’utente può accedere all’applicazione tramite il suo account Google.
> #### **Descrizione:**
>> 1. L’utente clicca sul pulsante login.
>> 2. Il sistema reindirizza l’utente sulla pagina di accesso di Google.
>> 3. L’utente inserisce le sue credenziali Google.
>> 4. Google genera un codice di autorizzazione e reindirizza l’utente sull’applicazione, inoltrando il codice al sistema. [[exception 1](#exceptions)]
>> 5. Il sistema valida il codice di autorizzazione e lo utilizza per richiedere un token a Google tramite APIs. [[exception 2](#exceptions)]
>> 6. Google invia al sistema un token con le informazioni sull'account dell'utente.
>> 7. Il sistema estrae le informazioni necessarie dal token ricevuto. [[exception 3](#exceptions)]
>> 8. Se è il primo accesso dell’utente, viene creata una nuova entry su MongoDB, con un id personale, la mail e l'url della foto profilo dell'account Google. [[exception 4](#exceptions)]
>> 9. Se è già avvenuto almeno un accesso, vengono recuperati i dati dell’utente da MongoDB. [[extension 1](#extension-points)] [[exception 4](#exceptions)]
> #### **Exceptions:**
>> - [exception 1] Le credenziali non sono corrette, e non viene generato nessun codice, all'utente viene chiesto di reinserire le proprie credenziali.
>> - [exception 2] Se il codice ricevuto risulta non valido, il sistema informa l'utente che si è verificato un errore e non è stato possibile effettuare il login.
>> - [exception 3] Errore nella verifica del token, il sistema informa l'utente che si è verificato un errore e non è stato possibile effettuare il login.
>> - [exception 4] Errore nella connessione con MongoDB, il sistema informa l'utente che si è verificato un errore e non è stato possibile effettuare il login.
> #### **Extension points:**
>> - [extension 1] Allo step [7](#descrizione), se il browser dell’utente lo permette, i dati individuali dell’utente verranno memorizzati sul dispositivo dell’utente.

----
![Consultare catalogo](D2/img/UCD/2.png)
> #### **Titolo:**
>> Consultare catalogo
> #### **Riassunto:**
>> Questo use case descrive come l'utente può consultare il catalogo di attività dell’applicazione e interagire con le singole attività presenti nell’elenco.
> #### **Descrizione:**
>> 1. Il sistema chiede l'elenco di attività a un database (MongoDB o IndexedDB). [[extension 1](#extension-points-1)] [[extension 2](#extension-points-1)] [[exception 2](#exceptions-1)]
>> 2. Il database fornisce l'elenco di attività con titolo e immagine delle stesse al sistema, e il sistema lo mostra all'utente. [[exception 3](#exceptions-1)]
>> 3. Cliccando su un’attività, l’utente viene reindirizzato alla schermata con le informazioni sull’attività stessa. [[exception 1](#exceptions-1)]
> #### **Exceptions:**
>> - [exception 1] Utente viene reindirizzato ad attività eliminata, catalogo non aggiornato.
>> - [exception 2] Non c’è connessione ad internet e non c’è una copia locale del catalogo, quindi non viene mostrato nessun catalogo e compare un messaggio di errore.
>> - [exception 3] In assenza di connessione a Internet non saranno visualizzate le immagini delle attività.
> #### **Extension points:**
>> - [extension 1] Allo step [1](#descrizione-1), qualora sia stata salvata una copia del catalogo delle attività sul dispositivo dell’utente, il sistema può consultare quei dati attraverso IndexedDB senza l'uso di connessione ad Internet (“Consultare catalogo locale”).
>> - [extension 2] Allo step [1](#descrizione-1), qualora ci sia connessione ad internet il server può chiedere la lista a MongoDB (“Consultare catalogo remoto”).

----
![Visualizzare attività](D2/img/UCD/2.png)
> #### **Titolo:**
>> Visualizzare attività
> #### **Riassunto:**
>> Questo use case descrive come l’utente può visualizzare i dettagli specifici di ogni attività a partire dalla schermata del catalogo o, unicamente nel caso dell’utente autenticato, di una lista.
> #### **Descrizione:**
>> 1. L’utente clicca sull’immagine o sul nome dell’attività scelta. [[exception 1](#exceptions-2)]
>> 2. Il sistema chiede le informazioni relative all'attività a un database (MongoDB o IndexedDB). [[extension 1](#extension-points-1)] [[extension 2](#extension-points-2)] [[exception 2](#exceptions-2)]
>> 3. Il database fornisce al sistema le informazioni, e il sistema reindirizza l’utente a una schermata con i dettagli dell’attività stessa. [[extension 3](#exceptions-2)]
> #### **Exceptions:**
>> - [exception 1] L’attività scelta non è più presente nel catalogo, MongoDB non aggiornato. Viene mostrato un messaggio di errore.
>> - [exception 2] Se non c’è connessione ad Internet e non c’è una copia locale del catalogo, non viene mostrata nessuna informazione e compare un messaggio di errore.
> #### **Extension points:**
>> - [extension 1] Allo step [2](#descrizione-2), qualora sia stata salvata una copia del catalogo delle attività sul dispositivo dell’utente, il sistema può consultare quei dati attraverso IndexedDB senza l'uso di connessione ad Internet ("Visualizzare attività locali").
>> - [extension 2] Allo step [2](#descrizione-1), qualora ci sia connessione ad internet il server può chiedere le informazioni sull'attività a MongoDB (“Visualizzare attività locali”).
>> - [extension 3] Allo step [3](#descrizione-2), l’utente può accedere al tool di creazione squadre con i parametri richiesti dalla specifica attività.

----
![Utilizzare i tool](D2/img/UCD/3.png)
> #### **Titolo:**
>> Utilizzare i tool
> #### **Riassunto:**
>> Questo use case descrive come l’utente può consultare la lista di tool presenti nell’applicazione a partire dal menù.
> #### **Descrizione:**
>> 1. L'utente clicca sul pulsante "Strumenti" presente nel menù e viene reindirizzato alla schermata contentente la lista di tool.
>> 2. Il sistema fornisce la lista di tool con titolo degli stessi, sui quali è possibile cliccare.
>> 3. Cliccando su un tool, l’utente viene reindirizzato alla schermata di utilizzo del tool stesso. [[extension 1](#extension-points-3)] [[extension 2](#extension-points-3)] [[extension 3](#extension-points-3)] [[extension 4](#extension-points-3)] [[extension 5](#extension-points-3)] [[extension 6](#extension-points-3)]
> #### **Exceptions:**
>> --
> #### **Extension points:**
> - [extension 1] Allo step [3](#descrizione-3), l’utente può cliccare sul tool DADI e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento DADI).
> - [extension 2] Allo step [3](#descrizione-3), l’utente può cliccare sul tool TIMER e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento TIMER).
> - [extension 3] Allo step [3](#descrizione-3), l’utente può cliccare sul tool CRONOMETRO e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento CRONOMETRO).
> - [extension 4] Allo step [3](#descrizione-3), l’utente può cliccare sul tool FISCHIETTO e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento FISCHIETTO).
> - [extension 5] Allo step [3](#descrizione-3), l’utente può cliccare sul tool SEGNA-PUNTI e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento SEGNA-PUNTI).
> - [extension 6] Allo step [3](#descrizione-3), l’utente può cliccare sul tool CREAZIONE SQUADRE e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento CREAZIONE SQUADRE).

----
![Visualizzare lista utenti](D2/img/UCD/4.png)
> #### **Titolo:**
>> Visualizzare lista utenti
> #### **Riassunto:**
>> Questo use case descrive come l’amministratore può consultare la lista degli utenti che hanno effettuato l’accesso all’applicazione a partire dal menù.
> #### **Descrizione:**
>> 1. L'utente clicca sul pulsante "Utenti" e viene reindirizzato alla schermata con la lista degli utenti dell'applicazione. [[exception 2](#exceptions-4)]
>> 2. Il sistema chiede a MongoDB la lista degli utenti con i relativi dati. [[exception 1](#exceptions-4)] [[exception 3](#exceptions-4)]
>> 3. Il sistema fornisce la lista degli utenti con foto profilo dell’account Google, id personale, email e ruolo.
> #### **Exceptions:**
>> - [exception 1] Lista mostra utenti non più esistenti, MongoDB non aggiornato.
>> - [exception 2] In assenza di connessione ad internet, il sistema impedisce all'utente di visualizzare la pagina.
>> - [exception 3] Impossibile stabilire una connessione con MongoDB, il sistema informa l'utente dell'impossibilità temporanea di visualizzare la pagina.
> #### **Extension points:**
>> --

----
![Modificare ruolo utenti](D2/img/UCD/5.png)
> #### **Titolo:**
>> Modificare ruolo utenti
> #### **Riassunto:**
>> Questo use case descrive come l’amministratore può modificare il ruolo degli utenti presenti su MongoDB a partire dalla schermata di visualizzazione lista utenti.
> #### **Descrizione:**
>> 1. L’utente amministratore modifica il ruolo di ciascun utente nella lista selezionando il ruolo desiderato dal menù a tendina presente vicino al nome dell’utente scelto. [[exception 1](#exceptions-5)] [[exception 2](#exceptions-5)] [[exception 3](#exceptions-5)]
>> 2. Il sistema aggiorna i dati dell’utente su MongoDB. [[exception 4](#exceptions-5)]
> #### **Exceptions:**
>> - [exception 1] Un amministratore può essere declassato a utente comune unicamente dall’amministratore che lo ha promosso.
>> - [exception 2] L’utente che si sta cercando di cui si vuole cambiare il ruolo non è presente nel sistema, MongoDB non aggiornato.
>> - [exception 3] In assenza di connessione internet, viene inviato un messaggio di errore.
>> - [exception 4] Impossibile stabilire una connessione con MongoDB, il sistema informa l'utente dell'impossibilità temporanea di modificare il ruolo.
> #### **Extension points:**
>> --

----
![Modificare attività](D2/img/UCD/6.png)
> #### **Titolo:**
>> Modificare attività
> #### **Riassunto:**
>> Questo use case descrive come un amministratore online può modificare un’attività presente nel catalogo a partire dalla pagina di visualizzazione delle informazioni dell’attività.
> #### **Descrizione:**
>> 1. L’utente amministratore clicca sul pulsante "Modifica attività" e viene reindirizzato alla schermata di modifica di un'attività. [[exception 1](#exceptions-6)] [[exception 2](#exceptions-6)]
>> 2. [[extension 1](#extension-points-6)].
>> 3. L’utente clicca sul pulsante di conferma per terminare la modifica. [[exception 1](#exceptions-6)], [[exception 2](#exceptions-6)], [[exception 3](#exceptions-6)]
>> 4. Il sistema invia a MongoDB l’attività aggiornata. [[extension 2](#extension-points-6)] [[exceptions 4](#exceptions-points-6)]
> #### **Exceptions:**
>> - [exception 1] L’attività sulla quale si clicca non è aggiornata e una modifica causerebbe delle collisioni, MongoDB non aggiornato.
>> - [exception 2] In assenza di connessione ad Internet, viene inviato un messaggio di errore.
>> - [exception 3] Se l’utente ha inserito un titolo corrispondente a quello di un’attività già presente nel catalogo o proposta da un’altro utente, il sistema mostrerà un messaggio di errore ed evidenzierà in rosso il campo di inserimento del titolo.
>> - [exception 4] Impossibile stabilire una connessione con MongoDB, il sistema informa l'utente dell'impossibilità temporanea di modificare l'attività.
> #### **Extension points:**
>> - [extension 1] Allo step 2 l’utente può modificare uno qualsiasi dei campi dell’attività, con modalità, eccezioni ed estensioni descritte negli step 2.-8. dello use case ([“Aggiungere una nuova attività”](#titolo-7)).
>> - [extension 2] Qualora il dispositivo dell'utente lo permetta, avverrà un aggiornamento della copia locale dei dati dell'utente e del catalogo (["Aggiornare catalogo locale"](#titolo-26)).

----
![Aggiungere una nuova attività](D2/img/UCD/7.png)
> #### **Titolo:**
>> Aggiungere una nuova attività
> #### **Riassunto:**
>> Questo use case descrive come un utente amministratore può aggiungere una nuova attività	al catalogo di attività a partire dal menù.
> #### **Descrizione:**
>> 1. L’utente clicca sul bottone “Aggiungi attività” e viene reindirizzato alla schermata di creazione di un’attività. [[exception 1](#exceptions-7)]
>> 2. L’utente inserisce il titolo dell’attività. [[exception 6](#exceptions-7)]
>> 3. L’utente inserisce la descrizione dell’attività. [[exception 2](#exceptions-7)]
>> 4. L’utente inserisce il range di età per cui l’attività è adeguata o raccomandata, fornendo un valore intero non negativo iniziale e un valore intero non negativo finale. [[exception 3](#exceptions-7)]
>> 5. L’utente inserisce il range di durata dell’attività in minuti. [[exception 4](#exceptions-7)]
>> 6. L’utente inserisce il range del numero di giocatori per cui l’attività è adeguata o raccomandata, fornendo un valore intero non negativo iniziale e un valore intero non negativo finale. [[exception 3](#exceptions-7)]
>> 7. [[extension 1](#extension points-7)], [[extension 3](#extension points-7)], [[extension 4](#extension points-7)], [[extension 5](#extension points-7)]
>> 8. L’utente clicca sul pulsante per confermare [[exception 5](#exceptions-7)] [[exception 1](#descrizione-7)]
>> 9. Il sistema invia l'attività creata a MongoDB [[extension 2](#exceptions-7)] [[exception 7](#descrizione-7)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione
>> - [exception 2] Dopo aver inserito 2000 caratteri nel campo relativo alla descrizione, se l’utente proverà ad inserire altri caratteri questi non verranno inseriti, il campo di inserimento sarà evidenziato di rosso e riporterà una scritta che informa l’utente che il limite massimo di caratteri è stato raggiunto
>> - [exception 3] Se il valore finale è strettamente minore del valore iniziale o se uno dei due valori non è intero o se uno dei due valori è negativo o se uno dei due valori è maggiore di 99, il campo di inserimento del range sarà evidenziato in rosso e riporterà una scritta che informa l’utente dei vincoli non rispettati
>> - [exception 4] Se il valore finale è strettamente minore del valore iniziale o se uno dei due valori non è intero o se uno dei due valori è negativo o se uno dei due valori è maggiore di 9.999, il campo di inserimento del range sarà evidenziato in rosso e riporterà una scritta che informa l’utente dei vincoli non rispettati
>> - [exception 5] Se l’utente ha inserito un titolo corrispondente a quello di un’attività già presente nel catalogo o proposta da un’altro utente, o se l'utente ha lasciato il campo del titolo vuoto, il sistema mostrerà un messaggio di errore ed evidenzierà in rosso il campo di inserimento del titolo
>> - [exception 6] Dopo aver inserito 20 caratteri nel campo relativo al titolo, se l’utente proverà ad inserire altri caratteri questi non verranno inseriti, il campo di inserimento sarà evidenziato di rosso e riporterà una scritta che informa l’utente che il limite massimo di caratteri è stato raggiunto
>> - [exception 7] Impossibile stabilire una connessione con MongoDB, il sistema informa l'utente dell'impossibilità temporanea di aggiungere l'attività.
> #### **Extension points:**
>> - [extension 1] Allo step [8](#descrizione-7), l’utente può scegliere una o più etichette con cui contrassegnare l’attività da un menù a tendina, o crearne una nuova impostando il nome, la descrizione e la categoria di appartenza, quest'ultima scelta da un menù a tendina o creata inserendone il nome. [[exception 6](#exceptions-7)] [[exception 2](#exceptions-7)]
>> - [extension 2] Allo step [9](#descrizione-7), se il browser dell’utente è compatibile con service workers, un id corrispondente all'attività creata verrà memorizzato anche sul dispositivo dell’utente.
>> - [extension 3] Allo step [8](#descrizione-7), l'utente può inserire uno o più collegamenti esterni inerenti alla descrizione dell'attività.
>> - [extension 4] Allo step [8](#descrizione-7), l'utente può inserire un collegamento esterno all'immagine dell'attività.
>> - [extension 5] Allo step [8](#descrizione-7), l'utente può inserire il numero di partecipanti per squadra e/o il numero di squadre indicati per svolgere l'attività, qualora questa preveda una divisione in squadre. [[exception 3](#exceptions-7)]

----
![Visualizzare elenco segnalazioni](D2/img/UCD/8.png)
> #### **Titolo:**
>> Visualizzare elenco segnalazioni
> #### **Riassunto:**
>> Questo use case descrive come l’amministratore può consultare l’elenco delle	segnalazioni fatte dagli utenti sulle attività a partire dal menù.
> #### **Descrizione:**
>> 1. L’utente clicca sul pulsante “Elenco segnalazioni” e viene reindirizzato alla schermata di elenco segnalazioni. [[exception 2](#exceptions-8)]
>> 2. Il sistema chiede a MongoDB la lista di segnalazioni fatte dagli utenti autenticati. [[exception 3](#exceptions-8)]
>> 3. Il sistema fornisce la lista di attività con un numero di segnalazioni maggiore di 0, con il nome dell’attività e il rispettivo numero di segnalazioni. [[exception 4](#exceptions-8)]
>> 4. L’utente clicca sull’attività scelta e viene reindirizzato alla schermata di segnalazioni specifiche dell’attività scelta. [[exception 1](#exceptions-8)]
>> 5. Il sistema fornisce la lista di segnalazioni della singola attività, con relativo titolo e breve descrizione.
> #### **Exceptions:**
>> - [exception 1] L'attività non esiste più, MongoDB non aggiornato.
>> - [exception 2] In assenza di connessione internet viene inviato un messaggio di errore.
>> - [exception 3] Impossibile stabilire una connessione con MongoDB, il sistema informa l'utente dell'impossibilità temporanea di visualizzare le segnalazioni.
>> - [exception 4] In assenza di attività con segnalazioni, il sistema informa l'utente dell'impossibilità di trovare le attività richieste.
> #### **Extension points:**
>> --

----
![Logout](D2/img/UCD/9.png)
> #### **Titolo:**
>> Logout
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato può effettuare il logout dall’applicazione, cambiando quindi ruolo in utente anonimo.
> #### **Descrizione**
>> 1. L'utente clicca sul pulsante logout. [[extension 1](#extension-points-9)] [[exception 1](#exceptions-9)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
> #### **Extension points:**
>> - [extension 1] Allo step [1](#descrizione-9) e erano presenti dati individuali dell’utente nello spazio riservato all’applicazione sul filesystem dell’utente, il sistema li elimina.

----
![Segnalare un'attività](D2/img/UCD/10.png)
> #### **Titolo:**
>> Segnalare un'attività
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato può segnalare un’attività a partire dalla pagina di visualizzazione delle informazioni dell’attività.
> #### **Descrizione:**
>> 1. L’utente clicca sul pulsante segnala.
>> 2. Il sistema fornisce all’utente due casella di testo e un pulsante di invio.
>> 3. L’utente inserisce un breve titolo e un messaggio di motivazione della segnalazione nella casella di testo. [[exception 2](#exceptions-10)]
>> 4. L’utente clicca sul pulsante d’invio. [[exception 1](#exceptions-10)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
>> - [exception 2] Il messaggio può avere lunghezza massima di 500 caratteri, mentre il titolo può avere lunghezza massima di 50 caratteri, e nessuno dei due può essere vuoto.
> #### **Extension points:**
>> --

----
![Valutare un'attività](D2/img/UCD/11.png)
> #### **Titolo:**
>> Valutare un'attività
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato può valutare un’attività con un punteggio numerico a partire dalla pagina di visualizzazione delle informazioni dell’attività.
> #### **Descrizione:**
>> 1. L’utente clicca su una barra con 5 stelline, in corrispondenza della valutazione che intende lasciare: il numero (semintero) di stelline da sinistra al punto selezionato dall’utente indica la valutazione in numeri decimali nel range [0-5] con scarto di 0.5.
>> 2. L’utente clicca sul pulsante per confermare. [[exception 1](#exceptions-11)]
>> 3. Il sistema invia il dato numerico a MongoDB. [[extension 1](#extension-points-11)] [[exception 2](#exceptions-11)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
>> - [exception 2] Impossibile stabilire una connessione con MongoDB, il sistema informa l'utente dell'impossibilità temporanea di valutare l'attività.
> #### **Extension points:**
>> - [extension 1] Allo step [3](#descrizione-11), se il browser dell’utente è compatibile con service workers, il dato numerico verrà memorizzato anche sul dispositivo dell’utente.

----
![Proporre un'attività](D2/img/UCD/12.png)
> #### **Titolo:**
>> Proporre un'attività
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato online può proporre una nuova attività per il catalogo delle attività a partire dal menù.
> #### **Descrizione:**
>> 1. L’utente clicca sul bottone “Aggiungi attività” e viene reindirizzato alla schermata di creazione di un’attività. [[exception 1](#exceptions-12)]
>> 2. L’utente inserisce il titolo dell’attività. [[exception 6](#exceptions-12)]
>> 3. L’utente inserisce la descrizione dell’attività. [[exception 2](#exceptions-12)]
>> 4. L’utente inserisce il range di età per cui l’attività è adeguata o raccomandata, fornendo un valore intero non negativo iniziale e un valore intero non negativo finale. [[exception 3](#exceptions-12)]
>> 5. L’utente inserisce il range di durata dell’attività in minuti. [[exception 4](#exceptions-12)]
>> 6. L’utente inserisce il range del numero di partecipanti per cui l’attività è adeguata o raccomandata, fornendo un valore intero non negativo iniziale e un valore intero non negativo finale. [[exception 3](#exceptions-12)]
>> 7. [[extension 1](#extension-points-12)], [[extension 3](#extension-points-12)], [[extension 4](#extension-points-12)], [[extension 5](#extension-points-12)]
>> 8. L’utente clicca sul pulsante per confermare [[extension 2](#extension-points-12)] [[exception 5](#exceptions-12)] [[exception 1](#descrizione-12)]
>> 9. Il sistema invia la proposta di attività a MongoDB [[extension 2](#exceptions-12)] [[exception 7](#exceptions-12)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione
>> - [exception 2] Dopo aver inserito 2000 caratteri nel campo relativo alla descrizione, se l’utente proverà ad inserire altri caratteri questi non verranno inseriti, il campo di inserimento sarà evidenziato di rosso e riporterà una scritta che informa l’utente che il limite massimo di caratteri è stato raggiunto
>> - [exception 3] Se il valore finale è strettamente minore del valore iniziale o se uno dei due valori non è intero o se uno dei due valori è negativo o se uno dei due valori è maggiore di 99, il campo di inserimento del range sarà evidenziato in rosso e riporterà una scritta che informa l’utente dei vincoli non rispettati
>> - [exception 4] Se il valore finale è strettamente minore del valore iniziale o se uno dei due valori non è intero o se uno dei due valori è negativo o se uno dei due valori è maggiore di 9.999, il campo di inserimento del range sarà evidenziato in rosso e riporterà una scritta che informa l’utente dei vincoli non rispettati
>> - [exception 5] Se l’utente ha inserito un titolo corrispondente a quello di un’attività già presente nel catalogo o proposta da un’altro utente, o se l'utente ha lasciato il campo del titolo vuoto, il sistema mostrerà un messaggio di errore ed evidenzierà in rosso il campo di inserimento del titolo
>> - [exception 6] Dopo aver inserito 20 caratteri nel campo relativo al titolo, se l’utente proverà ad inserire altri caratteri questi non verranno inseriti, il campo di inserimento sarà evidenziato di rosso e riporterà una scritta che informa l’utente che il limite massimo di caratteri è stato raggiunto
>> - [exception 7] Impossibile stabilire una connessione con MongoDB, il sistema informa l'utente dell'impossibilità temporanea di proporre un'attività.
> #### **Extension points:**
>> - [extension 1] Allo step [8](#descrizione-12), l’utente può scegliere una o più etichette con cui contrassegnare l’attività da un menù a tendina.
>> - [extension 2] Allo step [9](#descrizione-12), se il browser dell’utente è compatibile con service workers, un id corrispondente alla proposta di attività verrà memorizzato anche sul dispositivo dell’utente.
>> - [extension 3] L'utente può inserire uno o più collegamenti esterni inerenti alla descrizione dell'attività.
>> - [extension 4] L'utente può inserire un collegamento esterno all'immagine dell'attività.
>> - [extension 5] L'utente può inserire il numero di partecipanti per squadra e/o il numero di squadre indicati per svolgere l'attività, qualora questa preveda una divisione in squadre. [[exception 3](#exceptions-12)]

----
![Modificare un'attività proposta](D2/img/UCD/13.png)
> #### **Titolo:**
>> Modificare un'attività proposta
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato online può modificare una propria proposta di attività a partire dalla pagina di visualizzazione delle informazioni dell’attività.
> #### **Descrizione:**
>> 1. L’utente clicca sul bottone “Modifica proposta” e viene reindirizzato alla schermata di modifica di una proposta di attività. [[exception 1](#exceptions-13)]
>> 2. [[extension 1](#extension-points-13)]
>> 3. L’utente clicca sul pulsante per confermare. [[exception 1](#exceptions-13)] [[exception 2](#exceptions-13)]
>> 4. Il sistema invia i dati modificati a MongoDB. [[extension 2](#extension-points-13)] [[exception 3](#exceptions-13)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
>> - [exception 2] Se l’utente ha inserito un titolo corrispondente a quello di un’attività già presente nel catalogo o proposta da un’altro utente, il sistema mostrerà un messaggio di errore ed evidenzierà in rosso il campo di inserimento del titolo.
>> - [exception 3] Impossibile stabilire una connessione con MongoDB, il sistema informa l'utente dell'impossibilità temporanea di modificare un'attività proposta.
> #### **Extension points:**
>> - [extension 1] Allo step 2 l’utente può modificare uno qualsiasi dei campi dell’attività, con modalità, eccezioni ed estensioni descritte negli step 2.-8. dello use case ([“Proporre un’attività”](#titolo-12)).
>> - [extension 2] Qualora il dispositivo dell'utente lo permetta, avverrà un aggiornamento della copia locale dei dati dell'utente e del catalogo (["Aggiornare catalogo locale"](#titolo-26)).

----
![Manipolare liste di attività](D2/img/UCD/14.png)
> #### **Titolo:**
>> Manipolare liste di attività
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato online può effettuare un’azione di modifica delle sue liste di attività, a partire dalla schermata "Liste".
> #### **Descrizione:**
>> 1. [[extension 1](#extension-points-14)] [[extension 2](#extension-points-14)] [[extension 3](#extension-points-14)] [[extension 4](#extension-points-14)] [[exception 1](#exceptions-14)]
>> 2. [[extension 5](#extension-points-14)]
> #### **Exceptions:**
>> - [exception 1] Tentando di inziare una qualsiasi attività di manipolazione di liste in assenza di connessione ad Internet, il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione (ulteriore chiarimento nelle descrzioni degli use case delle singole operazioni di manipolazione di liste).
> #### **Extension points:**
>> - [extension 1] Allo step [2](#descrizione-14), use case “Creare una lista di attività”.
>> - [extension 2] Allo step [2](#descrizione-14), use case “Rimuovere una lista di attività”.
>> - [extension 3] Allo step [2](#descrizione-14), l’utente clicca una lista di attività, passa alla schermata della lista, use case “Rimuovere un’attività da una lista”.
>> - [extension 4] Allo step [2](#descrizione-14), spostarsi sulla pagina di visualizzazione delle informazioni di un’attività, use case “Aggiungere un’attività ad una lista di attività”.
>> - [extension 5] Qualora il dispositivo dell'utente lo permetta, dopo una qualsiasi operazione di manipolazione di liste, avverrà un aggiornamento della copia locale dei dati dell'utente e del catalogo (["Aggiornare catalogo locale"](#titolo-26)).

----
> #### **Titolo:**
>> Creare una lista di attività
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato online può creare una nuova lista di attività a partire dalla schermata “Liste”.
> #### **Descrizione:**
>> 1. L’utente clicca sul pulsante +. [[exception 1](#exceptions-15)][[exception 4](#exceptions-15)]
>> 2. L’utente inserisce il nome che intende dare alla nuova lista. [[exception 2](#exceptions-15)]
>> 3. L’utente clicca sul pulsante per confermare. [[exception 3](#exceptions-15)] [[exception 1](#exceptions-15)]
>> 4. Il sistema invia la lista di attività a MongoDB. [[extension 1](#extension-points-15)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
>> - [exception 2] Dopo aver inserito 20 caratteri nel campo relativo al nome, se l’utente proverà ad inserire altri caratteri questi non verranno inseriti, il campo di inserimento sarà evidenziato di rosso e riporterà una scritta che informa l’utente che il limite massimo di caratteri è stato raggiunto.
>> - [exception 3] Se l’utente ha inserito un nome corrispondente a quello di una lista di attività presente tra le sue liste personali, o se l'utente ha lasciato il campo del nome vuoto, il sistema mostrerà un messaggio di errore ed evidenzierà in rosso il campo di inserimento del nome.
>> - [exception 4] Se l'utente ha già creato 99 liste di attività, il pulsante più non sarà disponibile e il sistema mostrerà all'utente un messaggio di avviso per informarlo.
> #### **Extension points:**
>> - [extension 1] Allo step [4](#descrizione-15), se il browser dell’utente è compatibile con service workers, la lista creata verrà memorizzata anche sul dispositivo dell’utente.

----
> #### **Titolo:**
>> Rimuovere una lista di attività
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato online può eliminare una delle proprie liste di attività a partire dalla schermata “Liste”.
> #### **Descrizione:**
>> 1. L’utente clicca e tiene premuto su una propria lista di attività. [[exception 2](#exceptions-16)]
>> 2. L’utente clicca sul pulsante cestino. [[exception 1](#exceptions-16)]
>> 3. Il sistema invia a MongoDB la richiesta di rimozione della lista. [[extension 1](#extension-points-16)] [[exception 3](#exceptions-16)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
>> - [exception 2] Se l’utente proverà a rimuovere la lista dei preferiti il pulsante “Cestino” non comparirà.
>> - [exception 3] Impossibile stabilire una connessione con MongoDB, il sistema informa l'utente dell'impossibilità temporanea di manipolare una lista di attività.
> #### **Extension points:**
>> - [extension 1] Allo step [3](#descrizione-16), se il browser dell’utente è compatibile con service workers, la lista rimossa verrà rimossa anche dal dispositivo dell’utente.

----
> #### **Titolo:**
>> Aggiungere un'attività ad una lista
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato online può aggiungere un’attività ad una sua lista di attività a partire dalla pagina di visualizzazione delle informazioni di un’attività.
> #### **Descrizione:**
>> 1. L’utente clicca sul pulsante +. [[extension 1](#extension-points-17)] [[exception 1](#exceptions-17)]
>> 2. L’utente seleziona una lista di attività.
>> 3. L’utente clicca sul pulsante per confermare. [[exception 1](#exceptions-17)]
>> 4. Il sistema invia a MongoDB l’id dell’attività aggiunta. [[extension 2](#extension-points-17)] [[exception 3](#exceptions-17)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
>> - [exception 2] Se la lista selezionata ha già 9.999 attività, l’attività selezionata non verrà aggiunta e il sistema mostrerà all’utente un messaggio di errore.
>> - [exception 3] Impossibile stabilire una connessione con MongoDB, il sistema informa l'utente dell'impossibilità temporanea di aggiungere l'attività ad una lista.
> #### **Extension points:**
>> - [extension 1] Allo step [1](#descrizione-17), cliccando sul pulsante cuore l’attività verrà aggiunta direttamente alla lista dei preferiti. [[exception 1](#exceptions-17)] [[exception 2](#exceptions-17)]
>> - [extension 2] Allo step [4](#descrizione-17), se il browser dell’utente è compatibile con service workers, l’id dell’attività aggiunta verrà memorizzato anche sul dispositivo dell’utente.

----
> #### **Titolo:**
>> Rimuovere un’attività da una lista
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato online può rimuovere un’attività da una lista di attività personale a partire dalla schermata di visualizzazione della lista.
> #### **Descrizione:**
>> 1. L’utente clicca e tiene premuto sull’attività che intende rimuovere [[exception 2](#exceptions-18)]
>> 2. L’utente clicca sul pulsante cestino [[exception 1](#extension-points-18)]
>> 3. Il sistema invia a MongoDB la richiesta di rimozione dell’attività dalla lista [[extension 1](#extension-points-18)] [[exception 3](#exceptions-18)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
>> - [exception 2] Se la lista è vuota l’utente non può rimuovere alcuna attività.
>> - [exception 3] Impossibile stabilire una connessione con MongoDB, il sistema informa l'utente dell'impossibilità temporanea di rimuovere l'attività ad una lista.
> #### **Extension points:**
>> - [extension 1] Se il browser dell’utente è compatibile con service workers, l’attività verrà rimossa dalla relativa lista anche dal dispositivo dell’utente.

----
![Utilizzare strumento FISCHIETTO](D2/img/UCD/19.png)
> #### **Titolo:**
>> Utilizzare strumento FISCHIETTO
> #### **Riassunto:**
>> Questo use case descrive come l'utente può utilizzare lo strumento FISCHIETTO, a partire dal menù
> #### **Descrizione:**
>> 1. L'utente clicca sul pulsante "Strumenti" presente nel menù e viene reindirizzato alla schermata contentente la lista di tool.
>> 2. L'utente clicca sul pulsante "FISCHIETTO".
>> 3. [[extension 1](#extension-points-19)] [[extension 2](#extension-points-19)] [[extension 3](#extension-points-19)]
> #### **Exceptions:**
>> [exception 1] Il file selezionato supera i 100MB, il sistema informa l'utente che non è possibile caricare il suono selezionato.
> #### **Extension points:**
>> - [extension 1] Allo step [3](#descrizione-19), cliccando sul pulsante "Suoni", che apre un menù a tendina, l'utente può selezionare il suono desiderato.
>> - [extension 2] Allo step [3](#descrizione-19), cliccando sul pulsante "Suoni", che apre un menù a tendina, in fondo è presente un "+", che una volta cliccato permette all'utente di caricare un nuovo suono da utilizzare. [[exception 1](#exception-points-19)]
>> - [extension 3] Allo step [3](#descrizione-19), l'utente può cliccare sull'immagine del fischietto per riprodurre il suono selezionato.

----
![Utilizzare strumento TIMER](D2/img/UCD/20.png)
> #### **Titolo:**
>> Utilizzare strumento TIMER
> #### **Riassunto:**
>> Questo use case descrive come l'utente può utilizzare lo strumento TIMER, a partire dal menù.
> #### **Descrizione:**
>> 1. L'utente clicca sul pulsante "Strumenti" presente nel menù e viene reindirizzato alla schermata contenente la lista di tool.
>> 2. L'utente clicca sul pulsante "TIMER".
>> 3. Il sistema mostra di default il timer impostato al valore 00:00:00.
>> 4. [[extension 1](#extension-points-20)] [[extension 2](#extension-points-20)] [[extension 3](#extension-points-20)] [[extension 4](#extension-points-20)] [[extension 5](#extension-points-20)] [[extension 6](#extension-points-20)] [[extension 7](#extension-points-20)]
> #### **Exceptions:**
>> [exception 1] Il file selezionato supera i 100MB, il sistema informa l'utente che non è possibile caricare il suono selezionato.
> #### **Extension points:**
>> - [extension 1] Allo step [4](#descrizione-20), l'utente può scorrere sulle cifre per modificare il valore di partenza del timer.
>> - [extension 2] Allo step [4](#descrizione-20), l'utente può far partire il timer cliccando sul pulsante "Avvia". In quel momento al posto del pulsante "Avvia", compariranno due pulsanti, "Pausa" e "Annulla".
>> - [extension 3] Allo step [4](#descrizione-20), l'utente può mettere in pausa il timer cliccando sul pulsante "Pausa". Il valore verrà momentaneamente fermato e comparirà il pulsante "Riprendi".
>> - [extension 4] Allo step [4](#descrizione-20), l'utente può fermare il timer cliccando sul pulsante "Annulla". Il valore verrà resettato a quello impostato precedentemente e comparirà nuovamente il pulsante "Avvia", che andrà a sostituire "Pausa"/"Riprendi" e "Annulla".
>> - [extension 5] Allo step [4](#descrizione-20), cliccando sul pulsante "Suoni", che apre un menù a tendina, l'utente può selezionare il suono desiderato.
>> - [extension 6] Allo step [4](#descrizione-20), cliccando sul pulsante "Suoni", che apre un menù a tendina, in fondo è presente un "+", che una volta cliccato permette all'utente di caricare un nuovo suono da utilizzare. [[exception 1](#exception-points-20)]
>> - [extension 7] Allo step [4](#descrizione-20), allo scadere del timer verrà riprodotto il suono selezionato.

----
![Utilizzare strumento CRONOMETRO](D2/img/UCD/21.png)
> #### **Titolo:**
>> Utilizzare strumento CRONOMETRO
> #### **Riassunto:**
>> Questo use case descrive come l'utente può utilizzare lo strumento CRONOMETRO, a partire dal menù.
> #### **Descrizione:**
>> 1. L'utente clicca sul pulsante "Strumenti" presente nel menù e viene reindirizzato alla schermata contenente la lista di tool.
>> 2. L'utente clicca sul pulsante "CRONOMETRO".
>> 3. Il sistema mostra come valore di partenza 00:00.00
>> 4. Il sistema mostra due pulsanti, "Avvia" e "Parziale" con quest'ultimo inizialmente non disponibile, in quanto il cronometro non è ancora stato avviato.
>> 4. [[extension 1](#extension-points-21)] [[extension 2](#extension-points-21)] [[extension 3](#extension-points-21)] [[extension 4](#extension-points-21)]
> #### **Exceptions:**
>> [exception 1] Se l'utente ha già salvato 99 tempi parziali, il pulsante più non sarà disponibile e il sistema mostrerà all'utente un messaggio di avviso per informarlo.
> #### **Extension points:**
>> - [extension 1] Allo step [4](#descrizione-21), l'utente può far partire il cronometro cliccando sul pulsante "Avvia", rappresentato da un triangolino. In quel momento al posto del pulsante "Avvia", comparirà il pulsante "Ferma" e il pulsante "Parziale" diventerà disponibile.
>> - [extension 2] Allo step [4](#descrizione-21), l'utente può mettere in pausa il cronometro cliccando sul pulsante "Ferma". Il valore verrà momentaneamente fermato e compariranno il pulsante "Riprendi" al posto di "Ferma" e "Ripristina" al posto di "Parziale".
>> - [extension 3] Allo step [4](#descrizione-21), l'utente può fermare il cronometro cliccando sul pulsante "Ripristina". Il valore verrà riportato a 00:00:00 e compariranno nuovamente i pulsanti "Avvia" e "Parziale".
>> - [extension 4] Allo step [4](#descrizione-21), l'utente può cliccare sul pulsante "Parziale" per salvare il tempo mostrato in quel momento dal sistema e scriverlo a carattere ridotto sotto quello principale. [[exception 1](#exceptions-21)]

----
![Utilizzare strumento DADI](D2/img/UCD/22.png)
> #### **Titolo:**
>> Utilizzare strumento DADI
> #### **Riassunto:**
>> Questo use case descrive come l'utente può utilizzare lo strumento DADI, a partire dal menù.
> #### **Descrizione:**
>> 1. L'utente clicca sul pulsante "Strumenti" presente nel menù e viene reindirizzato alla schermata contenente la lista di tool.
>> 2. L'utente clicca sul pulsante "DADI".
>> 3. L'utente sceglie il tipo di elementi che vuole estrarre con i dadi, cliccando un'opzione tra: "Numeri", "Parole", "Colori", "Immagini".
>> 4. L'utente sceglie il numero di elementi totali presenti nel campione da cui estrarre. [[exception 1](#exceptions-22)]
>> 5. L'utente riempie il campione degli elementi che possono essere estratti, con diverse modalità a seconda del tipo di elementi che ha selezionato. [[extension 1](#extension-points-22)][[extension 2](#extension-points-22)][[extension 3](#extension-points-22)][[extension 4](#extension-points-22)]
>> 6. L'utente sceglie un'opzione tra "Estrazione con reimmissione" ed "Estrazione senza reimmissione".
>> 7. L'utente clicca sul pulsante "Estrai". [[exception 2](#exceptions-22)]
>> 8. Il sistema mostra all'utente l'elemento estratto e il numero di estrazioni effettuate fino a quel momento (dal momento di creazione della lista corrente)
> #### **Exceptions:**
>> - [exception 1] Se l’utente ha inserito un valore non intero o negativo o maggiore di 9.999, il campo di inserimento del valore sarà evidenziato in rosso e riporterà una scritta che informa l’utente dei vincoli non rispettati.
>> - [exception 2] Se l'utente ha selezionato "Estrazione senza reimmissione" e ha già estratto un numero di elementi pari a quelli presenti nel campione, il sistema mostrerà all'utente un messaggio di errore per informarlo che gli elementi da estrarre sono esauriti.
>> - [exception 3] Dopo aver inserito 20 caratteri nel campo relativo alla parola, se l’utente proverà ad inserire altri caratteri questi non verranno inseriti, il campo di inserimento sarà evidenziato di rosso e riporterà una scritta che informa l’utente che il limite massimo di caratteri è stato raggiunto.
>> - [exception 4] L'utente non potrà cliccare il pulsante per confermare se ha lasciato il campo di inserimento vuoto.
>> - [exception 5] Se l’utente prova ad inserire un'immagine la cui dimensione sommata alla dimensione totale delle immagini caricate nel campione corrente ecceda i 100MB o lo spazio disponibile al browser sul dispositivo dell'utente, questa non verrà inserita, il campo di inserimento sarà evidenziato di rosso e riporterà una scritta che informa l’utente che il limite massimo di dati di immagini è stato raggiunto, l'utente potrà scegliere di eliminare alcune immagini già inserite per ridurre il carico totale di dati.
> #### **Extension points:**
>> - [extension 1] Se la tipologia di elementi selezionata è "Numeri", l'utente dovrà scegliere l'estremo inferiore del range da cui vuole estrarre e il passo tra due elementi consecutivi. [[exception 1](#exceptions-21)]
>> - [extension 2] Se la tipologia di elementi selezionata è "Parole", il sistema chiederà all'utente di inserire una parola e di confermare, per un numero di volte pari al numero di elementi totali del campione. [[exception 3](#exceptions-22)] [[exception 4](#exceptions-22)]
>> - [extension 3] Se la tipologia di elementi selezionata è "Colori", il sistema mostrerà all'utente una griglia di colori, gli chiederà di selezionarne uno e di confermare, per un numero di volte pari al numero di elementi totali del campione. [[exception 4](#exceptions-22)]
>> - [extension 3] Se la tipologia di elementi selezionata è "Immagini", il sistema chiederà all'utente di inserire un'immagine dal proprio dispositivo e di confermare, per un numero di volte pari al numero di elementi totali del campione. [[exception 4](#exceptions-22)] [[exception 5](#exceptions-22)]

----
![Utilizzare strumento SEGNA-PUNTI](D2/img/UCD/23.png)
> #### **Titolo:**
>> Utilizzare strumento SEGNA-PUNTI
> #### **Riassunto:**
>> Questo use case descrive come l'utente può utilizzare lo strumento SEGNA-PUNTI, a partire dal menù.
> #### **Descrizione:**
>> 1. L'utente clicca sul pulsante "Strumenti" presente nel menù e viene reindirizzato alla schermata contenente la lista di tool.
>> 2. L'utente clicca sul pulsante "SEGNA-PUNTI"
>> 3. Per ogni contatore che vuole creare, l'utente clicca sul pulsante + e inserisce nella casella apposita il nome che vuole assegnare al contatore corrente. [[exception 1](#descrizione-23)] [[exception 2](#descrizione-23)] [[exception 3](#exceptions-23)]
>> 4. L'utente clicca sul pulsante di conferma.
>> 5. Il sistema mostrerà una lista di coppie di pulsanti "+1" e "-1" con il relativo nome e contatore inizialmente impostato a 0.
>> 6. [[extension 1](#extension-points-23)] [[exception 4](#exceptions-23)]
> #### **Exceptions:**
>> - [exception 1] L'utente non può procedere alla creazione di un nuovo contatore se ha lasciato vuoto il campo relativo al nome di quello corrente.
>> - [exception 2] L'utente può inserire fino a un massimo di 99 contatori.
>> - [exception 3] Il nome di ogni contatore può avere al massimo 99 caratteri.
>> - [exception 4] Ogni contatore può assumere valore massimo 500 e minimo -500.
> #### **Extension points:**
>> - [extension 1] Allo step [5](#descrizione-23), l'utente può incrementare o decrementare di 1, il contatore di ciascun segna punti.

----
![Utilizzare strumento CREAZIONE SQUADRE](D2/img/UCD/24.png)
> #### **Titolo:**
>> Utilizzare strumento CREAZIONE SQUADRE
> #### **Riassunto:**
>> Questo use case descrive come l'utente può utilizzare lo strumento CREAZIONE SQUADRE, a partire dal menù.
> #### **Descrizione:**
>> 1. L'utente clicca sul pulsante "Strumenti" presente nel menù e viene reindirizzato alla schermata contenente la lista di tool.
>> 2. L'utente clicca sul pulsante "CREAZIONE SQUADRE".
>> 3. [[extension 1](#extension-points-24)] [[extension 2](#extension-points-24)] [[extension 3](#extension-points-24)] [[exception 3](#exceptions-24)] [[exception 4](#exceptions-24)] [[exception 5](#exceptions-24)]
>> 4. L'utente clicca sul pulsante "Conferma". [[exception 1](#exceptions-24)] [[exception 2](#exceptions-24)]
>> 5. L'utente inserisce nelle caselle di testo apposite i nomi del numero di squadre prestabilito. [[exception 6](#exceptions-24)]
>> 6. [[extension 4](#extension-points-24)]
>> 7. L'utente clicca su "Inizia estrazione"
>> 8. Il sistema inizialmente mostra uno schermo interamente colorato con nessuna scritta, e ogni qualvolta esso viene premuto dall'utente appare il nome della squadra a cui l'utente viene assegnato. Questa operazione si ripete un numero di volte corrispondente al numero di partecipanti.
> #### **Exceptions:**
>> - [exception 1] Nel caso l'utente non abbia inserito almeno 2 tra le informazioni sul numero di partecipanti, numero di squadre e numero di componenti per squadra, il sistema mostrerà una schermata di errore dove chiede all'utente di inserire i valori richiesti.
>> - [exception 2] Nel caso i tre valori: numero di squadre, numero di partecipanti e numero di componenti per squadra non siano compatibili, il sistema ostrerà un messaggio di avviso all'utente e terrà in considerazione solamente il numero di partecipanti e il numero di squadre.
>> - [exception 3] L'utente può creare al più 99 squadre.
>> - [exception 4] Ogni squadre può avere al più 99 partecipanti.
>> - [exception 5] Il numero totale di partecipanti è al più 9801.
>> - [exception 6] Il nome di una squadra non può eccedere i 99 caratteri.
> #### **Extension points:**
>> - [extension 1] Allo step [3](#descrizione-24), l'utente può inserire nella casella di testo apposita, il numero di squadre che desidera creare.
>> - [extension 2] Allo step [3](#descrizione-24), l'utente può inserire nella casella di testo apposita, il numero di componenti per squadra.
>> - [extension 3] Allo step [3](#descrizione-24), l'utente può inserire nella casella di testo apposita, il numero di partecipanti dell'attività.
>> - [extension 4] Allo step [6](#descrizione-24), cliccando sul pulsante "Metodo divisione", l'utente può selezionare la metodologia di divisione in squadre desiderata, l'opzione di default è "Balanced".

----
![Filtrare catalogo](D2/img/UCD/25.png)
> #### **Titolo:**
>> Filtrare catalogo
> #### **Riassunto:**
>> Questo use case descrive come l'utente può filtrare le attività presenti nel catalogo a partire dal menù.
> #### **Descrizione:**
>> 1. L'utente clicca su "Catalogo" e viene reindirizzato alla schermata del catalogo.
>> 2. L'utente clicca su "Filtri" e il sistema mostrà all'utente un menù a tendina con un campo di inserimento per ogni campo delle attività.
>> 3. L'utente inserisce i valori desiderati nei campi per cui vuole filtrare. [[extension 1](#extension-points-25)] [[extension 2](#extension-points-25)] [[extension 3](#extension-points-25)] [[extension 4](#extension-points-25)] [[extension 5](#extension-points-25)] [[extension 6](#extension-points-25)] [[extension 7](#extension-points-25)]
>> 4. L'utente chiude il menù a tendina dei filtri e clicca sul pulsante "Cerca".
>> 5. Il sistema chiede a un database e mostra all'utente gli elementi del catalogo che rispettano i filtri selezionati, secondo le modalità, estensioni ed eccezioni di [["Consultare catalogo"](#titolo-1)]. [[exception 1](#exceptions-25)]
> #### **Exceptions:**
>> - [exception 1] Non verrà mostrato alcun risultato se nessun elemento del catalogo corrisponde ai filtri selezionati.
>> - [exception 2] Dopo aver inserito 20 caratteri nel campo relativo al titolo, se l’utente proverà ad inserire altri caratteri questi non verranno inseriti, il campo di inserimento sarà evidenziato di rosso e riporterà una scritta che informa l’utente che il limite massimo di caratteri è stato raggiunto.
>> - [exception 3] Dopo aver inserito 20 caratteri nel campo relativo alla descrizione, se l’utente proverà ad inserire altri caratteri questi non verranno inseriti, il campo di inserimento sarà evidenziato di rosso e riporterà una scritta che informa l’utente che il limite massimo di caratteri è stato raggiunto.
>> - [exception 4] Se il valore finale è strettamente minore del valore iniziale o se uno dei due valori non è intero o se uno dei due valori è negativo o se uno dei due valori è maggiore di 99, il campo di inserimento del range sarà evidenziato in rosso e riporterà una scritta che informa l’utente dei vincoli non rispettati.
>> - [exception 5] Se l’utente ha inserito un valore non intero o negativo o maggiore di 999, il campo di inserimento della durata sarà evidenziato in rosso e riporterà una scritta che informa l’utente dei vincoli non rispettati.
>> - [exception 6] Se il valore inserito non è intero o se è negativo o maggiore di 99, il campo di inserimento del range sarà evidenziato in rosso e riporterà una scritta che informa l’utente dei vincoli non rispettati.
> #### **Extension points:**
>> - [extension 1] L'utente può svuotare un campo in cui ha inserito un valore premendo un apposito pulsante accanto al campo, o, nel caso dei tag, può rimuovere un singolo tag cliccando su di esso.
>> - [extension 2] L'utente può inserire un'espressione che deve essere presente per intero (e non frammentata) all'interno del titolo di un'attività; di default il campo è vuoto. [[exception 2](#exceptions-25)]
>> - [extension 3] L'utente può inserire un'espressione che deve essere presente per intero (e non frammentata) all'interno della descrizione di un'attività; di default il campo è vuoto. [[exception 3](#exceptions-25)]
>> - [extension 4] L’utente può inserire un range di età dei partecipanti all'attività che deve essere compreso (estremi inclusi) nel range di età per cui l’attività è adeguata o raccomandata, fornendo un valore intero non negativo iniziale e un valore intero non negativo finale; di default il primo valore è 0, il secondo è 99. [[exception 4](#exceptions-25)]
>> - [extension 5] L’utente può scegliere un intervallo di tempo all'interno del quale deve essere compreso il range di durata dell'attività, fornendo un valore intero non negativo iniziale e un valore intero non negativo finale; di default il primo valore è 0, il secondo è 9.999. [[exception 5](#exceptions-25)]
>> - [extension 6] L'utente può inserire un numero partecipanti che deve essere compreso nel range del numero di partecipanti per cui l’attività è adeguata o raccomandata, fornendo un valore intero non negativo; di default il campo è vuoto. [[exception 6](#exceptions-25)]
>> - [extension 7] L'utente può aprire la lista dei tag e selezionare un insieme di tag che l'attività deve avere; di default il campo è vuoto.

----

![Aggiornare catalogo locale](D2/img/UCD/26.png)
> #### **Titolo:**
>> Aggiornare catalogo locale
> #### **Riassunto:**
>> Questo use case descrive come il sistema effettua la creazione o l'aggiornamento della copia del catalogo di attività (e dei dati relativi all'utente nel caso di un utente autenticato) presente sul dispositivo dell'utente.
> #### **Descrizione:**
>> 1. L'utente avvia l'applicazione o il tempo trascorso dall'ultimo aggiornamento del catalogo locale supera 30 minuti o l'utente autenticato effettua un'operazione di modifica del catalogo o delle liste personali o tramite il pulsante di sincronizzazione manuale. [[exception 2](#exceptions-26)][[exception 3](#exceptions-26)]
>> 2. Il sistema chiede a MongoDB le modifiche avvenute al catalogo remoto (e ai dati relativi all'utente nel caso di un utente autenticato) dall'ultimo aggiornamento del catalogo locale (posto di default a zero se questo non è presente in memoria). [[exception 1](#exceptions-26)] [[extension 1](#extension-points-26)]
>> 3. Il sistema integra attraverso IndexedDB i dati locali con le modifiche avvenute.
>> 4. Il sistema imposta la data dell'ultimo aggiornamento del catalogo locale alla data corrente nel momento in cui ha ricevuto risposta da MongoDB (comprensiva di ore, minuti, secondi, millisecondi e nanosecondi).
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
>> - [exception 2] Nel caso in cui il browser dell'utente non supporti l'installazione di service worker, il sistema mostrerà all’utente un messaggio di errore che indicherà che non è stato possibile creare una copia locale del catalogo e che non sarà possibile utilizzare alcuna funzionalità in assenza di connessione.
>> - [exception 2] Nel caso in cui il browser dell'utente non supporti l'uso di IndexedDB API ma supporti service workers, il sistema mostrerà all’utente un messaggio di errore che indicherà che non è stato possibile creare una copia locale del catalogo, che non sarà possibile consultare il catalogo (o i dati personali in caso di un utente autenticato) in assenza di connessione, ma che sarà comunque possibile utilizzare i tools in assenza di connessione.
> #### **Extension points:**
>> - [extension 1] Se l'utente ha effettuato l'accesso sull'applicazione, il sistema richiederà a MongoDB anche le modifiche avvenute ai dati riguardanti l'utente.

----
![Consultare le liste](D2/img/UCD/27.png)
> #### **Titolo:**
>> Consultare le liste
> #### **Riassunto:**
>> Questo use case descrive come l'utente può consultare le proprie liste di attività a partire dal menù.
> #### **Descrizione:**
>> 1. L'utente clicca su "Liste".
>> 2. Il sistema chiede l'elenco delle liste di attività a un database (MongoDB o IndexedDB). [[extension 1](#extension-points-27)] [[extension 2](#extension-points-27)] [[exception 2](#exceptions-27)]
>> 2. Il sistema fornisce l'elenco di lista di attività con titolo della lista, sulle quali è possibile cliccare.
>> 3. L'utente clicca su una lista e il sistema mostrà all'utente l'elenco di attività presenti in quella lista. [[extension 3](#extension-points-27)]
>> 4. Cliccando su un’attività, l’utente viene reindirizzato alla schermata con le informazioni sull’attività stessa. [[exception 1](#exceptions-27)]
> #### **Exceptions:**
>> - [exception 1] Se il catalogo non è aggiornato, l'utente potrebbe essere reindirizzato ad una attività eliminata, in tal caso il sistema mostrerà all'utente un messaggio di errore.
>> - [exception 2] Se non c’è connessione ad Internet e non c’è una copia locale delle liste, non viene mostrato nessun elenco e compare un messaggio di errore.
> #### **Extension points:**
>> - [extension 1] Allo step [2](#descrizione-27), qualora sia stata salvata una copia dell'elenco delle liste di attività sul dispositivo dell’utente, il sistema può consultare quei dati attraverso IndexedDB senza l'uso di connessione ad Internet (“Consultare le liste locali”).
>> - [extension 2] Allo step [2](#descrizione-27), qualora ci sia connessione ad Internet il server può chiedere l'elenco di liste a MongoDB (“Consultare le liste remote”).
>> - [extension 3] L'utente può cliccare sul pulsante per esportare la lista, scegliere un'opzione tra formato pdf e JSON in cui esportare la lista, scegliere se salvare la lista sul dispositivo specificando il percorso o trasferirla ad un'altra applicazione (quando il dispositivo lo permette).

----
<div class="page-break"></div>
