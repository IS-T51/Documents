
# Diagramma delle classi
Nel presente capitolo vengono presentate le classi previste nell'ambito del progetto Animati. Vengono riportate di seguito le classi individuate a partire dai diagrammi di contesto e dei componenti.

## Classi enumerative di supporto
### Unità
> La classe **Unità** è una classe di supporto utilizzata nella classe Info, che sta ad indicare con i suoi attributi la durata di un'attività.
### Ruolo
> La classe **Ruolo** è una classe di supporto utilizzata nella classe Utente, che sta ad indicare con i suoi attributi il ruolo assunto da uno specifico utente.
### Formato
> La classe **Formato** è una classe di supporto utilizzata ogniqualvolta si deve indicare il formato di un file da esportare. In questo caso nella classe ListaAttività, quando viene esportata una lista col metodo esporta(formato : Formato).
### TipoDado
> La classe **TipoDado** è una classe di supporto utilizzata nella classe Dado, che sta ad indicare con i suoi attributi il tipo di faccia utilizzata dallo strumento dado.
### MetodoDivisione
> La classe **MetodoDivisione** è una classe di supporto utilizzata nella classe CreazioneSquadre, che sta ad indicare con i suoi attributi la metodologia di divisione scelta dall'utente per l'estrazione delle squadre.
### Stato
> La classe **Stato** è una classe di supporto utilizzata nelle classi Cronometro e Timer, che serve per descrivere lo stato in cui si trovano gli stessi.

![Classi enumerative di supporto](D3/img/img1.png)

## Classi di supporto
### Data
> La classe **Data** è una classe di supporto che con i suoi attributi giorno, mese, anno, orario sta ad indicare un preciso momento, col suo metodo now() restituisce i valori di questi attributi e con il metodo lessThan(d2 : Data) : bool può confrontare due date.
### URL
> La classe **URL** è una classe di supporto che con i suoi attributi protocollo e percorso va ad indicare un immagine o un suono, a seconda dell'uso che si fa della classe.<br>
> Per esempio, nella classe Suono, l'url utilizzato per l'attributo sorgente rappresenta un suono. Al contrario, nelle classi Faccia, Attività e Utente, gli attributi immagine e banner rappresentano un'immagine.
### Time
> La classe **Time** è una classe di supporto, che con i suoi attributi, va a rappresentare un tempo con precisione massima nell'ordine dei centesimi di secondo.
### Colore
> La classe **Colore** è una classe di supporto che con i suoi attributi, va a rappresentare un colore espresso tramite codice RGB, uno spazio di colore che riproduce i colori visibili all’uomo tramite la mescolanza additiva dei tre colori di base: rosso, verde e blu.

![Classi di supporto](D3/img/img2.png)

### Info, Filtro ed Etichetta
> La classe **Etichetta** è una classe di supporto che con i suoi attributi, va a rappresentare nome, descrizione e categoria di un'etichettà che può essere assegnata ad un'attività. Viene usata nella classe Info.<br>
> La classe **Info** è una classe di supporto che con i suoi attributi va a definire tutte le informazioni riguardanti un'attività.<br>
> La classe **Filtro** è una classe di supporto ed è collegata tramite una generalizzazione alla classe Info. Viene utilizzata per contenere le informazioni secondo le quali le attività devono essere filtrate.

![Classi di supporto](D3/img/img3.png)

## Dado e Faccia
> La classe **Faccia** è una classe di supporto alla classe Dado, e presenta tutti gli attributi necessari a definire qual è il tipo di una faccia del dado e cosa vi è rappresentato.
> La classe **Dado** è una classe il quale compito è quello di fornire gli attributi e i metodi necessari all'utilizzo dello strumento dado. <br>
> Una volta determinati i parametri definiti dagli attributi, grazie ai metodi presenti, il metodo estrai() è quello che fa funzionare lo strumento.

![Dado e Faccia](D3/img/img4.png)

## Cronometro
> La classe **Cronometro** è una classe il quale compito è quello di fornire gli attributi e i metodi necessari all'utilizzo dello strumento cronometro.<br>
> Il tempo viene rappresentato grazie alla classe di supporto Time.

![Cronometro](D3/img/img5.png)

## Timer e Suono
> La classe **Suono** è una classe il quale compito è quello di fornire gli attributi e i metodi necessari all'utilizzo dello strumento fischietto, nonché di essere una classe di supporto alla classe Timer.<br>
> La classe **Suono**, grazie ai suoi attributi e metodi riesce a riprodurre un suono in base a come viene gestito l'attributo booleano inRiproduzione.<br>
> La classe **Timer** è una classe il quale compito è quello di fornire gli attributi e i metodi necessari all'utilizzo dello strumento timer.<br>
> I metodi stop() e start() di Timer hanno una funzione diversa rispetto a quelli di Suono, in quanto si occupano di fermare e avviare il timer e non di riprodurre o meno il suono.

![Timer e Suono](D3/img/img6.png)

## CreazioneSquadre
> La classe **CreazioneSquadre** è una classe il quale compito è quello di fornire gli attributi e i metodi necessari all'utilizzo dello strumento creazione squadre.<br>
> Gli attributi presenti indicano i valori dei parametri come anche se quei parametri sono stati impostati, nel caso degli attributi booleani Set.<br>
> Grazie ai metodi presenti viene poi fatta l'estrazione delle squadre, secondo la metodologia scelta dall'utente.

![Creazione Squadreo](D3/img/img7.png)

## SegnaPunti
> La classe **SegnaPunti** è una classe il quale compito è quello di fornire gli attributi e i metodi necessari all'utilizzo dello strumento segna punti.<br>
> L'attributo contatori rappresenta i contatori delle varie squadre, che vengono incrementati e/o decrementati grazie ai metodi presenti.

![Segna Punti](D3/img/img8.png)

## Utente
> La classe **Utente** è una classe che rappresenta colui che utilizza l'applicazione. Ci sono quindi attributi che rappresentano i dati identificativi di quell'utente, come anche il ruolo e lo stato, che può essere offline o online.<br>
> Il metodo login() crea un'istanza di Autenticazione e chiama diversi suoi metodi. Esso è associato al metodo logout().<br>
> Il metodo verificaRuolo(ruoloNecessario : Ruolo, richiedente : Utente) serve a confrontare due ruoli.<br>
> Un utente può promuovere gli altri utenti, ma l'attributo promossoDa, serve nel caso un utente voglia declassare un altro utente che ha il ruolo di amministratore. In tal caso, l'utente deve essere quello che lo ha promosso a tale.<br>
> Il metodo listaUtenti(richiedente : Utente) : Utente[0..N] fornisce una lista di utenti.<br>
> Un utente può creare una o più attività e/o liste di attività, rappresentate rispettivamente dalle classi Attività e ListaAttività.<br>
> Un utente può effettuare una o più segnalazioni e/o valutazioni, rappresentate rispettivamente dalle classi Segnalazione e Valutazione.

![Utente](D3/img/img9.png)

## Autenticazione
> La classe **Autenticazione** è una classe che rappresenta il processo di login di un utente. <br>
> Quando viene chiamato il metodo login() della classe Utente, viene creata un'istanza di Autenticazione e viene chiamata richiestaAutorizzativa().<br>
> Se il codice è valido viene chiamato il metodo richiestaToken() e successivamente dettagliAccount() che mette i risultati negli attributi id e mail dell'utente. <br>
> Viene chiesto a MongoDB il ruolo dell'utente e la sua foto profilo che vengono a loro volta assegnati agli attributi ruolo e immagine dell'utente.<br>
> Infine avviene un aggiornamento dei dati locali.

![Autenticazione](D3/img/img10.png)

## Segnalazione
> La classe **Segnalazione** è una classe che rappresenta la segnalazione fatta da un utente ad un'attività. Più segnalazioni possono riferirsi ad una stessa attività. Ogni segnalazione è stata effettuata da un solo utente. <br>
> Gli attributi rappresentano le informazioni relative alla segnalazione, ovvero descrizione, utente da cui è stata fatta e attività alla quale si riferisce. <br>
> Un utente può effettuare una segnalazione grazie al metodo presente.<br>
> Se un utente non esiste più le segnalazioni effettuate dallo stesso rimangono.
## Valutazione
> La classe **Valutazione** è una classe che rappresenta la valutazione fatta da un utente ad un'attività. Più valutazioni possono riferirsi ad una stessa attività. Un utente può dare una sola valutazione ad un'attività. <br>
> Gli attributi rappresentano le informazioni relative alla valutazione, ovvero il voto espresso con un numero intero, l'attività a cui si riferisce e l'utente da cui è stata fatta. <br>
> Un utente può effettuare una valutazione grazie al metodo presente. <br>
> Se un utente non esiste più le valutazioni effettuate dallo stesso rimangono.

![Segnalazione e Valutazione](D3/img/img11.png)

## GestoreDatiOffline
> La classe **GestoreDatiOffline** è una classe che rappresenta tutte le operazioni che vengono fatte sui dati presenti localmente, ovvero che non necessitano che l'utente sia online.<br>
> Oltre a ciò si occupa anche di aggiornare i dati locali grazie al metodo omonimo.

![Gestore Dati Offline](D3/img/img12.png)

## Attività
> La classe **Attività** è una classe che rappresenta tutto ciò riguardante un'attività.<br>
> Viene aiutata dalla classe di supporto Info, che contiene gran parte delle informazioni dell'attività stessa.<br>
> Essa può essere soggetta a modifiche grazie all'omonimo metodo.
> A un'attività si possono riferire delle segnalazioni e/o valutazioni. Il metodo mostraSegnalazioni() mostra tutte le segnalazioni associate a quella specifica attività. <br>
> Il metodo divisioneSquadre, reindirizza l'utente alla schermata di creazione squadre con i parametri già riempiti per rispettare i vincoli di quella specifica attività.<br>
> Un'attività è contenuta nel catalogo e può essere contenuta in una lista. Più liste possono contenere la stessa attività, e un'attività può essere contenuta più volte nella stessa lista.<br>
> Un'attività viene creata da un solo utente.

![Attività](D3/img/img13.png)

## Catalogo
> La classe **Catalogo** è una classe che rappresenta il catalogo di attività.<br>
> Tra gli attributi c'è un'istanza di Filtro. Grazie al metodo impostaFiltro(filtro : Filtro) si va a impostare gli attributi di filtroAttuale.<br>
> Grazie al metodo ottieniCatalogo si va a riempire l'attributo lista con il catalogo filtrato.<br>
> Il catalogo può contenere delle attività.<br>
> Il metodo mostraAttivitàSegnalate(richiedente : Utente) mostra la lista di attività segnalate e per ogni attività quante sono le segnalazioni.

![Catalogo](D3/img/img14.png)

## ListaAttività
> La classe **ListaAttività** è una classe che rappresenta le liste di attività create dagli utenti.<br>
> Un utente può creare più liste di attività. Ne ha almeno una in quanto ogni utente ha la lista "Preferiti". Ogni lista ha un solo utente, non esistono liste condivise.<br>
> Tra gli attributi della lista sono presenti le informazioni che la identificano e con i metodi forniti si può crearla, rimuoverla, mostrarla ed esportarla, oltre ad aggiungervi o rimuovere attività.

![Lista Attività](D3/img/img15.png)

## MongoDB
> La classe **MongoDB** è una classe che rappresenta in che modo il sistema si interfaccia con MongoDB.<br>
> Il metodo controllaConnessione() verifica se si è connessi o meno al DBMS.<br>
> I metodi presenti rappresentano tutti i modi in cui il sistema interagisce con MongoDB.

![MongoDB](D3/img/img16.png)

<div class="page-break"></div>
