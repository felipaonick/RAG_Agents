# 🧠 Flowise – Costruire una Applicazione RAG Locale con Modelli Locali (Ollama)

## 🎯 Obiettivo del Video

Imparare a costruire una **RAG application (Retrieval-Augmented Generation)** completamente **locale**, utilizzando modelli serviti con **Ollama** e senza inviare dati a terze parti. Questo tipo di applicazione è ideale per l’elaborazione di dati sensibili come documenti privati, contabilità o informazioni aziendali.

---

## 🧱 Struttura della Chat Flow

### 1. **Creazione di una nuova chat flow**

* Aprire un canvas vuoto e salvare con nome: `Local Ollama RAG`
* Struttura basata sulla catena `Conversational Retrieval QA Chain`

### 2. **Aggiunta dei nodi principali**

* `Chat Model` → `chat-llama` servito via **Ollama**
* `Vector Store` → `In-Memory Vector Store`
* `Embeddings Model` → `ollama-embeddings`
* `Document Loader` → `Folder with Files`
* `Text Splitter` → `Recursive Character Text Splitter`

---

## ⚙️ Configurazione Dettagliata dei Componenti

### 🗣️ Chat Model – LLaMA 3.2 via Ollama

* Comando per avviare server:

  ```bash
  ollama serve
  ```
* Verifica modelli disponibili:

  ```bash
  ollama list
  ```
* Modello usato: `llama3:instruct` (3B, float16)
* Temperatura: `0.9`
* Nessun upload immagine abilitato

### 📦 Vector Store

* Tipo: `In-Memory` (ideale per test locali)
* ⚠️ **Persistenza**: i dati **possono andare persi** alla chiusura dell’istanza

### 🔡 Embeddings

* Tipo: `ollama-embeddings`
* Modello suggerito: `nomic-embed-text`

  * Piccolo (\~270MB), gratuito e adatto all’uso locale
  * Comando di installazione:

    ```bash
    ollama run nomic-embed-text
    ```

### 📂 Document Loader

* Tipo: `Folder with Files`
* Path inserito: cartella contenente 4 PDF (es. su cani, Docusign, bundle, etc.)
* ⚠️ Rimozione di apici e barra finale nel path

### 🪓 Text Splitter

* Tipo: `Recursive Character Text Splitter`
* Chunk size: `1000`
* Overlap: `150`
* Ragione: uno dei PDF è disordinato e più lungo → miglior copertura semantica

---

## 🧪 Operazioni

### ✅ Upsert dei documenti

* Comando: `Upsert to Vector Store`
* Risultato: `57 chunks` di 1000 token ciascuno

### 🧪 Esempi di Query

* Domanda: `"What are the three dog trainers?"`

  * Risposta corretta con le categorie presenti nei PDF
* Domanda generica fuori contesto: `"What should I eat tonight?"`

  * Risposta: `"I'm not sure"` (rispetta la restrizione del prompt template)

---

## 🧰 Prompt Template della QA Chain

Il prompt predefinito forza l’LLM a rispondere **solo** sulla base dei dati caricati:

```txt
I want you to act as a document that I am having a conversation with. Your name is AI assistant.
Using the provided context, answer the user questions to the best of your abilities by using resources provided.
If there is nothing in the context relevant to the question at hand, just say I'm not sure.
Never break character.
```

---

## 📤 Esportazione

* Il flow è stato esportato tramite il comando `Export Chat Flow` → si ottiene un file `.json` per riutilizzo.

---

## ✅ Conclusioni

* Abbiamo costruito una **RAG application completamente locale**, senza usare API esterne.
* Tutto avviene su macchina locale: chat model + embeddings + database
* Perfetto per la gestione di documenti privati
* Pronto per essere personalizzato e potenziato (es. UI, hosting, agenti...)

