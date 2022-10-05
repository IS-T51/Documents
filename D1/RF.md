# Requisiti funzionali del progetto
Nel presente capitolo vengono riportati i requisiti funzionali (RF) del sistema, assumendo che le tipologie di utente che hanno accesso all’app siano:

- [Anonimo](#anonimo)
- [Autenticato](#autenticato)
- [Amministratore](#amministratore)

---

Per ogni tipologia di utente, il sistema deve permettere di:

## Anonimo
### In presenza di connessione al server
> #### RF1.
> Aggiornare la copia locale del catalogo delle attività con quella presente sul server
> <sub>[¶O1](#o1)</sub>

> #### RF2.
> Effettuare l’accesso tramite le credenziali di autenticazione Google
> <sub>[¶O3](#o3)</sub>

### In assenza di connessione al server 
> #### RF3.
> Consultare la copia locale del catalogo di attività
> <sub>[¶O1](#o1)</sub>

> #### RF4.
> Filtrare il catalogo di attività
> <sub>[¶O1](#o1)</sub>

> #### RF5.
> Utilizzare i tool
> <sub>[¶O2](#o2)</sub>

## Autenticato
### In presenza di connessione al server
> [RF1.](#rf1)

> #### RF6.
> Creare nuove liste di attività
> <sub>[¶O3](#o3)</sub>

> #### RF7.
> Rimuovere una propria lista di attività
> <sub>[¶O3](#o3)</sub>

> #### RF8.
> Aggiungere un'attività in una lista di attività
> <sub>[¶O3](#o3)</sub>

> #### RF9.
> Rimuovere un'attività da una lista di attività
> <sub>[¶O3](#o3)</sub>

> #### RF10.
> Consultare le proprie liste di attività
> <sub>[¶O3](#o3)</sub>

> #### RF11.
> Valutare ogni attività con un punteggio numerico
> <sub>[¶O3](#o3)</sub>

> #### RF12.
> Inviare una segnalazione associata ad un'attività
> <sub>[¶O3](#o3)</sub>

> #### RF13.
> Proporre una nuova attività
> <sub>[¶O3](#o3)</sub>

> #### RF14.
> Modificare una propria attività proposta
> <sub>[¶O3](#o3)</sub>

### In assenza di connessione al server
> [RF3.](#rf3)
> [RF4.](#rf4)
> [RF5.](#rf5)

> #### RF15.
> Consultare le proprie liste di attività già sincronizzate localmente
> <sub>[¶O3](#o3)</sub>

## Amministratore
### In presenza di connessione al server
> [RF1.](#rf1)
> [RF6.](#rf6)
> [RF7.](#rf7)
> [RF8.](#rf8)
> [RF9.](#rf9)
> [RF10.](#rf10)

> #### RF16.
> Inserire nuove attività nel catalogo di attività
> <sub>[¶O4](#o4)</sub>

> #### RF17.
> Modificare attività presenti nel catalogo di attività
> <sub>[¶O4](#o4)</sub>

> #### RF18.
> Visualizzare la lista di utenti
> <sub>[¶O4](#o4)</sub>

> #### RF19.
> Modificare il ruolo di un utenti
> <sub>[¶O4](#o4)</sub>

### In assenza di connessione al server
per gli [Amministratori](#amministratore) i requisiti funzionali del sistema sono i medesimi di un qualsiasi altro [Autenticato](#autenticato)

--- 

All'interno dei seguenti strumenti, il sistema deve permettere di:

### DADI
> #### RF20.
> Creare liste di parole, colori e immagini
> <sub>[¶O2.1](#o21)</sub>

> #### RF21.
> Proporre ripetutamente un elemento casuale della lista
> <sub>[¶O2.1](#o21)</sub>

> #### RF22.
> Permettere la scelta fra riselezionare un elemento o escluderlo nelle successive proposte
> <sub>[¶O2.1](#o21)</sub>

### TIMER
> #### RF23.
> Scegliere un valore di partenza, far partire, mettere in pausa o fermare il timer
> <sub>[¶O2.2](#o22)</sub>

### CRONOMETRO
> #### RF24.
> Far partire, mettere in pausa o fermare il cronometro
> <sub>[¶O2.3](#o23)</sub>

> #### RF25.
> Salvare tempi parziali
> <sub>[¶O2.3](#o23)</sub>

### FISCHIETTO
> #### RF26.
> Selezionare un suono per il fischietto
> <sub>[¶O2.4](#o24)</sub>

> #### RF27.
> Selezionare un file presente sul dispositivo da usare come suono
> <sub>[¶O2.4](#o24)</sub>

> #### RF28.
> Riprodurre il suono per il fischietto selezionato
> <sub>[¶O2.4](#o24)</sub>

### SEGNAPUNTI
> #### RF29.
> Scegliere il numero di contatori
> <sub>[¶O2.5](#o25)</sub>

> #### RF30.
> Incrementare o decrementare ogni contatore separatamente
> <sub>[¶O2.5](#o25)</sub>

### SQUADRE
> #### RF31.
> Scegliere il numero di squadre
> <sub>[¶O2.6](#o26)</sub>

> #### RF32.
> Scegliere il numero di componenti per squadra
> <sub>[¶O2.6](#o26)</sub>

> #### RF33.
> Immettere il nome delle squadre
> <sub>[¶O2.6](#o26)</sub>

> #### RF34.
> Scegliere il numero di partecipanti
> <sub>[¶O2.6](#o26)</sub>

> #### RF35.
> Scegliere la metodologia di divisione (round-robin, casuale, per squadra)
> <sub>[¶O2.6](#o26)</sub>

> #### RF36.
> Iniziare la divisione in squadre
> <sub>[¶O2.6](#o26)</sub>
