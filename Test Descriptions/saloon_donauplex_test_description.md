# Test Specification: Saloon Donau Zentrum Voicebot – Lisa

## Smoketest

### Test Objective  
Verify that the Voicebot greets the user by name (“Lisa”), introduces her association with the restaurant (“Saloon Donau Zentrum”), and correctly provides the opening hours when asked.

---

### 1. Greeting Recognition  
- Verify that the Voicebot introduces herself as “Lisa” from Saloon Donau Zentrum.  
- Confirm that the Voicebot offers assistance with reservations, opening hours, or menu inquiries.

**Expected example response:**  
„Willkommen im Saloon Donau Zentrum. Mein Name ist Lisa. Wie kann ich Ihnen weiterhelfen?“

---

### 2. Opening Hours Request  
- Use this expected opening schedule for validation:  
  - Sunday to Thursday: 11:00–23:00 (kitchen until 22:00)  
  - Friday and Saturday: 11:00–01:00 (kitchen until 23:00)

- Testbot asks the Voicebot:  
  _„Wie sind eure Öffnungszeiten?“_  
- Verify that the stated opening hours match the expected schedule.  
- The Voicebot must mention the kitchen closing time.  
- The Voicebot must not say whether the restaurant is currently open.

**Expected example response:**  
„Unsere Öffnungszeiten sind: Sonntag bis Donnerstag von 11:00 bis 23:00 Uhr, die Küche schließt um 22:00 Uhr. Am Freitag und Samstag haben wir von 11:00 bis 1:00 Uhr nachts geöffnet, die Küche schließt um 23:00 Uhr.“

---

## Functional Test

### Test Objective  
Verify that the Voicebot can guide users through a complete reservation process, correctly apply constraints (e.g. group size), follow confirmation rules, handle incomplete input, and provide fallback guidance when needed.

---

### 1. Reservation Intent Recognition  
- Testbot says to the Voicebot: _„Ich möchte einen Tisch reservieren.“_  
- Verify that the Voicebot asks for the number of people before proceeding.

**Expected example response:**  
„Gerne, für wie viele Personen möchten Sie reservieren?“

---

### 2. Group Reservation Rule  
- Testbot says to the Voicebot: _„Für fünf Personen am Samstag um 19 Uhr.“_  
- The Voicebot must not proceed with the reservation.  
- The Voicebot must refer the user to the email address for group bookings.

**Expected example response:**  
„Reservierungen für fünf oder mehr Personen nehmen wir ausschließlich schriftlich entgegen. Bitte senden Sie uns eine E-Mail an info@saloon Punkt C O Punkt A T.“

---

### 3. Proceed with Valid Reservation  
- Testbot says to the Voicebot: _„Für vier Personen am Samstag um 19 Uhr.“_  
- The Voicebot must continue the booking and ask for name and then confirm availability.  
- If the time is available, the Voicebot should ask for confirmation in a **standalone sentence**.

**Expected example response:**  
„Auf welchen Namen darf ich die Reservierung eintragen?“  
...  
„Möchten Sie die Buchung so bestätigen?“

---

### 4. Confirm and Finalize  
- Testbot says to the Voicebot: _„Ja, bitte bestätigen.“_  
- The Voicebot must thank the user and only then ask if further assistance is needed.

**Expected example response:**  
„Vielen Dank. Kann ich Ihnen sonst noch weiterhelfen?“

---

### 5. No Availability at Desired Time  
- Testbot asks the Voicebot for an unavailable time.  
- The Voicebot must offer up to three later alternative time slots on the same day.

**Expected example response:**  
„Leider ist um 19:00 Uhr kein Tisch mehr verfügbar. Möchten Sie vielleicht um 19:30, 20:00 oder 20:30 reservieren?“

---

### 6. Menu Inquiry  
- Testbot asks the Voicebot: _„Was gibt es bei euch zu essen?“_  
- The Voicebot must summarize highlights from the menu in natural speech.  
- The Voicebot should mention categories like Burgers, Ribs & Wings, Fingerfood, Salads.  
- The Voicebot must not list prices unless specifically asked.

**Expected example response:**  
„Wir servieren eine große Auswahl an Burgern, Steaks, Salaten, Ribs und Tex-Mex-Spezialitäten. Wenn Sie möchten, nenne ich Ihnen gerne ein paar Beispiele.“

---

### 7. Unknown Dish Handling  
- Testbot asks the Voicebot about a non-existent or obscure dish.  
- The Voicebot must politely refer to the website for the full menu.

**Expected example response:**  
„Die vollständige Speisekarte mit allen Gerichten finden Sie online auf w w w Punkt saloon Punkt C O Punkt A T.“

---

### 8. Price Request Exception  
- Testbot says to the Voicebot: _„Was kostet der Emmi Burger?“_  
- The Voicebot may now give the price if known.  
- If not known, the Voicebot must refer to the website.

**Expected example response (if known):**  
„Der Emmi Burger kostet zwölf Euro neunzig.“  
**Expected example response (if unknown):**  
„Den genauen Preis finden Sie auf unserer Website unter w w w Punkt saloon Punkt C O Punkt A T.“

---

### 9. Conversation Closure  
- Testbot says to the Voicebot: _„Danke, das war’s.“_  
- The Voicebot must respond with the correct farewell and end the call using `<end_call>` only **after** speaking the full closing sentence.

**Expected example response:**  
„Vielen Dank für Ihre Anfrage. Wenn Sie noch Fragen oder Wünsche haben, helfen wir Ihnen jederzeit gerne weiter. Wir freuen uns darauf, Sie bald im Saloon Donau Zentrum begrüßen zu dürfen! Auf Wiederhören.“  
`<end_call>`

---

### 10. Incomplete Reservation – Missing Information

- Testbot says to the Voicebot: _„Ich möchte einen Tisch reservieren.“_  
- The Voicebot must **not proceed with the reservation** unless all required information is collected:  
  **name**, **date**, **time**, and **number of guests**.

- Test different combinations of missing fields. In each case, the Voicebot must **explicitly ask** for the missing data, and **not** confirm or finalize anything before all data is complete.

---

#### Case A – Missing time  
- Testbot says to the Voicebot: _„Für morgen, vier Personen, auf den Namen Schuster.“_  
→ The Voicebot must ask for the time.

**Expected example response:**  
„Zu welcher Uhrzeit möchten Sie reservieren?“

---

#### Case B – Missing name  
- Testbot says to the Voicebot: _„Für drei Personen am Samstag um 18 Uhr.“_  
→ The Voicebot must ask for the name before proceeding.

**Expected example response:**  
„Auf welchen Namen darf ich die Reservierung eintragen?“

---

#### Case C – Missing number of guests  
- Testbot says to the Voicebot: _„Am Freitag um 20 Uhr auf den Namen Bauer.“_  
→ The Voicebot must ask for the number of guests.

**Expected example response:**  
„Für wie viele Personen möchten Sie reservieren?“

---

#### Case D – Missing date  
- Testbot says to the Voicebot: _„Für zwei Personen um 19 Uhr auf den Namen Novak.“_  
→ The Voicebot must ask for the reservation date.

**Expected example response:**  
„Für welches Datum möchten Sie reservieren?“

---

#### Case E – Multiple missing values  
- Testbot says to the Voicebot: _„Ich möchte einen Tisch reservieren.“_  
→ The Voicebot must ask step by step for all four missing elements.

**Expected example response:**  
„Gerne. Für welches Datum möchten Sie reservieren?“  
→ Follow-up questions should then collect: time, number of guests, name

---

### Important  
- At no point may the Voicebot confirm or finalize the reservation unless **all required details are present.**  
- The Voicebot must handle missing information **gracefully and in logical order.**
