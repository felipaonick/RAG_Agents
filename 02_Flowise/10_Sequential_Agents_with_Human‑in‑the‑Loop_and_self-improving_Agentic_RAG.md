# Agenti Sequenziali 🚶‍♂️💻

## Introduzione agli Agenti Sequenziali 🎬

Gli **agenti sequenziali** sono simili al framework multi-agente, ma con una differenza fondamentale: invece di avere un CEO che coordina i worker, ogni agente lavora in sequenza, uno dopo l'altro. Questo tipo di approccio permette una struttura di flusso più chiara e organizzata.

### Differenze rispetto agli Agenti Multi-Agente 🤖

* **Agenti Multi-Agente**: Un CEO coordina il lavoro di diversi agenti (worker) che eseguono compiti distinti, comunicando tra loro.
* **Agenti Sequenziali**: I compiti vengono eseguiti in sequenza, partendo da un nodo iniziale (start) e proseguendo con gli agenti uno dopo l'altro fino al nodo finale (end), senza la necessità di un CEO che assegni i compiti.

---

## Creazione di un Flusso con Agenti Sequenziali 🔄

### Struttura del Flusso Sequenziale 🧩

In un flusso sequenziale, la struttura di base include:

1. **Nodo di inizio (Start Node)**: Ogni flusso sequenziale deve partire da un nodo iniziale.
2. **Nodo di fine (End Node)**: Ogni flusso deve terminare con un nodo finale.
3. **Agenti**: I compiti vengono assegnati agli agenti in sequenza, da un nodo all'altro.

### Passaggi per Creare un Flusso Sequenziale 🚀:

1. **Inizia con il Nodo di Partenza** 🔑:

   * Ogni flusso sequenziale deve iniziare con un nodo di partenza.
2. **Aggiungi Agenti** 🧠:

   * Ogni agente può eseguire un compito specifico, come una ricerca, una scrittura o l'uso di uno strumento.
3. **Collega gli Agenti** 🔗:

   * Gli agenti vengono collegati uno dopo l'altro, formando una sequenza che va dal nodo di partenza al nodo finale.
4. **Nodo di Fine** ⏹️:

   * Ogni flusso deve terminare con un nodo di fine per completare il ciclo.

---

## Utilizzo 🛠️

### Aggiungere un Modello di Chat 🗣️

Puoi aggiungere un modello di chat per ogni agente, come **OpenAI**:

* Seleziona un nodo di chat, come **OpenAI Chat Model**, e collegalo al flusso.
* Imposta le credenziali, la temperatura del modello e le opzioni di caricamento delle immagini.
* Puoi anche utilizzare modelli come GPT-4 o GPT-3 mini, a seconda delle esigenze.

### Aggiungere Memoria dell'Agente 🧠

Puoi scegliere di usare un sistema di memoria per salvare i dati tra gli agenti:

* **SQLite** è un'opzione semplice per memorizzare lo stato tra i vari passaggi del flusso.
* La memoria permette di mantenere informazioni durante il ciclo di vita del flusso.

### Aggiungere Stato ⚙️

Lo stato è un oggetto che viene aggiornato man mano che i nodi vengono eseguiti:

* Lo stato può essere utilizzato per memorizzare valori dinamici come nomi, risposte e altre informazioni.
* Ogni nodo può aggiornare lo stato e passarlo al nodo successivo.

---

## Strumenti 🧰

### Utilizzo di Calcolatori e API 💻

Puoi integrare strumenti esterni, come calcolatori o API:

* Aggiungi un **calcolatore** o qualsiasi altro strumento come API esterne per eseguire calcoli o raccogliere dati.

### Flusso Completo di Agenti Sequenziali 🔄

Un esempio semplice di flusso sequenziale prevede un agente che fa una ricerca, un altro che scrive un contenuto, e un altro che pubblica sui social media. Ogni agente si attiva solo quando il precedente ha terminato il proprio compito. Puoi anche utilizzare modelli LLM differenti per ogni agente, personalizzando gli strumenti e le funzionalità in base al compito.

---

## Human in the Loop 👤

### Cos'è il "Human in the Loop"? 🤔

Quando un agente deve eseguire un'azione che potrebbe avere un impatto importante, come inviare una mail o modificare un calendario, è possibile inserire una **verifica umana** prima di proseguire.

### Funzionamento 🔄:

1. Un agente richiede approvazione prima di eseguire una determinata azione.
2. L'utente ha la possibilità di **approvare** o **rifiutare** l'azione.
3. Se l'azione è approvata, l'agente continua l'esecuzione; altrimenti, l'operazione viene interrotta.

### Esempio Pratico 📧:

Se un agente deve inviare una mail, prima chiederà all'utente se desidera procedere con l'invio. Questo meccanismo è utile per prevenire azioni non volute, specialmente per compiti sensibili come inviare email o fare modifiche su calendari.

---

## Creazione di Flussi in Sequenza 🔄🔄

Puoi aggiungere più agenti al flusso sequenziale, che verranno eseguiti uno dopo l'altro:

1. **Agente 1**: Esegue il primo compito, ad esempio, una ricerca.
2. **Agente 2**: Esegue un altro compito, come scrivere un articolo.
3. **Agente 3**: Pubblica il contenuto sui social media.

Ogni agente si attiva solo quando il precedente ha terminato il proprio compito. Puoi anche utilizzare modelli LLM differenti per ogni agente, personalizzando gli strumenti e i system prompts in base al loro compito.

In questo modo non abbiamo un Supervisor centrale che decide quale agente attivare, ma ogni agente viene attivato uno dopo l'altro in sequenza, in questo modo abbiamo il controllo sul flusso.

---

## Aggiunta di Condizioni al Flusso 🛑

### Condizioni nel Flusso 🔄

Puoi aggiungere un **nodo di condizione** per determinare quale percorso un agente deve seguire:

* Ad esempio, puoi usare una condizione per verificare se un determinato valore supera una certa soglia (es. un calcolo).
* In base al risultato della condizione, puoi dirigere il flusso verso agenti diversi.
* Questa condizione verso quale strada del fullo intraprendere può essere decisa da una semplice **funzione** che decidiamo noi oppure da un **agente** che decide quale rotta seguire.

---

## Esempio di Flusso con Condizione 📊

1. **Inizio** 🏁: Un agente riceve una richiesta.
2. **Condizione** 🔍: Il valore calcolato è maggiore o minore di una certa soglia.
3. **Agenti** 👥: A seconda del risultato della condizione, vengono attivati agenti differenti per continuare l'elaborazione.
4. **Fine** 🏁: Il flusso si conclude con un nodo di fine.

---

## Workflows dal Marketplace 🛒

### Esempio di Workflow: Human in the Loop con RAG 🌐

Questo workflow utilizza un sistema **Human in the Loop** e **Retrieval-Augmented Generation (RAG)**:

1. Un **agente finanziario** analizza i dati da una **memoria vettoriale** (ad esempio, Pinecone).
2. Un altro **agente di ricerca** cerca ulteriori informazioni su Google.
3. L'agente finanziario prima di usare il suo tool, viene chiesto all'utente di approvare o rifiutare l'azione.
4. Dopo l'approvazione, l'agente finanziario esegue la ricerca nel vectorstore circa domande su Apple e fornisce la risposta all'agente di ricerca.
5. L'agente di ricerca fornisce la risposta finale all'utente.

### Esempio di Workflow: Self-Improving RAG 🔄

Un altro esempio è un agente **self-improving** che migliora continuamente fino a trovare la risposta corretta. Se la risposta è incompleta o errata, l'agente rielabora la query e cerca nuovamente, fino a trovare la risposta giusta.

è esattamente come avevamo fatto con **self-RAG** fatto programmaticamente con LangGraph, ma fatto con **Flowise**.

**Importante**: Quì il ToolNode è collegato a due tools che usano due Vector Database diversi, uno per i documenti di Apple e l'latro per documenti di Tesla.

---

## Conclusione 🎯

In questo video, abbiamo esplorato:

* **Agenti sequenziali** che lavorano uno dopo l'altro in un flusso definito.
* **Human in the Loop** per approvare azioni sensibili.
* L'uso di **condizioni** per determinare quale percorso seguire.
* Flussi avanzati come il **self-improving RAG** e **Human in the Loop RAG**.

Puoi creare flussi complessi, combinando agenti sequenziali con condizioni, approvazioni umane, e vari strumenti, per costruire applicazioni AI molto potenti e personalizzabili.

