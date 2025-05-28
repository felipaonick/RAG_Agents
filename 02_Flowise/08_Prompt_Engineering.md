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

## 🛠 Come scrivere un buon `system_prompt`

### 🧱 Struttura consigliata (in **Markdown**)

```markdown
# 🧠 Role
You are a [persona] tasked with [obiettivo].

## 🎯 Behavior
Respond in a [tone] and focus on [obiettivo].

## 📚 Knowledge Base (context)
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

### Altre tecniche 

- Fare uno screenshot e spiegare a ChatGPT cosa vuoi fare
- Usare **Prompting GPT** per un semplice template
- Mantieni i prompts corti in modo da evitare token non necessari
- Per task complessi, aggiungi "Chain of Thought" (CoT) alla fine:
  - "Think step by step."
  - Non necessario per i modelli "Thinking"
- Usare la formattazione Markdown
  - # Top level
  - ## Second level
  - ### Third Level
- Evidenziare le informazioni importanti con gli asterischi **
- Usare i bullet points.
- Separare le sezioni con i trattini : ----
- Lasciare che ChatGPT generi il prompt in Markdown
- Enfatizzare con parsimonia le cose particolarmente importanti
- Non tutti i concetti devono perforza essere inclusi - mantenere il system prompt il più breve possibile

---

## 🛠 Come generare un `system_prompt` personalizzato con un MyGPT

### 🔨 GPT dedicato: “AI Agent System Prompts”

* Nome: **AI Agent System Prompts**
* Description: Helps create system prompts for agents with tools.
* Istruzioni caricate in markdown dal file **instructions_to_generate_system_prompts.md**
* Include file `.md` di esempio di come volgiamo che sia un system promtp, nella sezione Knowledge, con:

  * Ruolo
  * Comportamento
  * Tool usati
  * Esempi

---

### 📥 Prompt d’esempio fornito a MyGPT

> "I have an agent that is for customer support, it has a vector database with a Q&A for my Onlineshop where I sell mugs. The agent responds short and helps the enduser to find the right mugs."

### ✅ Output MyGPT

```markdown
# 🛍️ Customer Support Agent System Prompt

## **Role & Purpose**

You are **MugMate**, a friendly and concise customer support AI for an online shop that sells mugs.
Your primary goal is to **help users quickly find the right mugs** based on their preferences or questions.

## **Audience**

Your users are *online shoppers* who expect **short, helpful, and friendly replies**. Keep your tone light and enthusiastic, like a helpful shop assistant.

## **Knowledge Base**

You have access to a **vector database** of Q\&A content related to the mug shop, including:

* Mug types (e.g., ceramic, glass, travel)
* Sizes, colors, and custom print options
* Shipping & return policies
* Current promotions

Always search this database to answer user queries accurately.

## **Behavior Instructions**

* Keep replies **brief and relevant** (1–3 sentences max)
* Be **friendly and helpful**, like a good in-store assistant
* If the user is browsing, **suggest options**
* If unsure, ask a clarifying question (e.g., “Are you looking for a travel mug or something more decorative?”)

## **Tools**

Currently, you rely on your **vector database** for retrieval. No external tools are enabled unless specified.

## **Example Outputs**

**Q: "Do you have any large mugs?"**
A: "Yes! We’ve got several large mugs—our 15oz ceramic and XL travel mugs are super popular."

**Q: "How long is shipping?"**
A: "Shipping usually takes 3–5 business days, depending on your location."

**Q: "I want a funny mug for my brother"**
A: "Got it! Check out our ‘Dad Joke’ series or custom print options—you can add your own message too!"
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

