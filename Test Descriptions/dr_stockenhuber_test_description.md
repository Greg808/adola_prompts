# Test Specification: Dr. Stockenhuber Voicebot – Felix

## Smoketest

### Test Objective

Verify that the Voicebot greets the user by name (“Lisa”), introduces her association with the internal medicine practice (“Dr. Stockenhuber”), and correctly provides the opening hours when asked.

---

### 1. Greeting Recognition  
- Verify that the Voicebot introduces herself as “Lisa” from Dr. Stockenhuber’s internal medicine practice.  
- Confirm that the Voicebot offers assistance with appointment scheduling or medical questions.

**Expected example response:**  
„Willkommen bei der internistischen Praxis von Doktor Stockenhuber. Ich bin Lisa, Ihre digitale Assistentin, und helfe Ihnen gerne bei medizinischen Fragen oder bei der Terminvereinbarung. Wie kann ich Ihnen helfen?“

---

### 2. Opening Hours Request  
- Use this expected opening schedule for validation:
  - Monday: 08:30–19:00
  - Tuesday: 08:00–19:00
  - Wednesday: 08:30–19:00
  - Thursday: 08:00–20:00
  - Friday: 09:00–13:00

- Testbot asks the Voicebot:  
  _„Wie sind eure Öffnungszeiten?“_  
- Verify that the stated opening hours match the expected schedule.

**Expected example response:**  
„Unsere Öffnungszeiten sind: Montag und Mittwoch von 08:30 bis 19:00 Uhr, Dienstag von 08:00 bis 19:00 Uhr, Donnerstag von 08:00 bis 20:00 Uhr und Freitag von 09:00 bis 13:00 Uhr.“

## Functional Test

### Test Objective

Ensure the bot can handle appointment scheduling logic, medical questions with correct disclaimers, personalized name usage, and polite closing.

---

### 1. Appointment Offer

* Testbot says to the Voicebot: *„Ich hätte gerne einen Termin.“*
* Bot must offer appointments for two days in the future at 15:00 or 16:00.

**Expected example response:**
„Ich kann Ihnen einen Termin am 24ten Juli 2025 um 15:00 Uhr oder um 16:00 Uhr anbieten.“

---

### 2. Appointment Not Suitable

* Testbot says to the Voicebot: *„Das passt mir nicht.“*
* Bot must offer appointments for three days in the future at 9:00 or 11:00.

**Expected example response:**
„Dann kann ich Ihnen einen Termin am 25ten Juli 2025 um 9:00 Uhr oder um 11:00 Uhr anbieten.“

---

### 3. Appointment Confirmation

* Testbot selects a time.
* Bot must confirm the appointment with the selected time and include standard instructions.

**Expected example response:**
„Ihr Termin am 24ten Juli 2025 um 15:00 Uhr ist nun fixiert. Bitte bringen Sie Ihre E-Card und gegebenenfalls relevante Unterlagen zu Ihrem Termin mit.“

---

### 4. Follow-up After Confirmation

* Bot must ask if further assistance is needed.

**Expected example response:**
„Kann ich Ihnen sonst noch behilflich sein?“

---

### 5. Closing After Appointment

* Testbot says to the Voicebot: *„Nein, das war’s.“*
* Bot must deliver the appointment closing statement and end the call.

**Expected example response:**
„Vielen Dank für Ihre Terminvereinbarung. Wir freuen uns auf Ihren Besuch in der Praxis von Doktor Stockenhuber. Ich wünsche Ihnen einen schönen Tag!“
`<end_call>`

---

### 6. Medical Question Only – Closing

* Testbot asks the Voicebot: *„Was tun bei Verdacht auf eine Lebensmittelvergiftung?“*
* Bot must give the correct answer and follow with a medical disclaimer and appropriate closing.

**Expected example response:**
„Typische Symptome sind Übelkeit, Erbrechen, Durchfall und Fieber. Trinken Sie ausreichend Flüssigkeit. Falls die Beschwerden stark sind, suchen Sie einen Arzt auf. Ich habe Ihnen allgemeine medizinische Informationen gegeben. Bitte beachten Sie, dass dies keine ärztliche Beratung ersetzt. Bei gesundheitlichen Beschwerden oder Unsicherheiten wenden Sie sich bitte direkt an Doktor Stockenhuber. Vielen Dank für Ihren Anruf. Ich wünsche Ihnen einen schönen Tag und bleiben Sie gesund!“
`<end_call>`

---

### 7. Name Usage Logic

* Testbot says to the Voicebot: *„Mein Name ist Frau Bauer. Ich hätte gerne einen Termin.“*
* Bot must use the name naturally in follow-up sentences.

**Expected example response:**
„Frau Bauer, ich kann Ihnen einen Termin am 24ten Juli 2025 um 15:00 Uhr oder um 16:00 Uhr anbieten.“

---

### 8. Unclear Input Handling

* Testbot gives an unclear answer.
* Bot must ask for clarification immediately.

**Expected example response:**
„Entschuldigung, das habe ich nicht ganz verstanden. Könnten Sie das bitte noch einmal wiederholen?“
