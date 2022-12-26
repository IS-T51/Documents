
# Codice in Object Constraint Language
In questo capitolo è descritta in modo formale la logica prevista nell’ambito di alcune operazioni di alcune classi. Tale logica viene descritta in Object Constraint Language (OCL) (https://www.omg.org/spec/OCL/2.4/PDF) perché tali concetti non sono esprimibili in nessun altro modo formale nel contesto di UML.

## **Cronometro**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | ---|
|start()|**stato** deve essere in "reset" o in "pause"|**stato** assume valore "run"|
|pause()|**stato** deve essere in "run"|**stato** assume valore "pause"|
|stop()|**stato** deve essere in "pause"|<ul><li>**stato** assume valore "reset"</li><li>**parziali** è una lista vuota</li></ul>|
|parziale()|**stato** deve essere in "run"|<ul><li>**stato** rimane al valore "run"</li><li>aggiunto tempo a lista **parziali**</li></ul>|

```js
context Cronometro::start()
pre: (self.stato = "reset") OR (self.stato = "pause")
post: self.stato = "run"
```
```js
context Cronometro::pause()
pre: self.stato = "run"
post: self.stato = "pause"
```
```js
context Cronometro::stop()
pre: self.stato = "pause"
post: (self.stato = "reset") AND (self.parziali->isEmpty())
```
```js
context Cronometro::parziale()
pre: self.stato = "run"
post: (self.stato = "run") AND (self.parziali = self.parziali@pre->append(self.tempo))
```

---

## **Segna-Punti**

#### **Invarianti**:
#### contatori : Tuple{nome : String, punteggio : int}[0..N]
- contatori contiente al più 99 elementi
- il campo nome di ogni elemento di contatori deve avere tra 0 (escluso) e 99 (incluso) caratteri
- il campo punteggio di ogni elemento di contatori deve essere compreso tra -500 e 500

```js
context Segna-Punti inv :
self.contatori->size() <= 99
```
```js
context Segna-Punti inv :
self.contatori->forAll(c : Tuple{nome : String, punteggio : int} | 0 < c.nome.size() AND c.nome.size <= 99)
```
```js
context Segna-Punti inv :
self.contatori->forAll(c : Tuple{nome : String, punteggio : int} | -500 <= c.punteggio AND c.punteggio <= 99)
```

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|aggiungiContatore(indice : int)|<ul><li>Il nome non deve essere vuoto e non può eccedere i 99 caratteri</li><li>il numero di contatori può essere al massimo 98</li><ul>|la sequenza di contatori deve avere come ultimo elemento un contatore con il nome scelto e punteggio pari a 0|
|incrementa(indice : int)|il contatore all'indice scelto deve avere punteggio minore di 500|il punteggio del contatore alla posizione scelta viene incrementato di 1|
|decrementa(indice : int)|il contatore all'indice scelto deve avere punteggio maggiore di -500|il punteggio del contatore alla posizione scelta viene decrementato di 1|

```js
context Segna-Punti::aggiungiContatore(indice : int)
pre: (0 < nome.size() AND nome.size() <= 99) AND (self.contatori->size() < 99)
post: self.contatori = self.contator@pre->append(Tuple{nome : String = nome, punteggio : int = 0})
```
```js
context Segna-Punti::incrementa(indice : int)
pre: self.contatori->at(indice) < 500
post: (self.contatori->at(indice)).punteggio = (self.contatori@pre->at(indice)).punteggio + 1
```
```js
context Segna-Punti::decrementa(indice : int)
pre: self.contatori->at(indice) > -500
post: (self.contatori->at(indice)).punteggio = (self.contatori@pre->at(indice)).punteggio - 1
```
---

## **Timer**

#### **Invarianti**:
#### suono : Suono
- il suono non può essere in riproduzione se il timer non è scaduto
```js
context Timer inv :
self.suono.inRiproduzione implies self.stato = "run" AND self.tempo.ore = 0 AND self.tempo.minuti = 0 AND self.tempo.secondi = 0 AND self.tempo.centesimi = 0
```

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|start()|**stato** deve essere in "reset" o in "pause"|**stato** assume valore "run"|
|pause()|**stato** deve essere in "run"|**stato** assume valore "pause"|
|stop()|**stato** deve essere in "pause"|**stato** assume valore "reset"|
|imposta(ore : int, minuti : int, secondi : int)| il tempo fonito deve essere valido | **tempo** assume il valore del tempo fornito|
|spegni()|**self.suono.inRiproduzione** deve essere true|**self.suono.inRiproduzione** deve essere false e **stato** dev'essere reset|

```js
context Timer::start()
pre: (self.stato = "reset") OR (self.stato = "pause")
post: self.stato = "run"
```
```js
context Timer::pause()
pre: self.stato = "run"
post: self.stato = "pause"
```
```js
context Timer::stop()
pre: self.stato = "pause"
post: self.stato = "reset"
```
```js
context Timer::imposta(ore : int, minuti : int, secondi : int)
pre: 0<=ore AND 0<=minuti AND minuti<60 AND 0<=secondi AND secondi<60
post: self.tempo = tempo
```
```js
context Timer::spegni()
pre: self.suono.inRiproduzione
post: (NOT self.suono.inRiproduzione) AND stato = reset
```

---

## **Dado**

#### **Invarianti**:
#### dimensione : int
- La dimensione deve essere compresa tra 0 e 9.999 inclusi
#### campione : Faccia[0..N]
- La dimensione del campione deve essere al più 9.999 incluso
- ogni elemento del campione deve avere tipo corrispondente al tipo del dado
#### estremoInferiore : int
- L'estremo inferiore deve essere compreso tra 0 e 9.999 inclusi
#### passo : int
- Il passo deve essere compreso tra 1 e 9.999 inclusi
#### estrazioni : int
- Il numero di estrazioni effettuate deve essere non negativo

```js
context Dado inv :
0<=self.dimensione AND self.dimensione<=9.999 AND self.campione->size()<=9.999 AND self.campione.forALL(f : Faccia | f.tipo = self.tipo)
```
```js
0<=self.estremoInferiore AND self.estremoInferiore<=9.999 AND 1<=self.passo AND self.passo<=9.999
AND 0<=self.estrazioni
```

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|scegliModalità(reimmissione : bool)| non deve essere stata effettuata ancora alcuna estrazione |l'attributo reimmissione viene impostato al valore selezionato|
|scegliTipo(tipo : tipoDado)|<ul><li>non deve essere stata effettuata ancora alcuna estrazione</li><li>il campione dev'essere vuoto</li></ul>|l'attributo tipo viene impostato al valore selezionato|
| scegliDimensione(dim : int)|<ul><li>non può essere stata effettuata ancora alcuna estrazione</li><li>il valore fornito dev'essere una dimensione valida</li><li>il campione dev'essere vuoto</li></ul>|l'attributo dimensione viene impostato al valore selezionato|
|scegliEstremoPasso(estremo : int, passo : int)|<ul><li>non deve essere stata effettuata ancora alcuna estrazione</li><li>i valori forniti devono essere validi</li><li>il tipo del dado dev'essere "numeri"</li><li>il campione dev'essere vuoto</li></ul>|<ul><li>gli attributi estremoInferiore e passo vengono impostati ai valori selezionati</li><li>il campione viene riempitocon un numero di valori pari a dimensione che partono da estremoInferiore con scarto di passo tra due elementi consecutivi</li></ul>|
|aggiungiElemento(elemento :  Faccia)|<ul><li>non deve essere stata effettuata ancora alcuna estrazione</li><li>l'elemento fornito dev'essere del tipo del dado</li><li>il tipo del dado dev'essere diverso da "numeri"</li><li>la dimensione del campione dev'essere inferiore alla dimensione impostata</li></ul>|Il campione deve avere come ultimo elemento l'elemento fornito|
|estrai() : Faccia|il campione non dev'essere vuoto|<ul><li>il risultato è un elemento presente nel campione prima della chiamata al metodo</li><li>estrazioni viene incrementato di 1</li><li>se reimmissione è false, un'occorrenza del risultato viene rimossa dal campione</li></ul>|

```js
context Dado::scegliModalità(reimmissione : bool)
pre: self.estrazioni = 0
post: self.reimmissione = reimmissione
```
```js
context Dado::scegliTipo(tipo : tipoDado)
pre: self.estrazioni = 0 AND self.campione->isEmpty()
post: self.tipo = tipo
```
```js
context Dado::scegliDimensione(dim : int)
pre: self.estrazioni = 0 AND 0<dim AND dim<=9.999 AND self.campione->isEmpty()
post: self.dimensione = dim
```
```js
context Dado::scegliEstremoPasso(estremo : int, passo : int)
pre: self.estrazioni = 0 AND self.campione->isEmpty() AND 0<estremo AND estremo<=9.999 AND 1<passo AND passo<=9.99
post: self.estremoInferiore = estremo AND self.passo = passo AND self.campione->size() = dimensione AND self.campione->first().numero = estremoInferiore AND self.campione->forAll(f:Faccia | self.campione->count(f)=1 AND let i=self.campione->indexOf(f) in if i>1 then f.numero=passo+self.campione->at(i-1) endif)
```
```js
context Dado::aggiungiElemento(elemento :  Faccia)
pre: self.estrazioni = 0 AND elemento.tipo = self.tipo AND self.tipo <> "numeri" AND self.campione->size() < dimensione
post: self.campione = self.campione@pre->append(elemento)
```
```js
context Dado::estrai() : Faccia
pre: self.campione->notEmpty()
post: self.campione@pre->includes(result) AND self.estrazioni = self.estrazione@pre+1 if (NOT reimmissione) then (self.campione->size() = self.campione@pre->size() AND self.campione->forAll(f:Faccia | let c=self.campione@pre->count(f) in if f<>result then self.campione->count(f)=c else self.campione->count(f)=c-1 endif)) endif
```

---
## **Suono**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|start()|premuto deve assumere il valore "True"|il suono è in riproduzione|
|stop()|premuto deve assumere il valore "False"|il suono non è in riproduzione|
|scegliSuono()||lla sorgente del suono è quella scelta|


```js
context Fischietto::start()
pre: NOT self.premuto
post: self.suono.inRiproduzione = true
```
```js
context Fischietto::stop()
pre: self.premuto
post: self.suono.inRiproduzione = false
```
```js
context Fischietto::scegliSuono(sorgente : URL)
post: self.suono.sorgente = sorgente
```

## **Creazione Squadre**
#### metodo : Enum
#### **Invarianti**:
- metodo assume i valori "Round robin", "Random", "Fill first" e "Balanced"

```js
context Creazione Squadre inv :
(stato = "Round robin") OR (stato = "Random") OR (stato = "Fill first") OR (stato = "Balanced")
numeroSquadre <= 99
numeroComponeti <= 99
numeroPartecipanti <= 9801
```

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|inserisciNumSquadre(numero : int)|numeroSquadre deve essere minore di 99|informazioni viene incrementato di 1|
|inserisciNumComponenti(numero : int)|numeroComponenti deve essere minore di 99|informazioni viene incrementato di 1|
|inserisciNumPartecipanti(numero : int)|numeroPartecipanti deve essere minore di 9801|informazioni viene incrementato di 1|
|scegliMetodo(metodo : Enum)||l'attributo metodo viene impostato con quello scelto|
|inserisciNome(nome : String)|la lunghezza dei nomi non deve eccedere i 99 caratteri|l'attributo nomi viene impostato con i nomi scelti|
|estrai()|<ul><li>informazioni deve essere uguale a 2 o 3</li><li>nel caso i tre valori: numeroSquadre, numeroPartecipanti e numeroComponenti non siano compatibili, verranno solamente considerati numeroPartecipanti e numeroSquadre.</ul>|<ul><li>se metodo assume il valore "Random" l'ordine delle squadre assegnate sarà completamente casuale</li><li>se metodo assume il valore "Round robin" l'assegnamento delle squadre sarà sequenziale</li><li>se il metodo assume il valore "Fill first" l'assegnamento avverrà per completamento delle squadre, ovvero riempiendo i posti di ogni squadra prima di procedere con l'assegnamento per la prossima</li><li>se il metodo assume il valore "Balanced" tutte le squadre dovranno avere lo stesso numero di partecipanti prima di procedere con gli assegnamenti</li><li>qualsiasi sia il metodo scelto, ogni volta che un partecipante viene assegnato ad una squadra il contatore di quella squadra viene incrementato di 1</li></ul>|
---

## **Utente**
#### ruolo : Enum
#### **Invarianti**:
- ruolo assume i valori "Amministratore" e "Base"
```js
context Utente inv :
(ruolo = "Amministratore") OR (ruolo = "Base")
```

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|cambiaRuolo(utente, promotore, nuovoRuolo)|<ul><li>un amministratore può essere declassato a utente comune unicamente dall’amministratore che lo ha promosso</li><li>se l'attributo ruolo dell'utente ha il valore "Amministratore", il suo ruolo può essere cambiato solo se promotore è diverso dall'attributo promossoDa dell'utente</li><li>il promotore deve avere ruolo "Amministratore"</li></ul>|l'attributo ruolo dell'utente assume il valore di nuovoRuolo|
---

## **Autenticazione**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|verificaOAuth()|||
|generaToken()|||
|ottieniUtente() : Utente|||
|logout()|||
---

// TODO: @teopan21

---
## **Catalogo**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|aggiornaCatalogo() : Attività[0...N]||l'attributo ultimoAggiornamento assume il valore della data corrente|
|filtra(cerca : String, etichette : Etichette[0...N]) : Attività[0...N]|<ul><li>nella barra di ricerca del titolo non si possono inserire più di 20 caratteri</li><li>i due valori della durata media sono compresi tra 0 e 999, sono interi e il primo è minore del secondo</li><li>il numero di partecipanti non può superare 99</li></ul>|il catalogo viene filtrato secondo le etichette previste|
|creaAttività(attività : Attività)|<ul><li>la descrizione non può superare i 2000 caratteri</li><li>i due valori della durata media sono compresi tra 0 e 999, sono interi e il primo è minore del secondo</li><li>il numero di partecipanti non può superare 99</li><li>il titolo non può superare i 20 caratteri di lunghezza</li></ul>|viene aggiunta una nuova attività al catalogo|
---

```js
context Catalogo::aggiornaCatalogo()
post: self.ultimoAggiornamento = Data.now()
```
// TODO: @teopan21

---
## **Lista di Attività**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|creaLista() : listaAttivita|<ul><li>il nome della lista di attività non può superare i 20 caratteri di lunghezza</li><li>un utente non può creare più di 99 liste di attività</li><li>il nome della lista di attività non può essere uguale al nome di un'altra lista già presente</li><li>il nome della lista di attività non può essere nessuno</li></ul>|viene creata una nuova lista di attività|
|aggiungiAttività(attività : Attività)|il numero di attività in una lista non può superare 9999|l'attività scelta viene aggiunta alla lista|
|esporta(formato : String) : File||la lista viene esportata in formato pdf o json|
|eliminaAttività(indice : int)||l'attività con l'indice scelto viene rimossa dalla lista|
---

// TODO: @teopan21

---
## **Attività**

// TODO: @teopan21 Invarianti

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|modifica(attivitàModificata : Attività)|<ul><li>la descrizione non può superare i 2000 caratteri</li><li>i due valori della durata media sono compresi tra 0 e 999, sono interi e il primo è minore del secondo</li><li>il numero di partecipanti non può superare 99</li><li>il titolo non può superare i 20 caratteri di lunghezza</li></ul>|<ul><li>tutti gli attributi assumono il valore dell'attività modificata</li><li>l'attributo ultimaModifica assume il valore della data corrente</li></ul>|
---

## **Segnalazione**

// TODO: @teopan21 invarianti

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|inviaSegnala(autore : Utente, attività : Attività, voto : String)|l'attributo messaggio non può superare i 500 caratteri di lunghezza|viene aggiunta una segnalazione per l'attività scelta|
---

## **Valutazione**

// TODO: @teopan21 invarianti

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
|inviaValutazione(autore : Utente, attività : Attività, voto : String)|il voto inserito deve essere un numero decimale compreso tra 0 e 5, con scarto di 0.5|<ul><li>viene aggiunta la valutazione all'attività scelta</li><li>cambia la media di voti dell'attività scelta</li>|
---


## **Feedback**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
---

## **GestoreDatiOffline**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
---

## **MongoDB**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
---

## **Info**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
---


## **Filtro**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
---


## **Faccia**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
---


## **Colore**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
---


## **URL**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
---

## **Data**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
---

## **Time**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
---

## **Etichetta**

| Metodo | Precondizioni | Postcondizioni |
| --- | --- | --- |
---

<div class="page-break"></div>
