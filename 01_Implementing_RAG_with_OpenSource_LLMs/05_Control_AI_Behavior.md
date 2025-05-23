## 🧠 **Configurazione avanzata in AnythingLLM**

Il video tratta le seguenti impostazioni chiave per il comportamento dell'applicazione:

* System Prompt
* Chat Memory (storia)
* LLM Temperature
* Top-K (risultati)
* Similarity Score Threshold

---

### 📝 1. **System Prompt**

* Si accede da: **Chat Settings > System Prompt**
* Prompt predefinito:

  > "Given the following conversation, relevant context and follow-up questions, reply with an answer to the current question the user is asking. Return only your response following the user’s instructions."
* È già ottimizzato per applicazioni RAG.
* Può essere **personalizzato** per casi d’uso specifici (es. contabilità, supporto tecnico, ecc.).
* Es: "You are an AI accountant assistant. Your job is to provide only factual answers based on uploaded documents."

✅ **Consiglio:** Personalizza il prompt se il dominio è verticale e richiede risposte filtrate o specifiche.

---

### 💬 2. **Chat Memory (storia conversazionale)**

* Parametro: **Chat History Length**
* Default consigliato: **20**
* Range: da **1 a 45**, ma oltre 20 potrebbero verificarsi errori.
* La memoria è gestita tramite **buffer di Windows**, quindi il contesto viene salvato in locale.

✅ **Best Practice:** Lascia a 20 se non hai esigenze specifiche di memoria più estesa.

---

### 🎨 3. **LLM Temperature**

* Controlla **la creatività delle risposte**.
* Valori consigliati:

  | Range     | Descrizione                                                      |
  | --------- | ---------------------------------------------------------------- |
  | 0.0 – 0.3 | Molto preciso, adatto a compiti formali (es. contabilità, legge) |
  | 0.4 – 0.7 | Buon compromesso tra creatività e accuratezza                    |
  | 0.8 – 1.0 | Creativo, adatto a storytelling, brainstorming                   |

✅ Imposta **0.2–0.4 per casi d’uso strutturati**, **0.8–1 per uso generico o creativo**.

---

### 🔍 4. **Vector Database: Similarity Search Parameters**

#### a. **Top-K Results**

* Parametro: **Maximum Context Snippets**
* Default consigliato: **4**
* Range efficace: **4–8**
* Maggiore il valore, **più contesto viene restituito**, ma anche più rumore potenziale.

#### b. **Similarity Score Threshold**

* Default: **0.25 (25%)**
* Funzione: **filtra i risultati del motore di ricerca semantico**
* Comportamento:

  * **< 0.25** → può restituire documenti meno pertinenti.
  * **> 0.75** → restituirà solo documenti **altamente rilevanti**, ma rischia di **non restituire nulla**.

📊 **Suggerimenti per scenari:**

| Caso d'uso                | Similarity Threshold consigliato |
| ------------------------- | -------------------------------- |
| Contabilità / Finanza     | 0.6 – 0.75                       |
| Ricerca generale su testi | 0.25 – 0.5                       |
| Documenti tecnici ampi    | 0.3 – 0.6                        |

---

### 🤖 5. **Agente e Skills**

* Nella sezione **Agent Configurations > Agent Skills**
* Tutti i “skills” sono **attivabili** da toggle.
* Tra questi: Web search, SQL connector, Document summarization, File generation, ecc.

⚠️ **Approfondimento in un video successivo**.

---

## ✅ Riepilogo finale

| Impostazione         | Valore consigliato                 | Scopo principale                               |
| -------------------- | ---------------------------------- | ---------------------------------------------- |
| System Prompt        | Personalizzato o default           | Imposta il ruolo/comportamento dell’agente LLM |
| Chat History         | 20                                 | Gestione del contesto a breve termine          |
| Temperature          | 0.2–0.4 (formale), 0.7+ (creativo) | Controlla la variabilità nelle risposte        |
| Top-K                | 4–8                                | Numero di risultati dal vector store           |
| Similarity Threshold | 0.25–0.75                          | Livello di somiglianza minima per l’inclusione |

