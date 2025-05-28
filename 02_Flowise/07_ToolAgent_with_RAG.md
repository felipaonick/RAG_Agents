# Flowise – Tool Agent con RAG e Pinecone

Questa lezione mostra come costruire un'applicazione **RAG (Retrieval-Augmented Generation)** con il **Tool Agent** di Flowise, integrando **Pinecone** come vector store per una persistenza reale dei documenti.

---

## 🧠 Obiettivo
Creare un agente AI in Flowise che:
- Usa Pinecone per archiviare documenti in modo persistente
- Recupera chunk rilevanti via funzione tool calling
- Include modelli LLM via OpenRouter
- Utilizza documenti caricati via `Document Store`
- È pienamente configurabile e gestibile

---

## ⚙️ Step 1 – Duplicazione del Tool Agent
1. Vai su un flusso esistente in *Chat Flows*
2. Premi `Duplicate Chat Flow` → rinominalo in ad es. `Tool agent with rag`
3. Rimuovi strumenti non necessari (es. Perplexity, Write File)

---

## 🗂️ Step 2 – Configurare il Document Store
1. Vai in `Document Stores` → `Add New`
2. Inserisci nome (`rag course test`) e aggiungi documenti:
   - **PDF**: caricamento semplice, splitter `recursive character text splitter`
   - **TXT Markdown**: usa `markdown text splitter`
   - **Plain Text**: copia e incolla, metadati opzionali

Ogni documento viene spezzato in *chunk* e può essere etichettato con `metadata` per tracciabilità.

---

## 🧠 Step 3 – Upsert su Pinecone
1. Aggiungi **OpenAI Embedding** (`text-embedding-3-small`, economico e sufficiente)
2. Aggiungi **Vector Store** `Pinecone`:
   - Crea account su [pinecone.io](https://www.pinecone.io/)
   - Crea un index es. `prompting`, seleziona lo **stesso modello** di embedding
   - Copia **API key** e **index name** in Flowise
3. Premi `Upsert` → i chunk vengono salvati su Pinecone

Verifica la presenza dei chunk accedendo a Pinecone dashboard.

---

## 🔁 Step 4 – Collegare il Tool Agent al Pinecone Vector DB
1. Torna al flusso `Tool agent with rag`
2. Aggiungi `Retriever Tool`
3. Al suo interno:
   - Nome: `prompting`
   - Descrizione: `Use this tool on questions about prompting and Cod`
4. Collega il `Document Store Vector` e scegli `rag course test`

---

## 🧪 Step 5 – Testare le Query
Esempi:
- `What is Cod prompting?` → il tool recupera chunk rilevanti da PDF
- `What are three good prompting techniques?` → estrae chain of thought, react prompting, ecc.
- `How does prompting for diffusion models work?` (dopo caricamento markdown)

---

## 🧹 Step 6 – Gestione Avanzata del Document Store
- Aggiungi nuovi documenti via `Add Document Loader`
- Elimina chunk/documenti vecchi
- Svuota o elimina namespace su Pinecone
- Se desiderato: usa `Record Manager` con PostgreSQL (non raccomandato attualmente per bug)

---

## ✅ Conclusione
Hai costruito un'applicazione RAG robusta:
- Persistente grazie a Pinecone
- Interrogabile da agenti AI con tool calling
- Estendibile a nuove fonti, documenti, query

Puoi ora:
- Aggiornare chunk via interfaccia `Document Stores`
- Aggiungere ulteriori strumenti all'agente
- Usare prompt specifici per indirizzare le risposte

📌 **Prossimo step**: imparare a scrivere prompt ottimizzati per il Tool Agent.
