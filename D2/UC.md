
# Use Case
Nel presente capitolo vengono descritti i casi d'uso del sistema.

> #### **Titolo:**
>> Effettuare l'accesso
> #### **Riassunto:**
>> Questo use case descrive come l’utente può accedere all’applicazione tramite il suo account Google.
> #### **Descrizione:**
>> 1. L’utente clicca sul pulsante login.
>> 2. Il sistema reindirizza l’utente sulla pagina di accesso di Google.
>> 3. L’utente inserisce le sue credenziali Google.
>> 4. Google Oauth genera un token e reindirizza l’utente sull’applicazione. [[exception 1](#exceptions)]
>> 5. Il sistema verifica il token ricevuto tramite l’api di Google. [[exception 2](#exceptions)]
>> 6. Se è il primo accesso dell’utente, viene creata una nuova entry su MongoDB, con un id personale e la mail.
>> 7. Se è già avvenuto almeno un accesso, vengono recuperati i dati dell’utente da MongoDB. [[extension 1](#extension-points)]
> #### **Exceptions:**
>> - [exception 1] Le credenziali non sono corrette, e non viene generato nessun token.
>> - [exception 2] Errore nella verifica del token, token non valido.
> #### **Extension points:**
>> - [extension 1] Allo step [7](#descrizione), se il browser dell’utente lo permette, i dati individuali dell’utente verranno memorizzati sul dispositivo dell’utente.

----
> #### **Titolo:**
>> Consultare catalogo
> #### **Riassunto:**
>> Questo use case descrive come l'utente può consultare il catalogo di attività dell’applicazione e interagire con le singole attività presenti nell’elenco.
> #### **Descrizione:**
>> 1. Il sistema chiede la lista di attività a un database. [[extension 1](#extension-points-1)] [[extension 2](#extension-points-1)] [[exception 2](#exceptions-1)]
>> 2. Il sistema fornisce la lista di attività con titolo e immagine delle stesse, sulle quali è possibile cliccare.
>> 3. Cliccando su un’attività, l’utente viene reindirizzato alla schermata con le informazioni sull’attività stessa. [[exception 1](#exceptions-1)]
> #### **Exceptions:**
>> - [exception 1] Utente viene reindirizzato ad attività eliminata, catalogo non aggiornato.
>> - [exception 2] Non c’è connessione ad internet e non c’è una copia locale del catalogo, quindi non viene mostrato nessun catalogo e compare un messaggio di errore.
> #### **Extension points:**
>> - [extension 1] Allo step [1](#descrizione-1), qualora sia stata salvata una copia del catalogo delle attività sul dispositivo dell’utente, il sistema può consultare quei dati senza interagire con sistemi esterni (“Consultare catalogo locale”).
>> - [extension 2] Allo step [1](#descrizione-1), qualora ci sia connessione ad internet il server può chiedere la lista a MongoDB (“Consultare catalogo remoto”).

----
> #### **Titolo:**
>> Visualizzare attività
> #### **Riassunto:**
>> Questo use case descrive come l’utente può visualizzare i dettagli specifici di ogni attività a partire dalla schermata del catalogo o di una lista, unicamente nel caso dell’utente autenticato.
> #### **Descrizione:**
>> 1. L’utente clicca sull’immagine o sul nome dell’attività scelta. [[exception 1](#exceptions-2)]
>> 2. Il sistema reindirizza l’utente a una schermata con i dettagli dell’attività stessa. [[extension 1](#exceptions-2)]
> #### **Exceptions:**
>> - [exception 1] L’attività scelta non è più presente nel catalogo, MongoDB non aggiornato. Viene mostrato un messaggio di errore.
> #### **Extension points:**
>> - [extension 1] Allo step [2](#descrizione-2), l’utente può accedere al tool di creazione squadre con i parametri richiesti dalla specifica attività.

----
> #### **Titolo:**
>> Utilizzare i tool
> #### **Riassunto:**
>> Questo use case descrive come l’utente può consultare la lista di tool presenti nell’applicazione.
> #### **Descrizione:**
>> 1. Il sistema fornisce la lista di tool con titolo degli stessi, sui quali è possibile cliccare.
>> 2. Cliccando su un tool, l’utente viene reindirizzato alla schermata di utilizzo del tool stesso. [[extension 1](#extension-points-3)] [[extension 2](#extension-points-3)] [[extension 3](#extension-points-3)] [[extension 4](#extension-points-3)] [[extension 5](#extension-points-3)] [[extension 6](#extension-points-3)]
> #### **Exceptions:**
>> -- 
> #### **Extension points:**
> - [extension 1] Allo step [2](#descrizione-3), l’utente può cliccare sul tool DADI e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento DADI).
> - [extension 2] Allo step [2](#descrizione-3), l’utente può cliccare sul tool TIMER e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento TIMER).
> - [extension 3] Allo step [2](#descrizione-3), l’utente può cliccare sul tool CRONOMETRO e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento CRONOMETRO).
> - [extension 4] Allo step [2](#descrizione-3), l’utente può cliccare sul tool FISCHIETTO e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento FISCHIETTO).
> - [extension 5] Allo step [2](#descrizione-3), l’utente può cliccare sul tool SEGNA-PUNTI e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento SEGNA-PUNTI).
> - [extension 6] Allo step [2](#descrizione-3), l’utente può cliccare sul tool CREAZIONE SQUADRE e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento CREAZIONE SQUADRE).

----
> #### **Titolo:**
>> Visualizzare lista utenti
> #### **Riassunto:**
>> Questo use case descrive come l’amministratore può consultare la lista degli utenti che hanno effettuato l’accesso all’applicazione a partire dal menù.
> #### **Descrizione:**
>> 1. L'utente clicca sul pulsante "Utenti" e viene reindirizzato alla schermata con la lista degli utenti dell'applicazione.
>> 2. Il sistema chiede a MongoDB la lista degli utenti con i relativi dati. [[exception 1](#exceptions-4)]
>> 3. Il sistema fornisce la lista degli utenti con foto profilo dell’account Google, id personale, email e ruolo.
> #### **Exceptions:**
>> - [exception 1] Lista mostra utenti non più esistenti, MongoDB non aggiornato.
> #### **Extension points:**
>> --

----
> #### **Titolo:**
>> Modificare ruolo utenti
> #### **Riassunto:**
>> Questo use case descrive come l’amministratore può modificare il ruolo degli utentipresenti su MongoDB a partire dalla schermata di visualizzazione lista utenti.
> #### **Descrizione:**
>> 1. L’utente amministratore modifica il ruolo di ciascun utente nella lista selezionando il ruolo desiderato dal menù a tendina presente vicino al nome dell’utente scelto. [[exception 1](#exceptions-5)] [[exception 2](#exceptions-5)] [[exception 3](#exceptions-5)]
>> 2. Il sistema aggiorna i dati dell’utente su MongoDB.
> #### **Exceptions:**
>> - [exception 1] Un amministratore può essere declassato a utente comune unicamente dall’amministratore che lo ha promosso.
>> - [exception 2] L’utente che si sta cercando di cui si vuole cambiare il ruolo non è presente nel sistema, MongoDB non aggiornato.
>> - [exception 3] In assenza di connessione internet, viene inviato un messaggio di errore.
> #### **Extension points:**
>> --

----
> #### **Titolo:**
>> Modificare attività
> #### **Riassunto:**
>> Questo use case descrive come l’amministratore può modificare un’attività presente nel catalogo a partire dalla schermata catalogo.
> #### **Descrizione:**
>> 1. L’utente amministratore clicca sull’attività scelta.
>> 2. L’utente amministratore clicca sull’icona della matita. [[exception 1](#exceptions-6)] [[exception 2](#exceptions-6)]
>> 3. Il sistema permette all’utente di modificare tutto ciò riguardante l’attività.
>> 4. L’utente clicca sul pulsante di conferma per terminare la modifica.
>> 5. Il sistema invia a MongoDB l’attività aggiornata.
> #### **Exceptions:**
>> - [exception 1] L’attività sulla quale si clicca non è aggiornata e una modifica causerebbe delle collisioni, MongoDB non aggiornato.
>> - [exception 2] In assenza di connessione internet, viene inviato un messaggio di errore.
> #### **Extension points:**
>> --

----
> #### **Titolo:**
>> Aggiungere una nuova attività
> #### **Riassunto:**
>> Questo use case descrive come un utente amministratore può aggiungere una nuova attività	al catalogo di attività a partire dal menù.
> #### **Descrizione:**
>> 1. L’utente clicca sul bottone “Aggiungi attività” e viene reindirizzato alla schermata di creazione di un’attività. [[exception 1](#exceptions-7)]
>> 2. L’utente inserisce il titolo dell’attività. [[exception 6](#exceptions-7)]
>> 3. L’utente inserisce la descrizione dell’attività. [[exception 2](#exceptions-7)]
>> 4. L’utente inserisce il range di età per cui l’attività è adeguata o raccomandata, fornendo un valore intero non negativo iniziale e un valore intero non negativo finale. [[exception 3](#exceptions-7)]
>> 5. L’utente sceglie un’unità di misura per la durata media dell’attività da un menù a tendina.
>> 6. L’utente inserisce la durata media dell’attività nell’unità di misura scelta. [[exception 4](#exceptions-7)]
>> 7. L’utente inserisce il range del numero di giocatori per cui l’attività è adeguata o raccomandata, fornendo un valore intero non negativo iniziale e un valore intero non negativo finale. [[exception 3](#exceptions-7)]
>> 8. [[extension 1](#exceptions-7)]
>> 9. L’utente clicca sul pulsante per confermare [[extension 2](#extension-points-7)] [[exception 5](#exceptions-7)] [[exception 1](#descrizione-7)]
>> 10. Il sistema invia la proposta di attività a MongoDB [[extension 2](#exceptions-7)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione
>> - [exception 2] Dopo aver inserito 2000 caratteri nel campo relativo alla descrizione, se l’utente proverà ad inserire altri caratteri questi non verranno inseriti, il campo di inserimento sarà evidenziato di rosso e riporterà una scritta che informa l’utente che il limite massimo di caratteri è stato raggiunto
>> - [exception 3] Se il valore finale è strettamente minore del valore iniziale o se uno dei due valori non è intero o se uno dei due valori è negativo o se uno dei due valori è maggiore di 99, il campo di inserimento del range sarà evidenziato in rosso e riporterà una scritta che informa l’utente dei vincoli non rispettati
>> - [exception 4] Se l’utente ha inserito un valore non intero o negativo o maggiore di 999, il campo di inserimento della durata sarà evidenziato in rosso e riporterà una scritta che informa l’utente dei vincoli non rispettati
>> - [exception 5] Se l’utente ha inserito un titolo corrispondente a quello di un’attività già presente nel catalogo o proposta da un’altro utente, il sistema mostrerà un messaggio di errore ed evidenzierà in rosso il campo di inserimento del titolo
>> - [exception 6] Dopo aver inserito 20 caratteri nel campo relativo al titolo, se l’utente proverà ad inserire altri caratteri questi non verranno inseriti, il campo di inserimento sarà evidenziato di rosso e riporterà una scritta che informa l’utente che il limite massimo di caratteri è stato raggiunto
> #### **Extension points:**
>> - [extension 1] Allo step [8](#descrizione-7), l’utente può scegliere una o più etichette con cui contrassegnare l’attività da un menù a tendina.
>> - [extension 2] Allo step [9](#descrizione-7), se il browser dell’utente è compatibile con service workers, un id corrispondente alla proposta di attività verrà memorizzato anche sul dispositivo dell’utente.

----
> #### **Titolo:**
>> Visualizzare elenco segnalazioni
> #### **Riassunto:**
>> Questo use case descrive come l’amministratore può consultare l’elenco delle	segnalazioni fatte dagli utenti sulle attività a partire dal menù.
> #### **Descrizione:**
>> 1. L’utente clicca sul pulsante “Elenco segnalazioni” e viene reindirizzato alla schermata di elenco segnalazioni. [[exception 2](#exceptions-8)]
>> 2. Il sistema chiede a MongoDB la lista di segnalazioni fatte dagli utenti autenticati.
>> 3. Il sistema fornisce la lista di attività con un numero di segnalazioni maggiore di 0, con il nome dell’attività e il rispettivo numero di segnalazioni. [[exception 1](#exceptions-8)]
>> 4. L’utente clicca sull’attività scelta e viene reindirizzato alla schermata di segnalazioni specifiche dell’attività scelta.
>> 5. Il sistema fornisce la lista di segnalazioni della singola attività, con titolo e breve descrizione.
> #### **Exceptions:**
>> - [exception 1] L'attività non esiste più, MongoDB non aggiornato.
>> - [exception 2] In assenza di connessione internet viene inviato un messaggio di errore.
> #### **Extension points:**
>> --

----
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
> #### **Titolo:**
>> Segnalare un'attività
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato può segnalare un’attività a partire dalla pagina di visualizzazione delle informazioni dell’attività.
> #### **Descrizione:**
>> 1. L’utente clicca sul pulsante segnala.
>> 2. Il sistema fornisce all’utente una casella di testo e un pulsante di invio.
>> 3. L’utente inserisce un breve messaggio di motivazione della segnalazione nella casella di testo.
>> 4. L’utente clicca sul pulsante d’invio. [[exception 1](#exceptions-10)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
> #### **Extension points:**
>> --

----
> #### **Titolo:**
>> Valutare un'attività
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato può valutare un’attività con un punteggio numerico a partire dalla pagina di visualizzazione delle informazioni dell’attività.
> #### **Descrizione:**
>> 1. L’utente clicca su una barra con 5 stelline, in corrispondenza della valutazione che intende lasciare: il numero (semintero) di stelline da sinistra al punto selezionato dall’utente indica la valutazione in numeri decimali nel range [0-5] con scarto di 0.5.
>> 2. L’utente clicca sul pulsante per confermare. [[exception 1](#exceptions-11)]
>> 3. Il sistema invia il dato numerico a MongoDB. [[extension 1](#extension-points-11)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
> #### **Extension points:**
>> - [extension 1] Allo step [3](#descrizione-11), se il browser dell’utente è compatibile con service workers, il dato numerico verrà memorizzato anche sul dispositivo dell’utente.

----
> #### **Titolo:**
>> Proporre un'attività
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato online può proporre una nuova attività per il catalogo delle attività a partire dal menù.
> #### **Descrizione:**
>> 1. L’utente clicca sul bottone “Aggiungi attività” e viene reindirizzato alla schermata di creazione di un’attività. [[exception 1](#exceptions-12)]
>> 2. L’utente inserisce il titolo dell’attività. [[exception 6](#exceptions-12)]
>> 3. L’utente inserisce la descrizione dell’attività. [[exception 2](#exceptions-12)]
>> 4. L’utente inserisce il range di età per cui l’attività è adeguata o raccomandata, fornendo un valore intero non negativo iniziale e un valore intero non negativo finale. [[exception 3](#exceptions-12)]
>> 5. L’utente sceglie un’unità di misura per la durata media dell’attività da un menù a tendina.
>> 6. L’utente inserisce la durata media dell’attività nell’unità di misura scelta. [[exception 4](#exceptions-12)]
>> 7. L’utente inserisce il range del numero di giocatori per cui l’attività è adeguata o raccomandata, fornendo un valore intero non negativo iniziale e un valore intero non negativo finale. [[exception 3](#exceptions-12)] 
>> 8. [[extension 1](#extension-points-12)]
>> 9. L’utente clicca sul pulsante per confermare [[extension 2](#extension-points-12)] [[exception 5](#exceptions-12)] [[exception 1](#descrizione-12)]
>> 10. Il sistema invia la proposta di attività a MongoDB [[extension 2](#exceptions-12)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione
>> - [exception 2] Dopo aver inserito 2000 caratteri nel campo relativo alla descrizione, se l’utente proverà ad inserire altri caratteri questi non verranno inseriti, il campo di inserimento sarà evidenziato di rosso e riporterà una scritta che informa l’utente che il limite massimo di caratteri è stato raggiunto
>> - [exception 3] Se il valore finale è strettamente minore del valore iniziale o se uno dei due valori non è intero o se uno dei due valori è negativo o se uno dei due valori è maggiore di 99, il campo di inserimento del range sarà evidenziato in rosso e riporterà una scritta che informa l’utente dei vincoli non rispettati
>> - [exception 4] Se l’utente ha inserito un valore non intero o negativo o maggiore di 999, il campo di inserimento della durata sarà evidenziato in rosso e riporterà una scritta che informa l’utente dei vincoli non rispettati
>> - [exception 5] Se l’utente ha inserito un titolo corrispondente a quello di un’attività già presente nel catalogo o proposta da un’altro utente, il sistema mostrerà un messaggio di errore ed evidenzierà in rosso il campo di inserimento del titolo
>> - [exception 6] Dopo aver inserito 20 caratteri nel campo relativo al titolo, se l’utente proverà ad inserire altri caratteri questi non verranno inseriti, il campo di inserimento sarà evidenziato di rosso e riporterà una scritta che informa l’utente che il limite massimo di caratteri è stato raggiunto
> #### **Extension points:**
>> - [extension 1] Allo step [8](#descrizione-12), l’utente può scegliere una o più etichette con cui contrassegnare l’attività da un menù a tendina.
>> - [extension 2] Allo step [9](#descrizione-12), se il browser dell’utente è compatibile con service workers, un id corrispondente alla proposta di attività verrà memorizzato anche sul dispositivo dell’utente.

----
> #### **Titolo:**
>> Modificare un'attività proposta
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato online può modificare una propria proposta di attività a partire dalla pagina di visualizzazione delle informazioni dell’attività.
> #### **Descrizione:**
>> 1. L’utente clicca sul bottone “Modifica proposta” e viene reindirizzato alla schermata di modifica di una proposta di attività. [extension 1]
>> 2. [[extention 1](#extension-points-13)]
>> 3. L’utente clicca sul pulsante per confermare. [[exception 1](#exceptions-13)] [[exception 2](#exceptions-13)]
>> 4. Il sistema invia i dati modificati a MongoDB.
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
>> - [exception 2] Se l’utente ha inserito un titolo corrispondente a quello di un’attività già presente nel catalogo o proposta da un’altro utente, il sistema mostrerà un messaggio di errore ed evidenzierà in rosso il campo di inserimento del titolo.
> #### **Extension points:**
>> - [extension 1] Allo step ’utente può modificare uno qualsiasi dei campi dell’attività, con modalità, eccezioni ed estensioni descritte negli step 2.-8. dello use case “Proporre un’attività”.

----
> #### **Titolo:**
>> Manipolare liste di attività
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato online può effettuare un’azione di modifica delle sue liste di attività, a partire dal menù dell’applicazione.
> #### **Descrizione:**
>> 1. L’utente clicca sul pulsante “Liste”.
>> 2. [[extension 1](#extension-points-14)] [[extension 2](#extension-points-14)] [[extension 3](#extension-points-14)] [[extension 4](#extension-points-14)]
> #### **Exceptions:**
>> --
> #### **Extension points:**
>> - [extension 1] Allo step [2](#descrizione-14), use case “Creare una lista di attività”.
>> - [extension 2] Allo step [2](#descrizione-14), use case “Rimuovere una lista di attività”.
>> - [extension 3] Allo step [2](#descrizione-14), l’utente clicca una lista di attività, passa alla schermata della lista, use case “Rimuovere un’attività da una lista”.
>> - [extension 4] Allo step [2](#descrizione-14), spostarsi sulla pagina di visualizzazione delle informazioni di un’attività, use case “Aggiungere un’attività ad una lista di attività”.

----
> #### **Titolo:**
>> Creare una lista di attività
> #### **Riassunto:**
>> Questo use case descrive come un utente autenticato online può creare una nuova lista di attività a partire dalla schermata “Liste”.
> #### **Descrizione:**
>> 1. L’utente clicca sul pulsante +. [[exception 1](#exceptions-15)]
>> 2. L’utente inserisce il nome che intende dare alla nuova lista. [[exception 2](#exceptions-15)]
>> 3. L’utente clicca sul pulsante per confermare. [[exception 3](#exceptions-15)] [[exception 1](#exceptions-15)]
>> 4. Il sistema invia la lista di attività a MongoDB. [[extension 1](#extension-points-15)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
>> - [exception 2] Dopo aver inserito 20 caratteri nel campo relativo al nome, se l’utente proverà ad inserire altri caratteri questi non verranno inseriti, il campo di inserimento sarà evidenziato di rosso e riporterà una scritta che informa l’utente che il limite massimo di caratteri è stato raggiunto.
>> - [exception 3] Se l’utente ha inserito un nome corrispondente a quello di una lista di attività presente tra le sue liste personali, il sistema mostrerà un messaggio di errore ed evidenzierà in rosso il campo di inserimento del nome.
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
>> 3. Il sistema invia a MongoDB la richiesta di rimozione della lista. [[extension 1](#extension-points-16)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
>> - [exception 2] Se l’utente proverà a rimuovere la lista dei preferiti il pulsante “Cestino” non comparirà.
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
>> 4. Il sistema invia a MongoDB l’id dell’attività aggiunta. [[extension 2](#extension-points-17)]
> #### **Exceptions:**
>> - [exception 1] In assenza di connessione ad Internet il sistema mostrerà all’utente un messaggio di errore che indicherà l’assenza di connessione.
>> - [exception 2] Se la lista selezionata ha già 9.999 attività, l’attività selezionata non verrà aggiunta e il sistema mostrerà all’utente un messaggio di errore.
> #### **Extension points:**
>> - [extension 1] Allo step [1](#descrizione-17), cliccando sul pulsante stella l’attività verrà aggiunta direttamente alla lista dei preferiti. [[exception 1](#exceptions-17)] [[exception 2](#exceptions-17)]
>> - [extension 2] Allo step [4](#descrizione-17), se il browser dell’utente è compatibile con service workers, l’id dell’attività aggiunta verrà memorizzato anche sul dispositivo dell’utente.

----


<div class="page-break"></div>
