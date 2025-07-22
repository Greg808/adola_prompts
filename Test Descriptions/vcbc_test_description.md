# Test Specification: Vienna City Beach Club Voicebot – Lea

## Smoketest

### Test Objective

Verify that Lea introduces herself correctly and responds to a basic FAQ regarding dogs.

---

### 1. Greeting Recognition

* Verify that the Voicebot introduces herself as “Lea” from the Vienna City Beach Club.
* Confirm she speaks in a relaxed and friendly tone.

**Expected example response:**
„Hi und willkommen! Ich bin Lea, dein der digitale K.I. Assistent für alle Fragen rund um den Vienna City Beach Club. Wie kann ich dir helfen?“

---

### 2. FAQ – Dogs Allowed

* User asks: *„Darf man Hunde mitnehmen?“*
* Lea must respond that dogs on a leash or with muzzle are welcome.

**Expected example response:**
„Ja, Hunde an der Leine oder mit Beißkorb sind bei uns willkommen.“

## Functional Test

### Test Objective

Ensure that Lea can handle typical guest inquiries about events, reservations, late arrival timing, and ticket/payment questions.

---

### 1. Reservation Handling – Volleyball Court

* User asks: *„Wie reserviere ich bei euch einen Volleyballplatz?“*
* Lea must refer the user to the external website using proper speech formatting.

**Expected example response:**
„Für einen Volleyballplatz wende Dich bitte an w w w Punkt beachvolley Minus wien Punkt a t.“

---

### 2. External Tool Referral – Shisha Bar

* User asks: *„Gibt’s bei euch Shisha?“*
* Lea must confirm and refer to the external Shisha team.
* She should provide the correct website link in spoken format.

**Expected example response:**
„Ja, das Team der externen Shisha-Bar erwartet dich mit vielen köstlichen Geschmacksrichtungen. Weitere Infos findest du auf w w w Punkt seelavie Punkt o r g.“

---

### 3. Closing Time Handling – Plenty of Time

* User asks: *„Kann ich heute noch vorbeikommen?“*
* Assume it's **21:30 on Friday** (closing at 02:00).
* More than 30 minutes remain. Lea must confirm they can still come and mention closing time.

**Expected example response:**
„Klar, komm gern vorbei – wir haben heute bis 02:00 geöffnet.“

---

### 4. Late Arrival Handling – Closing Soon

* User says: *„Kann ich heute noch vorbeikommen?“*
* Assume the time is **22:40 on a Sunday** (closing at 23:00).
* Less than 30 minutes remain. Lea must warn that there’s limited time.

**Expected example response:**
„Nur damit du’s weißt – wir schließen am Sonntag um 23:00. Wenn du’s noch rechtzeitig schaffst, komm gern vorbei – aber viel Zeit bleibt dann nicht mehr.“

---

### 5. Parking Information

* User asks: *„Wo kann ich parken?“*
* Lea must mention the short-term zone and walking distance.

**Expected example response:**
„Du kannst am Parkplatz ‚Neue Donau Mitte‘ parken – das ist eine Kurzparkzone, nur zwei Gehminuten vom Club entfernt.“

---

### 6. Payment Options – Bars vs Automaten

* User asks: *„Kann man beim Zigarettenautomaten mit Karte zahlen?“*
* Lea must say that only cash is accepted there but that card is accepted at the bar.

**Expected example response:**
„Beim Zigarettenautomaten kannst du nur bar zahlen. Aber an der Bar kannst du Zigaretten auch mit Karte kaufen.“

---

### 7. Unknown Question Handling

* User asks: *„Was kostet ein Cocktail bei euch mit Memberkarte an Dienstagen?“*
* If this info is not part of the known database, Lea should ask for clarification, and if still unclear, refer to the website.

**Expected example response:**
„Da bin ich mir grad nicht ganz sicher. Schau am besten direkt auf unsere Website – da findest du alle aktuellen Infos.“

---

### 8. Outro and Call End

* User says: *„Nein danke, das war’s.“*
* Lea must respond with the official outro and end the call.

**Expected example response:**
„Danke für deinen Anruf! Falls du in Zukunft noch Fragen hast, melde dich jederzeit gerne wieder. Genieß den Sommer im Vienna City Beach Club – bis bald!“
`<end_call>`
