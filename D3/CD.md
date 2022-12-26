
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

## Classi di supporto
### Data
> La classe **Data** è una classe di supporto che con i suoi attributi giorno, mese, anno, orario sta ad indicare un preciso momento e che grazie al suo attributo now() restituisce i valori di questi attributi.
### URL
> La classe **URL** è una classe di supporto che con i suoi attributi protocollo e percorso va ad indicare un immagine o un suono, a seconda dell'uso che si fa della classe.<br>
> Per esempio, nella classe Suono, l'url utilizzato per l'attributo sorgente rappresenta un suono. Al contrario, nelle classi Faccia e Utente, l'attributo immagine rappresenta, come indicato dal nome, un'immagine.
### Time
> La classe **Time** è una classe di supporto che con i suoi attributi, va a rappresentare un tempo con la precisione massima nell'ordine dei centesimi di secondo.
### Colore
> La classe **Colore** è una classe di supporto che con i suoi attributi, va a rappresentare un colore espresso tramite codice RGB, uno spazio di colore che riproduce i colori visibili all’uomo tramite la mescolanza additiva dei tre colori di base: rosso, verde e blu.
### Info, Filtro ed Etichetta
> La classe **Etichetta** è una classe di supporto che con i suoi attributi, va a rappresentare nome, descrizione e categoria di un'etichettà che può essere assegnata ad un'attività.<br>
> La classe **Info** è una classe di supporto che con i suoi attributi va a definire tutte le informazioni riguardanti un'attività.<br>
> La classe **Filtro** è una classe di supporto ed è una generalizzazione della classe Info. Viene utilizzata per contenere le informazioni secondo le quali le attività devono essere filtrate.

## Dado e Faccia
> La classe **Faccia** è una classe di supporto alla classe Dado, e presenta tutti gli attributi necessari a definire qual è il tipo di una faccia del dado e cosa vi è rappresentato.
> La classe **Dado** è una classe il quale compito è quello di fornire gli attributi e i metodi necessari all'utilizzo dello strumento dado. <br>
> Una volta determinati i parametri definiti dagli attributi, grazie ai metodi presenti, il metodo estrai() è quello che fa funzionare lo strumento.
## Cronometro
> La classe **Cronometro** è una classe il quale compito è quello di fornire gli attributi e i metodi necessari all'utilizzo dello strumento cronometro.<br>
> Il tempo viene rappresentato grazie alla classe di supporto Time.
## Timer e Suono
> La classe **Suono** è una classe il quale compito è quello di fornire gli attributi e i metodi necessari all'utilizzo dello strumento fischietto, nonché di essere una classe di supporto alla classe Timer.<br>
> La classe **Suono**, grazie ai suoi attributi e metodi riesce a riprodurre un suono in base a come viene gestito l'attributo booleano inRiproduzione.<br>
> La classe **Timer** è una classe il quale compito è quello di fornire gli attributi e i metodi necessari all'utilizzo dello strumento timer.<br>
> I metodi stop() e start() di Timer hanno una funzione diversa rispetto a quelli di Suono, in quanto si occupano di fermare e avviare il timer e non di riprodurre o meno il suono.
## CreazioneSquadre
> La classe **CreazioneSquadre** è una classe il quale compito è quello di fornire gli attributi e i metodi necessari all'utilizzo dello strumento creazione squadre.<br>
> Gli attributi presenti indicano i valori dei parametri come anche se quei parametri sono stati impostati, nel caso degli attributi booleani Set.<br>
> Grazie ai metodi presenti viene poi fatta l'estrazione delle squadre, secondo la metodologia scelta dall'utente.
## SegnaPunti
> La classe **SegnaPunti** è una classe il quale compito è quello di fornire gli attributi e i metodi necessari all'utilizzo dello strumento segna punti.<br>
> L'attributo contatori rappresenta i contatori delle varie squadre, che vengono incrementati e/o decrementati grazie ai metodi presenti.
## Utente
## Autenticazione
## Segnalazione
## Valutazione
## GestoreDatiOffline
## Attività
## Catalogo
## ListaAttività
## MongoDB


<div class="page-break"></div>
