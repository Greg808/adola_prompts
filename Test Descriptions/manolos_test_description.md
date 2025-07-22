# Test Specification: Café Manolos Voicebot – Lisa  

## Smoketest

### Test Objective  
Ensure that Lisa responds correctly to a standard conversation opening and to a basic request for opening hours.

---

### 1. Greeting Recognition  
- Verify that the Voicebot introduces herself as “Lisa.”  
- Confirm that Lisa mentions she works for Café Manolos.  
- Ensure she invites the caller to ask about a reservation, the menu, or any other question.

**Expected example response:**  
„Herzlich willkommen bei Café Manolos! Mein Name ist Lisa, und ich freue mich, Sie heute zu unterstützen. Möchten Sie eine Reservierung vornehmen, mehr über unser köstliches Angebot erfahren oder haben Sie eine andere Frage? Lassen Sie es mich gerne wissen!“

---

### 2. Opening Hours Request  
- Simulate the user asking: _„Wie sind eure Öffnungszeiten?“_  
- Verify that Lisa responds with the full schedule using 24-hour format.  
- She must mention Monday is a rest day using the exact phrase:  
  _„Montags ist unser Ruhetag – da haben wir geschlossen.“_

**Expected example response:**  
„Unsere Öffnungszeiten sind: Dienstag bis Samstag von 12:00 bis 20:00 Uhr und Sonntag von 10:00 bis 18:00 Uhr. Montags ist unser Ruhetag – da haben wir geschlossen.“

---

## Functional Test

### Test Objective  
Test whether Lisa can correctly handle a complete reservation process including unavailable days, required information, logic branching, and menu inquiries. The conversation must close with the standard farewell.

---

### 1. Reservation Intent Recognition  
- Simulate the user saying: _„Ich möchte einen Tisch reservieren.“_  
- Verify that Lisa recognizes the intent and asks for the reservation date.

**Expected example response:**  
„Gerne! Für welches Datum darf ich die Reservierung eintragen?“

---

### 2. Handle Reservation on Closed Day  
- User says: _„Für nächsten Montag um 17 Uhr.“_  
- Lisa must check the weekday and state that the restaurant is closed.  
- She must use the exact rest day phrase and ask for an alternative.

**Expected example response:**  
„Montags ist unser Ruhetag – da haben wir geschlossen. Möchten Sie vielleicht an einem anderen Tag reservieren?“

---

### 3. Proceed with Valid Date  
- User says: _„Dann am Dienstag um 17 Uhr.“_  
- Lisa must accept the new date and ask for the number of people.

**Expected example response:**  
„Wunderbar. Für wie viele Personen darf ich reservieren?“

---

### 4. Collect Party Size  
- User says: _„Für zwei Personen.“_  
- Lisa should acknowledge and ask for the reservation name.

**Expected example response:**  
„Alles klar. Auf welchen Namen darf ich die Reservierung eintragen?“

---

### 5. Collect Name and Check Availability  
- User says: _„Auf den Namen Mayer.“_  
- Lisa must check availability for Tuesday at 17:00 for 2 people.  
- If available, confirm the reservation including all details.  
- If not, suggest up to three alternatives on the same date.

**Expected example response (available):**  
„Perfekt, ich habe Ihre Reservierung für Dienstag um 17:00 Uhr für zwei Personen auf den Namen Mayer eingetragen.“

**Expected example response (not available):**  
„Leider ist um 17:00 Uhr kein Tisch mehr frei. Möchten Sie vielleicht um 16:30, 18:00 oder 19:30 reservieren?“

---

### 6. Menu Inquiry  
- User asks: _„Und was habt ihr so auf der Karte?“_  
- Lisa must summarize the menu highlights and offer more details if needed.  
- She must speak naturally and use Austrian food terms.

**Expected example response:**  
„In unserem Café finden Sie köstliche Kaffeespezialitäten, hausgemachte Kuchen und Torten von der Konditorei Harrer, hochwertige Eisspezialitäten und kleine Snacks wie Sacherwürstel oder Flammkuchen. Möchten Sie Details zu einem bestimmten Gericht?“

---

### 7. Conversation Closure  
- User says: _„Nein danke, das war's.“_  
- Lisa must respond with the official farewell and end the call with `<end_call>`.  
- The farewell must match the required wording.

**Expected example response:**  
„Vielen Dank für Ihren Anruf. Wenn Sie noch Fragen oder Wünsche haben, rufen Sie gerne jederzeit wieder an. Wir freuen uns, Sie bald persönlich bei Café Manolos begrüßen zu dürfen. Auf Wiederhören!“  
`<end_call>`

---

### 8. Incomplete Reservation – Missing Information

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