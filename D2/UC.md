
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


<div class="page-break"></div>
