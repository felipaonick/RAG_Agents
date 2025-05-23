# 🎯 Prompt Engineering per System Prompt in Agenti AI (Flowise)

## ⚠️ Principio guida

> **Il miglior system prompt è *nessun* system prompt**, perché:

* Viene sempre inviato al modello LLM
* **Ogni token è a pagamento**
* **Evita** di usarlo se il tuo agente già funziona come desideri

---

## 🧠 Contesto dell’Agente

L’agente AI costruito:

* Ha accesso a:

  * Tool di scrittura file (`Write File`)
  * Internet (`Brave Search API`)
  * Data e ora correnti
  * Calcolatrice
  * Memoria (`Windowed Buffer Memory`)
* È collegato a un **retriever RAG** per interrogare documenti su **prompt engineering**

---

## ⚙️ Additional Parameters nei vari componenti

### 🧩 `Memory (Windowed Buffer)`

* `Session ID`: per tracciare la sessione (facoltativo)
* `Chat History` è la chiave di memoria (non modificarla)
* `Window size`: numero di messaggi che la memoria mantiene

### 🤖 `Chat Model (es. OpenRouter)`

* `max_tokens`, `top_p`, `frequency_penalty`: regolazioni avanzate
* `streaming`: disattivabile se non si vuole vedere il testo generato "dal vivo"

### 🧲 `Retriever Tool`

* `returnSourceDocuments`: se vuoi vedere da dove arriva l’informazione
* `topK`: numero di chunk da restituire (es. 4 o 8)

### 🧠 `Tool Agent`

* `max_iterations`: limita il numero di tool che può usare in un singolo ciclo (es. 5–10)
* **`system_prompt`**: il vero focus di questa lezione

---

## 🧪 Test funzionali (senza system prompt)

* ✅ Domanda: "What is the Bitcoin price today?"

  * → Usa correttamente il **Brave Search API**

* ✅ Domanda: "What day is today and what is 77 × 4?"

  * → Usa correttamente **Date/Time + Calculator**

* ✅ Prompt combinato avanzato:
  `"Search Cod Prompting in the web, summarize it, search Cod in the database, write it to file"`

  * → Esegue correttamente **3 tool** in sequenza: Web + RAG + File

* ✅ Prompt estremamente complesso:
  `"search info about CoT prompting in the web and make a summary, then search COD in the database, write the output in my local machine. Check date and time ( I live in Italy)"`

  * → Chiama **tutti i tool** con successo: Web, RAG, File, Time

---

## 🛠 Quando e come scrivere un buon `system_prompt`

### 🧱 Struttura consigliata (in **Markdown**)

```markdown
# 🧠 Role
You are a [persona] tasked with [obiettivo].

## 🎯 Behavior
Respond in a [tone] and focus on [obiettivo].

## 📚 Knowledge Base
Use vector database trained on [argomenti].

## 🧰 Tools
- Tool A: use to [funzione]
- Tool B: use to [funzione]

## 🔄 Example Interactions
**User**: [domanda]
**AI**: [risposta]
```

---

## ✍️ Tecniche di Prompting da includere

### ✅ Role Prompting

* Definisci chi è l'agente e la sua missione

### ✅ Few-shot Prompting *(opzionale)*

* Fornisci esempi utente–risposta
* Utile per output consistenti

### ✅ Definizione Strumenti

* Specifica strumenti disponibili
* Spiega quando usarli

### ✅ Inserimento Variabili

* Inserisci dinamicamente data/ora/utente (se serve)

---

## 🛠 Come generare un `system_prompt` personalizzato con GPT

### 🔨 GPT dedicato: “AI Agent System Prompts”

* Nome: **AI Agent System Prompts**
* Istruzioni caricate in markdown
* Include file `.md` con:

  * Ruolo
  * Comportamento
  * Tool usati
  * Esempi

### 📥 Prompt d’esempio fornito a GPT

> "I need a system prompt for a customer support agent with vector database trained on mugs"

### ✅ Output GPT (semplificato)

```markdown
# Role
You are a customer support AI for an online mug shop

## Behavior
Short, helpful, and friendly

## Knowledge Base
You have access to a vector DB with Q&A on mugs

## Tools
- Retriever Tool: fetch info about mug types
```

---

## 💡 Best Practices

| Linea guida                         | Descrizione                                               |
| ----------------------------------- | --------------------------------------------------------- |
| **Mantienilo corto**                | Solo info essenziali, evita sprechi di token              |
| **Usa Markdown**                    | Aiuta la formattazione e migliora leggibilità per l’LLM   |
| **Evita ridondanze**                | Non ripetere tool o istruzioni già note al modello        |
| **Non creare prompt "universali"**  | Personalizza per ciascun agente / caso d’uso              |
| **Non scrivere nulla se funziona!** | Non toccare il system prompt se l’agente è già affidabile |

---

## ✅ Conclusioni

* Il system prompt va **usato solo quando necessario**
* Usa markdown e struttura logica per chiarezza
* Testa SEMPRE senza prima, e aggiungi solo se:

  * L’agente fa errori
  * LLM non usa i tool giusti
  * Le risposte non sono nel tono/stile corretto

