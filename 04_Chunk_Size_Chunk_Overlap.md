## 📘 Chunk Size & Chunk Overlap 

* Imparare a **caricare un documento** in AnythingLLM.
* Comprendere a fondo i concetti di **chunking** e **chunk overlap**.
* Applicare strategie di segmentazione dei documenti per ottimizzare l’accuratezza e le prestazioni di una RAG (Retrieval-Augmented Generation).

---

## 📂 Embedding del documento

Per aggiungere un documento:

1. Vai sul tuo workspace in AnythingLLM.
2. Premi “Embed Document”.
3. Carica il tuo file (PDF, Markdown, testo, ecc.).

**Prima di fare embedding**, è fondamentale configurare correttamente il chunking nei **Settings > Text Splitter and Chunking**.

---

## 🔍 Chunking: cos’è e perché è importante

### 📌 Cos'è il *chunk size*?

* È la **dimensione (in token)** delle porzioni di testo in cui il documento viene diviso.
* Ogni chunk viene **indicizzato separatamente** nella vector database.
* Permette al modello di **recuperare informazioni** in modo mirato.

### 💡 Problema senza chunking

* Se carichi un documento intero come un unico chunk:

  * LLM tende a "capire" bene l'inizio e la fine.
  * Le sezioni centrali sono spesso meno accurate (perdita di contesto).
  * Peggiore accuratezza e performance nella RAG.

---

## 🔁 Chunk Overlap: cos’è?

* È la **sovrapposizione tra due chunk consecutivi**.
* Garantisce che **informazioni critiche al confine** tra due chunk non vadano perse.
* Migliora la **continuità del contesto** tra blocchi di testo.

Esempio:

* Chunk 1: token 0–1000
* Chunk 2: token 900–1900
  ➡️ Overlap = 100 token = 10%

---

## 📏 Regole pratiche per scegliere Chunk Size e Overlap

| Tipologia documento          | Chunk Size consigliato | Overlap consigliato (1–5%) |
| ---------------------------- | ---------------------- | -------------------------- |
| 📖 Libri / Lunghi articoli   | 1000–5000 tokens       | 50–250 tokens              |
| 📰 Articoli / Racconti brevi | 500–1000 tokens        | 10–50 tokens               |
| 📋 Liste / Tabelle / Prezzi  | 100–500 tokens         | 5–25 tokens (o anche 0%)   |

> ✨ *Ogni documento è unico*. Fai dei test: prova diverse combinazioni per trovare quella più efficace.

---

## 💸 Prezzo e Performance: perché chunk piccoli sono meglio

* **Modelli con contesto esteso** (es. 1M token di Google):

  * Possono elaborare documenti grandi, ma a costo elevato.
  * Caricare 50k token per ogni query = costo altissimo.

* **Chunking ottimale**:

  * Permette al modello di cercare solo nei chunk rilevanti.
  * Meno token da elaborare = **query più veloce e meno costosa**.

---

## 🎯 Best Practices

1. **Non caricare mai un intero documento come un unico chunk.**
2. Scegli il chunk size in base al contenuto:

   * Testo narrativo = chunk più grandi.
   * Tabelle, liste, prodotti = chunk piccoli.
3. Usa un overlap tra **1% e 5%**.
4. Gioca con i parametri: non esiste una regola unica.
5. Se il modello ha contesto limitato, usa chunk più piccoli.

---

## 📌 Conclusioni

* Chunking è **fondamentale** per la precisione di una RAG.
* Overlap garantisce coerenza e riduce le perdite di contesto.
* Impostare bene questi parametri è cruciale per:

  * Accuratezza.
  * Prestazioni.
  * Costi di esecuzione.
