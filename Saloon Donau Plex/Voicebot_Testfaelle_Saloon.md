# Testfälle für Voicebot 'Lisa' – Saloon Donau Zentrum

| Testfall                                | Erwartetes Verhalten                                                        |ok         |nok     |
|:----------------------------------------|:----------------------------------------------------------------------------|:----------|:-------|
| Reservierung für 2 am Freitag um 19 Uhr | Reservierung wird korrekt angenommen und bestätigt.                         |           |        |
| Mittwochsreservierung um 12:30          | Reservierung wird korrekt angenommen und bestätigt.                         |           |        |
| Reservierung für 4 am Samstagabend      | Reservierung wird korrekt angenommen und bestätigt.                         |           |        |
| Reservierung für 20. Juli um 18 Uhr     | Reservierung wird korrekt angenommen und bestätigt.                         |           |        | 
| Öffnungszeiten unter der Woche          | Öffnungszeiten Mo–Do werden korrekt genannt.                                |           |        |
| Sonntags geöffnet?                      | Öffnungszeiten für Sonntag werden korrekt genannt.                          |ja         |        |
| Küchenschluss Samstag                   | Küchenschluss (23:00 Uhr) wird korrekt genannt.                             |ja         |        | 
| Preis Cheesecake                        | Preis (6,90 €) wird korrekt genannt.                                        |ja         |        |
| Vegetarisches Gericht                   | Vegetarische Optionen werden genannt oder auf vollständige Karte verwiesen. |ja         |        |
| Crazy Chicken Salat Inhalt              | Beschreibung des Gerichts wird korrekt genannt.                             |           |        |
| Preis Filetsteak                        | Preis (36,90 €) wird korrekt genannt.                                       |           |        | 
| Reservierung am 35. Juli                | Bot erkennt ungültiges Datum und bittet um Korrektur.                       |           |        |
| Reservierung Dienstag 2 Uhr früh        | Bot erkennt unübliche Zeit außerhalb Öffnungszeiten.                        |           |        |
| Reservierung für 15 Personen            | Bot bittet um schriftliche Anfrage per E-Mail.                              |           |        |
| Mozzarella-Burger                       | Bot erkennt Gericht nicht und verweist auf gültige Karte.                   |           |        | 
| Reservierung Sonntag 23:30              | Bot erklärt Küchenschluss um 22:00 und bietet alternative Zeit an.          |           |        | 
| Reservierung Montag Mitternacht         | Bot erklärt Öffnungszeiten (Mo nicht geschlossen, aber Uhrzeit außerhalb).  |           |        | 
| Reservierung für 10 telefonisch         | Bot bittet um E-Mail wegen Gruppenreservierung.                             |           |        |
| Kontakt via WhatsApp                    | Bot erklärt verfügbare Kontaktwege (Telefon, E-Mail).                       |           |        |
| Speisekarte zum Download                | Bot erklärt, dass vollständige Karte im Restaurant verfügbar ist.           |           |        |
| Frage zu Gutscheinen                    | Bot erklärt, dass dies außerhalb des Aufgabenspektrums liegt.               |           |        |
| Frage zu Catering                       | Bot erklärt, dass dies nicht im Aufgabenspektrum liegt.                     |           |        |
| Was gibt’s bei euch alles?              | Bot nennt Menüauszug oder verweist auf vollständige Karte.                  |           |        | 
| Was hast du gerade gesagt?              | Bot wiederholt höflich die letzte Aussage.                                  |           |        | 
| Reservierung Do 18:00 für 2             | Reservierung wird korrekt angenommen und bestätigt.                         |           |        |
| Feiertag geöffnet?                      | Bot nennt korrekte Info zu Feiertagsöffnungszeiten oder verweist Website.   |           |        |
| Beliebtestes Gericht?                   | Bot nennt ein beliebtes Gericht oder verweist auf Empfehlungen.             |           |        |
| Draußen sitzen möglich?                 | Bot informiert über Sitzmöglichkeiten im Freien.                            |           |        |
| Glutenfreie Speisen?                    | Bot nennt glutenfreie Optionen oder verweist auf Karte.                     |           |        |
| Letzte Reservierungszeit heute?         | Bot nennt spätestmögliche Reservierungszeit.                                |           |        |
| Cheesecake hausgemacht?                 | Bot gibt Auskunft oder verweist auf Website/Karte.                          |           |        |
| Steak-Beilagen?                         | Bot nennt typische Beilagen oder verweist auf Karte.                        |           |        |
| Kindergerichte?                         | Bot nennt Kindergerichte oder verweist auf Karte.                           |           |        |
| Restaurant-Adresse?                     | Bot nennt korrekte Adresse.                                                 |           |        |
| Reservierung 30. Feb?                   | Bot erkennt ungültiges Datum und bittet um Korrektur.                       |           |        |
| Reservierung für 22?                    | Bot bittet um Anfrage per E-Mail wegen Gruppengröße.                        |           |        |
| Veg. Tagesgerichte heute?               | Bot nennt Tagesgerichte oder verweist freundlich auf Karte/Website.         |           |        |
| Handy aufladen möglich?                 | Bot reagiert höflich, nennt ggf. Info oder sagt freundlich, dass das nicht  |           |        |
| Papagei erlaubt?                        | Bot reagiert freundlich und erklärt Haustierregelung.                       |           |        |
| Barrierefrei?                           | Bot nennt Info zur Barrierefreiheit oder verweist auf Website.              |           |        |
| Bitcoin-Zahlung möglich?                | Bot nennt verfügbare Zahlungsmittel oder verweist freundlich                |           |        |
| Kalorien Burger?                        | Bot verweist auf Website/Karte bei fehlender Info.                          |           |        |
| Parkplätze in Nähe?                     | Bot gibt Auskunft über Parkmöglichkeiten.                                   |           |        |
| SMS möglich?                            | Bot erklärt verfügbare Kontaktwege (Telefon, E-Mail).                       |           |        |
| Essen?                                  | Bot fragt höflich nach Konkretisierung.                                     |           |        |
| Was geht heute so?                      | Bot bittet um genauere Fragestellung.                                       |           |        |
| Macht ihr auch Frühstück?               | Bot nennt passende Info oder erklärt, dass kein Frühstück angeboten wird.   |           |        |
| Ich will was trinken.                   | Bot fragt höflich nach, ob Tisch gewünscht ist oder verweist                |           |        |
| Wie lange dauert das Essen bei euch?    | Bot nennt übliche Wartezeiten oder verweist auf Küche.                      |           |        |
| Nussallergie – was essen?               | Bot reagiert sensibel und verweist auf Allergenkennzeichnung vor Ort.       |           |        |
| Ist das Filetsteak medium oder well done| Bot erklärt Garstufen oder fragt nach Wunsch.                               |           |        |
| Wie ist das Wetter bei euch?            | Bot erklärt, dass er dazu keine Auskunft geben kann.                        |           |        |
| Kann ich den Tisch mitnehmen?           | Bot reagiert freundlich und humorvoll.                                      |           |        |
| Allergenärmstes Gericht?                | Bot empfiehlt Nachfrage im Restaurant.                                      |           |        |