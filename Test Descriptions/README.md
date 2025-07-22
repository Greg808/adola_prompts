# README 

## Übersicht aller Voicebots & Testplattformen

### 📍 Plattform: https://restaurantbotconfig.azurewebsites.net/

Diese Bots sind über das interne Test-Tool abrufbar und haben eine zugewiesene Nummer:

- Café Manolos *(derzeit ohne Nummer, aber vorhanden)*
- Restaurant Landstein
- ReadyForFit Wien-Süd
- Saloon Donau Zentrum

---

### 📍 Plattform: https://adola.ai

Diese Bots laufen produktiv oder in Kundendemos und sind über unsere Hauptseite erreichbar:

- Dr. Philipp Mayr – Plastische Chirurgie Linz
- Dr. Felix Stockenhuber – Internistische Praxis Wien
- Dermazentrum Siebenhirten – Hautarztzentrum Wien
- Vienna City Beach Club (VCBC)
- ÖBB Verbindungsbahn Wien


## AI Voicebot Test Playbook

Dieses Repository enthält das **AI Voicebot Test Playbook**, mit dem strukturierte und standardisierte Testbeschreibungen für Voicebot-Prompts erstellt werden können.

---

### 📌 Ziel

Das Playbook hilft dir, **konsistente Smoketests und Functional Tests** zu erzeugen, um die LLM-Logik von Voicebots manuell zu validieren. Es dient als Grundlage für QA-Prozesse, Regressionstests und Prompt-Überwachung.

---

### ✅ So verwendest du das Playbook

#### 1. Öffne ChatGPT (mit Datei-Upload-Funktion)

#### 2. Lade dein Voicebot-Prompt hoch (z. B. `.md`, `.txt`, `.docx`)

#### 3. Gib folgenden Befehl ein:

> **„Bitte erstelle mir auf Basis dieses Prompts eine strukturierte Testbeschreibung im definierten Format (Smoketest + Functional Test). Nutze das AI Voicebot Test Playbook.“**

ChatGPT analysiert nun den Prompt und erstellt automatisch ein vollständiges Testdokument im Markdown-Format – **einschließlich Download-Link**.

---

### 🔁 Standardisierung

Das Playbook stellt sicher, dass:

- Die Teststruktur immer gleich ist
- Alle Fragen mit **„Testbot asks the Voicebot“** beginnen
- Alle Aussagen mit **„Testbot says to the Voicebot“** beginnen
- Begrüßung und Öffnungszeiten **immer** im Smoketest enthalten sind
- LLM-Antworten überprüfbar und realistisch testbar sind

---

### ❓ Fragen oder Erweiterungen?

Das Playbook kann jederzeit erweitert werden – z. B. um branchenspezifische Besonderheiten oder neue Testtypen.

---