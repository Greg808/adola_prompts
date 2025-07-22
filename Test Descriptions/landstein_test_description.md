# Test Specification: Restaurant Landstein Voicebot – Lisa  

## Smoketest

### Test Objective  
Ensure that Lisa starts the conversation correctly and responds accurately to a basic request for opening hours.

---

### 1. Greeting Recognition  
- Verify that the Voicebot introduces herself as “Lisa” from Restaurant Landstein.  
- Confirm that she offers assistance with reservations, opening hours, allergens, or menu inquiries.

**Expected example response:**  
„Willkommen im Restaurant Landstein. Ich bin Ihr digitaler K.I. Assistent. Fragen Sie mich gerne zu unserem Angebot, den Öffnungszeiten, Inhaltsstoffen oder Reservierungen. Wie kann ich helfen?“

---

### 2. Opening Hours Request  
- Simulate the user asking: _„Wie sind eure Öffnungszeiten?“_  
- Verify that Lisa only states the opening hours **if the restaurant is closed** on that day.  
- She must **not say** anything like “the restaurant is open.”  
- If closed, she must say so in natural speech.

**Expected example response (for Sunday request):**  
„Am Sonntag haben wir geschlossen.“

---

## Functional Test

### Test Objective  
Ensure Lisa can complete a reservation process including date validation, required info handling, time slot logic, confirmation behavior, and polite closing.

---

### 1. Reservation Intent Recognition  
- User says: _„Ich möchte einen Tisch reservieren.“_  
- Lisa must recognize the intent and ask for the desired date.

**Expected example response:**  
„Gerne. Für welches Datum möchten Sie reservieren?“

---

### 2. Handle Reservation on Closed Day  
- User says: _„Am Sonntag um 19 Uhr.“_  
- Lisa must identify that the restaurant is closed and say so.  
- She must suggest choosing another day.

**Expected example response:**  
„Am Sonntag haben wir geschlossen. Möchten Sie stattdessen an einem anderen Tag reservieren?“

---

### 3. Continue on Open Day  
- User says: _„Dann am Dienstag um 19 Uhr.“_  
- Lisa must continue the reservation and ask for number of guests.

**Expected example response:**  
„Wunderbar. Für wie viele Personen darf ich reservieren?“

---

### 4. Collect Party Size  
- User says: _„Für zwei Personen.“_  
- Lisa should acknowledge and ask for the name.

**Expected example response:**  
„Alles klar. Auf welchen Namen darf ich die Reservierung eintragen?“

---

### 5. Group Size Constraint  
- User says: _„Für zehn Personen.“_  
- Lisa must recognize this as a group reservation and instruct the caller to write an email to complete the booking.

**Expected example response:**  
„Reservierungen für mehr als acht Personen nehmen wir ausschließlich schriftlich entgegen. Bitte senden Sie uns eine E-Mail an restaurant@landstein Punkt at.“

---

### 6. No Availability at Desired Time  
- User says: _„Dienstag um 19 Uhr für zwei Personen.“_  
- Simulate that this time is unavailable.  
- Lisa must suggest **up to three later alternatives** on the same day.

**Expected example response:**  
„Leider ist um 19:00 Uhr kein Tisch mehr verfügbar. Möchten Sie vielleicht um 19:30, 20:00 oder 20:30 Uhr reservieren?“

---

### 7. Ask for Confirmation Separately  
- Simulate that Lisa has collected all valid reservation details and found an available time.  
- Verify that Lisa asks for confirmation using **only** a stand-alone sentence.  
- No additional suggestions or questions may be included in the same utterance.

**Expected example confirmation:**  
„Möchten Sie die Buchung so bestätigen?“

---

### 8. Follow-up Only After Confirmation  
- User says: _„Ja, bitte bestätigen.“_  
- Lisa must then continue and ask if further help is needed.

**Expected example response:**  
„Vielen Dank. Kann ich Ihnen sonst noch weiterhelfen?“

---

### 9. Conversation Closure  
- User says: _„Nein, das war’s.“_  
- Lisa must respond with the official closing sentence and end the call with `<end_call>`.

**Expected example response:**  
„Vielen Dank für Ihre Anfrage. Bei weiteren Fragen oder Wünschen stehen wir Ihnen jederzeit gerne zur Verfügung. Wir freuen uns darauf, Sie bald bei uns im Restaurant Landstein begrüßen zu dürfen! Auf Wiederhören.“  
`<end_call>`

### 10. Incomplete Reservation – Missing Information

- Simulate the user saying: _„Ich möchte einen Tisch reservieren.“_  
- Lisa must **not proceed with the reservation** unless all required information is collected:  
  **name**, **date**, **time**, and **number of guests**.

- Test different combinations of missing fields. In each case, Lisa must **explicitly ask** for the missing data, and **not** confirm or finalize anything before all data is complete.

---

#### Case A – Missing time  
User: _„Für morgen, vier Personen, auf den Namen Schuster.“_  
→ Lisa must ask for the time.

**Expected example response:**  
„Zu welcher Uhrzeit möchten Sie reservieren?“

---

#### Case B – Missing name  
User: _„Für drei Personen am Samstag um 18 Uhr.“_  
→ Lisa must ask for the name before proceeding.

**Expected example response:**  
„Auf welchen Namen darf ich die Reservierung eintragen?“

---

#### Case C – Missing number of guests  
User: _„Am Freitag um 20 Uhr auf den Namen Bauer.“_  
→ Lisa must ask for the number of guests.

**Expected example response:**  
„Für wie viele Personen möchten Sie reservieren?“

---

#### Case D – Missing date  
User: _„Für zwei Personen um 19 Uhr auf den Namen Novak.“_  
→ Lisa must ask for the reservation date.

**Expected example response:**  
„Für welches Datum möchten Sie reservieren?“

---

#### Case E – Multiple missing values  
User: _„Ich möchte einen Tisch reservieren.“_  
→ Lisa must ask step by step for all four missing elements.

**Expected example response:**  
„Gerne. Für welches Datum möchten Sie reservieren?“  
→ Follow-up questions should then collect: time, number of guests, name

---

### Important  
- At no point may Lisa confirm or finalize the reservation unless **all required details are present.**  
- She must handle missing information **gracefully and in logical order.**
- 