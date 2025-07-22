# Test Specification: Dr. Philipp Mayr Voicebot – Digital Assistant

## Smoketest

### Test Objective

Verify that the Voicebot greets the user by name (“Lisa”), introduces her association with the clinic (“Dr. Philipp Mayr”), and correctly provides the opening hours when asked.

---

### 1. Greeting Recognition  
- Verify that the Voicebot introduces herself as “Lisa” from Dr. Philipp Mayr’s clinic.  
- Confirm that the Voicebot offers assistance with consultations, opening hours, or aesthetic treatments.

**Expected example response:**  
„Willkommen bei der Praxis für Plastische, Ästhetische und Rekonstruktive Chirurgie von Doktor Philipp Mayr in Linz und Wels. Ich bin Lisa, Ihre digitale Assistentin und stehe Ihnen rund um ästhetische Behandlungen, Beratungen und Terminvereinbarungen zur Verfügung. Wie kann ich Ihnen heute helfen?"

---

### 2. Opening Hours Request  
- Use this expected opening schedule for validation:  
  - Monday: 08:00–12:00 & 13:00–15:00  
  - Tuesday: 09:00–12:00 & 13:00–16:00  
  - Wednesday: 09:00–12:00 & 13:00–16:00  
  - Thursday: 10:00–13:00 & 14:00–16:00  
  - Friday: 08:00–12:00  

- Testbot asks the Voicebot:  
  _„Wie sind eure Öffnungszeiten?“_  
- Verify that the stated opening hours match the expected schedule.  

**Expected example response:**  
„Unsere Ordinationszeiten sind: Montag von 08:00 bis 12:00 und 13:00 bis 15:00, Dienstag bis Mittwoch von 09:00 bis 12:00 und 13:00 bis 16:00, Donnerstag von 10:00 bis 13:00 und 14:00 bis 16:00 sowie Freitag von 08:00 bis 12:00.“

---

### 3. FAQ Response Check

* Testbot asks the Voicebot: *"Wie viel kostet Botox?"*
* Verify that the Voicebot gives the correct FAQ answer including base price and estimate.

**Expected example response:**
„Der Grundpreis ist €200. Jede weitere Einheit kostet €5. Für die Stirn, die Krähenfüße und die Zornesfalte kommt man auf ca. €400.“

---

## Functional Test

### Test Objective

Test full appointment logic, including Botox/Filler handling, new vs. existing patients, opening hour constraints, and polite call closure.

---

### 1. Botox Intent Detection

* Testbot says to the Voicebot: *"Ich möchte einen Termin für Botox."*
* The Voicebot must skip the initial check and go directly to Botox/Filler flow.

**Expected example response:**
„Sind Sie bereits Patient bei uns?“

---

### 2. Existing Patient Flow – Available Slots

* Testbot says to the Voicebot: *"Ja, ich bin bereits Patient.“*
* The Voicebot proposes two predefined appointments in November.

**Expected example response:**
„Die nächsten möglichen Termine sind am 5ten November 2025 um 09:00 Uhr oder am 7ten November 2025 um 10:00 Uhr. Würde Ihnen einer dieser Termine zusagen?“

---

### 3. New Patient Rejection with Redirect

* Testbot says to the Voicebot: *"Nein, ich bin neu hier.“*
* The Voicebot must refer the caller to Dr. Lebo with July appointment suggestions.

**Expected example response:**
„Doktor Mayr nimmt keine neuen Patienten mehr für Botox und Filler. Ich kann Ihnen gerne bei Frau Doktor Lebo, eine zweite plastische Chirurgin bei uns im Haus, einen Termin anbieten: am 3ten Juli 2025 um 09:00 Uhr oder am 8ten Juli 2025 um 11:00 Uhr. Würde Ihnen einer dieser Termine zusagen?“

---

### 4. Appointment with Specific Date Request (Unavailable)

* Testbot asks the Voicebot for a specific unavailable date (e.g., 9. Juli).
* The Voicebot must explain lack of availability and offer two alternatives.

**Expected example response:**
„Am 9ten Juli haben wir leider keine freien Termine. Darf ich Ihnen stattdessen diese nächsten beiden freien Termine anbieten: am 12ten Juli 2025 um 09:00 Uhr oder am 14ten Juli 2025 um 10:00 Uhr?“

---

### 5. General Appointment Logic (Non-Botox)

* Testbot says to the Voicebot: *"Ich brauche einen Beratungstermin für eine Nasenkorrektur.“*
* The Voicebot must offer slots +2 days from today, within opening hours.

**Expected example response:**
„Ich kann Ihnen einen Termin am 24ten Juli 2025 um 15:00 Uhr oder um 16:00 Uhr anbieten.“

---

### 6. Collect Missing Information – Name

* Testbot accepts a proposed appointment time.
* The Voicebot must ask for the caller's name before final confirmation.

**Expected example response:**
„Wie ist Ihr Name, damit ich den Termin korrekt eintragen kann?“

---

### 7. Appointment Confirmation

* The Voicebot must confirm appointment using date and caller name.

**Expected example response:**
„Okay, Herr Meier. Ihr Termin am 24ten Juli 2025 um 15:00 Uhr ist nun fixiert. Bitte bringen Sie relevante Unterlagen mit.“

---

### 8. Outro – With Appointment

* Testbot says to the Voicebot: *"Nein, das war’s.“* after appointment confirmed.
* The Voicebot must end with correct closing line and `<end_call>`.

**Expected example response:**
„Vielen Dank für Ihre Terminvereinbarung. Wir freuen uns auf Ihren Besuch in der Praxis von Doktor Philipp Mayr. Ich wünsche Ihnen einen schönen Tag!“
`<end_call>`

---

### 9. Outro – Without Appointment

* Testbot says to the Voicebot: *"Nein, danke."* after a general question.
* The Voicebot must state disclaimer, thank the caller, and end the call.

**Expected example response:**
„Ich habe Ihnen allgemeine medizinische Informationen gegeben. Bitte beachten Sie, dass dies keine ärztliche Beratung ersetzt. Bei gesundheitlichen Beschwerden oder Unsicherheiten wenden Sie sich bitte direkt an Doktor Philipp Mayr. Vielen Dank für Ihren Anruf. Ich wünsche Ihnen einen schönen Tag und bleiben Sie gesund!“
`<end_call>`

---

### 10. Handle Misunderstood Input

* Testbot says to the Voicebot: "Ich weiß nicht".
* The Voicebot must ask for clarification.

**Expected example response:**
„Entschuldigung, könnten Sie das bitte noch einmal genauer sagen?“

---

### 11. Handle Missing Information – No Date or Type

* Testbot says to the Voicebot: *"Ich möchte einen Termin vereinbaren."* but provides no further info.
* The Voicebot must ask for appointment type or proceed with Botox logic query.

**Expected example response:**
„Geht es um einen Termin für Botox oder Filler?“