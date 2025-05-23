# 🧠 Appunti – Interfaccia di Flowise (Panoramica e Funzionalità)

## 📌 Introduzione

Flowise è un’interfaccia visuale low-code basata su **LangChain** e **LangGraph** che permette di costruire applicazioni LLM in maniera semplice, sfruttando un sistema drag-and-drop. In questo video viene fornita una panoramica completa dell’interfaccia di Flowise e delle sue principali funzionalità.

---

## 🖥️ Interfaccia principale

### ⚙️ Impostazioni e Versione

* Nella dashboard iniziale (Flowise instance) puoi accedere a:

  * `Chat Flows`, `Agent Flows`, `Marketplace`, `Tools`, `Assistants`, `Credentials`, `Variables`, `API Keys`, `Document Stores`.
* Sezione `About Flowise` per:

  * Vedere la versione installata.
  * Verificare se è disponibile una nuova versione (es. Flowise 2.0.1).
  * Aggiornamento tramite comando da terminale:

    ```bash
    npm update -g flowise
    ```

---

## 🤖 Creazione di agenti

### Agent Flows

* Puoi creare nuovi agenti cliccando su `Add New`.
* Interfaccia visuale con nodi:

  * **Supervisori** (es. CEO dell’agente).
  * **Lavoratori** (Workers): possono essere collegati al supervisore.
  * È possibile duplicare nodi e connetterli.

### Nodi disponibili

* `Chat Models`: OpenAI, Olama, HuggingFace, ecc.
* `Document Loaders`, `Embeddings`, `Moderation`, `Multi-agent`, `Output Parsers`, `Prompts`, `Retrievers`, `Text Splitters`, `Vector Stores`.
* `Tools`: per il **Function Calling** (es. calcolatrice, strumenti personalizzati).
* `Custom Tools`: scrivibili in JavaScript per chiamare qualsiasi API.

---

## 🔧 Funzionalità avanzate

### Sequential Agents

* Struttura con:

  * Nodo di partenza (`Start`).
  * Nodo di fine (`End`).
  * Uno o più agenti in sequenza.

### Graph Nodes (Neo4j)

* Per costruire **applicazioni RAG avanzate con grafi semantici**.
* Utilizza `neo4j` per gestione di dati strutturati.

---

## 🧩 Marketplace

* Flows già pronti:

  * `BabyAGI`, `API Agent`, `Retrieval Q&A`, `OpenAI Assistant`, `Slack/Discord Bot`, `Lead Outreach Agent`, `React Agent`, `Web search tools`, `Stock info`, `Airtable`.
* Filtro per:

  * Tipo: `Agent Flow`, `Chat Flow`, `Tool`.
  * Framework: `LangChain`, `LlamaIndex`.
  * Categoria: `Chatbot`, `Document Q&A`, `Finance`, `Customer Support`, ecc.

### Esempio: Lead Outreach Agent

* Contiene Supervisor, Workers, Custom Tool (es. Google Search), LLM (OpenAI).
* Può essere usato premendo `Use Template`.

---

## 🧠 Assistants

* Simili agli **assistenti OpenAI**:

  * Configurazione: nome, descrizione, icona, sistema prompt, temperatura, top-p.
  * Tools integrabili: code interpreter, file search, document upload.
  * Richiede chiave API (OpenAI, Huggingface, ecc.).

---

## 🛠️ Tools & Custom Tools

* Tools predefiniti o creati manualmente (es. invio email, accesso a API per il prezzo del Bitcoin).
* È possibile creare webhooks con Make.
* Ogni Tool può essere collegato ad agenti o workers.

---

## 🔐 API Keys, Variables & Document Stores

* Gestione delle credenziali: OpenAI, Huggingface, Google, Server API.
* Creazione di chiavi API personalizzate per accesso esterno.
* Gestione di document store per RAG (es. Qdrant, Weaviate, Pinecone, ChromaDB, ecc.).

---

## 📄 Documentazione Flowise

* Molto ben fatta e utile in caso di dubbi:

  * Sezioni: `Jet Flows`, `Agent Flows`, `Integrations`, `Configurations`, `Tools`, `Embedding`, `Chains`, ecc.
* Contiene anche:

  * Guida per l’embedding HTML.
  * Riferimenti API.
  * Setup per hosting su Render, AWS, Azure, Docker.

---

## ✅ Conclusione

Flowise offre un’interfaccia semplice ma potentissima per creare agenti e workflow LLM senza (quasi) scrivere codice. Ideale per:

* Costruire agenti personalizzati.
* Integrazione con vector DB e strumenti esterni.
* Workflow multi-agente e sequential.
* Testing e prototipazione rapida di sistemi RAG.

> Nei prossimi video, inizieremo a **costruire agenti da zero**, lavorando passo-passo con i nodi disponibili.


