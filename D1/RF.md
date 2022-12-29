
# 2. Requisiti funzionali del progetto
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
> Consultare il catalogo di attività
> <sub>[¶O3](#o3)</sub>

> #### RF3.
> Filtrare il catalogo di attività
> <sub>[¶O1](#o1)</sub>

> #### RF4.
> Utilizzare i tool
> <sub>[¶O2](#o2)</sub>

> #### RF5.
> Effettuare l’accesso tramite le credenziali di autenticazione Google
> <sub>[¶O3](#o3)</sub>

### In assenza di connessione al server
> [RF2.](#rf2)
> [RF3.](#rf3)
> [RF4.](#rf4)

> #### RF6.
> Consultare la copia locale del catalogo di attività
> <sub>[¶O1](#o1)</sub>

## Autenticato
### In presenza di connessione al server
> [RF1.](#rf1)
> [RF2.](#rf2)
> [RF3.](#rf3)
> [RF4.](#rf4)

> #### RF7.
> Creare nuove liste di attività
> <sub>[¶O3](#o3)</sub>

> #### RF8.
> Rimuovere una propria lista di attività
> <sub>[¶O3](#o3)</sub>

> #### RF9.
> Aggiungere un'attività in una lista di attività
> <sub>[¶O3](#o3)</sub>

> #### RF10.
> Rimuovere un'attività da una lista di attività
> <sub>[¶O3](#o3)</sub>

> #### RF11.
> Consultare le proprie liste di attività
> <sub>[¶O3](#o3)</sub>

> #### RF12.
> Valutare ogni attività con un punteggio numerico
> <sub>[¶O3](#o3)</sub>

> #### RF13.
> Inviare una segnalazione associata ad un'attività
> <sub>[¶O3](#o3)</sub>

> #### RF14.
> Proporre una nuova attività
> <sub>[¶O3](#o3)</sub>

> #### RF15.
> Modificare una propria attività proposta
> <sub>[¶O3](#o3)</sub>

> #### RF16.
> Effettuare il logout
> <sub>[¶O3](#o3)</sub>

### In assenza di connessione al server
> [RF2.](#rf2)
> [RF3.](#rf3)
> [RF4.](#rf4)
> [RF6.](#rf6)

> #### RF17.
> Consultare le proprie liste di attività già sincronizzate localmente
> <sub>[¶O3](#o3)</sub>

## Amministratore
### In presenza di connessione al server
> [RF1.](#rf1)
> [RF2.](#rf2)
> [RF3.](#rf3)
> [RF4.](#rf4)
> [RF7.](#rf7)
> [RF8.](#rf8)
> [RF9.](#rf9)
> [RF10.](#rf10)
> [RF11.](#rf11)
> [RF12.](#rf12)
> [RF16.](#rf16)
> [RF17.](#rf17)

> #### RF18.
> Inserire nuove attività nel catalogo di attività
> <sub>[¶O4](#o4)</sub>

> #### RF19.
> Modificare attività presenti nel catalogo di attività
> <sub>[¶O4](#o4)</sub>

> #### RF20.
> Visualizzare la lista di utenti
> <sub>[¶O4](#o4)</sub>

> #### RF21.
> Modificare il ruolo di un utenti
> <sub>[¶O4](#o4)</sub>

> #### RF22.
> Visualizzare l'elenco delle segnalazioni alle attività
> <sub>[¶O4](#o4)</sub>

### In assenza di connessione al server
per gli [Amministratori](#amministratore) i requisiti funzionali del sistema sono i medesimi di un qualsiasi altro [Autenticato](#autenticato)

---

All'interno dei seguenti strumenti, il sistema deve permettere di:

### DADI
> #### RF23.
> Creare liste di parole, colori e immagini
> <sub>[¶O2.1](#o21)</sub>

> #### RF24.
> Proporre ripetutamente un elemento casuale della lista
> <sub>[¶O2.1](#o21)</sub>

> #### RF25.
> Permettere la scelta fra riselezionare un elemento o escluderlo nelle successive proposte
> <sub>[¶O2.1](#o21)</sub>

### TIMER
> [RF29.](#rf29)
> [RF31.](#rf31)

> #### RF26.
> Scegliere un valore di partenza, far partire, mettere in pausa o fermare il timer
> <sub>[¶O2.2](#o22)</sub>

### CRONOMETRO
> #### RF27.
> Far partire, mettere in pausa o fermare il cronometro
> <sub>[¶O2.3](#o23)</sub>

> #### RF28.
> Salvare tempi parziali
> <sub>[¶O2.3](#o23)</sub>

### FISCHIETTO
> #### RF29.
> Selezionare un suono
> <sub>[¶O2.4](#o24)</sub>

> #### RF30.
> Selezionare un file presente sul dispositivo da usare come suono
> <sub>[¶O2.4](#o24)</sub>

> #### RF31.
> Riprodurre il suono selezionato
> <sub>[¶O2.4](#o24)</sub>

### SEGNA-PUNTI
> #### RF32.
> Scegliere il numero di contatori
> <sub>[¶O2.5](#o25)</sub>

> #### RF33.
> Incrementare o decrementare ogni contatore separatamente
> <sub>[¶O2.5](#o25)</sub>

### CREAZIONE SQUADRE
> #### RF34.
> Scegliere il numero di squadre
> <sub>[¶O2.6](#o26)</sub>

> #### RF35.
> Scegliere il numero di componenti per squadra
> <sub>[¶O2.6](#o26)</sub>

> #### RF36.
> Immettere il nome delle squadre
> <sub>[¶O2.6](#o26)</sub>

> #### RF37.
> Scegliere il numero di partecipanti
> <sub>[¶O2.6](#o26)</sub>

> #### RF38.
> Scegliere la metodologia di divisione (round-robin, casuale, per squadra)
> <sub>[¶O2.6](#o26)</sub>

> #### RF39.
> Iniziare la divisione, estraendo le squadre sequenzialmente
> <sub>[¶O2.6](#o26)</sub>

<div class="page-break"></div>
