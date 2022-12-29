
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
> [RFE2.](#rfe3)
> [RFE2.](#rfe4)
> [RFE2.](#rfe5)
> [RFE2.](#rfe6)
> [RFE7.](#rfe7)

> #### RFE8.
> Lista di attività del catalogo comprensiva delle attività proposte dagli utenti, dove cliccando sul nome o sull’immagine l’utente viene reindirizzato alla schermata della relativa attività

### Visualizzato da [Amministratore](#amministratore)
> [RFE2.](#rfe2)
> [RFE3.](#rfe3)
> [RFE4.](#rfe4)
> [RFE5.](#rfe5)
> [RFE6.](#rfe6)
> [RFE7.](#rfe7)
> [RFE8.](#rfe8)
> [RFE9.](#rfe9)

> #### RFE11.
> Pulsante per la [modifica dell’attività](#modifica-attivita)

## Menu
### Visualizzato da [Anonimo](#anonimo)
> #### RFE13.
> Pulsante di collegamento alla schermata precedentemente utilizzata

> #### RFE14.
> Pallino che assume il colore grigio se l’utente non è connesso al server, verde altrimenti

> #### RFE15.
> Pulsante di collegamento alla schermata del catalogo

> #### RFE16.
> Pulsante di collegamento alla schermata degli strumenti

> #### RFE17.
> Pulsante di collegamento alla schermata dei preferiti, non utilizzabile senza autenticazione

> #### RFE18.
> Pulsante di collegamento alla schermata delle liste, non utilizzabile senza autenticazione

> #### RFE19.
> Pulsante di collegamento alla schermata di proposta attività, non utilizzabile senza autenticazione

> #### RFE20.
> Pulsante di collegamento alla schermata di autenticazione Google

<center><img alt="Menu visualizzato da Anonimo" src="D1/img/RFE/menu-anonimo.png" width="30%"/></center>

## Menu
### Visualizzato da [Autenticato](#autenticato)
> [RFE13.](#rfe13)
> [RFE14.](#rfe14)
> [RFE15.](#rfe15)
> [RFE16.](#rfe16)

> #### RFE21.
> Pulsante di collegamento alla schermata dei preferiti

> #### RFE22.
> Pulsante di collegamento alla schermata delle liste

> #### RFE23.
> Pulsante di collegamento alla schermata di proposta attività

> #### RFE24.
> Foto profilo dell’account

> #### RFE25.
> Pulsante per effettuare il logout

<center><img alt="Menu visualizzato da Autenticato" src="D1/img/RFE/menu-autenticato.png" width="30%"/></center>

### Visualizzato da [Amministratore](#amministratore)
> [RFE13.](#rfe13)
> [RFE14.](#rfe14)
> [RFE15.](#rfe15)
> [RFE16.](#rfe16)
> [RFE21.](#rfe21)
> [RFE22.](#rfe22)
> [RFE23.](#rfe23)
> [RFE24.](#rfe24)
> [RFE25.](#rfe25)

> #### RFE26.
> Pulsante di collegamento alla schermata di gestione utenti

> #### RFE27.
> Pulsante di collegamento alla schermata di segnalazioni

## Strumenti
> [RFE2.](#rfe2)

> #### RFE27.
> Pulsante di collegamento allo strumento [DADO](#dado)

> #### RFE28.
> Pulsante di collegamento allo strumento [FISCHIETTO](#fischietto)

> #### RFE29.
> Pulsante di collegamento allo strumento [CRONOMETRO](#cronometro)

> #### RFE30.
> Pulsante di collegamento allo strumento [TIMER](#timer)

> #### RFE31.
> Pulsante di collegamento allo strumento [SEGNA-PUNTI](#segna-punti)

> #### RFE32.
> Pulsante di collegamento allo strumento di [CREAZIONE SQUADRE](#creazione-squadre)

### DADO
> #### RFE33.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata strumenti

> #### RFE34.
> Pulsante che apre un menu a tendina contenente il tipo di elementi che si possono estrarre con i dadi

> #### RFE35.
> Campo testuale dove è possibile indicare il numero di elementi da estrarre

> #### RFE36. 
> Se il tipo degli elementi scelto è "Numeri" vi saranno da immettere in due campi testuali l'estremo inferiore del range da cui si vuole estrarre e il passo tra due elementi consecutivi

> #### RFE37.
> Se il tipo degli elementi scelto è "Parole" vi saranno un campo testuale ed un pulsante di conferma per ogni parola da inserire

> #### RFE38.
> Se il tipo degli elementi scelto è "Colori" verrà mostrata all'utente una griglia di colori e un pulsante di conferma per ogni colore da inserire

> #### RFE39.
> Se il tipo degli elementi scelto è "Immagini" ci sarà un pulsante "Inserisci" che l'utente cliccherà per inserire un'immagine e un pulsante conferma per ogni immagine da inserire

> #### RFE40.
> Campo selezionabile per l'estrazione con reimmissione.

> #### RFE41.
> Pulsante "Estrai", che sceglie un elemento casuale tra il campione di elementi scelto e lo mostra all'utente.

### FISCHIETTO
> [RFE33.](#rfe33)

> #### RFE36.
> Immagine di un fischietto, che una volta premuta fa riprodurre il suono selezionato

> #### RFE37.
> Pulsante che apre un menu a tendina contenente altri suoni che è possibile selezionare e un pulsante "+" che permette all'utente di caricare un nuovo suono da utilizzare

<center><img alt="Strumento FISCHIETTO" src="D1/img/RFE/fischietto.png" width="30%"/></center>

## CRONOMETRO
> [RFE33.](#rfe33)

> #### RFE38.
> Cronometro inizialmente azzerato, con segnati minuti, secondi e centesimi di secondo nella forma 00:00.00

> #### RFE39.
> Pulsante "Avvia" che serve ad avviare il cronometro. Una volta avviato il cronometro il pulsante "Avvia" sparisce sostituito da "Ferma"

> #### RFE40.
> Pulsante "Parziale" che serve a salvare i tempi parziali del cronometro senza fermarlo. Quando il cronometro non è ancora stato avviato il pulsante appare di colore grigio e non è ancora selezionabile, ma una volta che è stato premuto sul pulsante "Avvia" esso diventa disponibile

> #### RFE41.
> Pulsante "Ferma" che serve a mettere in pausa il cronometro. Una volta messo in pausa il cronometro i pulsanti "Ferma" e "Parziale" verrano sostituiti rispettivamente dai pulsanti "Riprendi" e "Ripristina"

> #### RFE42.
> Pulsante "Ripristina" che serve a riportare il valore del cronometro a 00:00.00. Una volta fatto il reset del valore compariranno nuovamente i pulsanti "Avvia" e "Parziale" al posto di "Riprendi" e "Ripristina"

> #### RFE43.
> Sotto al tempo del timer, ogni volta che il pulsante "Parziale" viene premuto, vengono riportati i tempi parziali salvati, scritti con un carattere più piccolo, mantenendo più in basso quello col valore minore

### TIMER
> [RFE33.](#rfe33)
> [RFE37.](#rfe37)

> #### RFE44.
> Timer inizialmente azzerato, con segnati ore, minuti e secondi nella forma 00:00:00. L’utente può impostare il tempo desiderato scorrendo sulle cifre.

> #### RFE45.
> Pulsante "Avvia" che serve ad avviare il timer. Una volta avviato il timer il pulsante "Avvia" sparisce e compaiono "Pausa" e "Annulla"

> #### RFE46.
> Pulsante "Pausa" che serve a fermare momentaneamente il conto alla rovescia del timer. Una volta messo in pausa il timer al posto del pulsante "Pausa" comparirà il pulsante "Riprendi"

> #### RFE47.
> Pulsante "Annulla" che serve a fermare il timer e riportarlo al valore impostato precedentemente. I pulsanti "Pausa"/"Riprendi" e "Annulla" spariranno, sostituiti dal pulsante "Avvia"

> #### RFE48.
> Una volta finito il tempo del timer, viene riprodotto il suono selezionato

### Impostazioni SEGNA-PUNTI
> [RFE33.](#rfe33)

> #### RFE49.
> Tasto per aggiungere una nuova squadra, specificandone il nome in un campo testuale

> #### RFE50.
> Lista delle squadre già presenti.

> #### RFE51.
> Pulsante di conferma, che porta alla schermata [SEGNA-PUNTI](#segna-punti)

### SEGNA-PUNTI
> #### RFE52.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata [Impostazioni SEGNA-PUNTI](#impostazioni-segna-punti)

> #### RFE53.
> Lista scorribile delle squadre, indicante nome e numero di punti correnti

> #### RFE54.
> Pulsante di incremento e di decremento punto accanto ad ogni squadra

### Impostazioni CREAZIONE SQUADRE
> [RFE33.](#rfe33)

> #### RFE55.
> Campo di inserimento del numero di giocatori

> #### RFE56.
> Campo di inserimento del numero di persone per squadra

> #### RFE57.
> Campo di inserimento del numero di squadre

> #### RFE58.
> Pulsante di conferma che reindirizza alla schermata [CREAZIONE SQUADRE](#creazione-squadre)

### CREAZIONE SQUADRE
> #### RFE59.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata [Impostazioni CREAZIONE SQUADRE](#impostazioni-creazione-squadre)

> #### RFE60.
> Campo di inserimento dei nomi delle squadre

> #### RFE61.
> Pulsante che apre menu a tendina per scegliere metodo di divisione in squadre. Il metodo impostato di default è "Balanced"

> #### RFE62.
> Pulsante "Inizia estrazione" che reindirizza l'utente alla schermata [Estrazione Squadre](#estrazione-squadre)

## Estrazione Squadre
> #### RFE63.
> Schermata colorata senza alcuna scritta che precede l'inizio delle estrazioni

> #### RFE62.
> Cliccare sullo schermo per passare alla prossima estrazione. A ogni estrazione viene visualizzato sullo schermo il nome della squadra di appartenenza

## Liste
### Visualizzato da [Autenticato](#autenticato) e [Amministratore](#amministratore)
> #### RFE63.
> Lista di liste create dall’utente

> #### RFE64.
> Cliccando sul nome di una lista, l’utente viene reindirizzato alla schermata "[Lista](#lista)" della relativa lista

> #### RFE65.
> Pulsante che aggiunge una lista, aprendo una finestra dove è presente un campo nel quale l’utente deve inserire il nome della nuova lista e un pulsante di conferma

> #### RFE66.
> Quando l'utente tiene premuto su una lista appare un pulsante con l'immagine di un cestino, che ha la funzione di eliminare tale lista

## Lista
### Visualizzato da [Autenticato](#autenticato) e [Amministratore](#amministratore)
> [RFE3.](#rfe3)
> [RFE4.](#rfe4)
> [RFE5.](#rfe5)
> [RFE6.](#rfe6)
> [RFE7.](#rfe7)
> [RFE8.](#rfe8)
> [RFE9.](#rfe9)

> #### RFE66.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata [Liste](lista)

> #### RFE67.
> Nome della lista indicato

> #### RFE68.
> Lista di attività appartenenti alla lista sopraindicata, dove cliccando sul nome o sull’immagine l’utente viene reindirizzato alla schermata della relativa attività

> #### RFE69.
> Pulsante che permette di esportare la lista con tutte le informazioni sulle attività, in formato PDF o JSON

> #### RFE70.
> Quando l'utente tiene premuto su un'attività appare un pulsante con l'immagine di un cestino, che ha la funzione di eliminare tale attività dalla lista

## Attività
### Visualizzato da [Anonimo](#anonimo)
> #### RFE70.
> Pulsante di collegamento alla schermata precedente, ovvero il [Catalogo](#catalogo) o una [Lista](#lista)

> #### RFE71.
> Nome e immagine dell’attività

> #### RFE72.
> Descrizione dell’attività e altri campi informativi

> #### RFE73.
> Etichette caratterizzanti l'attività

> #### RFE74.
> Pulsante di collegamento alla schermata [Creazione squadre](#creazione-squadre) nel caso l'attività stessa lo richieda

### Visualizzato da [Autenticato](#autenticato)
> [RFE9.](#rfe9)
> [RFE66.](#rfe66)
> [RFE67.](#rfe67)
> [RFE68.](#rfe68)
> [RFE69.](#rfe69)

> #### RFE74.
> Pulsante che aggiunge l’attività alla lista predefinita "preferiti"

> #### RFE75.
> Pulsante che aggiunge l’attività a una lista. Si apre un menu a tendina con tutte le liste e l’utente può selezionare le liste a cui aggiungere l’attività stessa

> #### RFE76.
> Per le attività create dall’utente compare un pulsante che apre la schermata [Modifica attività](#modifica-attività)

> #### RFE77.
> Cinque stelle situate sotto il titolo, grazie alle quali l'utente può aggiungere una valutazione che va da 1 a 5 stelle alla determinata attività

> #### RFE78.
> Pulsante situato accanto al titolo, che reindirizza l'utente alla schermata di [Segnalazione attività](#segnalazione-attività)

> #### RFE80.
> Valutazione media visualizzata con una barra posta al di sopra delle stelle usate per assegnare una valutazione

<center><img alt="Attività" src="D1/img/RFE/attività.png" width="30%"/></center>

### Visualizzato da [Amministratore](#amministratore)
> [RFE62.](#rfe62)
> [RFE63.](#rfe63)
> [RFE64.](#rfe64)
> [RFE65.](#rfe65)
> [RFE66.](#rfe66)
> [RFE67.](#rfe67)

> #### RFE77.
> Pulsante che apre la schermata [Modifica attività](#modifica-attività)

> #### RFE78.
> Campo situato accanto all'attività, che ne indica il numero di segnalazioni

## Modifica attività
### Visualizzato da [Amministratore](#amministratore)
> #### RFE78.
> Pulsante di collegamento alla schermata precedente, ovvero all’[Attività](#attività)

> #### RFE79.
> Campi di informazioni da modificare

> #### RFE80.
> Lista di etichette da selezionare

> #### RFE81.
> Pulsante di conferma

## Proponi attività
### Visualizzato da [Autenticato](#autenticato) e da [Amministratore](#amministratore)
> [RFE2.](#rfe2)
> [RFE74.](#rfe74)
> [RFE75.](#rfe75)
> [RFE76.](#rfe76)
> [RFE77.](#rfe77)
> [RFE78.](#rfe78)
> [RFE79.](#rfe79)
> [RFE80.](#rfe80)

> #### RFE85.
> Campo di inserimento dell’autore dell’attività

## Tutorial
### Visualizzato da [Anonimi](#anonimi)
> #### RFE86.
> Per ogni schermata compare inizialmente una finestra contenente una breve spiegazione di utilizzo

> #### RFE87.
> Per ogni finestra c’è un campo contrassegnabile che impedisce alla finestra stessa di essere nuovamente visualizzata

## Gestione utenti
### Visualizzato da [Amministratore](#amministratore)
> [RFE2.](#rfe2)

> #### RFE88.
> Lista degli utenti che hanno effettuato l’accesso all’applicazione

> #### RFE89.
> Per ogni utente è presente un pulsante che, selezionato assume il colore verde e indica la promozione dell’utente stesso ad amministratore, mentre deselezionato assume il colore grigio e indica che l’utente stesso non è un amministratore

## Segnalazione attività
### Lista attività segnalate
> #### RFE90.
> Lista delle attività segnalate, con accanto il numero di segnalazioni per ogni attività. Cliccando sul nome dell'attività, l'utente viene reindirizzato alla lista di segnalazioni per la specifica attività

### Lista segnalazioni
> #### RFE91.
> Lista delle segnalazioni con titolo e descrizione consultabile dall'utente.

<div class="page-break"></div>
