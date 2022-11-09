
# Definizione dei Componenti
In questa sezione vengono definiti i componenti.
> ### Gestione Catalogo
> #### *Motivazione*
> 
> #### *Spiegazione*
> Il componente gestisce le attività presenti nel catalogo, [...]

> ### Gestione Liste di Attività
> #### *Motivazione*
> [...]
> #### *Spiegazione*
> [...]

> ### Gestione Autenticazione
> #### *Motivazione*
> Dato il RF[...], al fine di permettere l'autenticazione di un utente nel sistema è stato identificato un componente Gestione Autenticazione, che si interfaccerà al servizio Google OAuth e provvederà a verificare che l'OAuth token fornito dall'utente sia valido.<br>
> Per soddisfare il RF[...], il presente gestionale permetterà agli utenti di effettuare il logout dal proprio account.
> #### *Spiegazione*
> Il componente permette all'utente di effettuare l'accesso nell'app, accedendo alle funzioni riservate agli autenticati.<br>
> Esso si occupa di inoltrare il token ricevuto dall'utente al servizio di Google OAuth per la validazione.<br>
> Qualora il token risultasse essere autentico, il componente si occuperà di recuperare le informazioni dell'account Google (lista completa delle informazioni acquisite al RNF[...]).<br>
> Su richiesta dell'utente, il componente permetterà il logout, rimuovendo i file personali salvati localmente.

> ### Gestione Utenti
> #### *Motivazione*
> [...]
> #### *Spiegazione*
> [...]

> ### Gestione Feedback
> #### *Motivazione*
> [...]
> #### *Spiegazione*
> [...]

> ## Strumenti
> #### *Motivazione*
> Dato il RF[...], è stato identificato un modulo Strumenti conentente tutti i componenti che si occupano del funzionamento dei tool offerti dal sistema.<br>
> Ogni tool è un sistema autonomo che permette all'utente di accedere a dei singoli servizi.
>> ### Dado
>> #### *Motivazione*
>> Per soddisfare il RF[...], il sistema deve prevedere un componente che si occupi della creazione di un dado personalizzato (un'urna di valori composti da immagini, numeri, colori o parole) e dell'estrazione di un valore casuale presente su di esso.
>> #### *Spiegazione*
>> Il componente Dado si occupa di raccogliere dall'utente gli elementi estraibili dal dado, di esprimere la volontà o meno di avere un ripescaggio e di permettere l'estrazione di un elemento.
>
>> ### Cronometro
>> #### *Motivazione*
>> [...]
>> #### *Spiegazione*
>> [...]
>
>> ### Timer
>> #### *Motivazione*
>> [...]
>> #### *Spiegazione*
>> [...]
>
>> ### Fischietto
>> #### *Motivazione*
>> [...]
>> #### *Spiegazione*
>> [...]
>
>> ### Creazione Squadre
>> #### *Motivazione*
>> [...]
>> #### *Spiegazione*
>> [...]
>
>> ### Segna-Punti
>> #### *Motivazione*
>> [...]
>> #### *Spiegazione*
>> [...]

<center><img alt="Diagramma delle Componenti" src="D2/img/CPD/component-diagram.png" width="100%"/></center>

<div class="page-break"></div>
