
# 4. Requisiti del front-end del progetto
Nel presente capitolo vengono riportati i requisiti del front-end (RFE) e mockup del sistema.

L’applicazione presenterà diverse schermate:

## Catalogo
### Visualizzato da [Anonimo](#anonimo)
> #### RFE1.
> Lista di attività del catalogo, dove cliccando sul nome o sull’immagine l’utente viene reindirizzato alla schermata della relativa attività

> #### RFE2.
> Pulsante di collegamento alla schermata del menù

> #### RFE3.
> Pulsante che apre un menu a tendina contenente i filtri se questo è chiuso, e lo chiude altrimenti. Il pulsante è di colore arancione se il menu a tendina è chiuso, grigio altrimenti

> #### RFE4.
> Campi del filtro per le varie informazioni e lista di etichette

<center><img alt="Catalogo" src="D1/img/RFE/catalogo.png" width="30%"/></center>

<center><img alt="Catalogo con filtro" src="D1/img/RFE/catalogo-filtri.png" width="30%"/></center>

### Visualizzato da [Autenticato](#autenticato)
> [RFE2.](#rfe2)
> [RFE3.](#rfe3)
> [RFE4.](#rfe4)

> #### RFE5.
> Lista di attività del catalogo comprensiva delle attività proposte dagli utenti, dove cliccando sul nome o sull’immagine l’utente viene reindirizzato alla schermata della relativa attività

### Visualizzato da [Amministratore](#amministratore)
> [RFE2.](#rfe2)
> [RFE3.](#rfe3)
> [RFE4.](#rfe4)
> [RFE5.](#rfe5)

> #### RFE6.
> Pulsante per la [modifica dell’attività](#modifica-attivita)

## Menu
### Visualizzato da [Anonimo](#anonimo)
> #### RFE7.
> Pulsante di collegamento alla schermata precedentemente utilizzata

> #### RFE8.
> Pallino che assume il colore grigio se l’utente non è connesso al server, verde altrimenti

> #### RFE9.
> Pulsante di collegamento alla schermata del catalogo

> #### RFE10.
> Pulsante di collegamento alla schermata degli strumenti

> #### RFE11.
> Pulsante di collegamento alla schermata dei preferiti, non utilizzabile senza autenticazione

> #### RFE12.
> Pulsante di collegamento alla schermata delle liste, non utilizzabile senza autenticazione

> #### RFE13.
> Pulsante di collegamento alla schermata di proposta attività, non utilizzabile senza autenticazione

> #### RFE14.
> Pulsante di collegamento alla schermata di autenticazione Google

<center><img alt="Menu visualizzato da Anonimo" src="D1/img/RFE/menu-anonimo.png" width="30%"/></center>

## Menu
### Visualizzato da [Autenticato](#autenticato)
> [RFE7.](#rfe7)
> [RFE8.](#rfe8)
> [RFE9.](#rfe9)
> [RFE10.](#rfe10)

> #### RFE15.
> Pulsante di collegamento alla schermata dei preferiti

> #### RFE16.
> Pulsante di collegamento alla schermata delle liste

> #### RFE17.
> Pulsante di collegamento alla schermata di proposta attività

> #### RFE18.
> Foto profilo dell’account

> #### RFE19.
> Pulsante per effettuare il logout

<center><img alt="Menu visualizzato da Autenticato" src="D1/img/RFE/menu-autenticato.png" width="30%"/></center>

### Visualizzato da [Amministratore](#amministratore)
> [RFE7.](#rfe7)
> [RFE8.](#rfe8)
> [RFE9.](#rfe9)
> [RFE10.](#rfe10)
> [RFE15.](#rfe15)
> [RFE16.](#rfe16)
> [RFE17.](#rfe17)
> [RFE18.](#rfe18)
> [RFE19.](#rfe19)

> #### RFE20.
> Pulsante di collegamento alla schermata di gestione utenti

> #### RFE21.
> Pulsante di collegamento alla schermata di segnalazioni

## Strumenti
> [RFE2.](#rfe2)

> #### RFE22.
> Pulsante di collegamento allo strumento [DADO](#dado)

> #### RFE23.
> Pulsante di collegamento allo strumento [FISCHIETTO](#fischietto)

> #### RFE24.
> Pulsante di collegamento allo strumento [CRONOMETRO](#cronometro)

> #### RFE25.
> Pulsante di collegamento allo strumento [TIMER](#timer)

> #### RFE26.
> Pulsante di collegamento allo strumento [SEGNA-PUNTI](#segna-punti)

> #### RFE27.
> Pulsante di collegamento allo strumento di [CREAZIONE SQUADRE](#creazione-squadre)

### DADO
> #### RFE28.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata strumenti

> #### RFE29.
> Pulsante che apre un menu a tendina contenente il tipo di elementi che si possono estrarre con i dadi

> #### RFE30.
> Campo testuale dove è possibile indicare il numero di elementi da estrarre

> #### RFE31. 
> Se il tipo degli elementi scelto è "Numeri" vi saranno da immettere in due campi testuali l'estremo inferiore del range da cui si vuole estrarre e il passo tra due elementi consecutivi

> #### RFE32.
> Se il tipo degli elementi scelto è "Parole" vi saranno un campo testuale ed un pulsante di conferma per ogni parola da inserire

> #### RFE33.
> Se il tipo degli elementi scelto è "Colori" verrà mostrata all'utente una griglia di colori e un pulsante di conferma per ogni colore da inserire

> #### RFE34.
> Se il tipo degli elementi scelto è "Immagini" ci sarà un pulsante "Inserisci" che l'utente cliccherà per inserire un'immagine e un pulsante conferma per ogni immagine da inserire

> #### RFE35.
> Campo selezionabile per l'estrazione con reimmissione.

> #### RFE36.
> Pulsante "Estrai", che sceglie un elemento casuale tra il campione di elementi scelto e lo mostra all'utente.

### FISCHIETTO
> [RFE28.](#rfe28)

> #### RFE37.
> Immagine di un fischietto, che una volta premuta fa riprodurre il suono selezionato

> #### RFE38.
> Pulsante che apre un menu a tendina contenente altri suoni che è possibile selezionare e un pulsante "+" che permette all'utente di caricare un nuovo suono da utilizzare

<center><img alt="Strumento FISCHIETTO" src="D1/img/RFE/fischietto.png" width="30%"/></center>

## CRONOMETRO
> [RFE28.](#rfe28)

> #### RFE39.
> Cronometro inizialmente azzerato, con segnati minuti, secondi e centesimi di secondo nella forma 00:00.00

> #### RFE40.
> Pulsante "Avvia" che serve ad avviare il cronometro. Una volta avviato il cronometro il pulsante "Avvia" sparisce sostituito da "Ferma"

> #### RFE41.
> Pulsante "Parziale" che serve a salvare i tempi parziali del cronometro senza fermarlo. Quando il cronometro non è ancora stato avviato il pulsante appare di colore grigio e non è ancora selezionabile, ma una volta che è stato premuto sul pulsante "Avvia" esso diventa disponibile

> #### RFE42.
> Pulsante "Ferma" che serve a mettere in pausa il cronometro. Una volta messo in pausa il cronometro i pulsanti "Ferma" e "Parziale" verrano sostituiti rispettivamente dai pulsanti "Riprendi" e "Ripristina"

> #### RFE43.
> Pulsante "Ripristina" che serve a riportare il valore del cronometro a 00:00.00. Una volta fatto il reset del valore compariranno nuovamente i pulsanti "Avvia" e "Parziale" al posto di "Riprendi" e "Ripristina"

> #### RFE44.
> Sotto al tempo del timer, ogni volta che il pulsante "Parziale" viene premuto, vengono riportati i tempi parziali salvati, scritti con un carattere più piccolo, mantenendo più in basso quello col valore minore

### TIMER
> [RFE28.](#rfe28)
> [RFE38.](#rfe38)

> #### RFE45.
> Timer inizialmente azzerato, con segnati ore, minuti e secondi nella forma 00:00:00. L’utente può impostare il tempo desiderato scorrendo sulle cifre.

> #### RFE46.
> Pulsante "Avvia" che serve ad avviare il timer. Una volta avviato il timer il pulsante "Avvia" sparisce e compaiono "Pausa" e "Annulla"

> #### RFE47.
> Pulsante "Pausa" che serve a fermare momentaneamente il conto alla rovescia del timer. Una volta messo in pausa il timer al posto del pulsante "Pausa" comparirà il pulsante "Riprendi"

> #### RFE48.
> Pulsante "Annulla" che serve a fermare il timer e riportarlo al valore impostato precedentemente. I pulsanti "Pausa"/"Riprendi" e "Annulla" spariranno, sostituiti dal pulsante "Avvia"

> #### RFE49.
> Una volta finito il tempo del timer, viene riprodotto il suono selezionato

### Impostazioni SEGNA-PUNTI
> [RFE28.](#rfe28)

> #### RFE50.
> Tasto per aggiungere una nuova squadra, specificandone il nome in un campo testuale

> #### RFE51.
> Lista delle squadre già presenti.

> #### RFE52.
> Pulsante di conferma, che porta alla schermata [SEGNA-PUNTI](#segna-punti)

### SEGNA-PUNTI
> #### RFE53.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata [Impostazioni SEGNA-PUNTI](#impostazioni-segna-punti)

> #### RFE54.
> Lista scorribile delle squadre, indicante nome e numero di punti correnti

> #### RFE55.
> Pulsante di incremento e di decremento punto accanto ad ogni squadra

### Impostazioni CREAZIONE SQUADRE
> [RFE28.](#rfe28)

> #### RFE56.
> Campo di inserimento del numero di giocatori

> #### RFE57.
> Campo di inserimento del numero di persone per squadra

> #### RFE58.
> Campo di inserimento del numero di squadre

> #### RFE59.
> Pulsante di conferma che reindirizza alla schermata [CREAZIONE SQUADRE](#creazione-squadre)

### CREAZIONE SQUADRE
> [RFE28.](#rfe28)

> #### RFE60.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata [Impostazioni CREAZIONE SQUADRE](#impostazioni-creazione-squadre)

> #### RFE61.
> Campo di inserimento dei nomi delle squadre

> #### RFE62.
> Pulsante che apre menu a tendina per scegliere metodo di divisione in squadre. Il metodo impostato di default è "Balanced"

> #### RFE63.
> Pulsante "Inizia estrazione" che reindirizza l'utente alla schermata [Estrazione Squadre](#estrazione-squadre)

## Estrazione Squadre
> #### RFE64.
> Schermata colorata senza alcuna scritta che precede l'inizio delle estrazioni

> #### RFE65.
> Cliccare sullo schermo per passare alla prossima estrazione. A ogni estrazione viene visualizzato sullo schermo il nome della squadra di appartenenza

## Liste
### Visualizzato da [Autenticato](#autenticato) e [Amministratore](#amministratore)
> #### RFE66.
> Lista di liste create dall’utente

> #### RFE67.
> Cliccando sul nome di una lista, l’utente viene reindirizzato alla schermata "[Lista](#lista)" della relativa lista

> #### RFE68.
> Pulsante che aggiunge una lista, aprendo una finestra dove è presente un campo nel quale l’utente deve inserire il nome della nuova lista e un pulsante di conferma

> #### RFE69.
> Quando l'utente tiene premuto su una lista appare un pulsante con l'immagine di un cestino, che ha la funzione di eliminare tale lista

## Lista
### Visualizzato da [Autenticato](#autenticato) e [Amministratore](#amministratore)
> [RFE3.](#rfe3)
> [RFE4.](#rfe4)
> [RFE5.](#rfe5)

> #### RFE70.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata [Liste](lista)

> #### RFE71.
> Nome della lista indicato

> #### RFE72.
> Lista di attività appartenenti alla lista sopraindicata, dove cliccando sul nome o sull’immagine l’utente viene reindirizzato alla schermata della relativa attività

> #### RFE73.
> Pulsante che permette di esportare la lista con tutte le informazioni sulle attività, in formato PDF o JSON

> #### RFE74.
> Quando l'utente tiene premuto su un'attività appare un pulsante con l'immagine di un cestino, che ha la funzione di eliminare tale attività dalla lista

## Attività
### Visualizzato da [Anonimo](#anonimo)
> #### RFE75.
> Pulsante di collegamento alla schermata precedente, ovvero il [Catalogo](#catalogo) o una [Lista](#lista)

> #### RFE76.
> Nome e immagine dell’attività

> #### RFE77.
> Descrizione dell’attività e altri campi informativi

> #### RFE78.
> Etichette caratterizzanti l'attività

> #### RFE79.
> Pulsante di collegamento alla schermata [Creazione squadre](#creazione-squadre) nel caso l'attività stessa lo richieda

### Visualizzato da [Autenticato](#autenticato)
> [RFE75.](#rfe75)
> [RFE76.](#rfe76)
> [RFE77.](#rfe77)
> [RFE78.](#rfe78)
> [RFE79.](#rfe79)

> #### RFE80.
> Pulsante che aggiunge l’attività alla lista predefinita "preferiti"

> #### RFE81.
> Pulsante che aggiunge l’attività a una lista. Si apre un menu a tendina con tutte le liste e l’utente può selezionare le liste a cui aggiungere l’attività stessa

> #### RFE82.
> Per le attività create dall’utente compare un pulsante che apre la schermata [Modifica attività](#modifica-attività)

> #### RFE83.
> Cinque stelle situate sotto il titolo, grazie alle quali l'utente può aggiungere una valutazione che va da 1 a 5 stelle alla determinata attività

> #### RFE84.
> Pulsante situato accanto al titolo, che reindirizza l'utente alla schermata di [Segnalazione attività](#segnalazione-attività)

> #### RFE85.
> Valutazione media visualizzata con una barra posta al di sopra delle stelle usate per assegnare una valutazione

<center><img alt="Attività" src="D1/img/RFE/attività.png" width="30%"/></center>

### Visualizzato da [Amministratore](#amministratore)
> [RFE75.](#rfe75)
> [RFE76.](#rfe76)
> [RFE77.](#rfe77)
> [RFE78.](#rfe78)
> [RFE79.](#rfe79)
> [RFE80.](#rfe80)
> [RFE81.](#rfe81)
> [RFE83.](#rfe83)
> [RFE84.](#rfe84)
> [RFE85.](#rfe85)

> #### RFE86.
> Pulsante che apre la schermata [Modifica attività](#modifica-attività)

> #### RFE87.
> Campo situato accanto all'attività, che ne indica il numero di segnalazioni

## Modifica attività
### Visualizzato da [Amministratore](#amministratore)
> #### RFE88.
> Pulsante di collegamento alla schermata precedente, ovvero all’[Attività](#attività)

> #### RFE89.
> Campi di informazioni da modificare

> #### RFE90.
> Lista di etichette da selezionare

> #### RFE91.
> Pulsante di conferma

## Proponi attività
### Visualizzato da [Autenticato](#autenticato) e da [Amministratore](#amministratore)
> [RFE2.](#rfe2)
> [RFE88.](#rfe88)
> [RFE89.](#rfe89)
> [RFE90.](#rfe90)
> [RFE91.](#rfe91)

> #### RFE92.
> Campo di inserimento dell’autore dell’attività

## Tutorial
### Visualizzato da [Anonimi](#anonimi)
> #### RFE93.
> Per ogni schermata compare inizialmente una finestra contenente una breve spiegazione di utilizzo

> #### RFE94.
> Per ogni finestra c’è un campo contrassegnabile che impedisce alla finestra stessa di essere nuovamente visualizzata

## Gestione utenti
### Visualizzato da [Amministratore](#amministratore)
> [RFE2.](#rfe2)

> #### RFE95.
> Lista degli utenti che hanno effettuato l’accesso all’applicazione

> #### RFE96.
> Per ogni utente è presente un pulsante che, selezionato assume il colore verde e indica la promozione dell’utente stesso ad amministratore, mentre deselezionato assume il colore grigio e indica che l’utente stesso non è un amministratore

## Segnalazione attività
### Lista attività segnalate

> [RFE2.](#rfe2)

> #### RFE97.
> Lista delle attività segnalate, con accanto il numero di segnalazioni per ogni attività. Cliccando sul nome dell'attività, l'utente viene reindirizzato alla lista di segnalazioni per la specifica attività

### Lista segnalazioni

> #### RFE98.
> Pulsante di collegamento alla schermata precedente, ovvero [Lista attività segnalate](#lista-attività-segnalate)
> #### RFE90.
> Lista delle segnalazioni con titolo e descrizione consultabile dall'utente.

<div class="page-break"></div>
