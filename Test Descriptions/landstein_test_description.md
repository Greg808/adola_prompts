# Test Specification: Restaurant Landstein Voicebot – Lisa

---

## Smoketest

### Test Objective  
Verify that the Voicebot greets the user by name (“Lisa”), introduces her association with the restaurant (“Landstein”), and correctly provides the opening hours when asked.

---

### 1. Greeting Recognition  
- Verify that the Voicebot introduces herself as “Lisa” from Restaurant Landstein.  
- Confirm that the Voicebot offers assistance with reservations, opening hours, or menu inquiries.

**Expected example response:**  
„Willkommen im Restaurant Landstein. Ich bin Ihr digitaler K.I. Assistent. Fragen Sie mich gerne zu unserem Angebot, den Öffnungszeiten oder Reservierungen. Wie kann ich helfen?“

---

### 2. Opening Hours Request  
- Use this expected opening schedule for validation:  
  - Monday: closed (day of rest)  
  - Tuesday to Friday: 12:00–23:00 (kitchen from 12:00–14:00 and 17:00–22:00)  
  - Saturday: 17:00–00:00  
  - Sunday: closed  

- Testbot asks the Voicebot:  
  _„Wie sind eure Öffnungszeiten?“_  
- Verify that the stated opening hours match the expected schedule.  

**Expected example response:**  
„Unsere Öffnungszeiten sind Dienstag bis Freitag von 12:00 bis 23:00 Uhr – mit Küche von 12:00 bis 14:00 Uhr und 17:00 bis 22:00 Uhr. Am Samstag haben wir von 17:00 bis Mitternacht geöffnet. Sonntag und Montag ist geschlossen.“

---

## Functional Test

### Test Objective  
Ensure the Voicebot can complete a reservation process including date validation, required info handling, time slot logic, confirmation behavior, and polite closing.

---

### 1. Reservation Intent Recognition  
- Testbot says to the Voicebot: _„Ich möchte einen Tisch reservieren.“_  
- The Voicebot must recognize the intent and ask for the desired date.

**Expected example response:**  
„Gerne. Für welches Datum möchten Sie reservieren?“

---

### 2. Handle Reservation on Closed Day  
- Testbot says to the Voicebot: _„Am Sonntag um 19 Uhr.“_  
- The Voicebot must identify that the restaurant is closed and say so.  
- The Voicebot must suggest choosing another day.

**Expected example response:**  
„Am Sonntag haben wir geschlossen. Möchten Sie stattdessen an einem anderen Tag reservieren?“

---

### 3. Continue on Open Day  
- Testbot says to the Voicebot: _„Dann am Dienstag um 19 Uhr.“_  
- The Voicebot must continue the reservation and ask for number of guests.

**Expected example response:**  
„Wunderbar. Für wie viele Personen darf ich reservieren?“

---

### 4. Collect Party Size  
- Testbot says to the Voicebot: _„Für zwei Personen.“_  
- The Voicebot should acknowledge and ask for the name.

**Expected example response:**  
„Alles klar. Auf welchen Namen darf ich die Reservierung eintragen?“

---

### 5. Group Size Constraint  
- Testbot says to the Voicebot: _„Für zehn Personen.“_  
- The Voicebot must recognize this as a group reservation and instruct the caller to write an email to complete the booking.

**Expected example response:**  
„Reservierungen für mehr als acht Personen nehmen wir ausschließlich schriftlich entgegen. Bitte senden Sie uns eine E-Mail an restaurant@landstein Punkt at.“

---

### 6. No Availability at Desired Time  
- Testbot says to the Voicebot: _„Dienstag um 19 Uhr für zwei Personen.“_  
- Simulate that this time is unavailable.  
- The Voicebot must suggest **up to three later alternatives** on the same day.

**Expected example response:**  
„Leider ist um 19:00 Uhr kein Tisch mehr verfügbar. Möchten Sie vielleicht um 19:30, 20:00 oder 20:30 Uhr reservieren?“

---

### 7. Ask for Confirmation Separately  
- Simulate that the Voicebot has collected all valid reservation details and found an available time.  
- Verify that the Voicebot asks for confirmation using **only** a stand-alone sentence.  
- No additional suggestions or questions may be included in the same utterance.

**Expected example confirmation:**  
„Möchten Sie die Buchung so bestätigen?“

---

### 8. Follow-up Only After Confirmation  
- Testbot says to the Voicebot: _„Ja, bitte bestätigen.“_  
- The Voicebot must then continue and ask if further help is needed.

**Expected example response:**  
„Vielen Dank. Kann ich Ihnen sonst noch weiterhelfen?“

---

### 9. Conversation Closure  
- Testbot says to the Voicebot: _„Nein, das war’s.“_  
- The Voicebot must respond with the official closing sentence and end the call with `<end_call>`.

**Expected example response:**  
„Vielen Dank für Ihre Anfrage. Bei weiteren Fragen oder Wünschen stehen wir Ihnen jederzeit gerne zur Verfügung. Wir freuen uns darauf, Sie bald bei uns im Restaurant Landstein begrüßen zu dürfen! Auf Wiederhören.“  
`<end_call>`

---

-### 10. Incomplete Reservation – Missing Information

- Simulate Testbot saying to the Voicebot: _„Ich möchte einen Tisch reservieren.“_  
- The Voicebot must **not proceed with the reservation** unless all required information is collected:  
  **name**, **date**, **time**, and **number of guests**.

- Test different combinations of missing fields. In each case, the Voicebot must **explicitly ask** for the missing data, and **not** confirm or finalize anything before all data is complete.

---

#### Case A – Missing time  
Testbot says to the Voicebot: _„Für morgen, vier Personen, auf den Namen Schuster.“_  
→ The Voicebot must ask for the time.

**Expected example response:**  
„Zu welcher Uhrzeit möchten Sie reservieren?“

---

#### Case B – Missing name  
Testbot says to the Voicebot: _„Für drei Personen am Samstag um 18 Uhr.“_  
→ The Voicebot must ask for the name before proceeding.

**Expected example response:**  
„Auf welchen Namen darf ich die Reservierung eintragen?“

---

#### Case C – Missing number of guests  
Testbot says to the Voicebot: _„Am Freitag um 20 Uhr auf den Namen Bauer.“_  
→ The Voicebot must ask for the number of guests.

**Expected example response:**  
„Für wie viele Personen möchten Sie reservieren?“

---

#### Case D – Missing date  
Testbot says to the Voicebot: _„Für zwei Personen um 19 Uhr auf den Namen Novak.“_  
→ The Voicebot must ask for the reservation date.

**Expected example response:**  
„Für welches Datum möchten Sie reservieren?“

---

#### Case E – Multiple missing values  
Testbot says to the Voicebot: _„Ich möchte einen Tisch reservieren.“_  
→ The Voicebot must ask step by step for all four missing elements.

**Expected example response:**  
„Gerne. Für welches Datum möchten Sie reservieren?“  
→ Follow-up questions should then collect: time, number of guests, name

---

### Important  
- At no point may the Voicebot confirm or finalize the reservation unless **all required details are present.**  
- The Voicebot must handle missing information **gracefully and in logical order.**
