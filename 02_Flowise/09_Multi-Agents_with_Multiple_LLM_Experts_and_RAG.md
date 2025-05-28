# 🧠 Multi-Agent System in Flowise: Appunti Completi

## ✅ Introduzione

In precedenza abbiamo costruito agenti singoli con strumenti come il Tool Agent per creare applicazioni RAG. Con il sistema **Multi-Agent**, possiamo strutturare flussi di lavoro più sofisticati basati su un **Supervisor** (CEO) e vari **Worker** (specializzati per compiti precisi). Questo modello riflette una struttura aziendale: il Supervisor assegna compiti e coordina i Worker.

---

## ⚙️ Architettura Multi-Agent

### 👤 Supervisor
- Funziona da "capo" dell’organizzazione.
- Riceve la richiesta utente.
- Smista il lavoro ai Worker appropriati.
- Può avere un modello LLM avanzato di ragionamento (es: Claude 3, GPT-4, O3-mini).

### 👷 Worker
- Ogni Worker ha un compito ben definito.
- Esempi:
  - **Research Worker**: interroga una vector DB.
  - **Web Search Worker**: fa ricerche online (es. Brave Search).
  - **Creative Writer**: genera articoli o post.
  - **Social Media Agent**: pubblica contenuti via Compose.io.
- Ogni Worker può usare un **modello diverso** (es: GPT-4 per il writer, O3-mini per ricerca) e un **system prompt** specifico.

---

## 🏗️ Costruzione in Flowise

1. **Vai su Agent Flows > Add New**
2. **Inserisci un Supervisor**
   - Collega un modello abilitato al tool calling (es. O3-mini, GPT-4).
   - Aggiungi eventuale `system_prompt` con regole di orchestrazione.
3. **Aggiungi uno o più Worker**
   - Assegna nome, modello e prompt specifico.
   - Ogni Worker riceve il suo `system_prompt`.

---

## 🧠 Esempio Multi-Agent con 3 Worker

### Prompt Utente:
> “Cerca informazioni su prompt engineering per LLMs e diffusion models. Scrivi un articolo e salvalo localmente.”

### Architettura:

- 🧑‍💼 **Supervisor (CEO)**: O3-mini  
- 👷‍♂️ **Worker 1 - Vector DB Researcher**  
  - Tool: retriever (document store)
  - Modello: O3-mini
- 👷‍♂️ **Worker 2 - Internet Research Specialist**  
  - Tool: Brave Search API  
  - Modello: O3-mini
- 👷‍♀️ **Worker 3 - Blog Post Writer**  
  - Tool: Write file to disk  
  - Modello: Claude 3.7 Sonnet

---

## 🛠️ Prompt Engineering Team (Template già disponinbile nel marketplace)

Abbiamo un supervisor, che prende le istruzioni date dall'utente per generare dei system prompts, e coordina 2 worker:

1. **Prompt Creator**: per creare prompt specifici.
2. **Prompt Reviewer**: per rivedere e migliorare i prompt.

---

## 📝 Esempio di system prompts generati dal prompt engineering team

### Richiesta dell'utente: 
> I want to build an app with 3 workers.
> The first worker has access to a vector database and should search it for the topic of Prompting Engineering for LLMs and Diffusion Models.
> The second worker should have internet access via Brave search tool.
> The third worker should write a detailed blog post with good structure and save it locally. 

### Output del Prompt Engineering Team:
```text
AGENT 1

Name:

Vector Database Researcher

System Prompt:

As a Vector Database Researcher, your mission is to explore the vector database to extract pertinent information on the topic of Prompting Engineering for LLMs and Diffusion Models. Utilize advanced search techniques to identify and retrieve data that provides insights into the latest advancements, methodologies, and applications in this field. Your role is crucial in establishing a solid foundation for further exploration and content creation.

Instructions:

Conduct a comprehensive search in the vector database for information related to Prompting Engineering for LLMs and Diffusion Models.
Focus on retrieving data that highlights key concepts, techniques, and recent developments.
Produce a detailed report summarizing the findings, emphasizing significant trends, methodologies, and notable case studies or applications.
Ensure accuracy by relying solely on verified information.
Pass the summarized findings to the Internet Researcher.

AGENT 2

Name:

Internet Researcher

System Prompt:

As an Internet Researcher, your role is to build upon the foundational knowledge provided by the Vector Database Researcher. Using the Brave search tool, access the internet to gather additional insights, recent articles, and expert opinions on Prompting Engineering for LLMs and Diffusion Models. Your efforts will enrich the understanding of the topic and provide a broader perspective.

Instructions:

Utilize the Brave search tool to find recent articles, papers, and discussions on the topic.
Gather a variety of perspectives, including expert opinions, industry applications, and emerging trends.
Produce a comprehensive summary of your internet research, highlighting new insights and perspectives that complement the initial findings.
Ensure accuracy by relying solely on verified information.
Pass the summarized findings to the Blog Post Writer.

AGENT 3

Name:

Blog Post Writer

System Prompt:

As a Blog Post Writer, your task is to craft a detailed and well-structured blog post on the topic of Prompting Engineering for LLMs and Diffusion Models. Drawing from the reports provided by the Vector Database Researcher and Internet Researcher, create content that is informative, engaging, and accessible to a broad audience. Your writing will play a key role in disseminating knowledge and sparking interest in this field.

Instructions:

Use the detailed reports from the Vector Database Researcher and Internet Researcher to write a blog post covering the key aspects of the topic.
Ensure the content is well-organized, with clear sections that guide the reader through the topic.
Include an introduction, main body with subheadings, and a conclusion that summarizes the findings and suggests future directions.
Ensure accuracy by relying solely on verified information.
Save the polished blog post locally, ready for publication.
Maintain an engaging, informative tone suitable for readers interested in advanced AI topics.

Annotations and Explanations:

Clarity and Consistency: The instructions for each agent have been standardized to ensure clarity and consistency across all roles. This makes it easier for each agent to understand their specific tasks and responsibilities.

Instruction Structure: Each agent's instructions are now divided into clear bullet points, making them easier to follow and execute.

Emphasis on Accuracy: Reiterated the importance of using verified information to maintain the credibility and reliability of the output.

Output Specifications: Clearly defined the expected output for each agent, ensuring that the final deliverable is well-structured and meets the intended purpose.
```

---

## 📥 Utilizziamo i tre system prompts creati 

Come suggerito dal Prompt Engineering Team, possiamo ora costruire il nostro flusso in Flowise.

1. Al primo worker assegniamo il nome "Vector Database Researcher", il system prompt creato, il modello più adatto (modello di embedding usato da pinecone), ed il tool che recupera informazioni dal database vettoriale.
2. Al secondo worker assegniamo il nome "Internet Researcher", il system prompt creato, il modello più adatto (GPT o3-mini lo stesso del supervisor quindi non serve collegarlo) ed il tool Brave Search.
3. Al terzo worker assegniamo il nome "Blog Post Writer", il system prompt creato, il modello più adatto (Claude sonnet 3.7 via OpenRouter) ed il tool per scrivere file localmente. Se invece di scrivere un file locale si vuole scrivere direttamente il post su un social, si può usare Compose.io.
4. Colleghiamo i worker al Supervisor, che li attiverà in sequenza in maniera iterativa (ciclando).

5. Possiamo migliorare anche il system prompt del Supervisor, in modo che sappia come attivare i worker e cosa aspettarsi da loro.
```text
You are a supervisor tasked with managing a conversation between the following workers: {team_members}.
Given the following user request, respond with the worker to act next.
Each worker will perform a task and respond with their results and status.
When finished, respond with FINISH.
Select strategically to minimize the number of steps taken.

You have 3 workers.

Use the Vector Database Researcher to search info about prompting first.
Use the Internet Researcher to search other topics.
Use the Blog Post Writer always last after you have your info.
```

---

## 🧪 Esempi di Test

### Esempio 1:

> “How to write diffusion prompts?”

* Il Supervisor attiva Worker 1 (vector DB) per recuperare informazioni sui prompt di diffusione.
* IL Worker 1 restituisce i dati e il Supervisor li passa a Worker 2 (Brave Search) per ulteriori ricerche online.
* Poi attiva Worker 3 (Blog Writer) per scrivere l'articolo in locale nel file `diffusion_prompting_guide.md`.
* Il Supervisor vede che i Worker hanno completato i loro compiti e risponde con `FINISH`, quindi restituisce il risulato finale ovvero la risposta del worker 3.

### Esempio 2:

> “Search Tesla news and write a blog post.”

* Il Supervisor attiva Worker 2 (Brave Search).
* Worker 2 cerca le ultime notizie su Tesla e genera un summary e restituisce i risultati al Supervisor.
* Il Supervisor passa i risultati a Worker 3 (Blog Writer).
* Worker 3 scrive un articolo dettagliato basato sui risultati di ricerca.
* Articolo salvato in `tesla_news_blog_post.md`.
* Il Supervisor risponde con `FINISH` e restituisce il risultato finale ovvero la risposta del worker 3.

---

## 🧩 Errori Comuni

* **Prompts mal definiti** → I worker agiscono in modo errato.
* **Worker senza nomi coerenti** → Il Supervisor non li identifica.
* **System Prompt troppo specifico o mancante** → Incertezza sul flusso.

---

## 🧠 Benefici del Multi-Agent System

* **Specializzazione**: ogni LLM esegue un compito specifico.
* **Efficienza**: modelli più leggeri per compiti semplici.
* **Flessibilità**: strumenti e modelli personalizzati per ogni worker.
* **Estendibilità**: puoi aggiungere Compose.io per integrazioni API complesse.

---

## 📌 Considerazioni Finali

* 🔁 Puoi espandere il sistema con più Worker e tool.
* 🎯 Ottieni output di alta qualità grazie a modelli mirati per ciascun ruolo.
* 💾 Personalizza il salvataggio locale o automatizza la pubblicazione.
* 🔍 Il Supervisor deve avere un prompt chiaro per garantire la corretta esecuzione dei compiti.

---

## 📤 Esportazione

Una volta completata la configurazione, premi `Export Agent` per salvare il flusso.

> 💡 **Tip finale**: Inizia i prompt con una richiesta generica (“News su Tesla”) per far agire il Supervisor in modo dinamico, senza sequenze pre-impostate.

