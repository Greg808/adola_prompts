# Test Specification: Saloon Donau Zentrum Voicebot – Lisa

---

## Smoketest

### Test Objective  
Ensure that Lisa starts the conversation correctly and responds appropriately to a basic inquiry about the restaurant's opening hours.

---

### 1. Greeting Recognition  
- Verify that Lisa introduces herself by name and mentions the restaurant “Saloon Donau Zentrum.”  
- Confirm that she offers assistance in a friendly and professional manner.

**Expected example response:**  
„Willkommen im Saloon Donau Zentrum. Mein Name ist Lisa. Wie kann ich Ihnen weiterhelfen?“

---

### 2. Opening Hours Inquiry  
- Simulate the user asking: _„Wann habt ihr geöffnet?“_  
- Verify that Lisa provides correct opening hours in natural speech.  
- The response must reflect whether the current day is a weekday or weekend.  
- Include the kitchen closing time.

**Expected example response (for Friday):**  
„Wir haben am Freitag von 11:00 bis 1:00 Uhr nachts geöffnet, die Küche schließt um 23:00 Uhr.“

---

## Functional Test

### Test Objective  
Verify that Lisa can guide users through a complete reservation process, correctly apply constraints (e.g. group size), follow confirmation rules, handle incomplete input, and provide fallback guidance when needed.

---

### 1. Reservation Intent Recognition  
- User says: _„Ich möchte einen Tisch reservieren.“_  
- Verify that Lisa asks for the number of people before proceeding.

**Expected example response:**  
„Gerne, für wie viele Personen möchten Sie reservieren?“

---

### 2. Group Reservation Rule  
- User says: _„Für fünf Personen am Samstag um 19 Uhr.“_  
- Lisa must not proceed with the reservation.  
- She must refer the user to the email address for group bookings.

**Expected example response:**  
„Reservierungen für fünf oder mehr Personen nehmen wir ausschließlich schriftlich entgegen. Bitte senden Sie uns eine E-Mail an info@saloon Punkt C O Punkt A T.“

---

### 3. Proceed with Valid Reservation  
- User says: _„Für vier Personen am Samstag um 19 Uhr.“_  
- Lisa must continue the booking and ask for name and then confirm availability.  
- If the time is available, she should ask for confirmation in a **standalone sentence**.

**Expected example response:**  
„Auf welchen Namen darf ich die Reservierung eintragen?“  
...  
„Möchten Sie die Buchung so bestätigen?“

---

### 4. Confirm and Finalize  
- Simulate user saying: _„Ja, bitte bestätigen.“_  
- Lisa must thank the user and only then ask if further assistance is needed.

**Expected example response:**  
„Vielen Dank. Kann ich Ihnen sonst noch weiterhelfen?“

---

### 5. No Availability at Desired Time  
- Simulate user asking for an unavailable time.  
- Lisa must offer up to three later alternative time slots on the same day.

**Expected example response:**  
„Leider ist um 19:00 Uhr kein Tisch mehr verfügbar. Möchten Sie vielleicht um 19:30, 20:00 oder 20:30 reservieren?“

---

### 6. Menu Inquiry  
- User asks: _„Was gibt es bei euch zu essen?“_  
- Lisa must summarize highlights from the menu in natural speech.  
- She should mention categories like Burgers, Ribs & Wings, Fingerfood, Salads.  
- She must not list prices unless specifically asked.

**Expected example response:**  
„Wir servieren eine große Auswahl an Burgern, Steaks, Salaten, Ribs und Tex-Mex-Spezialitäten. Wenn Sie möchten, nenne ich Ihnen gerne ein paar Beispiele.“

---

### 7. Unknown Dish Handling  
- User asks about a non-existent or obscure dish.  
- Lisa must politely refer to the website for the full menu.

**Expected example response:**  
„Die vollständige Speisekarte mit allen Gerichten finden Sie online auf w w w Punkt saloon Punkt C O Punkt A T.“

---

### 8. Price Request Exception  
- User says: _„Was kostet der Emmi Burger?“_  
- Lisa may now give the price if known.  
- If not known, she must refer to the website.

**Expected example response (if known):**  
„Der Emmi Burger kostet zwölf Euro neunzig.“  
**Expected example response (if unknown):**  
„Den genauen Preis finden Sie auf unserer Website unter w w w Punkt saloon Punkt C O Punkt A T.“

---

### 9. Conversation Closure  
- User says: _„Danke, das war’s.“_  
- Lisa must respond with the correct farewell and end the call using `<end_call>` only **after** speaking the full closing sentence.

**Expected example response:**  
„Vielen Dank für Ihre Anfrage. Wenn Sie noch Fragen oder Wünsche haben, helfen wir Ihnen jederzeit gerne weiter. Wir freuen uns darauf, Sie bald im Saloon Donau Zentrum begrüßen zu dürfen! Auf Wiederhören.“  
`<end_call>`

---

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