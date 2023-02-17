
# 2. Application Implementation and Documentation
Nelle sezioni precedenti abbiamo identificato le varie features che devono essere implementate
per la nostra applicazione con uno schema preciso di come i nostri utenti finali possono utilizzarle nel
suo flusso applicativo.
Abbiamo individuato un sottoiensieme variegto di queste features, sia tra le API sia tra le funzionalità delegate al solo frontend, e lo abbiamo sviluppato nella nostra applicazione; le sezioni seguenti illustreranno le funzionalità scelte e la loro implementazione.

Il server è stato sviluppato utilizzando NodeJS e OAS3-Tools, il client è stato sviluppato utilizzando Bootstrap e JQuery, mentre per la gestione dei dati abbiamo fatto affidamento a MongoDB.

## 2.1 Project Structure
### Server
Il codice del server è contenuto nella repository "animati-server". La sua struttura è la seguente:
> **api/** - *cartella per la configurazione delle api*
>> **openapi.yaml** - *file di configurazione di OpenAPI per la generazione automatica delle route per le API e per la documentazione delle API tramite Swagger**
>
> **index.js** - *file di avvio del server, responsabile dell'inizializzazione del server http e della connessione iniziale al database*
>
> **package.json** - *file di configurazione del progetto NodeJS*
>
> **vercel.json** - *file di configurazione di Vercel, responsabile del deployment*
>
> **src** - *cartella contenente il codice in esecuzione sul server, le API, i test e tutta la logica del sistema*
>
>> **app.js** - *file principale del server, responsabile dell'inizializzazione e dell'orchestrazione delle varie componenti*
>>
>> **controllers/** - *cartella conenente i controllori per le richieste in ingresso*
>>> **\<componente\>.js** - *files responsabili per il collegamento fra route e services*
>>
>> **models/** - *cartella contenente la definizione dei modelli usati dalla libreria Mongoose per interfacciarsi con MongoDB*
>>>  **\<modello\>.js**- *file contenente la definizione del modello*
>>
>> **schema/** - *cartella contenente la definizione delle strutture dati usate durante la definizione dei modelli*
>>> **\<schema\>.js**- *file contenente la definizione della struttura del documento*
>>
>> **service/** - *cartella contenente l'implementazione della logica del server*
>> **\<servizio\>.js** - *file con l'implementazione dei vari servizi offerti da Animati*
>>
>> **test/** - *cartella contenente i file di test*
>>> **<test>.test.js** - *file responsabile del testing dei servizi offerti dal server Animati*
>>
>> **utils/** - *cartella contenente file d'utilità*
>>> **database.js** - *file contenente funzioni di utilità per il collegamento ed inizializzazione del database*
>>> **writer.js** - *file contenente funzioni di utilità per la scrittura delle risposte HTTP*

### Client
Il codice del frontend è contenuto nella repository "animati". La sua struttura è la seguente:
> **assets/** - *cartella contenente i file statici*
>> **bootstrap/** - *cartella contenente i file di Bootstrap*
>>> **css/** - *cartella contenente i file CSS di Bootstrap*
>>>> **bootstrap.min.css** - *file CSS di Bootstrap*
>>>
>>> **js/** - *cartella contenente i file JavaScript di Bootstrap*
>>>> **bootstrap.bundle.min.js** - *file JavaScript di Bootstrap*
>>
>> **css/** - *cartella contenente i file CSS dell'intero client*
>>>**style.css** - *file responsabile della definizione del tema del client*
>>>
>>> **markdown-editor.min.css** - *file CSS del Markdown Editor*
>>
>> **fonts/** - *cartella contenente i file dei font utilizzati nel progetto*
>>> **\<font\>** - *file del font*
>>
>> **html/** - *cartella contenente alcuni componenti HTML comuni all'intero client*
>>> **header.html** - *file conenente la definizione della barra di navigazione*
>>>
>>> **modulo.html** - *file contenente la definizione del modulo per la creazione, proposta o modifica di un'attività*
>>
>> **img/** - *cartella contenente le immagini utilizzate nel progetto*
>>> **logo.svg** - *l'immagine vettoriale del logo*
>>>
>>> **logo\<dim\>.png** - *l'immagine del logo in formato PNG*
>>
>> **js/** - *cartella contenente i file JavaScript dell'intero client*
>>> **jquery-3.6.1.min.js** - *file della libreria JQuery*
>>>
>>> **markdown-editor.min.js** - *file JavaScript del Markdown Editor*
>>>
>>> **markdown-it.min.js** - *file JavaScript del renderizzatore Markdown*
>>>
>>> **purify.min.js** - *file JavaScript per la pulizia del codice HTML*
>>>
>>> **script.js** - *file JavaScript contenente le funzioni di utilità per il client*
>
> **\<route\>/** - *cartella contenente i file relativi alla pagina di una specifica route*
>> **index.html** - *file contenente la definizione della pagina*
>>
>> **script.js** - *file JavaScript contenente la logica della pagina*
>>
>> **style.css** - *file CSS contenente la definizione del tema della pagina*
>
> **index.html** - *file contenente la definizione della pagina principale del client*
>
> **manifest.webmanifest** - *file contenente la definizione del manifest del client*
>
> **sw.js** - *file contenente la definizione del service worker del client*

## 2.2 Project Dependencies
### Server
Le dipendenze del server sono le seguenti:
| Nome | Versione |
| --- | --- |
| connect | ^3.2.0 |
| cors | ^2.8.5 |
| dotenv | ^16.0.3 |
| google-auth-library | ^8.7.0 |
| googleapis | ^110.0.0 |
| js-yaml | ^3.3.0 |
| jsonwebtoken | ^9.0.0 |
| mongoose | ^6.9.1 |
| oas3-tools-cors | ^2.3.5 |

Inoltre per eseguire i test sono necessarie anche le dipendenze di sviluppo:
| Nome | Versione |
| --- | --- |
| jest | ^29.4.0 |
| supertest | ^6.3.3 |

("^" indica che è possibile utilizzare qualsiasi versione compatibile con quella indicata)
Tali moduli NodeJS sono stati utilizzati e aggiunti al file `package.json`.

### Client
Le dipendenze del client sono le seguenti:
| Nome | Versione |
| --- | --- |
| bootstrap | v5.3.0-alpha1 |
| jquery | v3.6.1 |
| markdown-it | v12.2.0 |
| krajee-markdown-editor | v1.0.1 |
| purify | v0.7.4 |
| fontawesome-free | v5.12.0 |

## 2.3 Project Data
Per la gestione dei dati, Animati utilizza un database MongoDB. Tale database è stato creato su MongoDB Atlas, un servizio cloud offerto da MongoDB. Il database è stato creato tramite il servizio Atlas e contiene le seguenti collezioni:
| Nome | Descrizione |
| --- | --- |
| Catalogo | Contiene i dati delle attività |
| Etichette | Contiene le etichette delle attività |
| Liste | Contiene le liste di attività |
| Segnalazioni | Contiene le segnalazioni di attività |
| Utenti | Contiene i dati degli utenti registrati |
| Valutazioni | Contiene le valutazioni delle attività |

---
Per rappresentare i dati, Animati utilizza i seguenti schemi:
### `Attività`
```js
{
    banner: String,
    informazioni: InformazioniSchema,
    collegamenti: [CollegamentoSchema],
    ultimaModifica: {
        type: Date,
        default: Date.now
    },
    autore: {
        type: mongoose.Types.ObjectId,
        ref: 'Utenti',
        default: mongoose.Types.ObjectId('000000000000000000000000')
    },
    mediaValutazioni: Number,
    numeroSegnalazioni: Number
}
```

### `Collegamento`
```js
{
    nome: {
        type: String,
        required: true
    },
    link: {
        type: String,
        required: true
    }
}
```

### `Etichetta`
```js
{
    nome: {
        type: String,
        required: true
    },
    descrizione: {
        type: String,
        required: true
    },
    categoria: {
        type: String,
        required: true
    }
}
```

### `Informazioni`
```js
{
    titolo: String,
    descrizione: String,
    etàMin: Number,
    etàMax: Number,
    durataMin: Number,
    durataMax: Number,
    giocatoriMin: Number,
    giocatoriMax: Number,
    giocatoriPerSquadra: Number,
    giocatoriPerSquadraSet: Boolean,
    numeroSquadre: Number,
    numeroSquadreSet: Boolean,
    etichette: [EtichetteSchema]
}
```

### `Lista`
```js
{
    nome: {
        type: String,
        required: true
    },
    autore: {
        type: mongoose.Types.ObjectId,
        ref: 'Utenti',
        required: true
    },
    'attività': {
        type: [mongoose.Types.ObjectId],
        ref: 'Catalogo',
        default: []
    },
    ultimaModifica: {
        type: Date,
        default: Date.now
    }
}
```

### `Segnalazione`
```js
{
    messaggio: {
        type: String,
        required: true
    },
    titolo: {
        type: String,
        required: true
    },
    'attività': {
        type: mongoose.Types.ObjectId,
        ref: 'Catalogo',
        required: true
    },
    autore: {
        type: mongoose.Types.ObjectId,
        ref: 'Utenti',
        required: true
    }
}
```

### `Utenti`
```js
{
    email: {
        type: String,
        required: true
    },
    ruolo: {
        type: String,
        default: 'autenticato'
    },
    promossoDa: {
        type: mongoose.Types.ObjectId,
        ref: 'Utenti',
        default: mongoose.Types.ObjectId('000000000000000000000000')
    },
    immagine: {
        type: String,
        default: 'https://animati.app/assets/img/logo512.png'
    }
}
```

### `Valutazione`
```js
{
    voto: {
        type: Number,
        required: true
    },
    'attività': {
        type: mongoose.ObjectId,
        ref: 'Catalogo',
        required: true
    },
    autore: {
        type: mongoose.ObjectId,
        ref: 'Utenti',
        required: true
    }
}
```

<div class="page-break"></div>
