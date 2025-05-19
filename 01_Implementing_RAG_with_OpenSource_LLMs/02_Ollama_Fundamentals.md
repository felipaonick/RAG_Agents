# 🧠 Guida Completa a Ollama: Setup Locale, Scelta dei Modelli e Esecuzione

Questa lezione fornisce una panoramica pratica e approfondita sull’uso di **Ollama** per eseguire **modelli LLM localmente**, controllare l'hardware disponibile, selezionare modelli adatti e configurare un server accessibile da applicazioni esterne come AnythingLLM, Flowise o terminale.

---

## 📦 1. Installazione di Ollama

### ✅ Procedura:

1. Vai su **[ollama.com](https://ollama.com)**
2. Clicca su **Download**
3. Scegli la versione per il tuo sistema operativo: **Windows / Mac / Linux**
4. Esegui l'installer (`.exe`, `.pkg`, ecc.)
5. Dopo l'installazione:

   * Ollama è **attivo in background**
   * Verifica la presenza dell'icona in basso a destra (Windows)
   * Per riaprirlo, cerca *"Ollama"* nel menu Start

---

## 🧪 2. Verifica Hardware (VRAM)

Per eseguire un modello LLM localmente, è importante verificare che la tua **VRAM** sia sufficiente.

### 🔍 Tool consigliato:

* **TechPowerUp GPU-Z** ([techpowerup.com](https://www.techpowerup.com/gpuz/))

  * Mostra memoria disponibile, tipo GPU e altre specifiche.

### 📌 Regola generale:

> **VRAM ≥ dimensione modello (in GB) × 1.1**

---

## 📥 3. Scaricare un Modello

### 🔍 Come trovare modelli:

1. Vai su [ollama.com/library](https://ollama.com/library)
2. Filtra per:

   * `Embeddings`, `Vision`, `Tools`, ecc.
   * Ordinamento: `Popular`, `Newest`
3. Seleziona il modello (es: `llama3`, `mistral`, `dolphin`, `gemma`)

### 🧠 Parametri importanti:

* **Parametri modello (es. 3B, 7B, 13B)** → più alto = più intelligente (generalmente)
* **Formato:**

  * `FP16`: modello completo, più preciso
  * `Q8`, `Q6`, `Q4`, `Q2`: versioni quantizzate → meno VRAM, ma meno precisi

### 🗂 Esempio:

| Modello           | Dimensione | Formato | VRAM richiesta |
| ----------------- | ---------- | ------- | -------------- |
| LLaMA 3.2 3B Q4   | 2.1 GB     | Q4      | ≥ 2.5 GB       |
| LLaMA 3.2 3B FP16 | 6.4 GB     | FP16    | ≥ 7 GB         |

---

## 💻 4. Usare il Terminale con Ollama

### 📌 Comandi fondamentali:

| Comando                 | Descrizione                                   |
| ----------------------- | --------------------------------------------- |
| `ollama pull modello`   | Scarica il modello desiderato                 |
| `ollama list`           | Elenca i modelli installati                   |
| `ollama run modello`    | Avvia un modello in modalità chat interattiva |
| `ollama rm modello`     | Rimuove un modello                            |
| `ollama show modello`   | Mostra tutte le caratteristiche del modello   |
| `ollama serve`          | Avvia il server API REST sulla porta 11434    |

---

## 🌐 5. Avviare il Server

Dopo aver installato un modello, puoi esporre un'**API compatibile con OpenAI** in locale:

```bash
ollama serve
```

* **Porta predefinita**: `http://localhost:11434`
* Può essere usata da:

  * AnythingLLM
  * Flowise
  * Postman
  * Terminale con `curl`

---

## 🧪 6. Esempio Pratico

1. Scarica un modello (es. LLaMA 3.2 3B Q4):

```bash
ollama pull llama3:3b-q4
```

2. Avvia il modello:

```bash
ollama run llama3:3b-q4
```

3. Chatta con il modello:

```bash
> Give me the code for snake
```

4. Avvia il server:

```bash
ollama serve
```

---

## 📚 7. Dolphin Models – Modelli Uncensored

* Basati su LLaMA (es. `dolphin-llama3-8b`)
* **Non censurati**: rispondono anche a prompt sensibili o controversi
* Ideali per:

  * Coding
  * Math
  * Funzioni generiche
  * Evitare filtri imposti da provider cloud

---

## 📁 8. Info Modelli & Documentazione

Consulta il repository ufficiale:

* [GitHub - Ollama](https://github.com/ollama/ollama)

### Contenuti utili:

* Comandi CLI
* Documentazione Docker
* API Reference
* Modelli supportati
* Quantizzazione (`gguf` format)

---

## ✅ Riepilogo Finale

| Step                   | Descrizione                             |
| ---------------------- | --------------------------------------- |
| ✅ Installa Ollama      | Dal sito ufficiale                      |
| ✅ Verifica la tua VRAM | Usa TechPowerUp GPU-Z                   |
| ✅ Scegli un modello    | Usa FP16 per qualità, Q4 per leggerezza |
| ✅ Scarica ed esegui    | `ollama pull`, `ollama run`             |
| ✅ Avvia il server      | `ollama serve` per endpoint locale      |
| ✅ Integra in altre app | AnythingLLM, Flowise, terminale, ecc.   |
