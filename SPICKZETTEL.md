# Spickzettel EKG-AI · 8 Stunden

Acht Blöcke. Jeden Prompt in Claude Code kopieren, das Ergebnis prüfen, dann weiter. Wer schneller ist, baut frei, die „Fertig, wenn“-Punkte gelten trotzdem.

| Block | Zeit | Thema |
|---|---|---|
| 1 | 30 Min. | Setup |
| 2 | 30 Min. | Medizinische Spezifikation |
| 3 | 45 Min. | Foto-Upload mit Vorschau |
| 4 | 45 Min. | KI-Anbindung |
| 5 | 60 Min. | Strukturierter Befund mit Ampel |
| 6 | 75 Min. | Prompt mit Testfällen verbessern |
| 7 | 75 Min. | Robustheit und Handy-Test |
| 8 | 60 Min. | Blind-Test, Demo, Pitch |

Bleibt eine Stunde Puffer.

## Block 1 · Setup
Schlüssel eintragen: `.env.example` zu `.env` kopieren und den ausgehändigten Schlüssel eintragen (im Texteditor, nicht über Claude Code).
```
Lies README.md und CLAUDE.md. Prüfe, ob Node.js ab Version 20 installiert ist, und lege die leeren Ordner testfaelle, prompt und ergebnisse an. Sag mir in drei Sätzen, was als Nächstes kommt.
```
**Fertig, wenn:** Node passt, `.env` existiert, Ordner sind da.

## Block 2 · Medizinische Spezifikation (ohne Code)
Das Medizin-Team legt in `spec.md` fest, was die App sagen darf und wann sie wie warnt:
- Ampel-Definition: ROT (zeitkritisch), GELB (auffällig), GRÜN (keine akut kritischen Zeichen), GRAU (nicht beurteilbar)
- Liste der zeitkritischen Befunde
- Schwellenwerte, jeder mit Quelle oder als „offen“ markiert
- Über- oder Untertriage: Was ist im Zweifel die sichere Seite?

**Fertig, wenn:** die Ampel-Definition von zwei Personen gegengelesen ist.

## Block 3 · Foto-Upload mit Vorschau
```
Baue die Grundversion: server.js und public/index.html. Ein großer Button „EKG fotografieren / Bild wählen“, danach Vorschau mit den Buttons „Analysieren“ und „Anderes Bild“. Verkleinere das Bild im Browser auf höchstens 1600 Pixel Kantenlänge (JPEG). Darunter drei Fototipps: gut beleuchtet, gerade von oben, ganzes EKG im Bild. Der Hinweis aus CLAUDE.md ist immer sichtbar. Zeige beim Start die Adresse für den Laptop und für Handys im selben WLAN.
```
**Fertig, wenn:** Bild wählen und Vorschau funktionieren auf Laptop und Handy.

## Block 4 · KI-Anbindung
```
Binde die KI an: neuer Endpunkt POST /api/analyse, der das Bild mit dem Text „Werte dieses EKG aus.“ an die Anthropic Messages API schickt. Den System-Prompt liest der Server bei jeder Anfrage frisch aus prompt/system.md. Schlüssel und Modell kommen nur aus .env. Zeige die Antwort zunächst als Rohtext. Fehler erscheinen als kurze deutsche Meldung ohne technische Details.
```
**Fertig, wenn:** ein Test-EKG eine Antwort liefert und der Schlüssel nirgends in `public/` steht.

## Block 5 · Strukturierter Befund mit Ampel
```
Stelle die Ausgabe auf JSON um mit den Feldern: beurteilbar, ampel, hauptbefund, kritische_zeichen (mit Ableitungen), parameter (Rhythmus, Frequenz, Lagetyp, PQ, QRS, QTc, ST/T), differenzialdiagnosen, unsicherheiten, konfidenz, handlungshinweis. Übernimm Ampel-Definition, zeitkritische Befunde und Schwellenwerte WORTGETREU aus spec.md in prompt/system.md. Zeige oben einen breiten Ampelbalken (Farbe plus Text), darunter Hauptbefund und Parametertabelle. Bei ungültiger Antwort einmal wiederholen. Mit ?demo=1 zeigt die Seite drei feste Beispielbefunde ohne Netz.
```
**Fertig, wenn:** die Ampel ohne Scrollen sichtbar ist und der Demo-Modus läuft.

## Block 6 · Prompt mit Testfällen verbessern
Testfälle aus `daten/testfaelle/` in den Ordner `testfaelle` kopieren. Fünf Fälle zum Verbessern, drei Blind-Fälle bleiben bis Block 8 ungesehen.
```
Baue testlauf.js: schickt alle Bilder aus testfaelle durch dieselbe Auswertung wie die App und schreibt eine CSV nach ergebnisse/ mit Datei, KI-Hauptbefund, Ampel, Konfidenz und leeren Spalten Bewertung_Medizin und Kritischer_Fehler. Die Dateien Fall06 bis Fall08 laufen nur mit dem Zusatz --blind mit. Bewerte nichts selbst.
```
Dann die Schleife: Testlauf, jede Zeile bewerten, **eine** Prompt-Änderung, erneut testen. Verschlechterung zurücknehmen.

**Fertig, wenn:** drei Testläufe dokumentiert sind und kein Kontrollbild eine Ampelfarbe außer GRAU bekommt.

## Block 7 · Robustheit und Handy-Test
```
Mache die App robuster, ohne prompt/system.md zu ändern: zu kleine oder zu dunkle Bilder ablehnen, verständliche Meldungen bei fehlendem Netz und Zeitüberschreitung mit Button „Erneut versuchen“, Ladeanzeige mit Sekunden, kein Doppelklick während der Analyse. Buttons mindestens 60 Pixel hoch, Dunkelmodus nach Handy-Einstellung, Ampel zusätzlich mit Symbol für Rot-Grün-Schwäche.
```
**Fertig, wenn:** der ganze Ablauf auf einem Handy mit einer Hand funktioniert.

## Block 8 · Blind-Test, Demo, Pitch
- Prompt einfrieren, Blind-Fälle **einmal** laufen lassen, Ergebnis nicht nachbessern
- `ergebnis.md`: Aufbau, Zahlen, Limitationen (kleine Fallzahl, Labels nicht unabhängig bestätigt, Laborbedingungen)
- Demo zweimal durchspielen, `?demo=1` und Screenshots als Backup
- Pitch: Problem, Live-Demo, wie getestet, nächste Schritte

Nur Aussagen wie „bei 3 Blindfällen …“, nie „erkennt STEMI zuverlässig“.
