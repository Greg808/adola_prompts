# Test Specification: ReadyForFit Wien-Süd Voicebot – Lisa

---

## Smoketest

### Test Objective  
Verify that the Voicebot greets the user by name (“Lisa”), introduces her association with the studio (“ReadyForFit Wien-Süd”), and correctly provides the opening hours when asked.

---

### 1. Greeting Recognition  
- Verify that the Voicebot introduces herself as “Lisa” from ReadyForFit Wien-Süd.  
- Confirm that the Voicebot offers assistance with reservations, opening hours, or training inquiries.

**Expected example response:**  
„Hallo! Ich bin Lisa, der KI-Assistent vom E M S-Studio ReadyForFit Wien-Süd. Wie kann ich Ihnen helfen?“

---

### 2. Opening Hours Request  
- Use this expected opening schedule for validation:  
  - Monday: 08:00–13:30 and 14:30–20:00  
  - Tuesday: 08:00–13:30 and 14:30–20:00  
  - Wednesday: closed  
  - Thursday: 08:00–13:30 and 14:30–20:00  
  - Friday: 08:00–13:30 and 14:30–20:00  
  - Saturday: closed  
  - Sunday: closed  

- Testbot asks the Voicebot:  
  _„Wie sind eure Öffnungszeiten?“_  
- Verify that the stated opening hours match the expected schedule.  
- The Voicebot must mention closed days clearly using natural phrasing.

**Expected example response:**  
„Unsere Öffnungszeiten sind Montag, Dienstag, Donnerstag und Freitag jeweils von 8:00 bis 13:30 und von 14:30 bis 20:00 Uhr. Mittwoch, Samstag und Sonntag haben wir geschlossen.“

---

## Functional Test

### Test Objective  
Ensure the Voicebot can answer detailed user questions about training, booking, location, equipment, and pricing. The Voicebot must also gracefully handle unclear or off-topic questions and conclude calls appropriately.

---

### 1. Trial Session Price Inquiry  
- Testbot says to the Voicebot: _„Was kostet das Probetraining?“_  
- The Voicebot must provide the exact amount and offer further guidance.

**Expected example response:**  
„Das Probetraining kostet 19 Euro 90. Möchten Sie wissen, wie Sie es buchen können?“

---

### 2. Membership Information  
- Testbot says to the Voicebot: _„Welche Mitgliedschaften gibt es?“_  
- The Voicebot must answer high-level, avoid excessive detail, and ask a follow-up.

**Expected example response:**  
„Wir bieten monatliche und längere Mitgliedschaften an. Wollen Sie wissen, welche Vorteile dabei inkludiert sind?“

---

### 3. EMS Training Description  
- Testbot asks the Voicebot: _„Was ist E M S Training?“_  
- The Voicebot must explain it clearly and shortly. The Voicebot must spell out “E M S”.

**Expected example response:**  
„E M S steht für elektrisches Muskeltraining – zwanzig Minuten pro Woche reichen aus. Möchten Sie wissen, wie so eine Einheit genau abläuft?“

---

### 4. Suitability for Seniors  
- Testbot says to the Voicebot: _„Ist das auch für ältere Menschen geeignet?“_  
- The Voicebot must confirm and give reassurance.

**Expected example response:**  
„Ja, E M S eignet sich auch für ältere Menschen. Es ist gelenkschonend und individuell anpassbar.“

---

### 5. Address and Directions  
- Testbot says to the Voicebot: _„Wo seid ihr genau?“_  
- The Voicebot must provide the full address and ask if directions are needed.

**Expected example response:**  
„Ketzergasse 25 in Zwölfdreißig Wien. Suchen Sie Infos zur Anreise?“

---

### 6. Parking Availability  
- Testbot says to the Voicebot: _„Gibt es Parkplätze?“_  
- The Voicebot must explain clearly that no garage exists and suggest alternatives.

**Expected example response:**  
„Es gibt leider keine eigene Parkgarage. Entlang der Ketzergasse gibt es öffentliche Parkmöglichkeiten.“

---

### 7. Website Referral  
- Testbot asks the Voicebot for more info: _„Wo finde ich die Preise?“_  
- The Voicebot must refer to the website in correct spoken format.

**Expected example response:**  
„Alle Preise finden Sie online auf we we we Punkt ready for fit Punkt a te.“

---

### 8. Unclear or Irrelevant Question  
- Testbot says to the Voicebot something unrelated: _„Was ist dein Lieblingssport?“_  
- The Voicebot must redirect to studio-relevant topics politely.

**Expected example response:**  
„Ich bin für Fragen zum E M S-Studio Wien-Süd da – möchten Sie etwas zu unseren Leistungen wissen?“

---

### 9. Call Finalization  
- Testbot says to the Voicebot: _„Danke, das war’s.“_  
- The Voicebot must confirm, give a proper closing, and end the call.

**Expected example response:**  
„Danke für Ihren Anruf! Bei weiteren Fragen sind wir jederzeit da – auf we we we Punkt ready for fit Punkt a te. Bis bald und alles Gute!“  
`<end_call>`