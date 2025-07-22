# Test Specification: Dr. Philipp Mayr Voicebot – Digital Assistant

## Smoketest

### Test Objective

Verify that the Voicebot introduces the clinic, presents herself correctly, and responds to a simple procedural question in line with the FAQ.

---

### 1. Greeting Recognition

* Simulate a call without user input.
* Verify that the assistant introduces herself as the digital assistant for Dr. Philipp Mayr and offers help.

**Expected example response:**
„Willkommen bei der Praxis für Plastische, Ästhetische und Rekonstruktive Chirurgie von Doktor Philipp Mayr in Linz und Wels. Ich bin Ihr digitaler KI-Assistent und stehe Ihnen rund um ästhetische Behandlungen, Beratungen und Terminvereinbarungen zur Verfügung. Wie kann ich Ihnen heute helfen?"

---

### 2. FAQ Response Check

* Simulate user asking: *"Wie viel kostet Botox?"*
* Verify that the assistant gives the correct FAQ answer including base price and estimate.

**Expected example response:**
„Der Grundpreis ist €200. Jede weitere Einheit kostet €5. Für die Stirn, die Krähenfüße und die Zornesfalte kommt man auf ca. €400.“

---

## Functional Test

### Test Objective

Test full appointment logic, including Botox/Filler handling, new vs. existing patients, opening hour constraints, and polite call closure.

---

### 1. Botox Intent Detection

* User says: *"Ich möchte einen Termin für Botox."*
* Assistant must skip the initial check and go directly to Botox/Filler flow.

**Expected example response:**
„Sind Sie bereits Patient bei uns?“

---

### 2. Existing Patient Flow – Available Slots

* User says: *"Ja, ich bin bereits Patient.“*
* Assistant proposes two predefined appointments in November.

**Expected example response:**
„Die nächsten möglichen Termine sind am 5ten November 2025 um 09:00 Uhr oder am 7ten November 2025 um 10:00 Uhr. Würde Ihnen einer dieser Termine zusagen?“

---

### 3. New Patient Rejection with Redirect

* User says: *"Nein, ich bin neu hier.“*
* Assistant must refer the caller to Dr. Lebo with July appointment suggestions.

**Expected example response:**
„Doktor Mayr nimmt keine neuen Patienten mehr für Botox und Filler. Ich kann Ihnen gerne bei Frau Doktor Lebo, eine zweite plastische Chirurgin bei uns im Haus, einen Termin anbieten: am 3ten Juli 2025 um 09:00 Uhr oder am 8ten Juli 2025 um 11:00 Uhr. Würde Ihnen einer dieser Termine zusagen?“

---

### 4. Appointment with Specific Date Request (Unavailable)

* Simulate user asking for a specific unavailable date (e.g., 9. Juli).
* Assistant must explain lack of availability and offer two alternatives.

**Expected example response:**
„Am 9ten Juli haben wir leider keine freien Termine. Darf ich Ihnen stattdessen diese nächsten beiden freien Termine anbieten: am 12ten Juli 2025 um 09:00 Uhr oder am 14ten Juli 2025 um 10:00 Uhr?“

---

### 5. General Appointment Logic (Non-Botox)

* User says: *"Ich brauche einen Beratungstermin für eine Nasenkorrektur.“*
* Assistant must offer slots +2 days from today, within opening hours.

**Expected example response:**
„Ich kann Ihnen einen Termin am 24ten Juli 2025 um 15:00 Uhr oder um 16:00 Uhr anbieten.“

---

### 6. Collect Missing Information – Name

* Simulate user accepting a proposed appointment time.
* Assistant must ask for the caller's name before final confirmation.

**Expected example response:**
„Wie ist Ihr Name, damit ich den Termin korrekt eintragen kann?“

---

### 7. Appointment Confirmation

* Assistant must confirm appointment using date and caller name.

**Expected example response:**
„Okay, Herr Meier. Ihr Termin am 24ten Juli 2025 um 15:00 Uhr ist nun fixiert. Bitte bringen Sie relevante Unterlagen mit.“

---

### 8. Outro – With Appointment

* Caller says: *"Nein, das war’s.“* after appointment confirmed.
* Assistant must end with correct closing line and `<end_call>`.

**Expected example response:**
„Vielen Dank für Ihre Terminvereinbarung. Wir freuen uns auf Ihren Besuch in der Praxis von Doktor Philipp Mayr. Ich wünsche Ihnen einen schönen Tag!“
`<end_call>`

---

### 9. Outro – Without Appointment

* Caller says: *"Nein, danke."* after a general question.
* Assistant must state disclaimer, thank the caller, and end the call.

**Expected example response:**
„Ich habe Ihnen allgemeine medizinische Informationen gegeben. Bitte beachten Sie, dass dies keine ärztliche Beratung ersetzt. Bei gesundheitlichen Beschwerden oder Unsicherheiten wenden Sie sich bitte direkt an Doktor Philipp Mayr. Vielen Dank für Ihren Anruf. Ich wünsche Ihnen einen schönen Tag und bleiben Sie gesund!“
`<end_call>`

---

### 10. Handle Misunderstood Input

* User gives unclear answer (e.g. "Ich weiß nicht").
* Assistant must ask for clarification.

**Expected example response:**
„Entschuldigung, könnten Sie das bitte noch einmal genauer sagen?“

---

### 11. Handle Missing Information – No Date or Type

* User says: *"Ich möchte einen Termin vereinbaren."* but provides no further info.
* Assistant must ask for appointment type or proceed with Botox logic query.

**Expected example response:**
„Geht es um einen Termin für Botox oder Filler?“
 