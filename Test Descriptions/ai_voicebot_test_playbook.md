# AI Voicebot Test Description Playbook

## Ziel des Playbooks

Erzeuge **strukturierte, konsistente und klar validierbare** Testbeschreibungen zur technischen Absicherung von Voicebot-Prompts.
Die Tests dienen der **manuellen LLM-Logikprüfung** und helfen auch, Regressionen im Prompt zu erkennen.

---

## Struktur der Tests

### Smoketest

**Ziel:** Schneller Funktionstest zur Produktionsüberwachung
**Inhalte:**

* 1. Greeting Recognition
* 2. Opening Hours Request (mit validierbarem Wochenplan)

### Functional Test

**Ziel:** Vollständiger Logiktest zentraler Features
**Inhalte:**

* Konkrete Branch-Logik (z. B. Reservierungen, Weiterleitungen, FAQs)
* Bedingungen, Entscheidungslogik
* Verweise auf externe Tools oder Daten
* Abschlusssätze mit `<end_call>`-Validierung

---

## Format- und Sprachregeln (immer einhalten!)

* Alle **Fragen** beginnen mit: `Testbot asks the Voicebot:`
* Alle **Aussagen** beginnen mit: `Testbot says to the Voicebot:`
* Keine Formulierungen wie “User”, “User asks” etc.
* Der Botname in der Testlogik ist immer **“the Voicebot”**, nie „Lisa“ oder „Lea“ (nur in der gesprochenen Antwort).
* Der Abschnitt **Greeting Recognition** ist **immer Punkt 1** im Smoketest.
* Der Abschnitt **Opening Hours Request** ist **immer Punkt 2** im Smoketest (außer wenn Öffnungszeiten im Use Case irrelevant sind).
* Die **Test Objective**-Formulierung im Smoketest ist **immer gleich** (siehe unten).
* Die Öffnungszeiten müssen **immer explizit validiert werden**.
* Der Voicebot darf **niemals** sagen, ob gerade geöffnet ist oder nicht.

---

## Smoketest Template (Standard)

## Smoketest

### Test Objective

Verify that the Voicebot greets the user by name (“Lisa”), introduces her association with \[Studio/Restaurant/Arztpraxis/etc.], and correctly provides the opening hours when asked.

---

### 1. Greeting Recognition

* Verify that the Voicebot introduces herself as “Lisa” from \[Name].
* Confirm that she offers assistance with reservations, opening hours, or menu inquiries.

**Expected example response:**
„Hallo! Ich bin Lisa, der KI-Assistent von \[Name]. Wie kann ich Ihnen helfen?“

---

### 2. Opening Hours Request

* Use this expected opening schedule for validation:

  * Monday: closed (day of rest)
  * Tuesday to Saturday: 12:00–20:00
  * Sunday: 10:00–18:00

* Testbot asks the Voicebot:
  *„Wie sind eure Öffnungszeiten?“*

* Verify that the stated opening hours match the expected schedule.

* She must mention Monday is a rest day using the exact phrase:
  *„Montags ist unser Ruhetag – da haben wir geschlossen.“*

**Expected example response:**
„Unsere Öffnungszeiten sind: Dienstag bis Samstag von 12:00 bis 20:00 Uhr und Sonntag von 10:00 bis 18:00 Uhr. Montags ist unser Ruhetag – da haben wir geschlossen.“

---

## Functional Test Template (angepasst auf das Prompt)

Mindestens 5–8 realistische Branch-Tests, z. B. zu FAQs, Reservierungen, Toolcalls, etc.

Für jeden Testabschnitt:

### \[Titel des Tests, z. B. “Reservation with Missing Time”]

* Testbot says to the Voicebot: *„Ich möchte für Donnerstag einen Tisch reservieren.“*
* The Voicebot must ask for the missing time and not proceed with the reservation.
  **Expected example response:**
  „Dafür brauche ich bitte noch die gewünschte Uhrzeit – wann genau möchten Sie reservieren?“

---

📌 Dieses Playbook ist der Standard für alle Voicebot-Testbeschreibungen bei Adola.ai

Stand: Juli 2025
