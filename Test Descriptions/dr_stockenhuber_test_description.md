# Test Specification: Dr. Stockenhuber Voicebot – Felix

## Smoketest

### Test Objective

Ensure that the bot greets the caller politely and answers a basic medical question clearly.

---

### 1. Greeting Recognition

* Simulate a call without user input.
* Verify that the bot introduces himself as a digital assistant of Dr. Stockenhuber's internal medicine practice.
* Confirm that it offers help with medical questions or appointment scheduling.

**Expected example response:**
„Willkommen bei der internistischen Praxis von Doktor Stockenhuber. Ich bin Ihr digitaler KI-Assistent und helfe Ihnen gerne weiter. Sie können mir medizinische Fragen stellen oder einen Termin vereinbaren. Wie kann ich Ihnen helfen?“

---

### 2. Basic Medical FAQ

* User says: *„Was sind die Symptome eines Herzinfarkts?“*
* The bot must respond with an appropriate, clear answer and recommend calling the emergency service if applicable.

**Expected example response:**
„Typische Symptome sind starke Brustschmerzen, die in den linken Arm oder den Kiefer ausstrahlen, Atemnot, Übelkeit und Kaltschweiß. Rufen Sie bei Verdacht sofort den Notruf 144 an.“

---

## Functional Test

### Test Objective

Ensure the bot can handle appointment scheduling logic, medical questions with correct disclaimers, personalized name usage, and polite closing.

---

### 1. Appointment Offer

* User says: *„Ich hätte gerne einen Termin.“*
* Bot must offer appointments for two days in the future at 15:00 or 16:00.

**Expected example response:**
„Ich kann Ihnen einen Termin am 24ten Juli 2025 um 15:00 Uhr oder um 16:00 Uhr anbieten.“

---

### 2. Appointment Not Suitable

* User says: *„Das passt mir nicht.“*
* Bot must offer appointments for three days in the future at 9:00 or 11:00.

**Expected example response:**
„Dann kann ich Ihnen einen Termin am 25ten Juli 2025 um 9:00 Uhr oder um 11:00 Uhr anbieten.“

---

### 3. Appointment Confirmation

* User selects a time.
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

* User says: *„Nein, das war’s.“*
* Bot must deliver the appointment closing statement and end the call.

**Expected example response:**
„Vielen Dank für Ihre Terminvereinbarung. Wir freuen uns auf Ihren Besuch in der Praxis von Doktor Stockenhuber. Ich wünsche Ihnen einen schönen Tag!“
`<end_call>`

---

### 6. Medical Question Only – Closing

* User only asked a question, e.g.: *„Was tun bei Verdacht auf eine Lebensmittelvergiftung?“*
* Bot must give the correct answer and follow with a medical disclaimer and appropriate closing.

**Expected example response:**
„Typische Symptome sind Übelkeit, Erbrechen, Durchfall und Fieber. Trinken Sie ausreichend Flüssigkeit. Falls die Beschwerden stark sind, suchen Sie einen Arzt auf. Ich habe Ihnen allgemeine medizinische Informationen gegeben. Bitte beachten Sie, dass dies keine ärztliche Beratung ersetzt. Bei gesundheitlichen Beschwerden oder Unsicherheiten wenden Sie sich bitte direkt an Doktor Stockenhuber. Vielen Dank für Ihren Anruf. Ich wünsche Ihnen einen schönen Tag und bleiben Sie gesund!“
`<end_call>`

---

### 7. Name Usage Logic

* User says: *„Mein Name ist Frau Bauer. Ich hätte gerne einen Termin.“*
* Bot must use the name naturally in follow-up sentences.

**Expected example response:**
„Frau Bauer, ich kann Ihnen einen Termin am 24ten Juli 2025 um 15:00 Uhr oder um 16:00 Uhr anbieten.“

---

### 8. Unclear Input Handling

* User gives an unclear answer.
* Bot must ask for clarification immediately.

**Expected example response:**
„Entschuldigung, das habe ich nicht ganz verstanden. Könnten Sie das bitte noch einmal wiederholen?“
