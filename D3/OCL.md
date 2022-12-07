
# OCL
Nel presente capitolo vengono descritti i vincoli OCL delle classi.

## **Cronometro**
#### stato : Enum 
#### **Invarianti**:
- stato assume i valori “reset”, “run”, “pause”

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | ---|
|start()|**stato** deve essere in "reset"|**stato** assume valore "run"|
|stop()|**stato** deve essere in "run"|**stato** assume valore "pause"|
|riprendi()|**stato** deve essere in "pause"|**stato** assume valore "run"|
|ripristina()|**stato** deve essere in "pause"|**stato** assume valore "reset"|
|parziale()|**stato** deve essere in "run"|<ul><li>**stato** rimane al valore "run"</li><li>aggiunto tempo a lista **parziali**</li></ul>|
---

## **Segna punti**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
---
## **Timer**
#### stato : Enum
#### **Invarianti**
- stato assume i valori "reset", "run", "pause"

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|start()|**stato** deve essere in "reset"|**stato** assume valore "run"|
|riprendi()|**stato** deve essere in "pause"|**stato** assume valore "run"|
|stop()|**stato** deve essere in "run"|**stato** assume valore "pause"|
|annulla()|**stato** deve essere in "pause"|**stato** assume valore "reset"|
---

## **Dado**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|estrai() : Object|||
|cambiaModalità(riestrazione : bool)|||
|aggiungi(oggetto : Object)|

## **Fischietto**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|start()|il fischietto deve essere premuto|il suono viene riprodotto|
|stop()|il fischietto non deve essere premuto|nessun suono viene riprodotto|
|scegliSuono()||l'attributo suono viene impostato con il suono scelto|

## **Creazione squadre**
#### metodo : Enum
#### **Invarianti**:
- metodo assume i valori "Round robin", "Random", "Fill first" e "Balanced"

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|inserisciNumSquadre(numero : int)|numeroSquadre può essere al massimo 99|informazioni viene incrementato di 1|
|inserisciNumComponenti(numero : int)|numeroComponenti può essere al massimo 99|informazioni viene incrementato di 1|
|inserisciNumPartecipanti(numero : int)|numeroPartecipanti può essere al massimo 9801|informazioni viene incrementato di 1|
|scegliMetodo(metodo : Enum)||l'attributo metodo viene impostato con quello scelto|
|inserisciNome(nome : String)|la lunghezza dei nomi non deve eccedere i 99 caratteri|l'attributo nomi viene impostato con i nomi scelti|
|estrai()|<ul><li>informazioni deve essere uguale a 2 o 3</li><li>nel caso i tre valori: numeroSquadre, numeroPartecipanti e numeroComponenti non siano compatibili, verranno solamente considerati numeroPartecipanti e numeroSquadre.</ul>|<ul><li>se metodo assume il valore "Random" l'ordine delle squadre assegnate sarà completamente casuale</li><li>se metodo assume il valore "Round robin" l'assegnamento delle squadre sarà sequenziale</li><li>se il metodo assume il valore "Fill first" l'assegnamento avverrà per completamento delle squadre, ovvero riempiendo i posti di ogni squadra prima di procedere con l'assegnamento per la prossima</li><li>se il metodo assume il valore "Balanced" tutte le squadre dovranno avere lo stesso numero di partecipanti prima di procedere con gli assegnamenti</li><li>qualsiasi sia il metodo scelto, ogni volta che un partecipante viene assegnato ad una squadra il contatore di quella squadra viene incrementato di 1</li></ul>|

## **Utente**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |

## **Autenticazione**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |

## **Catalogo**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |

## **Lista di attività**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |

## **Attività**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |

## **Segnalazione**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|inviaSegnala(autore : Utente, attività : Attività, voto : String)|||

## **Valutazione**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|inviaValutazione(autore : Utente, attività : Attività, voto : String)

<div class="page-break"></div>
