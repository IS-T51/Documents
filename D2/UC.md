
# Use Case
Nel presente capitolo vengono descritti i casi d'uso del sistema.

> **Titolo:**
>> Effettuare l'accesso
> **Riassunto:**
>> Questo use case descrive come l’utente può accedere all’applicazione tramite il suo account Google
> **Descrizione:**
>> 1. L’utente clicca sul pulsante login
>> 2. Il sistema reindirizza l’utente sulla pagina di accesso di Google
>> 3. L’utente inserisce le sue credenziali Google
>> 4. Google Oauth genera un token e reindirizza l’utente sull’applicazione [exception 1]
>> 5. Il sistema verifica il token ricevuto tramite l’api di Google [exception 2]
>> 6. Se è il primo accesso dell’utente, viene creata una nuova entry su MongoDB, con un id personale e la mail
>> 7. Se è già avvenuto almeno un accesso, vengono recuperati i dati dell’utente da MongoDB [extension 1]


<div class="page-break"></div>
