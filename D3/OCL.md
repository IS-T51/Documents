
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
#### contatori : (String, int)[0...N]
#### **Invarianti**:
- nell'array contatori, la dimensione N assume al massimo il valore 99

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
|scegliSuono()| | |
|riproduciSuono()| | |

## **Creazione squadre**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |

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
