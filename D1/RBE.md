# Requisiti del back-end del progetto
Nel presente capitolo vengono riportati i requisiti del backend (RBE) del sistema, ovvero quei sistemi esterni con i quali il sistema deve interfacciarsi.

Il server deve:

> #### RBE1.
> interfacciarsi con le API di Google per verificare l'autenticazione dell'utente
> <sub>[¶O3](#o3)</sub>
>
> Attraverso questo sistema, sarà possibile autenticare gli utenti per permettere l’accesso a numerose funzionalità dell’applicativo esclusive. Il ruolo degli utenti autenticati verrà invece gestito all’interno dell’applicativo stesso.

> #### RBE2.
> utilizzare il servizio per la gestione di basi di dati offerto da MongoDB
>
> Attraverso i servizi offerti da MongoDB, sarà possibile distribuire la propria base di dati sulla rete, permettendo agli utenti di aggiornare catalogo di attività e di sincronizzare tra più dispositivi le liste create dall’utente autenticato.

![Requisiti back-end](D1/img/RBE/schema.png)

<div style="page-break-after: always;">~</div>

