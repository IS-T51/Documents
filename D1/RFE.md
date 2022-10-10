# Requisiti del front-end del progetto
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

![Catalogo](D1/img/RFE/catalogo.png)

![Catalogo con filtro](D1/img/RFE/catalogo-filtri.png)

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
> Pulsante situato accanto al titolo, che aggiunge un like alla determinata attività

> #### RFE10.
> Pulsante situato accanto al titolo, che aggiunge una segnalazione alla determinata attività

### Visualizzato da [Amministratore](#amministratore)
> [RFE2.](#rfe2)
> [RFE2.](#rfe3)
> [RFE2.](#rfe4)
> [RFE2.](#rfe5)
> [RFE2.](#rfe6)
> [RFE7.](#rfe7)

> #### RFE11.
> Pulsante di modifica dell’attività

> #### RFE12.
> Numero di segnalazioni per attività

## Menu
### Visualizzato da [Anonimo](#anonimo)
> #### RFE13.
> Pulsante di collegamento alla schermata precedentemente utilizzata

> #### RFE14.
> Pallino che assume il colore grigio se l’utente non è connesso al    server, verde altrimenti

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

> #### RFE21.
> Attività giornaliera presa casualmente dal catalogo

![Menu visualizzato da Anonimo](D1/img/RFE/menu-anonimo.png)

## Menu
### Visualizzato da [Autenticato](#autenticato) e da [Amministratore](#amministratore)
> [RFE13.](#rfe13)
> [RFE14.](#rfe14)
> [RFE15.](#rfe15)
> [RFE16.](#rfe16)

> #### RFE22.
> Pulsante di collegamento alla schermata dei preferiti

> #### RFE23.
> Pulsante di collegamento alla schermata delle liste

> #### RFE24.
> Pulsante di collegamento alla schermata di proposta attività

> #### RFE25.
> Foto profilo dell’account

![Menu visualizzato da Autenticato](D1/img/RFE/menu-autenticato.png)

## Strumenti
> [RFE2.](#rfe2)

> #### RFE26.
> Pulsante di collegamento allo strumento [DADO](#dado)

> #### RFE27.
> Pulsante di collegamento allo strumento [FISCHIETTO](#fischietto)

> #### RFE28.
> Pulsante di collegamento allo strumento [CRONOMETRO](#cronometro)

> #### RFE29.
> Pulsante di collegamento allo strumento [TIMER](#timer)

> #### RFE30.
> Pulsante di collegamento allo strumento [SEGNA-PUNTI](#segna-punti)

> #### RFE31.
> Pulsante di collegamento allo strumento di [CREAZIONE SQUADRE](#creazione-squadre)

### DADO
> #### RFE32.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata strumenti

> #### RFE33.
> Spazio di inserimento per il numero di facce del dado

> #### RFE34.
> Pulsante avvia, che sceglie un numero casuale da 1 al numero di facce del dado e lo scrive su schermo

### FISCHIETTO
> [RFE32.](#rfe32)

> #### RFE35.
> Immagine di fischietto, che una volta premuta fa riprodurre il suono selezionato

> #### RFE36.
> Pulsante che apre un menu a tendina contenente altri suoni che è possibile selezionare

![Strumento FISCHIETTO](D1/img/RFE/fischietto.png)

## CRONOMETRO
> [RFE32.](#rfe32)

> #### RFE37.
> Cronometro inizialmente azzerato, con segnati ore, minuti e secondi nella forma 00:00:00

> #### RFE38.
> Pulsante di avvio del cronometro. Una volta avviato quest’ultimo, il pulsante diventa pausa/avvio

> #### RFE39.
> Pulsante di stop e riavvio. Quando il cronometro è avviato l’utente lo usa per fermarlo. Quando il cronometro è stato fermato l’utente lo usa per riavviare il cronometro, per riportarlo a zero

### TIMER
> [RFE32.](#rfe32)
> [RFE36.](#rfe36)

> #### RFE40.
> imer inizialmente azzerato, con segnati ore, minuti e secondi nella forma 00:00:00. L’utente può impostare il tempo desiderato scorrendo sulle cifre.

> #### RFE41.
> Pulsante di avvio del timer. Una volta avviato quest’ultimo, il pulsante diventa pausa/avvio

> #### RFE42.
> Pulsante di stop. Quando il timer è avviato l’utente lo usa per fermarlo e il timer torna al tempo impostato precedentemente, in attesa di un nuovo avvio o di una modifica

> #### RFE43.
> Una volta finito il tempo del timer, viene riprodotto il suono selezionato

### Impostazioni SEGNA-PUNTI
> [RFE32.](#rfe32)

> #### RFE44.
> Spazio di inserimento per il numero di squadre

> #### RFE45.
> Una volta inserito il numero delle squadre compare una lista di campi da compilare, che sono tanti quanti il numero delle squadre, e dove l’utente può inserire i nomi manualmente. Alternativamente c’è un pulsante default, che assegna i numeri da 1 al numero delle squadre ai campi

> #### RFE46.
> Pulsante di avvio, che porta alla schermata "Segna-punti"

### SEGNA-PUNTI
> #### RFE47.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata "Impostazioni segna-punti"

> #### RFE48.
> Lista scorribile delle squadre, con indicato nome e numero di punti fino a quel momento

> #### RFE49.
> Pulsante di aggiunta punto accanto a ogni squadra

### Impostazioni CREAZIONE SQUADRE
> [RFE32.](#rfe32)

> #### RFE50.
> Campo di inserimento del numero di giocatori

> #### RFE51.
> Campo di inserimento del numero di persone per squadra

> #### RFE52.
> Campo di inserimento del numero di squadre

> #### RFE53.
> Campo di inserimento dei nomi delle squadre

> #### RFE54.
> Pulsante che apre menu a tendina per scegliere metodo di divisione in squadre

> #### RFE55.
> Pulsante che reindirizza alla schermata "[CREAZIONE SQUADRE](#creazione-squadre)"

### CREAZIONE SQUADRE
> #### RFE56.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata "[Impostazioni CREAZIONE SQADRE](#impostazioni-creazione-squadre)"

> #### RFE57.
> Pulsante per passare alla prossima estrazione. A ogni estrazione viene visualizzato sullo schermo il nome della squadra di appartenenza

## Liste
### Visualizzato da [Autenticato](#autenticato) e [Amministratore](#amministratore)
> #### RFE58.
> Lista di liste create dall’utente

> #### RFE59.
> Cliccando sul nome di una lista, l’utente viene reindirizzato alla schermata "[Lista](#lista)" della relativa lista

> #### RFE60.
> Pulsante che aggiunge una lista, aprendo una finestra dove è presente un campo nel quale l’utente deve inserire il nome della nuova lista

## Lista
### Visualizzato da [Autenticato](#autenticato) e [Amministratore](#amministratore)
> [RFE3.](#rfe3)
> [RFE4.](#rfe4)
> [RFE5.](#rfe5)
> [RFE6.](#rfe6)
> [RFE7.](#rfe7)

> #### RFE61.
> Pulsante di collegamento alla schermata precedente, ovvero la schermata "[Liste](lista)"

> #### RFE62.
> Nome della lista indicato

> #### RFE63.
> Lista di attività appartenenti alla lista sopraindicata

## Attività
### Visualizzato da [Anonimo](#anonimo)
> #### RFE64.
> Pulsante di collegamento alla schermata precedente, ovvero il catalogo, i preferiti o una lista

> #### RFE65.
> Nome e immagine dell’attività

> #### RFE66.
> Descrizione dell’attività, età media consigliata, numero di giocatori e durata

> #### RFE67.
> Tag caratterizzanti l'attività

### Visualizzato da [Anonimo](#autenticato)
> [RFE64.](#rfe64)
> [RFE65.](#rfe65)
> [RFE66.](#rfe66)
> [RFE67.](#rfe67)

> #### RFE68.
> Pulsante che aggiunge l’attività ai preferiti

> #### RFE69.
> Pulsante che aggiunge l’attività a una lista. Si apre un menu a tendina con tutte le liste e l’utente può selezionare le liste a cui aggiungere l’attività stessa

![Attività](D1/img/RFE/attività.png)

### Visualizzato da [Amministratore](#amministratore)
> [RFE64.](#rfe64)
> [RFE65.](#rfe65)
> [RFE66.](#rfe66)
> [RFE67.](#rfe67)
> [RFE67.](#rfe68)
> [RFE67.](#rfe69)

> #### RFE70.
> Pulsante che apre la schermata “[Modifica](#modifica)”

## Modifica
### Visualizzato da [Amministratore](#amministratore)
> #### RFE71.
> Pulsante di collegamento alla schermata precedente, ovvero all’[attività](#attività)

> #### RFE72.
> Campo di inserimento del titolo

> #### RFE73.
> Campo di inserimento della descrizione

> #### RFE74.
> Campo di inserimento dell’età media consigliata

> #### RFE75.
> Campo di inserimento della durata

> #### RFE76.
> Campo di inserimento del numero di giocatori

> #### RFE77.
> Lista di tag da selezionare

## Proposte attività
### Visualizzato da [Autenticato](#autenticato) e da [Amministratore](#amministratore)
> [RFE64.](#rfe64)

> #### RFE78.
> Campo di inserimento dell’autore dell’attività

## Tutorial
> #### RFE79.
> Per ogni schermata compare inizialmente una finestra contenente una breve spiegazione di utilizzo

> #### RFE80.
> Per ogni finestra c’è un campo contrassegnabile che impedisce alla finestra stessa di essere nuovamente visualizzata

<div style="page-break-after: always;">~</div>

