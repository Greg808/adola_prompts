# Test Specification: ReadyForFit Wien-Süd Voicebot – Lisa

---

## Smoketest

### Test Objective  
Ensure that Lisa begins the call correctly and responds appropriately to a basic inquiry about opening hours.

---

### 1. Greeting Recognition  
- Verify that Lisa introduces herself as the assistant from “ReadyForFit Wien-Süd.”  
- Confirm that she offers help in a friendly, motivating tone.

**Expected example response:**  
„Hallo! Ich bin Lisa, der KI-Assistent vom E M S-Studio ReadyForFit Wien-Süd. Wie kann ich Ihnen helfen?“

---

### 2. Opening Hours Inquiry  
- Simulate the user asking: _„Wann habt ihr geöffnet?“_  
- Lisa must provide opening hours, differentiated by weekday, including mention of closed days.  
- Must use 24-hour time format and Austrian phrasing.

**Expected example response (for Monday):**  
„Wir haben am Montag von 8 bis 13 Uhr 30 und von 14 Uhr 30 bis 20 Uhr geöffnet. Mittwoch, Samstag und Sonntag ist geschlossen.“

---

## Functional Test

### Test Objective  
Ensure Lisa can answer detailed user questions about training, booking, location, equipment, and pricing. She must also gracefully handle unclear or off-topic questions and conclude calls appropriately.

---

### 1. Trial Session Price Inquiry  
- User says: _„Was kostet das Probetraining?“_  
- Lisa must provide the exact amount and offer further guidance.

**Expected example response:**  
„Das Probetraining kostet 19 Euro 90. Möchten Sie wissen, wie Sie es buchen können?“

---

### 2. Membership Information  
- User says: _„Welche Mitgliedschaften gibt es?“_  
- Lisa must answer high-level, avoid excessive detail, and ask a follow-up.

**Expected example response:**  
„Wir bieten monatliche und längere Mitgliedschaften an. Wollen Sie wissen, welche Vorteile dabei inkludiert sind?“

---

### 3. EMS Training Description  
- User asks: _„Was ist E M S Training?“_  
- Lisa must explain it clearly and shortly. She must spell out “E M S”.

**Expected example response:**  
„E M S steht für elektrisches Muskeltraining – zwanzig Minuten pro Woche reichen aus. Möchten Sie wissen, wie so eine Einheit genau abläuft?“

---

### 4. Suitability for Seniors  
- User says: _„Ist das auch für ältere Menschen geeignet?“_  
- Lisa must confirm and give reassurance.

**Expected example response:**  
„Ja, E M S eignet sich auch für ältere Menschen. Es ist gelenkschonend und individuell anpassbar.“

---

### 5. Address and Directions  
- User says: _„Wo seid ihr genau?“_  
- Lisa must provide the full address and ask if directions are needed.

**Expected example response:**  
„Ketzergasse 25 in Zwölfdreißig Wien. Suchen Sie Infos zur Anreise?“

---

### 6. Parking Availability  
- User says: _„Gibt es Parkplätze?“_  
- Lisa must explain clearly that no garage exists and suggest alternatives.

**Expected example response:**  
„Es gibt leider keine eigene Parkgarage. Entlang der Ketzergasse gibt es öffentliche Parkmöglichkeiten.“

---

### 7. Website Referral  
- User asks for more info: _„Wo finde ich die Preise?“_  
- Lisa must refer to the website in correct spoken format.

**Expected example response:**  
„Alle Preise finden Sie online auf we we we Punkt ready for fit Punkt a te.“

---

### 8. Unclear or Irrelevant Question  
- User says something unrelated: _„Was ist dein Lieblingssport?“_  
- Lisa must redirect to studio-relevant topics politely.

**Expected example response:**  
„Ich bin für Fragen zum E M S-Studio Wien-Süd da – möchten Sie etwas zu unseren Leistungen wissen?“

---

### 9. Call Finalization  
- User says: _„Danke, das war’s.“_  
- Lisa must confirm, give a proper closing, and end the call.

**Expected example response:**  
„Danke für Ihren Anruf! Bei weiteren Fragen sind wir jederzeit da – auf we we we Punkt ready for fit Punkt a te. Bis bald und alles Gute!“  
`<end_call>`