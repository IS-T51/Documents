
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
> Spazio di inserimento per il numero di giocatori vicino al filtro "Numero Giocatori"

> #### RFE5.
> Spazio di inserimento per la durata del gioco vicino al filtro "Durata (minuti)"

> #### RFE6.
> Spazio di inserimento per l’età media dei giocatori vicino al filtro "Età media giocatori"

> #### RFE7.
> Casella contrassegnabile con un clic per selezionare tutti i filtri eccetto "Numero Giocatori", "Età media giocatori" e "Durata (minuti)"

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

> #### RFE9.
> Cinque stelle situate sotto il titolo, grazie alle quali l'utente può aggiungere una valutazione che va da 1 a 5 stelle alla determinata attività

> #### RFE10.
> Pulsante situato accanto al titolo, che aggiunge una segnalazione alla determinata attività

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

> #### RFE12.
> Numero di segnalazioni per attività

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
Pulsante di collegamento alle schermata di gestione utenti

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
> Spazio di inserimento per il numero di facce del dado

> #### RFE35.
> Pulsante avvia, che sceglie un numero casuale da 1 al numero di facce del dado e lo scrive su schermo

### FISCHIETTO
> [RFE33.](#rfe33)

> #### RFE36.
> Immagine di fischietto, che una volta premuta fa riprodurre il suono selezionato

> #### RFE37.
> Pulsante che apre un menu a tendina contenente altri suoni che è possibile selezionare

<center><img alt="Strumento FISCHIETTO" src="D1/img/RFE/fischietto.png" width="30%"/></center>

## CRONOMETRO
> [RFE33.](#rfe33)

> #### RFE38.
> Cronometro inizialmente azzerato, con segnati ore, minuti e secondi nella forma 00:00:00

> #### RFE39.
> Pulsante di avvio del cronometro. Una volta avviato quest’ultimo, il pulsante diventa pausa/avvio

> #### RFE40.
> Pulsante di stop e riavvio. Quando il cronometro è avviato l’utente lo usa per fermarlo. Quando il cronometro è stato fermato l’utente lo usa per riavviare il cronometro, per riportarlo a zero

### TIMER
> [RFE33.](#rfe33)
> [RFE37.](#rfe37)

> #### RFE41.
> imer inizialmente azzerato, con segnati ore, minuti e secondi nella forma 00:00:00. L’utente può impostare il tempo desiderato scorrendo sulle cifre.

> #### RFE42.
> Pulsante di avvio del timer. Una volta avviato quest’ultimo, il pulsante diventa pausa/avvio

> #### RFE43.
> Pulsante di stop. Quando il timer è avviato l’utente lo usa per fermarlo e il timer torna al tempo impostato precedentemente, in attesa di un nuovo avvio o di una modifica

> #### RFE44.
> Una volta finito il tempo del timer, viene riprodotto il suono selezionato

### Impostazioni SEGNA-PUNTI
> [RFE33.](#rfe33)

> #### RFE45.
> Tasto per aggiungere una nuova squadra, specificandone il nome in un campo testuale

> #### RFE46.
> Lista delle squadre già presenti, nella quale è possibile eliminare una squadra o modificarne il nome

> #### RFE47.
> Pulsante di avvio, che porta alla schermata [SEGNA-PUNTI](#segna-punti)

### SEGNA-PUNTI
> #### RFE48.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata [Impostazioni SEGNA-PUNTI](#impostazioni-segna-punti)

> #### RFE49.
> Lista scorribile delle squadre, indicante nome e numero di punti correnti

> #### RFE50.
> Pulsante di incremento e di decremento punto accanto per ogni squadra

### Impostazioni CREAZIONE SQUADRE
> [RFE33.](#rfe33)

> #### RFE51.
> Campo di inserimento del numero di giocatori

> #### RFE52.
> Campo di inserimento del numero di persone per squadra

> #### RFE53.
> Campo di inserimento del numero di squadre

> #### RFE54.
> Campo di inserimento dei nomi delle squadre

> #### RFE55.
> Pulsante che apre menu a tendina per scegliere metodo di divisione in squadre

> #### RFE56.
> Pulsante che reindirizza alla schermata [CREAZIONE SQUADRE](#creazione-squadre)

### CREAZIONE SQUADRE
> #### RFE57.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata [Impostazioni CREAZIONE SQADRE](#impostazioni-creazione-squadre)

> #### RFE58.
> Pulsante per passare alla prossima estrazione. A ogni estrazione viene visualizzato sullo schermo il nome della squadra di appartenenza

## Liste
### Visualizzato da [Autenticato](#autenticato) e [Amministratore](#amministratore)
> #### RFE59.
> Lista di liste create dall’utente

> #### RFE60.
> Cliccando sul nome di una lista, l’utente viene reindirizzato alla schermata "[Lista](#lista)" della relativa lista

> #### RFE61.
> Pulsante che aggiunge una lista, aprendo una finestra dove è presente un campo nel quale l’utente deve inserire il nome della nuova lista

## Lista
### Visualizzato da [Autenticato](#autenticato) e [Amministratore](#amministratore)
> [RFE3.](#rfe3)
> [RFE4.](#rfe4)
> [RFE5.](#rfe5)
> [RFE6.](#rfe6)
> [RFE7.](#rfe7)
> [RFE8.](#rfe8)
> [RFE9.](#rfe9)

> #### RFE62.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata [Liste](lista)

> #### RFE63.
> Nome della lista indicato

> #### RFE64.
> Lista di attività appartenenti alla lista sopraindicata

> #### RFE65.
> Pulsante che permette di esportare la lista con tutte le informazioni sulle attività, in formato PDF

## Attività
### Visualizzato da [Anonimo](#anonimo)
> #### RFE66.
> Pulsante di collegamento alla schermata precedente, ovvero il [Catalogo](#catalogo) o una [Lista](#lista)

> #### RFE67.
> Nome e immagine dell’attività

> #### RFE68.
> Descrizione dell’attività, valutazione media, fascia d'età consigliata, numero di giocatori e durata

> #### RFE69.
> Etichette caratterizzanti l'attività

### Visualizzato da [Autenticato](#autenticato)
> [RFE9.](#rfe9)
> [RFE66.](#rfe66)
> [RFE67.](#rfe67)
> [RFE68.](#rfe68)
> [RFE69.](#rfe69)

> #### RFE70.
> Pulsante che aggiunge l’attività alla lista predefinita "preferiti"

> #### RFE71.
> Pulsante che aggiunge l’attività a una lista. Si apre un menu a tendina con tutte le liste e l’utente può selezionare le liste a cui aggiungere l’attività stessa

> #### RFE72.
> Per le attività create dall’utente compare un pulsante che apre la schermata [Modifica attività](#modifica-attività)

<center><img alt="Attività" src="D1/img/RFE/attività.png" width="30%"/></center>

### Visualizzato da [Amministratore](#amministratore)
> [RFE62.](#rfe62)
> [RFE63.](#rfe63)
> [RFE64.](#rfe64)
> [RFE65.](#rfe65)
> [RFE66.](#rfe66)
> [RFE67.](#rfe67)

> #### RFE73.
> Pulsante che apre la schermata [Modifica attività](#modifica-attività)

## Modifica attività
### Visualizzato da [Amministratore](#amministratore)
> #### RFE74.
> Pulsante di collegamento alla schermata precedente, ovvero all’[Attività](#attività)

> #### RFE75.
> Campo di inserimento del titolo

> #### RFE76.
> Campo di inserimento della descrizione

> #### RFE77.
> Campo di inserimento della fascia di età

> #### RFE78.
> Campo di inserimento della durata

> #### RFE79.
> Campo di inserimento del numero di giocatori

> #### RFE80.
> Lista di etichette da selezionare

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

> #### RFE81.
> Campo di inserimento dell’autore dell’attività

## Tutorial
### Visualizzato da [Anonimi](#anonimi)
> #### RFE82.
> Per ogni schermata compare inizialmente una finestra contenente una breve spiegazione di utilizzo

> #### RFE83.
> Per ogni finestra c’è un campo contrassegnabile che impedisce alla finestra stessa di essere nuovamente visualizzata

## Gestione utenti
### Visualizzato da [Amministratore](#amministratore)
> [RFE2.](#rfe2)

> #### RFE84.
> Lista degli utenti che hanno effettuato l’accesso all’applicazione

> #### RFE85.
> Per ogni utente è presente un pulsante che, selezionato assume il colore verde e indica la promozione dell’utente stesso ad amministratore, mentre deselezionato assume il colore grigio e indica che l’utente stesso non è un amministratore

<div class="page-break"></div>
