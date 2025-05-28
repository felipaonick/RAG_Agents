# ⚙️ Introduzione a n8n: Automazione e RAG con Node-based Workflows

## 🧩 Cos'è n8n?

**n8n** è una piattaforma open-source per l'automazione dei flussi di lavoro (workflow automation), simile a strumenti come Zapier o Make, ma con molta più flessibilità e orientata agli sviluppatori.

Permette di:
- Automatizzare processi aziendali
- Creare applicazioni RAG con inserimento automatico dei dati in vettori
- Collegare facilmente API di terze parti (Gmail, Google Sheets, Google Drive)
- Integrare scraping web (in modo legale)

---

## 🛠️ Requisiti di Base

### 📦 1. Installazione di Node.js

Per eseguire n8n in locale:
- Installa [Node.js](https://nodejs.org/)
- Verifica l'installazione con:
  ```bash
  node -v
  npm -v
````

> 🔄 È possibile usare [nvm](https://github.com/nvm-sh/nvm) o `n` per gestire versioni multiple di Node.js.

### ☁️ Alternativa Cloud

* Se **non vuoi installare n8n in locale**, puoi usare la versione **cloud gratuita per 2 settimane** disponibile su [n8n.io](https://n8n.io/).
* Ideale per test rapidi senza configurazioni locali.

---

## 🚀 Introduzione ai Concetti Chiave

### ⚡ Trigger

* Punto di innesco del flusso.
* Esempio: file aggiunto in una cartella Google Drive.

### 🔧 Action

* Azione eseguita dopo il trigger.
* Esempio: invio a Pinecone, salvataggio su database, scraping, invio email, ecc.

### 🔄 Flusso dei Dati

* I dati passano da un nodo all'altro.
* Ogni nodo può trasformare, filtrare o arricchire i dati ricevuti prima di passarli al successivo.

---

## 🧠 Caso Studio: App RAG con Automazione

### Obiettivo:

Creare un'app RAG automatizzata che:

1. Riceve file in una cartella di Google Drive
2. Estrae il contenuto dei file
3. Inserisce automaticamente i dati in un database vettoriale Pinecone
4. Rende il contenuto interrogabile via chatbot

> 📁 Ogni file caricato nel folder avvia automaticamente il flusso!

### Estensioni Possibili:

* Integrazione con OCR (per documenti scansionati)
* Pre-elaborazione linguistica (con LLM)
* Notifica su Slack o email al termine dell’inserimento

---

## 🧰 Integrazioni Potenti

n8n supporta centinaia di **integrazioni native** (no codice!) tra cui:

* **Google Drive**
* **Google Sheets**
* **Gmail**
* **HTTP/Webhook**
* **Pinecone**
* **OpenAI, HuggingFace, Cohere**, ecc.

---

## 🗃️ Import/Export dei Workflow

* Come in Flowise, è possibile **esportare** flussi già pronti e **importarli** in n8n.
* Questo permette di:

  * Riutilizzare workflow complessi
  * Condividere flussi con colleghi o clienti
  * Fare versioning

> ✅ Puoi "rubare" i flussi già pronti e adattarli ai tuoi progetti.

---

## 🕸️ Web Scraping Gratuito (e Legale)

* n8n permette il **web scraping gratuito** usando nodi HTTP + Cheerio.
* Non serve software esterno costoso.
* Ideale per:

  * Raccolta dati da siti pubblici
  * Monitoraggio di news o mercati
  * Aggregazione di contenuti

⚠️ Ricorda: **fare scraping legalmente** significa rispettare i `robots.txt` e i termini d’uso dei siti.

---

## 🔄 Quando Torna utile n8n nel Corso?

* Verrà utilizzato anche più avanti per:

  * **Vendita di applicazioni AI**
  * **Esecuzioni pianificate**
  * **Automazione continua dei RAG pipelines**

---

## 🎯 Conclusione

n8n è uno strumento essenziale per chi desidera:

* Automatizzare pipeline AI
* Integrare strumenti e dati senza scrivere codice complesso
* Espandere facilmente un'app RAG o GPT-based
* Creare **prodotti scalabili e vendibili**

> 💡 Nei prossimi video: esploreremo **flussi reali**, **scraping legale**, e **come monetizzare le app AI automatizzate** con n8n.

