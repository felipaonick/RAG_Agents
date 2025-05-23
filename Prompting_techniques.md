## 🧠 Tecniche di Prompting

[Prompting Techniques](https://www.promptingguide.ai/techniques)

### 🔹 1. Zero-shot Prompting

**Descrizione**: Si fornisce al modello solo l’istruzione, senza esempi.

**Vantaggi**:

* Semplice e immediato.
* Utile per compiti generici.([educational--academy.blogspot.com][1])

**Limiti**:

* Meno preciso in compiti complessi o specializzati.

---

### 🔹 2. Few-shot Prompting

**Descrizione**: Il prompt include alcuni esempi di input/output per guidare il modello.([SlideServe][2])

**Vantaggi**:

* Aumenta l’accuratezza fornendo contesto.
* Migliora le prestazioni su compiti specifici.([Marketing Hackers][3])

**Limiti**:

* Richiede spazio nel prompt.
* Necessita di selezione accurata degli esempi.

---

### 🔹 3. Chain-of-Thought (CoT) Prompting

**Descrizione**: Si guida il modello a ragionare esplicitamente in più passaggi intermedi per arrivare alla risposta finale.

**Vantaggi**:

* Migliora la performance su compiti logici e matematici.
* Favorisce una maggiore trasparenza nel processo decisionale del modello.

**Limiti**:

* Può allungare la risposta.
* Non sempre migliora l'output in compiti semplici.([educational--academy.blogspot.com][1])

---

### 🔹 4. Self-Consistency

**Descrizione**: Si generano più catene di ragionamento e si seleziona la risposta più comune tra quelle generate.

**Vantaggi**:

* Riduce risposte incoerenti o casuali.
* Migliora l'affidabilità delle risposte in compiti complessi.([Prompting Guide][4])

**Limiti**:

* Richiede più inferenze, aumentando i costi computazionali.

---

### 🔹 5. Tree of Thoughts (ToT)

**Descrizione**: Estensione del CoT che esplora diramazioni di pensiero come un albero, permettendo esplorazione e valutazione di diverse linee di ragionamento.

**Vantaggi**:

* Potente per la risoluzione di problemi complessi.
* Permette una valutazione più approfondita delle opzioni disponibili.

**Limiti**:

* Complessità implementativa.
* Richiede maggiore potenza computazionale.

---

### 🔹 6. Prompt Chaining

**Descrizione**: Sequenza di prompt in cui l’output di uno diventa input del successivo, consentendo operazioni o trasformazioni successive.([SlideServe][2])

**Vantaggi**:

* Modularità e controllo dei passaggi logici.
* Adatto per compiti complessi suddivisi in sottocompiti.

**Limiti**:

* Può accumulare errori lungo la catena.
* Richiede una progettazione attenta della sequenza di prompt.

---

### 🔹 7. Retrieval Augmented Generation (RAG)

**Descrizione**: Il modello interroga un database o documenti esterni e utilizza le risposte nel prompt per generare output più informati.

**Vantaggi**:

* Risposte più aggiornate e specifiche.
* Riduce le "allucinazioni" del modello.([Marketing Hackers][3])

**Limiti**:

* Richiede un sistema di recupero informazioni esterno.
* Complessità nell'integrazione tra modello e sistema di retrieval.

---

### 🔹 8. ReAct

**Descrizione**: Combina ragionamento e azione, permettendo al modello di interagire con strumenti esterni durante il processo decisionale.

**Vantaggi**:

* Modello può interagire con ambienti esterni.
* Adatto per compiti che richiedono interazione dinamica.

**Limiti**:

* Richiede orchestrazione complessa.
* Potenziale aumento della latenza nelle risposte.

---

### 🔹 9. Meta Prompting

**Descrizione**: Si chiede al modello di generare o migliorare i prompt stessi, automatizzando la creazione di prompt efficaci.

**Vantaggi**:

* Automazione nella creazione di prompt efficaci.
* Può adattarsi a diversi compiti e contesti.

**Limiti**:

* Richiede validazione manuale dei prompt generati.
* Possibile generazione di prompt subottimali senza supervisione.

---

### 🔹 10. Reflexion

**Descrizione**: Il modello valuta la propria risposta e cerca di migliorarla attraverso un processo di auto-riflessione.

**Vantaggi**:

* Migliora accuratezza e coerenza delle risposte.
* Favorisce l'autocorrezione e l'apprendimento continuo.

**Limiti**:

* Aumenta il tempo di inferenza.
* Richiede meccanismi per valutare l'efficacia della riflessione.

---

### 🔹 11. Graph Prompting

**Descrizione**: Struttura il ragionamento del modello come un grafo di concetti, facilitando la comprensione di relazioni complesse.

**Vantaggi**:

* Efficace su compiti complessi interconnessi.
* Permette una visualizzazione chiara delle relazioni tra concetti.([SlideServe][2])

**Limiti**:

* Implementazione avanzata.
* Richiede strumenti per la gestione e la visualizzazione dei grafi.([LinkedIn][5])

---

### 🔹 12. Program-Aided Language Models (PALM)

**Descrizione**: Il modello scrive codice per risolvere task e ne interpreta l’output, combinando capacità linguistiche e computazionali.

**Vantaggi**:

* Precisione nei task computazionali.
* Adatto per compiti che richiedono calcoli o manipolazioni di dati.

**Limiti**:

* Richiede capacità di eseguire codice.
* Potenziali rischi di sicurezza nell'esecuzione di codice generato.

---

### 🔹 13. Automatic Prompt Engineer (APE)

**Descrizione**: Algoritmi che generano automaticamente prompt ottimizzati per specifici compiti o modelli.

**Vantaggi**:

* Efficienza e scalabilità nella creazione di prompt.
* Adattabilità a diversi contesti e modelli.

**Limiti**:

* I risultati possono variare in qualità.
* Necessità di supervisione per garantire l'efficacia dei prompt generati.

---

### 🔹 14. Active-Prompt

**Descrizione**: Seleziona dinamicamente esempi o strategie durante il prompting, adattandosi alle esigenze del compito.

**Vantaggi**:

* Adattivo e performante.
* Migliora la pertinenza delle risposte in contesti variabili.

**Limiti**:

* Necessita un controller o feedback loop.
* Complessità nella progettazione del sistema di selezione dinamica.

---

### 🔹 15. Directional Stimulus Prompting (DSP)

**Descrizione**: Modella un’influenza intenzionale nelle risposte tramite stimoli mirati, guidando il modello verso determinate direzioni.

**Vantaggi**:

* Utile in contesti etici o di controllo.
* Permette di indirizzare il modello verso risposte desiderate.

**Limiti**:

* Richiede test e raffinamento.
* Possibile riduzione della creatività o spontaneità del modello.([Prompting Guide][6])

---

Ecco la continuazione del riepilogo dettagliato delle tecniche di prompting, completando la sezione sulle tecniche avanzate:

---

### 🔹 16. **Multimodal Chain-of-Thought (CoT)**

**Descrizione**:
Estensione del Chain-of-Thought applicata a input multimodali, in cui il modello elabora contemporaneamente testo e immagini per eseguire ragionamenti step-by-step. Utilizzato in modelli vision-language.

**Vantaggi**:

* Integra la comprensione visiva con il ragionamento logico-testuale.
* Ideale per task complessi che coinvolgono diagrammi, grafici, disegni tecnici, o scene visive.
* Permette spiegazioni passo-passo anche per contenuti visuali (es. "spiega cosa accade in questa scena").

**Limiti**:

* Richiede modelli addestrati su dati multimodali (es. GPT-4V, Qwen-VL, MiniCPM-V).
* Maggiore complessità computazionale.
* Ancora poco standardizzato e supportato nei tool di prompt engineering.

---

### 🔹 17. **Automatic Reasoning and Tool-use (ART)**

**Descrizione**:
Tecnica che consente al modello di ragionare automaticamente e decidere se usare strumenti esterni per completare un compito. Rientra nella categoria dei Tool-augmented LLMs.

**Vantaggi**:

* Estende notevolmente le capacità del modello combinando LLM + tool esterni (API, calcolatori, search engine).
* Molto utile in agent frameworks (es. LangChain, LangGraph, AutoGen).

**Limiti**:

* Richiede tool registry e gestione dell'invocazione.
* Errori nei tool esterni possono influire negativamente sull'output.

---

### 🔹 18. **Graph Prompting**

**Descrizione**:
Tecnica che struttura la conoscenza in forma di grafo concettuale, che viene poi codificato nel prompt. Adatta a task che richiedono relazioni complesse tra concetti, come Q\&A su knowledge graph o reasoning ontologico.

**Vantaggi**:

* Altamente esplicativo.
* Perfetto per relazioni logiche complesse (es. in medicina, legge, bioinformatica).

**Limiti**:

* Creazione manuale o automatica del grafo può essere costosa.
* Necessita modelli capaci di interpretare testo strutturato da grafi.

---

### 🔹 19. **Program-Aided Language Models (PALM)**

**Descrizione**:
Tecnica in cui il modello viene aiutato da un esecutore di codice (es. Python, SQL). Il modello genera del codice che risolve il problema, e il risultato del codice viene usato per produrre la risposta.

**Vantaggi**:

* Altissima accuratezza in task computazionali (math, data analysis, stats).
* Approccio interpretabile.

**Limiti**:

* Necessita sandbox sicuro per l’esecuzione del codice.
* Rischio di codice errato o dannoso se non controllato.

---

### 🔹 20. **Automatic Prompt Engineer (APE)**

**Descrizione**:
Sistema che automatizza la generazione e l’ottimizzazione dei prompt tramite ricerca evolutiva, reinforcement learning o gradient-free optimization.

**Vantaggi**:

* Rimuove il trial-and-error umano nella scrittura di prompt.
* Utile per task altamente ripetitivi o su larga scala.

**Limiti**:

* Può richiedere molte iterazioni di prova.
* Prompt generati possono non essere sempre interpretabili o generalizzabili.

---

### 🔹 21. **Active-Prompt**

**Descrizione**:
Tecnica in cui il prompt viene adattato dinamicamente durante l’inferenza, sulla base di input, feedback o caratteristiche del task.

**Vantaggi**:

* Maggiore adattabilità.
* Migliora performance su dati non visti o in contesti mutevoli.

**Limiti**:

* Necessita controller che valuta continuamente il contesto.
* Più difficile da testare e validare.

---

### 🔹 22. **Directional Stimulus Prompting (DSP)**

**Descrizione**:
Tecnica per dirigere intenzionalmente il modello verso una classe di risposte, usando stimoli strutturati (es. esempi positivi, contrasti, segnali guida).

**Vantaggi**:

* Ottimo per controllare il tono, la direzione o la sensibilità del modello.
* Utile in ambiti normativi o etici.

**Limiti**:

* Richiede tuning empirico dei segnali guida.
* Potrebbe ridurre la diversità di risposte.