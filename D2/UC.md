
# Use Case
Nel presente capitolo vengono descritti i casi d'uso del sistema.

> #### **Titolo:**
>> Effettuare l'accesso

> #### **Riassunto:**
>> Questo use case descrive come l’utente può accedere all’applicazione tramite il suo account Google

> #### **Descrizione:**
>> 1. L’utente clicca sul pulsante login
>> 2. Il sistema reindirizza l’utente sulla pagina di accesso di Google
>> 3. L’utente inserisce le sue credenziali Google
>> 4. Google Oauth genera un token e reindirizza l’utente sull’applicazione [[exception 1](#exceptions)]
>> 5. Il sistema verifica il token ricevuto tramite l’api di Google [[exception 2](#exceptions)]
>> 6. Se è il primo accesso dell’utente, viene creata una nuova entry su MongoDB, con un id personale e la mail
>> 7. Se è già avvenuto almeno un accesso, vengono recuperati i dati dell’utente da MongoDB [[extension 1](#extension-points)]

> #### **Exceptions:**
>> - [exception 1] Le credenziali non sono corrette, e non viene generato nessun token
>> - [exception 2] Errore nella verifica del token, token non valido

> #### **Extension points:**
>> - [extension 1] Nello step [7](#descrizione), se il browser dell’utente lo permette, i dati individuali dell’utente verranno memorizzati sul dispositivo dell’utente

----
> #### **Titolo:**
>> Consultare catalogo

> #### **Riassunto:**
>> Questo use case descrive come l'utente può consultare il catalogo di attività dell’applicazione e interagire con le singole attività presenti nell’elenco

> #### **Descrizione:**
>> 1. Il sistema chiede la lista di attività a un database [[extension 1](#extension-points-1)] [[extension 2](#extension-points-1)] [[exception 2](#exceptions-1)]
>> 2. Il sistema fornisce la lista di attività con titolo e immagine delle stesse, sulle quali è possibile cliccare
>> 3. Cliccando su un’attività, l’utente viene reindirizzato alla schermata con le informazioni sull’attività stessa [[exception 1](#exceptions-1)]

> #### **Exceptions:**
>> - [exception 1] Utente viene reindirizzato ad attività eliminata, catalogo non aggiornato
>> - [exception 2] Non c’è connessione ad internet e non c’è una copia locale del catalogo, quindi non viene mostrato nessun catalogo e compare un messaggio di errore

> #### **Extension points:**
>> - [extension 1] Nello step [1](#descrizione-1), qualora sia stata salvata una copia del catalogo delle attività sul dispositivo dell’utente, il sistema può consultare quei dati senza interagire con sistemi esterni (“Consultare catalogo locale”)
>> - [extension 2] Nello step [1](#descrizione-1), qualora ci sia connessione ad internet il server può chiedere la lista a MongoDB (“Consultare catalogo remoto”)

----
> #### **Titolo:**
>> Visualizzare attività

> #### **Riassunto:**
>> Questo use case descrive come l’utente può visualizzare i dettagli specifici di ogni attività a partire dalla schermata del catalogo o di una lista, unicamente nel caso dell’utente autenticato

> #### **Descrizione:**
>> 1. L’utente clicca sull’immagine o sul nome dell’attività scelta
>> 2. Il sistema reindirizza l’utente a una schermata con i dettagli dell’attività stessa [[extension 1](#exceptions-2)]

> #### **Exceptions:**
>> - [exception 1] L’attività scelta non è più presente nel catalogo, MongoDB non aggiornato. Viene mostrato un messaggio di errore

> #### **Extension points:**
>> - [extension 1] Nello step [2](#descrizione-2), l’utente può accedere al tool di creazione squadre con i parametri richiesti dalla specifica attività

----
> #### **Titolo:**
>> Utilizzare i tool

> #### **Riassunto:**
>> Questo use case descrive come l’utente può consultare la lista di tool presenti nell’applicazione

> #### **Descrizione:**
>> 1. Il sistema fornisce la lista di tool con titolo degli stessi, sui quali è possibile cliccare
>> 2. Cliccando su un tool, l’utente viene reindirizzato alla schermata di utilizzo del tool stesso [[extension 1](#extension-points-3)] [[extension 2](#extension-points-3)] [[extension 3](#extension-points-3)] [[extension 4](#extension-points-3)] [[extension 5](#extension-points-3)] [[extension 6](#extension-points-3)]

> #### **Exceptions:**
>> - 

> #### **Extension points:**
> - [extension 1] Nello step [2](#descrizione-3), l’utente può cliccare sul tool DADI e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento DADI)
> - [extension 2] Nello step [2](#descrizione-3), l’utente può cliccare sul tool TIMER e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento TIMER)
> - [extension 3] Nello step [2](#descrizione-3), l’utente può cliccare sul tool CRONOMETRO e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento CRONOMETRO)
> - [extension 4] Nello step [2](#descrizione-3), l’utente può cliccare sul tool FISCHIETTO e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento FISCHIETTO)
> - [extension 5] Nello step [2](#descrizione-3), l’utente può cliccare sul tool SEGNA-PUNTI e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento SEGNA-PUNTI)
> - [extension 6] Nello step [2](#descrizione-3), l’utente può cliccare sul tool CREAZIONE SQUADRE e quindi venire reindirizzato alla schermata di questo specifico tool (Utilizzare strumento CREAZIONE SQUADRE)

----
> #### **Titolo:**
>> Visualizzare attività

> #### **Riassunto:**
>> Questo use case descrive come l’utente può visualizzare i dettagli specifici di ogni attività a partire dalla schermata del catalogo o di una lista, unicamente nel caso dell’utente autenticato

> #### **Descrizione:**
>> 1. L'utente clicca sull'immagine o sul nome dell'attività scelta [[exception 1](#exceptions-4)]
>> 2. Il sistema reindirizza l’utente a una schermata con i dettagli dell’attività stessa [[extension 1](#extension-points-4)]

> #### **Exceptions:**
>> - [exception 1] L’attività scelta non è presente nel catalogo, MongoDB non aggiornato. Viene mostrato un messaggio di errore

> #### **Extension points:**
>> - [extension 1] Nello step [2](#descrizione-4), l’utente può accedere al tool di creazione squadre con i parametri richiesti dalla specifica attività

----


<div class="page-break"></div>
