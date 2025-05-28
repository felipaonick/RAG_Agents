# 🧠 Flowise – Creare una Standalone Application

In questo video viene spiegato come trasformare un chatbot creato con **Flowise** in un'applicazione standalone o incorporarlo in una pagina web. Di seguito gli appunti dettagliati:

---

## ✅ Obiettivo

* Rendere il chatbot accessibile tramite un'interfaccia autonoma (standalone app)
* Possibilità di **incorporare** (embed) il chatbot in:

  * HTML popup
  * HTML full page
  * React popup
  * React full page
  * Webhook (`curl`)
  * App Python/JavaScript

---

## 🔧 Condivisione e Avvio dell’App

1. **Accedi al tuo Chat Flow**
2. Clicca su **“Share Chatbot”**
3. Per renderlo utilizzabile:

   * Imposta **“Make Public”** per rimuovere il login username/password
   * Ottieni un link pubblico (funziona solo se il server è online!)
   * Esempio output:

     * Interfaccia a destra → domande/risposte
     * A sinistra → messaggio introduttivo

> ⚠️ Se Flowise è in esecuzione in locale (via Node.js), **nessun altro può accedere al chatbot**. Serve l’hosting (es. Render, VPS, ecc.)

---

## 🎨 Personalizzazione Interfaccia

### 🧾 Titolo e Avatar

* Cambia il **nome del bot** → es. “Prompting Bot”
* Inserisci un'immagine avatar tramite URL

### 🎨 Colori

* Cambia:

  * Colore sfondo titolo
  * Colore testo titolo
  * Colore sfondo generale
  * Colore input utente
  * Colore pulsante “Send”

### 🗨️ Messaggi

* **Welcome Message** → es: *"Hey little one, tell me what you need"*
* **Errore** → es: *"Sorry, this was an error"*

### 🖍 Font

* Dimensione font personalizzabile → es. `18px`

---

## 🧼 Rimozione del “Powered by Flowise”

Trucco per nasconderlo:

* Imposta:

  * Background color = bianco (`#FFFFFF`)
  * Powered by text color = bianco (`#FFFFFF`)
* Così il testo non sarà visibile (ma sarà comunque presente nel DOM)

> 🔍 Può essere fatto anche nel codice incorporato (più professionale)

---

## 🔗 Embed e Accesso via Codice

Puoi accedere o integrare il chatbot anche via codice:

* **Python** → Importare endpoint nella tua app
* **JavaScript** → Funzione integrabile con codice copiato da Flowise
* **`curl`** → Utile per chiamate API o webhook

---

## 🚫 Limitazione locale

> Tutto quanto sopra funziona **solo localmente** finché non si pubblica il chatbot su un host esterno.
> Hosting sarà trattato nei prossimi video.

---

## 🧠 Conclusione

Hai imparato a:

* Creare un'app standalone con Flowise
* Personalizzarne estetica e comportamento
* Renderla accessibile (localmente)
* Prepararla per hosting e distribuzione futura

