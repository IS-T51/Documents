
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
> L'interfaccia catalogo remoto manda una richiesta a MongoDB con i filtri inseriti dall'utente, e ottiene in risposta l'elenco delle attività che rispettano i filtri.
> #### *Interfaccia richiesta - catalogo locale*
> L'interfaccia catalogo localemanda una richiesta al componente Gestione Dati Offline con i filtri inseriti dall'utente, e ottiene in risposta l'elenco delle attività che rispettano i filtri.

> ### Attività
> #### *Motivazione*
> Dati gli **RF12-15** e **RF18-19**, è stato individuato un componente Attività distinto dal componente Catalogo per gestire le operazioni che riguardano le singole attività, ovvero la loro visualizzazione e la loro modifica.
> #### *Spiegazione*
> Su richiesta di visualizzazione di un'attività da parte del componente Catalogo o del componente Liste, il componente Attività richiede le informazioni dell'attività corrispondente al sistema esterno MongoDB, oppure delega il recupero delle informazioni al componente Gestione Dati Offline. Dopo aver recuperato i dati necessari, mostra i dettagli dell'attività all'utente.
> #### *Interfaccia richiesta - crea nuova attività*
> L'interfaccia crea nuova attività raccoglie il titolo della nuova attività per poi reindirizzare l'utente alla schermata di modifica dell'attività in cui saranno inseriti gli altri campi.
> #### *Interfaccia richiesta - campi attività*
> L'interfaccia campi attività richiede un modulo che l'utente deve riempire con le informazioni riguardanti l'attività da modificare o creare.<br>
> Se l'attività viene creata da zero, tutti i campi saranno inizialmente vuoti, altrimenti conterranno le informazioni precedentemente inserite.<br>
> Se l'attività è proposta sarà presente un tag non rimuovibile "proposta", mentre se l'attività viene creata dall'amministratore non ci sarà.

> ### Liste
> #### *Motivazione*
> Dati gli **RF8-11**, è stato individuato un componente Liste per gestire l'elenco, la visualizzazione, l'esportazione, la creazione e la manipolazione delle liste di attività di un utente.
> #### *Spiegazione*
> Il componente permette all'utente di creare o eliminare delle liste di attività, aggiungere o togliere un'attività da una lista inviando tali modifiche al sistema esterno MongoDB e richiedendo l'aggiornamento dei Dati Offline.<br>
> L'utente può, inoltre, richiedere la visualizzazione di una lista salvata localmente e l'esportazione della stessa in formato PDF o JSON.
> #### *Interfaccia richiesta - nuova lista*
> L'interfaccia nuova lista richiede, da parte dell'utente che vuole creare una nuova lista, di inserire il titolo della stessa rispettando i vincoli descritti dagli use case.

> ### Gestione Dati Offline
> #### *Motivazione*
> Dati gli **RF6** e **RF17**, il componente Gestione Dati Offline, si occupa di tutte le operazioni riguardanti la lettura e memorizzazione di dati offline, come per esempio il catalogo e le liste offline.
> #### *Spiegazione*
> Il componente permette di memorizzare e visualizzare liste, catalogo e attività localmente al dispositivo (se compatibile) dell'utente.
> #### *Interfaccia richiesta - lista modifiche remote*
> L'interfaccia lista modifiche remote, in base a un parametro interno a Gestione Dati Offline che corrisponde al momento in cui è avvenuto l'ultimo aggiornamento dei dati locali, chiede a MongoDB quali sono le attività e (pre un utente autenticato) le liste personali di attività che hanno subito una modifica da quel momento, per poter conseguentemente integrare le modifiche nel database locale.
> #### *Interfaccia fornita - aggiorna dati locali*
> L'interfaccia aggiorna dati locali, quando l'utente compie un'azione di modifica sulle liste, sulle sue proposte di attività o attività i generale nel caso di un amministratore, il componente che ha permesso tale operazione di modifica richiede al gestore dati offline di eseguire un aggiornamento dei dati locali.

> ### Autenticazione
> #### *Motivazione*
> Dato il **RF5**, al fine di permettere l'autenticazione di un utente nel sistema è stato identificato un componente Autenticazione, che si interfaccerà al servizio Google OAuth 2.0 per autenticare l'utente tramite le sue credenziali Google, mantenendo poi attiva la sessione utente all’interno dell’applicazione.<br>
> Per soddisfare il **RF16**, il presente gestionale permetterà agli utenti di effettuare il logout dal proprio account.
> #### *Spiegazione*
> Il componente permette all'utente di effettuare l'accesso nell'app, accedendo alle funzioni riservate agli autenticati.<br>
> Su richiesta dell'utente, esso si occupa in primo luogo di inviare una richiesta di autenticazione a Google e ricevere da esso codice autorizzativo. Il componente effettua in seguito dei controlli interni su tale codice, e, qualora questo risulti valido, il componente scambia il codice con Google per ottenere le informazioni desiderate sull'account Google dell'utente. Queste informazioni saranno infine trasmesse al componente Utenti per l'immagazzinamento e la gestione delle stesse.<br>
> Sempre su richiesta dell'utente, il componente permetterà il logout, rimuovendo i file personali salvati localmente se presenti, e disattivare la sessione autenticata per tornare a quella anonima.
> #### *Interfaccia fornita - login*
> Su richiesta dell'utente, l'interfaccia fornisce all'utente uno specifico URL ad un endpoint di Google su cui inserire le proprie credenziali per dare il permesso all'applicazione Animati di accedere ad alcuni dati dell'account Google dell'utente.
> #### *Interfaccia richiesta - codice autorizzativo*
> L'interfaccia attenderà che l'endpoint di Google menzionato in precedenza reindirizzi l'utente sull'applicazione Animati fornendo come parametro una stringa contenente il codice autorizzativo con i permessi concessi all'app dall'utente riguardo al suo account Google.
> #### *Interfaccia richiesta - dettagli account*
> L'interfaccia dettagli account scambia presso google il codice autorizzativo (dopo che questo è stato validato internamente dal componente) con un access token e un id token; in seguito il componente decodificherà l'id token da base 64 per ottenere email e id del account Google, e potrà (in caso l'utente lo desideri) usare invece l'access token per ottenere la foto profilo presso un altro endpoint di Google<br>
> #### *Interfaccia fornita - utente autenticato*
> L'interfaccia trasmette le informazioni sopra menzionate al componente Utenti per indicare l'inizio della sessione autenticata da parte dell'utente che ha effettuato il login e, in caso di primo accesso, registrare i suoi dati nel sistema esterno MongoDB

> ### Utenti
> #### *Motivazione*
> Dati **RF20-21**, è stato identificato un componente Utenti, che si occupa di tutte operazioni riguardanti aggiunta, visualizzazione e modifica del ruolo degli utenti.
> #### *Spiegazione*
> Il componente permette di recuperare la lista di utenti dal sistema esterno MongoDB per poi permettere agli utenti amministratori di visualizzarlo. <br>
> Il componente permette agli utenti amministratori di modificare il ruolo degli altri utenti, aggiornando il sistema esterno MongoDB.<br>
> In concomitanza al primo accesso tramite login di un utente attraverso il componente Autenticazione, il componente Utente aggiorna il sistema esterno MongoDB, registrando il nuovo utente con i rispettivi dati.
> #### *Interfaccia fornita - verifica ruolo*
> L'interfaccia verifica ruolo, permette di controllare il ruolo dell'utente in sessione e determinare a quali funzionalità ha accesso all'interno del componente che richiede la verifica.<br>

> ### Feedback
> #### *Motivazione*
> Dati **RF12-13** e **RF22**, è stato identificato un componente Feedback, che si occupa di tutte le operazioni riguardanti la valutazione e/o segnalazione di un'attività.
> #### *Spiegazione*
> Il componente permette di recuperare le segnalazioni di ogni attività dal sistema esterno MongoDB e di mostrare agli utenti amministratori la lista di attività segnalate e la lista di segnalazioni per ogni attività. <br>
> Il componente permette agli utenti autenticati all'interno della schermata di informazioni di un'attività di visualizzare la valutazione media corrente di quell'attività e di aggiungere o modificare la propria.<br>
> #### *Interfaccia richiesta - segnalazione attività*
> L'interfaccia segnalazione attività richiede all'utente di inserire un titolo e una breve descrizione all'attività che intende segnalare secondo i vincoli imposti negli use case.

> ## Strumenti
> #### *Motivazione*
> Dato il **RF35**, è stato identificato un modulo Strumenti conentente tutti i componenti che si occupano del funzionamento dei tool offerti dal sistema.<br>
> Ogni tool è un sistema autonomo che permette all'utente di accedere a dei servizi a sé stanti, opzionalmente con parametri forniti da un altro componente.
>> ### Dado
>> #### *Motivazione*
>> Per soddisfare **RF23-25**, il sistema prevede la presenza di un componente che si occupi della creazione di un dado personalizzato (un'urna di valori scelti tra immagini, numeri, colori o parole) e dell'estrazione di un valore casuale presente su di esso, con o senza reimmisione.
>> #### *Spiegazione*
>> Il componente Dado si occupa di raccogliere dall'utente gli elementi estraibili dal dado, far indicare all'utente se si vuole consentire la ri-estrazione di valori già estratti o meno, e infine permettere all'utente l'estrazione di uno o più elementi dal dado creato.
>> #### *Interfaccia richiesta - consenti reimmissione*
>> L'interfaccia consenti reimissione, permette di determinare se gli elementi già estratti dal campione possano o meno essere riestratti tramite un attributo booleano. Se tale attributo assume valore True, gli elementi possono essere riestratti, altrimenti no.
>
>> ### Cronometro
>> #### *Motivazione*
>> Per soddisfare **RF27-28**, è stato individuato un componente Cronometro, che si occupa della gestione delle funzionalità dello strumento Cronometro.
>> #### *Spiegazione*
>> Grazie al componente Cronometro, l'utente può avviare, fermare, ripristinare e registrare i tempi parziali di un cronometro, e quindi misurare quanto tempo è passato da un determinato momento, visualizzando sia il tempo totale che i tempi parziali.
>> #### *Interfaccia richiesta - salva tempo parziale*
>> L'interfaccia salva tempo parziale richiede all'utente di cliccare sul pulsante parziale ogni qualvolta lo stesso voglia salvare un tempo senza fermare il cronometro. Questi tempi verranno salvati in una lista.
>
>> ### Gestore Suoni
>> #### *Motivazione*
>> Per soddisfare **RF29** e **RF31**, è stato individuato un componente Gestore Suoni, che si occupa della gestione delle funzionalità di riproduzione e selezione di suoni per i componenti Timer e Fischietto.
>> #### *Spiegazione*
>> Il componente Gestore Suoni permette di selezionare, visualizzare e riprodurre un file audio, o anche di aggiungerne uno dal dispositivo utilizzato.
> #### *Interfaccia richiesta - mostra suono*
> L'interfaccia mostra suono, dato il menù a tendina chiuso, mostra all'utente il suonfile audio selezionato in quel momento nel rettangolo che serve per aprire il menù.
>
>> ### Fischietto
>> #### *Motivazione*
>> Per soddisfare **RF29-31**, è stato individuato un componente Fischietto, che si occupa dell'emulazione di un fischietto.
>> #### *Spiegazione*
>> Grazie al componente Fischietto, l'utente può tenere premuto lo schermo per riprodurre un suono la cui gestione è delegata al componente Gestore Suoni.
>
>> ### Timer
>> #### *Motivazione*
>> Dato il **RF26**, è stato individuato un componente Timer, che si occupa della gestione delle funzionalità dello strumento Timer.
>> #### *Spiegazione*
>> Grazie al componente Timer, l'utente può specificare un valore di inizializzazione, può avviare, mettere in pausa, o annullare un conto alla rovescia e in ogni dato momento visualizzare il tempo rimanente allo scadere del timer.<br>
>> Una volta che il conto alla rovescia raggiunge il valore 0, verrà riprodotto un suono dal componente Gestore Suoni
>
>> ### Creazione Squadre
>> #### *Motivazione*
>> Dati **RF34-39**, è stato individuato un componente Creazione Squadre, che si occupa della suddivisione dei partecipanti alle attività in squadre distinte, secondo dei parametri di divisione decisi dall'utente.
>> #### *Spiegazione*
>> Grazie al componente Creazione Squadre, l'utente può scegliere il numero di squadre, persone per squadra e partecipanti totali, oltre che i nomi delle squadre e il metodo di divisione.<br>
>> Una volta definiti tutti i parametri si procede alla divisione in squadre.
>> #### *Interfaccia fornita - estrae squadra*
>> Ogni volta che lo schermo viene premuto, appare il nome della squadra a cui appartiene l'utente che ha interagito. Questo appare seguendo la metodologia di divisione scelta.
>> #### *Interfaccia richiesta - metodologia divisione*
>> L'interfaccia metodologia divisione si occupa di chiedere all'utente con che metodo voglia estrarre le squadre, scegliendo tra: random, round robin, fill first, e balanced.
>
>> ### Segna-Punti
>> #### *Motivazione*
>> Dati **RF32-33**, è stato individuato un componente Segna-Punti, che si occupa di tenere conto, per ogni squadra inserita, dei punti fatti per la durata dell'attività.
>> #### *Spiegazione*
>> Grazie al componente Segna-Punti, l'utente può scegliere il numero di squadre, nonché il nome per ogni squadra, e incrementare o decrementare il punteggio di ciascuna squadra.

## 4.2 Diagramma dei componenti
<center><img alt="Diagramma dei Componenti" src="D2/img/CPD/component-diagram_v4.png" width="100%"/></center>
La figura mostra i componenti di sistema e la loro interconnessione. A seguire una descrizione delle interfacce presenti nel diagramma.



<div class="page-break"></div>
