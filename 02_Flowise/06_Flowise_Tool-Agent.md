# Flowise: Introduzione al Tool Agent

## 🧠 Obiettivo del Video

In questo video si introduce il **Tool Agent** di Flowise. È il primo di due video dedicati:

* **In questo**: panoramica teorica delle potenzialità del tool agent.
* **Nel prossimo**: implementazione pratica di un'applicazione completa con il Dual Agent.

---

## 📌 Cos'è il Dual Agent

Il **Tool Agent** in Flowise è un agente avanzato basato su un **modello LLM con tool calling** che consente di:

* Effettuare **chiamate a strumenti esterni** (web scraping, calcoli, API, file system, calendari, ecc.)
* Estendere le capacità dei modelli LLM con funzioni reali.
* Combinare più strumenti (calculator, file writer, API tools, Compose.IO, ecc.)

---

## 🛠️ Configurazione di Base

### 1. Creazione di un nuovo Chat Flow

* Accedere alla sezione `Chat Flows`
* Premere `Add New` → dare un nome es. "Tool Agent Test Course"
* Salvare il canvas

### 2. Aggiunta di un Dual Agent

* Da `Langchain > Agents`, selezionare **Tool Agent**
* Il Tool Agent può accedere a tutti i tool Flowise disponibili

### 3. Selezione del modello LLM

* È richiesto un modello **con funzione di Tool Calling**
* Esempio suggerito: **OpenRouter** (piattaforma che aggrega modelli come Claude, GPT-4, Gemini, ecc.)

#### 🔧 OpenRouter Setup:

* Registrarsi su [openrouter.ai](https://openrouter.ai)
* Aggiungere credito minimo (es. 5\$)
* Esplorare e selezionare modelli (Claude 3.7 Sonnet, GPT-4 mini, Gemini, ecc.)
* Copiare il nome del modello
* Creare una **API Key** su OpenRouter
* Configurare in Flowise:

  * Node: `Tool Calling Chat Model`
  * Nome modello: es. `anthropic/claude-3-sonnet`
  * Credenziali API di OpenRouter

---

## 🧠 Aggiunta di Memoria

### Buffer Window Memory

* Aggiungere nodo `Buffer Window Memory`
* Collegarlo al modello
* Impostare: es. `Window Size = 20` per ricordare i messaggi recenti

---

## 🔧 Tool disponibili e loro utilizzo

### 📐 1. Calculator

* Test per espressioni matematiche (es. `77 × 5`)
* Risposta via `function calling` al tool `calculator`

### 🌍 2. Brave Search API

* Tool per accesso a contenuti web in tempo reale
* Richiede API key Brave
* Domanda d’esempio: “Qual è il prezzo del Bitcoin oggi?”

### 🕸️ 3. Web Scraper (Cherrio)

* Permette scraping di contenuti HTML da siti web

### 🧮 4. Code Interpreter

* Simile al code interpreter di ChatGPT
* Esegue codice Python in sandbox
* Ideale per:

  * Creare grafici
  * Eseguire calcoli avanzati
  * Elaborazioni dati

### 📆 5. Current Time/Date Tool

* Fornisce l’orario e la data attuali

### 📂 6. Write File

* Scrive un file di testo in una directory locale
* Esempio:

  * Prompt: “Scrivi le ultime notizie su Tesla in un file”
  * Output: file `Tesla News.txt` nella directory specificata

---

## 🧩 Integrazione con Compose.IO

### Cos'è Compose.IO?

Un tool per collegare agenti AI a **qualsiasi API** esterna tramite una sola API key.

* Esempi di servizi supportati:

  * Google Calendar, Gmail, Notion, Slack
  * Perplexity, Twitter, Airtable, YouTube, ecc.

### Setup:

1. Registrarsi su [app.compose.io](https://app.compose.io)
2. Collegare le app (es. Google Calendar)
3. Generare una API key
4. Configurare Flowise:

   * Tool `ComposeIO`
   * Inserire app name (es. `Google Calendar`)
   * Selezionare azione (es. `create event`)

### Esempio:

> “Crea un evento per domani alle 18:00: ‘Shopping per il PC’”

Il tool esegue:

* Calcolo della data corretta
* Chiamata all’azione `Create Event` su Google Calendar
* Scrittura dell’evento con dettagli

---

## 🛠️ Custom Tools

* Possibilità di creare strumenti personalizzati scrivendo codice JavaScript
* Ogni custom tool definisce:

  * Nome
  * Descrizione
  * Input schema
  * Funzione `run(input)` per la logica
* È possibile importare template già pronti dal marketplace di Flowise (es. Perplexity Search)

---

## 🧪 Test e Prompt Template

* Ogni Tool Agent può avere:

  * **System Prompt** personalizzato (non obbligatorio se il modello è già ottimizzato)
  * Moderation Input
  * Prompt di fallback in caso di errore
  * Output documentato

---

## 🔁 Esempi di Flusso

1. Utente: “Quanto fa 77 × 2?”
2. AI: utilizza `calculator`
3. Utente: “Mi chiamo Arnie”
4. AI: risponde
5. Dopo 20 messaggi: “Qual è il mio nome?”
6. AI: Ricorda “Arnie” (grazie a buffer memory)

---

## 📥 Esportazione del Flusso

* Una volta completato, esportare il chat flow come file `.json`
* Utile per riutilizzare o condividere flussi tra ambienti

---

## ✅ Riepilogo

| Componente        | Funzionalità                                     |
| ----------------- | ------------------------------------------------ |
| **Tool Agent**    | Centro di controllo per il tool calling          |
| **OpenRouter**    | Integrazione con modelli multipli via 1 API      |
| **Tool**          | Calcolatrice, web scraping, file, API, date      |
| **Compose.IO**    | Connessione ad app esterne senza scrivere codice |
| **Custom Tool**   | Estensioni scritte in JS per strumenti avanzati  |
| **Buffer Memory** | Conservazione contesto in conversazioni lunghe   |

---

## 🚀 Conclusione

Il Dual Agent è uno strumento **estremamente potente** per:

* Automazione personalizzata
* Integrazione API esterne
* Estensioni con tool nativi o custom
* Costruzione di applicazioni multi-funzione in Flowise

👉 **Non sottovalutarlo**. È il cuore delle automazioni intelligenti in Flowise!

