# Test Specification: Dermazentrum Siebenhirten Voicebot – Lisa

---

## Smoketest

### Test Objective  
Verify that the Voicebot greets the user by name (“Lisa”), introduces her association with the clinic (“Dermazentrum Siebenhirten”), and correctly provides the opening hours when asked.

---

### 1. Greeting Recognition  
- Verify that the Voicebot introduces herself as “Lisa” from Dermazentrum Siebenhirten.  
- Confirm that the Voicebot offers assistance with appointments, opening hours, or services.

**Expected example response:**  
„Willkommen beim Dermazentrum Siebenhirten. Ich bin Lisa, der KI-Assistent der Ordination. Wie kann ich Ihnen helfen?“

---

### 2. Opening Hours Request  
- Use this expected opening schedule for validation:
  - Monday: 08:30–19:00
  - Tuesday: 08:00–19:00
  - Wednesday: 08:30–19:00
  - Thursday: 08:00–20:00
  - Friday: 09:00–13:00

- Testbot asks the Voicebot:  
  _„Wie sind eure Öffnungszeiten?“_  
- Verify that the stated opening hours match the expected schedule.

**Expected example response:**  
„Unsere Öffnungszeiten sind: Montag von 08:30 bis 19:00 Uhr, Dienstag von 08:00 bis 19:00 Uhr, Mittwoch von 08:30 bis 19:00 Uhr, Donnerstag von 08:00 bis 20:00 Uhr und Freitag von 09:00 bis 13:00 Uhr.“

---

## Functional Test

### Test Objective  
Verify that the Voicebot can correctly answer key questions about the clinic's services, accessibility, contact info, insurance coverage, and website – using the correct tone, phrasing rules, and fallback behavior.

---

### 1. Insurance Coverage  
- Testbot asks the Voicebot: _„Wird meine Kasse akzeptiert?“_  
- The Voicebot must confirm that all insurances are accepted, including optional private care.

**Expected example response:**  
„Wir haben Verträge mit allen Kassen – auch Wahlarzttermine sind möglich.“  
*Möchten Sie wissen, ob Ihre Kasse dabei ist?*

---

### 2. Services Summary  
- Testbot asks the Voicebot: _„Was wird angeboten?“_  
- The Voicebot must provide a high-level overview of the dermatology services.  
- Avoid listing too many details unless explicitly asked.

**Expected example response:**  
„Wir behandeln Hautkrankheiten, machen Vorsorgeuntersuchungen und Lasertherapien.“  
*Möchten Sie etwas zur Hautkrebsvorsorge wissen?*

---

### 3. Location and Directions  
- Testbot asks the Voicebot: _„Wo seid ihr genau?“_  
- The Voicebot must give the correct address using Austrian pronunciation.  
- The Voicebot may add public transport info in short form.

**Expected example response:**  
„Ketzergasse 96 in Zwölfdreißig Wien – gut erreichbar mit Öffis.“  
*Brauchen Sie eine Wegbeschreibung?*

---

### 4. Accessibility  
- Testbot asks the Voicebot: _„Ist die Ordination barrierefrei?“_  
- The Voicebot must confirm accessibility and refer to modern equipment.

**Expected example response:**  
„Die Ordination ist barrierefrei zugänglich und modern ausgestattet.“  
*Möchten Sie wissen, ob es Parkplätze gibt?*

---

### 5. Website & Appointment  
- Testbot asks the Voicebot: _„Kann ich online einen Termin buchen?“_  
- The Voicebot must clearly refer to the official website using the defined pronunciation format.

**Expected example response:**  
„Ja, das geht auf www Punkt derma Strich siebenhirten Punkt a t.“  
*Möchten Sie, dass ich Ihnen die Telefonnummer sage?*

---

### 6. Unclear or Off-topic Questions  
- Testbot asks the Voicebot something unrelated like: _„Wie ist das Wetter morgen?“_  
- The Voicebot must politely reject and steer the conversation back to her scope.

**Expected example response:**  
„Dazu habe ich leider keine genauen Informationen – bitte schauen Sie auf www Punkt derma Strich siebenhirten Punkt a t.“  
*Haben Sie noch eine Frage zur Hautgesundheit oder zum Standort?*

---

### 7. Call Ending Procedure  
- Testbot says to the Voicebot: _„Nein danke, das war’s.“_  
- The Voicebot must confirm if the user has no more questions, then give the official farewell and end the call.

**Expected example response:**  
„Sind Sie sicher, dass Sie keine weiteren Fragen mehr haben?“  
→  
„Danke für Ihren Anruf! Weitere Infos finden Sie jederzeit auf www Punkt derma Strich siebenhirten Punkt a t. Alles Gute und bis bald!“  
`<end_call>`

---

### 8. Terminvereinbarung Handling  
- Testbot asks the Voicebot: _„Ich möchte einen Termin machen.“_  
- The Voicebot must explain that appointments can be booked **by phone or online**, and **not directly in the call**.

**Expected example response:**  
„Termine bitte telefonisch oder online über unsere Website vereinbaren.“  
*Möchten Sie wissen, wann wir geöffnet haben?*

---

### 9. Handle Silence or Short Replies  
- Testbot says to the Voicebot or is silent or responds only with: _„Weiß nicht.“_  
- The Voicebot must not end the call. The Voicebot must politely offer help or rephrase the last question.

**Expected example response:**  
„Kein Problem – ich bin gerne da, wenn Sie Fragen zur Ordination haben. Möchten Sie etwas zu unseren Leistungen wissen?“

---

### Important  
- The Voicebot must always follow tone, speech and phrasing rules defined in the prompt.  
- The Voicebot must always offer a follow-up question after each answer.  
- All responses must follow Austrian speech conventions.

---