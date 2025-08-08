# LEGGIMI - Assegnazione Condizioni Partecipanti SMPO ITA

File CSV per assegnare i partecipanti agli ID e alle condizioni sperimentali con generazione automatica dei link di partecipazione.

Nel subfolder `ESEMPIO_Assegnazione_condizioni_partecipanti/` è disponibile un file esempio:
* `partecipanti_smpo_ita.csv`

## 📋 Struttura del File CSV

| **Campo** | **Descrizione** | **Esempio** |
|-----------|-----------------|-------------|
| Nome | Nome del partecipante | Marco |
| Cognome | Cognome del partecipante | Rossi |
| Data_Nascita | Data di nascita (YYYY-MM-DD) | 1995-03-15 |
| Sesso | Genere (M/F) | M |
| ID | Identificativo numerico univoco | 1, 2, 3... |
| Condizione | Condizione sperimentale (1-3) | 1, 2, 3 |
| Link_Partecipazione | URL generato automaticamente (formula) | - |

## 🎯 Condizioni Sperimentali

| **Valore** | **Condizione** | **Descrizione** |
|------------|----------------|-----------------|
| 1 | OSTRACISMO | Pochi like ricevuti |
| 2 | INCLUSIONE | Like normali |
| 3 | SOVRAINCLUSIONE | Molti like ricevuti |

## 🔧 Formula per Link Automatici con Redirect

Per Excel/LibreOffice:
```excel
=CONCATENA("https://villinodippsi.github.io/smpo-socialmedia-ita/index.html?c=";F2;"&p=";E2;"&redirect=https%3A//tuodominio.qualtrics.com/jfe/form/SV_TUOCODICE")
```

Per Google Sheets:
```
="https://villinodippsi.github.io/smpo-socialmedia-ita/index.html?c="&F2&"&p="&E2&"&redirect=https%3A//tuodominio.qualtrics.com/jfe/form/SV_TUOCODICE"
```

**Dove:**
* `F2` = Cella della Condizione (colonna F)
* `E2` = Cella dell'ID (colonna E)
* `https%3A//tuodominio.qualtrics.com/jfe/form/SV_TUOCODICE` = Il tuo URL Qualtrics già codificato

## 🔐 Come Preparare l'URL Codificato

1. **Prendi il tuo link Qualtrics:**
   ```
   https://tuodominio.qualtrics.com/jfe/form/SV_TUOCODICE
   ```

2. **Codificalo usando un tool online:** 
   ```
   https%3A//tuodominio.qualtrics.com/jfe/form/SV_TUOCODICE
   ```

3. **Sostituisci nella formula** al posto di `https%3A//tuodominio.qualtrics.com/jfe/form/SV_TUOCODICE`

## 📊 Esempio di Dati

### Esempio con URL Completo

| Nome | Cognome | Data_Nascita | Sesso | ID | Condizione | Link_Partecipazione |
|------|---------|--------------|-------|----|-----------|--------------------|
| Marco | Rossi | 1995-03-15 | M | 1 | 1 | https://villinodippsi.github.io/smpo-socialmedia-ita/index.html?c=1&p=1&redirect=https%3A//tuodominio.qualtrics.com/jfe/form/SV_TUOCODICE |
| Giulia | Bianchi | 1997-07-22 | F | 2 | 2 | https://villinodippsi.github.io/smpo-socialmedia-ita/index.html?c=2&p=2&redirect=https%3A//tuodominio.qualtrics.com/jfe/form/SV_TUOCODICE |
| Alessandro | Verdi | 1993-11-08 | M | 3 | 3 | https://villinodippsi.github.io/smpo-socialmedia-ita/index.html?c=3&p=3&redirect=https%3A//tuodominio.qualtrics.com/jfe/form/SV_TUOCODICE |
| Sofia | Romano | 1996-09-12 | F | 4 | 1 | https://villinodippsi.github.io/smpo-socialmedia-ita/index.html?c=1&p=4&redirect=https%3A//tuodominio.qualtrics.com/jfe/form/SV_TUOCODICE |

## 💡 Utilizzo

### Setup Iniziale

1. **Compila** i dati dei partecipanti (Nome, Cognome, Data_Nascita, Sesso)
2. **Assegna** ID numerici progressivi (1, 2, 3...)
3. **Assegna** condizioni (1, 2, 3) secondo il tuo disegno sperimentale
4. **Codifica** l'URL del tuo questionario Qualtrics
5. **Sostituisci** nella formula l'URL codificato al posto di `https%3A//tuodominio.qualtrics.com/jfe/form/SV_TUOCODICE`
6. **Copia** la formula nella colonna Link_Partecipazione
7. **Invia** il link personalizzato a ciascun partecipante

## 🔐 Sicurezza e Privacy

**Vantaggi di questo approccio:**
- ✅ Repository pubblico senza link privati esposti nel codice
- ✅ URL completo direttamente utilizzabile dai partecipanti
- ✅ Formula semplice con tutto incluso
- ✅ Redirect automatico al questionario al termine dell'esperimento

## 🛠️ Strumenti Utili

- **URL Encoder online**: Cerca "URL encoder" su Google
- **Tool SMPO originale**: http://smpo.github.io/dencoder/
- **Fogli di calcolo**: Excel, LibreOffice Calc, Google Sheets

## 📈 Bilanciamento Sperimentale

Per un disegno bilanciato, assegna le condizioni in modo equilibrato:

```
Partecipanti 1-3-5-7-9...  → Condizione 1 (OSTRACISMO)
Partecipanti 2-4-6-8-10... → Condizione 2 (INCLUSIONE)  
Partecipanti 11-13-15...   → Condizione 3 (SOVRAINCLUSIONE)
Partecipanti 12-14-16...   → Ripeti schema
```

La formula genererà automaticamente l'URL corretto per ogni partecipante con il proprio ID e condizione assegnata.

---

*2025 - emiliano.pes@uniroma1.it
