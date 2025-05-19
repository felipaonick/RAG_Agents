## 🧠 **Obiettivo del video**

Installare e configurare **AnythingLLM** localmente e integrarlo con **Ollama**, per costruire applicazioni RAG private e gratuite sul proprio PC.

---

## 🔧 **Installazione di AnythingLLM**

1. **Download**:

   * Cerca “AnythingLLM” su Google.
   * Accedi al sito ufficiale.
   * Clicca su **Download for Desktop**.
   * Scegli il tuo sistema operativo (es. Windows).

2. **Installazione**:

   * Lancia l’eseguibile (`AnythingLLM Desktop .exe`).
   * Conferma i passaggi dell’installazione.
   * AnythingLLM si avvia e installa automaticamente i pacchetti richiesti per Ollama.

---

## 🖥️ **Interfaccia di AnythingLLM**

* Simile a ChatGPT:

  * Sidebar per i workspace (progetti/conversazioni).
  * Campo input per chat e pulsante per caricare documenti.
  * Possibilità di creare nuovi thread per ogni workspace.

---

## ⚙️ **Configurazione iniziale**

### 1. **Modello LLM (Ollama)**

* Vai su **Settings > LLM Provider**:

  * Scegli “Ollama” come provider.
  * Seleziona il modello installato (es. `llama3.2:fp16`).
  * Inserisci correttamente la **Ollama Base URL** (es: `http://localhost:11434` o quello mostrato nel terminale con `ollama serve`).

### 2. **Vector Database**

* Seleziona **LanceDB**: funziona completamente offline ed è integrato.

### 3. **Embedder**

* Seleziona **AnythingLLM Embedder**: locale e gratuito.
* Evita OpenAI per ora, poiché richiede API Key.

### 4. **Text Chunking**

* Chunk Size: `1000`
* Chunk Overlap: `20`
* (Ulteriori ottimizzazioni verranno spiegate nei video successivi).

### 5. **Speech & Transcription**

* Speech: lascia impostato su **Local Whisper**.
* Transcription: usa l’opzione integrata (evita API esterne).

---

## 🛠️ **Abilitare le Agent Skills**

* Vai su **Settings > Agent Skills**:

  * Abilita: RAG, Long-Term Memory, Web Scraper, File Generator, Chart Generator, Web Search, SQL connector, ecc.
  * Obiettivo: avere tutto pronto per il tuo sistema RAG personalizzato.

---

## 🎨 **Altre Impostazioni**

* **System Prompt**:

  * Personalizzabile come in ChatGPT.
  * Può includere variabili come data, ora, ecc.
* **Lingua e Tema**: modificabili da “Customization”.

---

## ✅ **Test rapido del setup**

1. Entra in un workspace.
2. Invia un prompt (es: “Hey”).
3. Ricevi risposta dal modello locale LLaMA configurato via Ollama.

---

## 📌 **Note aggiuntive**

* Tutte le impostazioni restano **locali e private**.
* **AnythingLLM non usa cloud** o servizi esterni se non configurati esplicitamente.
* Le funzionalità avanzate (MCP, agent flows) saranno esplorate in altri strumenti (es. Flowise) perché meglio implementate lì.

---

## 🔜 **Prossimi step**

* Costruire un’applicazione RAG completa all’interno di AnythingLLM.
* Approfondire la gestione di chunking e overlap.


