
# 4. Analisi dei Componenti
Nel presente capitolo viene presentata l’architettura in termini di componenti interni al sistema.
Essi verranno definiti sulla base dei requisiti analizzati nei precedenti documenti.<br>Viene poi adottato l’uso di Component Diagram per rappresentare l’interconnessione tra i vari componenti, identificando quindi le interfacce tra questi e verso sistemi esterni.

## 4.1 Definizione dei componenti
In questa sezione vengono definiti i componenti.

> ### Catalogo
> #### *Motivazione*
> Dati gli **RF2**, **3**, **6**, al fine di permettere la consultazione e il filtraggio del catalogo di attività, è stato identificato un componente Catalogo, che si occuperà di gestire le operazioni riguardanti le attività del catalogo in blocco.
> #### *Spiegazione*
> Il componente permette all'utente di selezionare i filtri desiderati sulle attività da visualizzare (eventualmente nessuno), e richiede l'elenco di attività corrispondenti al sistema esterno MongoDB, oppure delega il recupero delle informazioni al componente Gestione Dati Offline. Dopo aver recuperato i dati necessari, mostra il catalogo filtrato all'utente.<br>
> Qualora l'utente selezioni un'attività da visualizzare, il componente passa l'informazione al componente Attività.<br>
> Qualora l'utente decida di creare una nuova attività o proposta di attività, il catalogo richiede al componente Gestione Utenti di verificare che l'utente attualmente in sessione abbia i permessi necessari a svolgere l'operazione di creazione attività, e in caso affermativo delega il compito di creazione attività al componente Gestione Attività.

> ### Attività
> #### *Motivazione*
> Dati gli **RF12-15** e **RF18-19**, è stato individuato un componente Attività distinto dal componente Catalogo per gestire le operazioni che riguardano le singole attività, ovvero la loro visualizzazione e la loro modifica.
> #### *Spiegazione*
> Su richiesta di visualizzazione di un'attività da parte del componente Catalogo o del componente Liste, il componente Attività richiede le informazioni dell'attività corrispondente al sistema esterno MongoDB, oppure delega il recupero delle informazioni al componente Gestione Dati Offline. Dopo aver recuperato i dati necessari, mostra i dettagli dell'attività all'utente.


> ### Liste
> #### *Motivazione*
> Dati gli **RF8-11**, è stato indiividuato un componente Liste per gestire l'elenco, la visualizzazione, l'esportazione, lacreazione e il manipolamento delle liste di attività.
> #### *Spiegazione*
> Il componente permette all'utente di creare o eliminare delle liste di attività, aggiungere o togliere un'attività da una lista inviando tali modifiche al sistema esterno MongoDB e richiedendo l'aggiornamento dei Dati Offline.<br>
> L'utente può, inoltre, richiedere la visualizzazione di una lista salvata localmente e l'esportazione della stessa in formato PDF.

> ### Gestione Dati Offline
> #### *Motivazione*
> [...]
> #### *Spiegazione*
> [...]

> ### Autenticazione
> #### *Motivazione*
> Dato il **RF5**, al fine di permettere l'autenticazione di un utente nel sistema è stato identificato un componente Autenticazione, che si interfaccerà al servizio Google OAuth 2.0 per autenticare l'utente tramite le sue credenziali Google, mantenendo poi attiva la sessione utente all’interno dell’applicazione.<br>
> Per soddisfare il **RF16**, il presente gestionale permetterà agli utenti di effettuare il logout dal proprio account.
> #### *Spiegazione*
> Il componente permette all'utente di effettuare l'accesso nell'app, accedendo alle funzioni riservate agli autenticati.<br>
> Su richiesta dell'utente, esso si occupa in primo luogo di inviare una richiesta di autenticazione a Google e riceve da esso codice autorizzativo. Il componente effettua in seguito dei controlli interni su tale codice, e, qualora questo risulti valido, il componente scambia il codice con Google per ottenere le informazioni desiderate sull'account Google dell'utente.<br>
> Sempre su richiesta dell'utente, il componente permetterà il logout, rimuovendo i file personali salvati localmente se presenti.

> ### Utenti
> #### *Motivazione*
> [...]
> #### *Spiegazione*
> [...]

> ### Feedback
> #### *Motivazione*
> [...]
> #### *Spiegazione*
> [...]

> ## Strumenti
> #### *Motivazione*
> Dato il **RF35**, è stato identificato un modulo Strumenti conentente tutti i componenti che si occupano del funzionamento dei tool offerti dal sistema.<br>
> Ogni tool è un sistema autonomo che permette all'utente di accedere a dei singoli servizi.
>> ### Dado
>> #### *Motivazione*
>> Per soddisfare il **RF23-25**, il sistema deve prevedere un componente che si occupi della creazione di un dado personalizzato (un'urna di valori composti da immagini, numeri, colori o parole) e dell'estrazione di un valore casuale presente su di esso con o senza re-immisione.
>> #### *Spiegazione*
>> Il componente Dado si occupa di raccogliere dall'utente gli elementi estraibili dal dado, di esprimere la volontà o meno di avere un ripescaggio e di permettere l'estrazione di un elemento.
>
>> ### Cronometro
>> #### *Motivazione*
>> Per soddisfare il **RF27-28**, è stato individuato un componenete Cronometro, che si occupa della gestione delle funzionalità dello strumento Timer.
>> #### *Spiegazione*
>> Grazie al componenete Cronometro, l'utente può avviare, fermare, ripristinare e registrare i tempi parziali di un cronometro, e quindi sapere quanto tempo è passato da un determinato momento, visualizzando sia il tempo totale che i tempi parziali.
>
>> ### Gestore Suoni
>> #### *Motivazione*
>> [...]
>> #### *Spiegazione*
>> [...]
>
>> ### Fischietto
>> #### *Motivazione*
>> Per soddisfare il **RF29-31**, è stato individuato un componente Fischietto, che si occupa della riproduzione di suoni.
>> #### *Spiegazione*
>> Grazie al componente cronometro, l'utente può riprodurre un suono grazie al componente Gestore Suoni.
>
>> ### Timer
>> #### *Motivazione*
>> Dato il **RF26**, è stato individuato un componente Timer, che si occupa della gestione delle funzionalità dello strumento Timer.
>> #### *Spiegazione*
>> Grazie al componente Timer, l'utente può comunicare un valore di inizializzazione, può iniziare, mettere in pausa, fermare un conto alla rovescia e visualizzare il tempo rimanente.<br>
>> Una volta che il conto alla rovescia raggiunge il valore 0, verrà riprodotto un suono dal componente Gestore Suoni
>
>> ### Creazione Squadre
>> #### *Motivazione*
>> Dato il **RF34-39**, è stato individuato un componente Creazione Squadre, che si occupa della suddivisione dei partecipanti alle attività in squadre distinte, secondo dei parametri di divisione decisi dall'utente.
>> #### *Spiegazione*
>> Grazie al componente Creazione Squadre, l'utente può scegliere il numero di squadre, persone per squadra e partecipanti totali, oltre che i nomi delle squadre e il metodo di divisione.<br>
>> Una volta definiti tutti i parametri lo schermo mostrerà ad ogni tocco a quale squadra appartiene l'utente che ha interagito, fino all'esaurimento dei posti.
>
>> ### Segna-Punti
>> #### *Motivazione*
>> Dato il **RF32-33**, è stato individuato un componente Segna-Puni, che si occupa di tenere conto, per ogni squadra inserita, dei punti fatti per la durata dell'attività.
>> #### *Spiegazione*
>> Grazie al componente Segna-Punti, l'utente può scegliere il numero di squadre, nonché il nome per ogni squadra, e incrementare e decrementare il punteggio di ogni squadre.

## 4.2 Diagramma dei componenti
<center><img alt="Diagramma dei Componenti" src="D2/img/CPD/component-diagram_v2.png" width="100%"/></center>
La figura mostra i componenti di sistema e la loro interconnessione. A seguire una descrizione delle interfacce presenti nel diagramma.



<div class="page-break"></div>
