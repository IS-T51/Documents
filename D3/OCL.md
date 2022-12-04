
# OCL
Nel presente capitolo vengono descritti i vincoli OCL delle classi.

## **Cronometro**
#### stato : Enum 
#### **Invarianti**:
- stato assume i valori “reset”, “run”, “pause”

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | ---|
|start()|**stato** deve essere in "reset"|**stato** assume valore "run"|
|riprendi()|**stato** deve essere in "pause"|**stato** assume valore "run"|
|ripristina()|**stato** deve essere in "pause"|**stato** assume valore "reset"|
|parziale()|**stato** deve essere in "run"|<ul><li>**stato** rimane al valore "run"</li><li>aggiunto tempo a lista **parziali**</li></ul>|

## **Segna punti**
#### contatori : (String, int)[0...N]
#### **Invarianti**:
- nell'array contatori, la dimensione N assume al massimo il valore 99

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |

## **Timer**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |

## **Dado**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |

## **Fischietto**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |

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

## **Valutazione**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |

<div class="page-break"></div>
