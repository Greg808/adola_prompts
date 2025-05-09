# Useful Prompts

## prompt to genarate test data for an outbound prompt 

**Hinweis:** Es handelt sich um **Outbound-Kaltakquise-Telefonate**, bei denen der Bot das Gespräch initiiert.

Nutze das ChatGPT‑VSCode‑Plugin, um die aktuell in Visual Studio Code geöffnete Prompt-Datei zu analysieren. Identifiziere alle relevanten Abschnitte, Variablen und Branch-Definitionen direkt aus dieser Datei.

Generiere 15 realistische Test-Telefonate mit jeweils 8–14 Bot‑User‑Wechseln, inklusive typischer, abweichender und problematischer Verläufe (z. B. Missverständnisse, Rückfragen, unerwartete Antworten).

Gruppiere die Antworten des Anrufers je Branch. Gib jedes Telefonat einzeln und vorlesebereit im Format:

Bot: …  
User: …  
Bot: …  
User: …  
…

Achte darauf, dass jede Simulation aus der echten Branch-Logik der Prompt-Datei abgeleitet wird. Nutze stets die aktuell geöffnete Datei im Editor als Quelle.

Ziel ist es, sowohl den Happy Path als auch Edge Cases und Sonderfälle zu testen.

## prompt to generate test data for an inbound prompt

**Hinweis:** Es handelt sich um **Inbound-Service-Telefonate**, bei denen der Anrufer den Bot kontaktiert (z. B. wegen einer Reservierung, Rückfrage oder eines Anliegens).

Nutze das ChatGPT‑VSCode‑Plugin, um die aktuell in Visual Studio Code geöffnete Prompt-Datei zu analysieren. Identifiziere alle relevanten Abschnitte, Variablen und Branch-Definitionen direkt aus dieser Datei.

Generiere 15 realistische Test-Telefonate mit jeweils 8–14 Bot‑User‑Wechseln, inklusive typischer, abweichender und problematischer Verläufe (z. B. unklare Anliegen, Rückfragen, nicht vorhandene Daten).

Gruppiere die Anliegen des Anrufers je Branch. Gib jedes Telefonat einzeln und vorlesebereit im Format:

Bot: …  
User: …  
Bot: …  
User: …  
…

Achte darauf, dass jede Simulation aus der echten Branch-Logik der Prompt-Datei abgeleitet wird. Nutze stets die aktuell geöffnete Datei im Editor als Quelle.

Ziel ist es, sowohl den Happy Path als auch Edge Cases und Sonderfälle zu testen.
