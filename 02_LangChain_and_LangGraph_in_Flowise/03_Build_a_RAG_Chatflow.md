# Costruzione di un'Applicazione RAG in Flowise (con Web Scraping)

## 🎯 Obiettivo del video

Creare una **applicazione RAG (Retrieval-Augmented Generation)** in **Flowise**, che consenta di:

* Usare **web scraping** (tramite Brave Search API)
* Embeddare i contenuti in un **vector store**
* Interrogare i documenti tramite **Conversational Retrieval Q\&A Chain**

---

## 🧩 Passaggi principali

### 1. Creazione del Chat Flow

* Vai nella sezione **Chat Flows**
* Premi **Add New**
* Salva subito il canvas con un nome, es. `RAG Q&A from Web`

---

### 2. Aggiunta del nodo centrale

#### Nodo: `Conversational Retrieval QA Chain` (LangChain)

* È il cuore dell'applicazione RAG
* Richiede obbligatoriamente:

  * Un **Chat Model**
  * Un **Vector Store**
* Opzionali:

  * **Memory** (per contesto delle conversazioni)
  * **Input moderation**

---

## 🤖 Impostazione del Chat Model

### Modello: `ChatOpenAI`

* Aggiunto dalla sezione **Chat Models**
* Connessione solo agli slot validi (protetta da errori)
* Richiede **API Key di OpenAI**

#### ✅ Come ottenere l'API Key

1. Vai su OpenAI Dashboard > API Keys
2. Crea nuova chiave > Copiala
3. Inseriscila in Flowise sotto **Credentials**

#### Impostazioni consigliate

* **Model**: `gpt-4-0613` o `gpt-4-mini` (più economico per test)
* **Temperature**: 0.9 (risposte più creative)
* **Image Upload**: disabilitato se non necessario

---

## 🧠 Embeddings & Vector Store

### 1. Vector Store: `In-Memory Vector Store`

* Nessuna chiave API richiesta
* Solo per test locale (volatile)
* Connettibile facilmente alla chain

### 2. Embedding Model: `OpenAIEmbeddings`

* Modello suggerito: `text-embedding-3-small`
  Costo: **\$0.02 / 1M tokens**
* Connettibile a:

  * Vector Store
  * Document loader
* Riutilizza le stesse API Key già create

---

## 📄 Documenti da embeddare

### Metodo scelto: **Web scraping**

#### Strumento: `Brave Search API Document Loader`

##### Come usarlo

1. Crea un account su [Brave Search API](https://search.brave.com)
2. Ottieni l’API Key gratuita (2.000 query/mese)
3. Aggiungi la chiave tra le credenziali in Flowise

##### Query di esempio

* URL: guida su Prompt Engineering
* Query generica: `Tesla` (per notizie aggiornate)

---

## 🪓 Text Splitter

### Scelto: `HTML to Markdown Text Splitter`

* Specifico per scraping HTML
* Parametri consigliati:

  * **Chunk Size**: 2000
  * **Chunk Overlap**: 200

---

## 🧬 Esecuzione embedding (`Upsert to Vector Store`)

* Premi il pulsante `Upsert`
* Processo:

  * Lo splitter converte HTML → Markdown
  * OpenAI crea embeddings
  * Inseriti nel vector store
* Output: es. 20 chunks embeddati

---

## 💬 Interrogazione dell’assistente

### Prompt di test

* **"What is prompt engineering?"**

  > LLM risponde correttamente grazie al contenuto embeddato

* **"What should I eat today?"**

  > Risposta: *“I’m not sure”* → nessuna informazione nel vector store

---

## 🧠 Personalizzazione del prompt

### Prompt predefinito della chain:

```plaintext
Act as a document I’m having a conversation with. Your name is AI Assistant.
Answer ONLY using the provided context. If nothing is found, say: “I’m not sure.”
Never break character.
```

### Modifiche possibili:

* Nome dell’agente
* Messaggio d’introduzione personalizzato

---

## 🔁 Memoria conversazionale (opzionale)

### Nodo: `BufferWindowMemory`

* Ricorda fino a 20 messaggi
* Migliora la coerenza nel tempo

---

## 📎 Altre opzioni

* `Return Source Documents`: restituisce i chunk usati nella risposta
* `Input Moderation`: filtra input inappropriati (opzionale)

---

## ✅ Riepilogo nodi usati

| Tipo            | Nodo                              |
| --------------- | --------------------------------- |
| Chain           | Conversational Retrieval QA Chain |
| Chat Model      | ChatOpenAI (GPT-4 mini)           |
| Embeddings      | OpenAI (`text-embedding-3-small`) |
| Vector Store    | In-Memory Vector Store            |
| Document Loader | Brave Search API Document Loader  |
| Text Splitter   | HTML to Markdown Text Splitter    |
| Memory (opz.)   | BufferWindowMemory                |

---

## 📌 Note importanti

* **Non è un crawler**: il document loader Brave non esplora tutti i link.
* **Query semplici supportate**: puoi scrivere "Tesla" invece di un URL.
* **Prompt robusto**: l’agente rifiuta domande fuori contesto.
* **Consigliato**: usa Pinecone o Chroma per progetti di produzione.


