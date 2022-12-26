
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
> #### *Interfaccia richiesta - catalogo remoto*
> L'interfaccia catalogo remoto manda una richiesta a MongoDB e ottiene in ritorno il catalogo locale.
> #### *Interfaccia fornita - catalogo locale*
> L'interfaccia catalogo locale, dopo aver ricevuto una richiesta da MongoDB, fornisce in ritorno il catalogo stesso.

> ### Attività
> #### *Motivazione*
> Dati gli **RF12-15** e **RF18-19**, è stato individuato un componente Attività distinto dal componente Catalogo per gestire le operazioni che riguardano le singole attività, ovvero la loro visualizzazione e la loro modifica.
> #### *Spiegazione*
> Su richiesta di visualizzazione di un'attività da parte del componente Catalogo o del componente Liste, il componente Attività richiede le informazioni dell'attività corrispondente al sistema esterno MongoDB, oppure delega il recupero delle informazioni al componente Gestione Dati Offline. Dopo aver recuperato i dati necessari, mostra i dettagli dell'attività all'utente.
> #### *Interfaccia richiesta - crea nuova attività*
> L'interfaccia crea nuova attività raccoglie il titolo della nuova attività per poi reindirizzare l'utente al modulo di modifica attività.
> #### *Interfaccia richiesta - campi attività*
> L'interfaccia campi attività richiede un modulo che l'utente deve riempire con le informazioni riguardanti l'attività.<br>
> Se l'attività viene creata da zero, tutti i campi saranno inizialmente vuoti, altrimenti conterranno le informazioni precedentemente inserite.<br>
> Se l'attività è proposta sarà presente un tag non rimuovibile "proposta", mentre se l'attività viene creata dall'amministratore non ci sarà.

> ### Liste
> #### *Motivazione*
> Dati gli **RF8-11**, è stato individuato un componente Liste per gestire l'elenco, la visualizzazione, l'esportazione, la creazione e il manipolamento delle liste di attività.
> #### *Spiegazione*
> Il componente permette all'utente di creare o eliminare delle liste di attività, aggiungere o togliere un'attività da una lista inviando tali modifiche al sistema esterno MongoDB e richiedendo l'aggiornamento dei Dati Offline.<br>
> L'utente può, inoltre, richiedere la visualizzazione di una lista salvata localmente e l'esportazione della stessa in formato PDF.
> #### *Interfaccia richiesta - nuova lista*
> L'interfaccia nuova lista richiede da parte dell'utente di cliccare sul pulsante + e di inserire il titolo rispettando i vincoli descritti dagli use case.

> ### Gestione Dati Offline
> #### *Motivazione*
> Dato il **RF6** e **RF17**, il componente Gestione Dati Offline, si occupa di tutte le operazioni riguardanti la lettura e memorizzazione di dati offline, come per esempio il catalogo e le liste offline. 
> #### *Spiegazione*
> Il componente permette di visualizzare liste, catalogo e attività locali.
> #### *Interfaccia richiesta - lista modifiche remote*
> L'interfaccia lista modifiche remote, in base a un parametro interno a Gestione Dati Offline, che corrisponde al momento in cui è avvenuto l'ultimo aggiornamento del catalogo locale, chiede a MongoDB quali sono le attività che hanno subito una modifica e date quelle attività integra le modifiche nel database locale.
> #### *Interfaccia fornita - aggiorna dati locali*
> L'interfaccia aggiorna dati locali, quando l'utente compie un'azione di modifica sulle liste o sulle sue proposte di attività, la relativa classe comunica al gestore dati offline che bisogna effettuare un aggiornamento dei dati locali.

> ### Autenticazione
> #### *Motivazione*
> Dato il **RF5**, al fine di permettere l'autenticazione di un utente nel sistema è stato identificato un componente Autenticazione, che si interfaccerà al servizio Google OAuth 2.0 per autenticare l'utente tramite le sue credenziali Google, mantenendo poi attiva la sessione utente all’interno dell’applicazione.<br>
> Per soddisfare il **RF16**, il presente gestionale permetterà agli utenti di effettuare il logout dal proprio account.
> #### *Spiegazione*
> Il componente permette all'utente di effettuare l'accesso nell'app, accedendo alle funzioni riservate agli autenticati.<br>
> Su richiesta dell'utente, esso si occupa in primo luogo di inviare una richiesta di autenticazione a Google e riceve da esso codice autorizzativo. Il componente effettua in seguito dei controlli interni su tale codice, e, qualora questo risulti valido, il componente scambia il codice con Google per ottenere le informazioni desiderate sull'account Google dell'utente.<br>
> Sempre su richiesta dell'utente, il componente permetterà il logout, rimuovendo i file personali salvati localmente se presenti.
> #### *Interfaccia richiesta - dettagli account*
> L'interfaccia dettagli account richiede la mail dell'account google dell'utente, l'id del profilo e il collegamento all'immagine di profilo<br/>
> #### *Interfaccia richiesta - codice autorizzativo*
> L'interfaccia chiederà una stringa contenente il codice autorizzativo necessario ad ottenere un token associato all'account Google.

> ### Utenti
> #### *Motivazione*
> Dato il **RF20-21**, è stato identificato un componente Utenti, che si occupa di tutte operazioni riguardanti la aggiunta, visualizzazione e modifica del ruolo degli utenti.
> #### *Spiegazione*
> Il componente permette di recuperare la lista di utenti dal sistema esterno MongoDB per poi permettere agli utenti amministratori di visualizzarlo. <br>
> Il componente permette agli utenti amministratori di modificare il ruolo degli altri utenti, aggiornando il sistema esterno MongoDB.<br>
> Una volta fatta per la prima volta da parte di un utente l'operazione di login, tramite il componente Autenticazione, il componente Utente aggiorna il sistema esterno MongoDB, aggiungendo il nuovo utente con i rispettivi dati.
> #### *Interfaccia fornita - verifica ruolo*
> L'interfaccia verifica ruolo, permette di controllare il ruolo dell'utente e determinare a quali funzionalità ha accesso.<br>
> Nel caso del Catalogo, può variare tra non autenticato, autenticato e amministratore, il che filtra il catalogo escludendo o meno alcune attività.<br>
> Nel caso di Feedback, esso è permesso se il ruolo dell'utente è autenticato o amministratore. <br>
> Nel caso di Liste, al componente vi si può accedere solo se il ruolo è autenticato o amministratore. <br>
> Nel caso di Attività, le attività che è possibile consultare variano se si è autenticati o meno, come anche la capacità di modificarle.

> ### Feedback
> #### *Motivazione*
> Dato il **RF12-13** e **RF22**, è stato identificato un componente Feedback, che si occupa di tutte le operazioni riguardanti la valutazione e/o segnalazione di un'attività.
> #### *Spiegazione*
> Il componente permette di recuperare le segnalazioni di ogni attività dal sistema esterno MongoDB e di mostrare agli utenti amministratori la lista di attività segnalate e la lista di segnalazioni per ogni attività. <br>
> Il componente permette agli utenti autenticati per ogni attività, di visualizzare la valutazione corrente e di modificare/dare la propria, all'interno della schermata di informazioni dell'attività.<br>
> #### *Interfaccia richiesta - segnalazione attività*
> L'interfaccia segnalazione attività richiede un titolo e una breve descrizione secondo i vincoli imposti negli use case.

> ## Strumenti
> #### *Motivazione*
> Dato il **RF35**, è stato identificato un modulo Strumenti conentente tutti i componenti che si occupano del funzionamento dei tool offerti dal sistema.<br>
> Ogni tool è un sistema autonomo che permette all'utente di accedere a dei singoli servizi.
>> ### Dado
>> #### *Motivazione*
>> Per soddisfare il **RF23-25**, il sistema deve prevedere un componente che si occupi della creazione di un dado personalizzato (un'urna di valori composti da immagini, numeri, colori o parole) e dell'estrazione di un valore casuale presente su di esso con o senza re-immisione.
>> #### *Spiegazione*
>> Il componente Dado si occupa di raccogliere dall'utente gli elementi estraibili dal dado, di esprimere la volontà o meno di avere un ripescaggio e di permettere l'estrazione di uno o più elementi.
>> #### *Interfaccia richiesta - consenti reimmissione*
>> L'interfaccia consenti reimissione, permette di determinare se gli elementi già estratti dal campione possano o meno essere riestratti tramite un attributo booleano. Se tale attributo assume valore True, gli elementi possono essere riestratti, altrimenti no.
>
>> ### Cronometro
>> #### *Motivazione*
>> Per soddisfare il **RF27-28**, è stato individuato un componenete Cronometro, che si occupa della gestione delle funzionalità dello strumento Timer.
>> #### *Spiegazione*
>> Grazie al componenete Cronometro, l'utente può avviare, fermare, ripristinare e registrare i tempi parziali di un cronometro, e quindi sapere quanto tempo è passato da un determinato momento, visualizzando sia il tempo totale che i tempi parziali.
>> #### *Interfaccia richiesta - salva tempo parziale*
>> L'interfaccia salva tempo parziale richiede all'utente di cliccare sul pulsante parziale ogniqualvolta lo stesso vuole salvare un tempo senza fermare il cronometro. Questi tempi verranno salvati in una lista.
>
>> ### Gestore Suoni
>> #### *Motivazione*
>> Per soddisfare il **RF29** e **RF31**, è stato individuato un componente Gestore Suoni, che si occupa della gestione delle funzionalità di riproduzione e selezione di suoni per le componenti Timer e Fischietto.
>> #### *Spiegazione*
>> Il componente Gestore Suoni permette di selezionare, visualizzare e riprodurre un suono, o anche di aggiungerne uno dal dispositivo utilizzato.
> #### *Interfaccia richiesta - mostra suono*
> L'interfaccia mostra suono, dato il menù a tendina chiuso, mostra all'utente il suono selezionato in quel momento nel rettangolino che serve per aprire il menù.
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
>> Una volta definiti tutti i parametri si procede alla divisione in squadre.
>> #### *Interfaccia fornita - estrae squadra*
>> Ogni volta che lo schermo viene premuto, appare il nome della squadra a cui appartiene l'utente che ha interagito. Questo appare seguendo la metodologia di divisione scelta. Ogni squadra ha un contatore rappresentante il totale di posti rimasti. Ogniqualvolta un utente viene assegnato ad una squadra, il contatore della stessa viene decrementato di uno.
>> #### *Interfaccia richiesta - metodologia divisione*
>> L'interfaccia metodologia divisione si occupa di chiedere all'utente come voglia estrarre le squadre, ritornando un valore enumerativo
>
>> ### Segna-Punti
>> #### *Motivazione*
>> Dato il **RF32-33**, è stato individuato un componente Segna-Puni, che si occupa di tenere conto, per ogni squadra inserita, dei punti fatti per la durata dell'attività.
>> #### *Spiegazione*
>> Grazie al componente Segna-Punti, l'utente può scegliere il numero di squadre, nonché il nome per ogni squadra, e incrementare e decrementare il punteggio di ogni squadre.

## 4.2 Diagramma dei componenti
<center><img alt="Diagramma dei Componenti" src="D2/img/CPD/component-diagram_v4.png" width="100%"/></center>
La figura mostra i componenti di sistema e la loro interconnessione. A seguire una descrizione delle interfacce presenti nel diagramma.



<div class="page-break"></div>
