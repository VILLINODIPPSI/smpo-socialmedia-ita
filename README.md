# SMPO - Social Media Ostracism Paradigm (Versione Italiana)

Paradigma di Ostracismo sui Social Media - Versione tradotta in italiano per esperimenti di ricerca psicologica.

## 🌐 Demo Online
**Sito Live:** [https://VILLINODIPPSI.github.io/smpo-socialmedia-ita/](https://VILLINODIPPSI.github.io/smpo-socialmedia-ita/)

## 📋 Descrizione

Questo progetto è una versione italiana del Social Media Ostracism Paradigm (SMPO), uno strumento di ricerca progettato per studiare gli effetti dell'ostracismo sociale in ambiente digitale simulando un'esperienza sui social media.

I partecipanti interagiscono con profili virtuali attraverso like e commenti, mentre i ricercatori possono manipolare il livello di inclusione/esclusione sociale ricevuto dal partecipante.

## 🔧 Configurazione Rapida

### 1. File da Tradurre - Profili Virtuali

Il file principale per le traduzioni dei profili è:
```
profiles.json
```

**Struttura del file profiles.json:**
```json
{
  "profiles": [
    {
      "id": 1,
      "name": "Marco Rossi",
      "avatar": "avatars/avatar1.jpg",
      "bio": "Studente di psicologia, amante della musica",
      "posts": [
        {
          "text": "Oggi è stata una giornata fantastica! ☀️",
          "likes": 15,
          "comments": ["Che bello!", "Anch'io ho avuto una bella giornata"]
        }
      ]
    }
  ]
}
```

**Campi da tradurre nel profiles.json:**
- `name`: Nome del profilo (usa nomi italiani tipici)
- `bio`: Biografia del profilo in italiano
- `posts.text`: Contenuto dei post in italiano
- `posts.comments`: Commenti in italiano

**Esempi di nomi italiani suggeriti:**
- Marco Rossi, Giulia Bianchi, Alessandro Verdi
- Sofia Romano, Lorenzo Ferrari, Chiara Ricci
- Matteo Marino, Francesca Costa, Davide Conti

### 2. Configurazione Avatar

**Directory avatar:** `avatars/` o `images/avatars/`

**Numero di avatar consigliati:**
- **Minimo:** 8-12 avatar per varietà
- **Ottimale:** 15-20 avatar per massima diversità
- **Formato:** JPG, PNG (consigliato 150x150px)

**Configurazione nel codice:**
```javascript
// In main.js - cerca questa variabile
const TOTAL_AVATARS = 16; // Cambia questo numero in base ai tuoi avatar

// Oppure cerca
var avatarCount = 12; // Aggiorna con il tuo numero di avatar
```

### 3. Configurazione Tempo del Test

**Nel file main.js cerca queste variabili:**

```javascript
// Durata totale dell'esperimento (in millisecondi)
const EXPERIMENT_DURATION = 180000; // 3 minuti (180 secondi)

// Intervallo tra le interazioni automatiche
const INTERACTION_INTERVAL = 5000; // 5 secondi

// Tempo di attesa iniziale
const INITIAL_DELAY = 2000; // 2 secondi
```

**Valori consigliati:**
- Test breve: 120000 (2 minuti)
- Test standard: 180000 (3 minuti)  
- Test lungo: 300000 (5 minuti)

### 4. Configurazione URL di Redirect

**Metodo consigliato: Parametro URL**

Invece di configurare un URL fisso nel codice, usa il parametro `redirect` nell'URL:

```
https://VILLINODIPPSI.github.io/smpo-socialmedia-ita/index.html?c=1&p=001&redirect=[URL_QUESTIONARIO_CODIFICATO]
```

**Come codificare l'URL del questionario:**
1. Vai su un tool di URL encoding online
2. Inserisci il tuo link del questionario
3. Copia il risultato codificato
4. Usalo nel parametro `redirect`

### 5. Esempi di Link con ID e Condizioni

**Link per ID 001 (formato numerico con zero padding):**

**🎯 Condizione 1 - OSTRACISMO (ID 001):**
```
https://VILLINODIPPSI.github.io/smpo-socialmedia-ita/index.html?c=1&p=001&redirect=[URL_QUESTIONARIO_CODIFICATO]
```

**🎯 Condizione 2 - INCLUSIONE (ID 001):**
```
https://VILLINODIPPSI.github.io/smpo-socialmedia-ita/index.html?c=2&p=001&redirect=[URL_QUESTIONARIO_CODIFICATO]
```

**🎯 Condizione 3 - SOVRAINCLUSIONE (ID 001):**
```
https://VILLINODIPPSI.github.io/smpo-socialmedia-ita/index.html?c=3&p=001&redirect=[URL_QUESTIONARIO_CODIFICATO]
```

**Altri esempi di ID numerici:**
```
ID 002: ?c=1&p=002&redirect=[URL_QUESTIONARIO_CODIFICATO]
ID 010: ?c=1&p=010&redirect=[URL_QUESTIONARIO_CODIFICATO]
ID 099: ?c=1&p=099&redirect=[URL_QUESTIONARIO_CODIFICATO]
ID 150: ?c=1&p=150&redirect=[URL_QUESTIONARIO_CODIFICATO]
```

**Nel codice JavaScript per catturare i parametri:**
```javascript
// Ottieni parametri dall'URL
const urlParams = new URLSearchParams(window.location.search);
const participantId = urlParams.get('p') || '001';        // Parametro 'p' per ID (solo numerico)
const condition = parseInt(urlParams.get('c')) || 1;      // Parametro 'c' per condizione
const redirectUrl = urlParams.get('redirect');            // Parametro 'redirect' per questionario

// Impostazioni condizioni
switch(condition) {
    case 1:
        likesProbability = 0.1;  // Condizione 1: OSTRACISMO (pochi like)
        break;
    case 2:
        likesProbability = 0.5;  // Condizione 2: INCLUSIONE (like normali)
        break;
    case 3:
        likesProbability = 0.8;  // Condizione 3: SOVRAINCLUSIONE (molti like)
        break;
}
```

## 📁 Struttura File Principali

```
smpo-socialmedia-ita/
├── index.html          # Pagina principale
├── main.js             # Logica principale del test
├── profiles.json       # PROFILI DA TRADURRE
├── style.css           # Stili dell'interfaccia
├── shortcut.js         # Script di supporto
├── avatars/            # Directory con immagini avatar
│   ├── avatar1.jpg
│   ├── avatar2.jpg
│   └── ...
├── docs/               # Documentazione e file esempio
│   ├── ESEMPIO_Assegnazione_condizioni_partecipanti/
│   │   └── partecipanti_smpo_ita.csv
│   ├── ESEMPIO_Risultati_Qualtrics/
│   │   ├── Risultati_Qualtrics_esempio.csv
│   │   └── Risultati_Qualtrics_esempio.xlsx
│   ├── LEGGIMI_Assegnazione_Condizioni_id_Partecipanti_SMPO_ITA.md
│   └── LEGGIMI_Risultati_Qualtrics_SMPO_ITA.md
└── README.md          # Questo file
```

### 📚 Documentazione Aggiuntiva

Nella cartella `docs/` sono disponibili due guide dettagliate con relativi file esempio:
- **Assegnazione partecipanti**: Come creare la lista partecipanti con link automatici
- **Interpretazione risultati**: Come leggere i dati esportati da piattaforme di survey

## 🎯 Personalizzazione Avanzata

### Modificare i Messaggi dell'Interfaccia

Cerca nel file **main.js** o **index.html** questi testi da tradurre:

```javascript
// Messaggi da tradurre
const MESSAGES = {
    welcome: "Benvenuto nel nostro social network!",
    instructions: "Interagisci con i post mettendo like e commentando",
    waiting: "Attendere prego...",
    thankyou: "Grazie per la partecipazione!"
};
```

### Impostazioni Condizioni Sperimentali

```javascript
// Configurazione condizioni nel main.js
const CONDITIONS = {
    1: {
        name: "OSTRACISMO",
        likesReceived: "low",       // Pochi like ricevuti
        commentsReceived: "low",    
        socialFeedback: "negative",
        probability: 0.1
    },
    2: {
        name: "INCLUSIONE", 
        likesReceived: "medium",    // Like normali
        commentsReceived: "medium", 
        socialFeedback: "neutral",
        probability: 0.5
    },
    3: {
        name: "SOVRAINCLUSIONE",
        likesReceived: "high",      // Molti like ricevuti
        commentsReceived: "high",   
        socialFeedback: "positive",
        probability: 0.8
    }
};
```

## 🔗 Integrazione con Piattaforme di Survey

Per l'integrazione con piattaforme di questionari online puoi:

**Configurazione:**
1. Crea il tuo questionario sulla piattaforma scelta
2. **NON modificare il codice** - usa invece il parametro `redirect` nell'URL
3. Codifica l'URL del questionario usando un tool online
4. Distribuisci URL completi con i parametri: `c`, `p`, e `redirect`
5. Il codice invierà automaticamente i dati dell'esperimento al questionario

**Vantaggi di questo approccio:**
- Repository pubblico senza link privati esposti
- Flessibilità per usare questionari diversi
- Nessuna modifica del codice necessaria

### File Esempio Risultati

Nel subfolder `docs/ESEMPIO_Risultati_Qualtrics/` sono disponibili file esempio di risultati esportati da piattaforme di survey. La documentazione completa per interpretare i risultati è disponibile in `docs/LEGGIMI_Risultati_Qualtrics_SMPO_ITA.md`.

## 📊 Riferimenti Scientifici

Questo paradigma si basa sulla ricerca di:

> Wolf, W., Levordashka, A., Ruff, J. R., Kraaijeveld, S., Lueckmann, J.-M., & Williams, K. D. (2014). Ostracism Online: A social media ostracism paradigm. Behavior Research Methods.

## 🛠️ Tool Utili

- [Documentazione SMPO originale](http://smpo.github.io/socialmedia/)
- [Tool per codificare URL](http://smpo.github.io/dencoder/)
- Tool online per URL encoding (cerca "URL encoder" su Google)

---

*2025 - emiliano.pes@uniroma1.it*
