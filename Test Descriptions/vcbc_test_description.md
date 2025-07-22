# Test Specification: Vienna City Beach Club Voicebot – Lea

## Smoketest

### Test Objective

Verify that the Voicebot greets the user by name (“Lea”), introduces her association with the Vienna City Beach Club, and correctly provides the opening hours when asked.

---

### 1. Greeting Recognition

- Verify that the Voicebot introduces herself as “Lisa” from the Vienna City Beach Club.
- Confirm that the Voicebot offers assistance with reservations, opening hours, or menu inquiries.

**Expected example response:**
„Hi und willkommen! Ich bin Lea, dein der digitale K.I. Assistent für alle Fragen rund um den Vienna City Beach Club. Wie kann ich dir helfen?“

---

### 2. Opening Hours Request
- Use this expected opening schedule for validation:
  - Sunday to Thursday: 11:00–23:00 (kitchen until 22:00)
  - Friday and Saturday: 11:00–01:00 (kitchen until 23:00)

- Testbot asks the Voicebot:  
  _„Wie sind eure Öffnungszeiten?“_  
- Verify that the stated opening hours match the expected schedule.
- The Voicebot must not say whether the venue is currently open.

**Expected example response:**  
„Unsere Öffnungszeiten sind von Sonntag bis Donnerstag jeweils von 11:00 bis 23:00 Uhr – die Küche ist bis 22:00 geöffnet. Am Freitag und Samstag haben wir von 11:00 bis 01:00 Uhr geöffnet, die Küche ist bis 23:00 Uhr für euch da.“

---

## Functional Test

### Test Objective

Ensure that Lea can handle typical guest inquiries about events, reservations, late arrival timing, and ticket/payment questions.

---

### 1. Reservation Handling – Volleyball Court

* Testbot asks the Voicebot: *„Wie reserviere ich bei euch einen Volleyballplatz?“*
* The Voicebot must refer the user to the external website using proper speech formatting.

**Expected example response:**
„Für einen Volleyballplatz wende Dich bitte an w w w Punkt beachvolley Minus wien Punkt a t.“

---

### 2. External Tool Referral – Shisha Bar

* Testbot asks the Voicebot: *„Gibt’s bei euch Shisha?“*
* The Voicebot must confirm and refer to the external Shisha team.
* The Voicebot should provide the correct website link in spoken format.

**Expected example response:**
„Ja, das Team der externen Shisha-Bar erwartet dich mit vielen köstlichen Geschmacksrichtungen. Weitere Infos findest du auf w w w Punkt seelavie Punkt o r g.“

---

### 3. Closing Time Handling – Plenty of Time

* Testbot asks the Voicebot: *„Kann ich heute noch vorbeikommen?“*
* Assume it's **21:30 on Friday** (closing at 02:00).
* More than 30 minutes remain. The Voicebot must confirm they can still come and mention closing time.

**Expected example response:**
„Klar, komm gern vorbei – wir haben heute bis 02:00 geöffnet.“

---

### 4. Late Arrival Handling – Closing Soon

* Testbot says to the Voicebot: *„Kann ich heute noch vorbeikommen?“*
* Assume the time is **22:40 on a Sunday** (closing at 23:00).
* Less than 30 minutes remain. The Voicebot must warn that there’s limited time.

**Expected example response:**
„Nur damit du’s weißt – wir schließen am Sonntag um 23:00. Wenn du’s noch rechtzeitig schaffst, komm gern vorbei – aber viel Zeit bleibt dann nicht mehr.“

---

### 5. Parking Information

* Testbot asks the Voicebot: *„Wo kann ich parken?“*
* The Voicebot must mention the short-term zone and walking distance.

**Expected example response:**
„Du kannst am Parkplatz ‚Neue Donau Mitte‘ parken – das ist eine Kurzparkzone, nur zwei Gehminuten vom Club entfernt.“

---

### 6. Payment Options – Bars vs Automaten

* Testbot asks the Voicebot: *„Kann man beim Zigarettenautomaten mit Karte zahlen?“*
* The Voicebot must say that only cash is accepted there but that card is accepted at the bar.

**Expected example response:**
„Beim Zigarettenautomaten kannst du nur bar zahlen. Aber an der Bar kannst du Zigaretten auch mit Karte kaufen.“

---

### 7. Unknown Question Handling

* Testbot asks the Voicebot: *„Was kostet ein Cocktail bei euch mit Memberkarte an Dienstagen?“*
* If this info is not part of the known database, the Voicebot should ask for clarification, and if still unclear, refer to the website.

**Expected example response:**
„Da bin ich mir grad nicht ganz sicher. Schau am besten direkt auf unsere Website – da findest du alle aktuellen Infos.“

---

### 8. Outro and Call End

* Testbot says to the Voicebot: *„Nein danke, das war’s.“*
* The Voicebot must respond with the official outro and end the call.

**Expected example response:**
„Danke für deinen Anruf! Falls du in Zukunft noch Fragen hast, melde dich jederzeit gerne wieder. Genieß den Sommer im Vienna City Beach Club – bis bald!“
`<end_call>`
