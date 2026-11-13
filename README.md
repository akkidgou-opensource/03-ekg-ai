# 03 · EKG-AI

> Prototyp für den AKKI Hackathon 2026. Nur Test-EKGs, kein Medizinprodukt, kein Ersatz für ärztliche Beurteilung.

**Bereich:** Präklinik

**Idee:** EKG fotografieren, die KI liefert in Sekunden einen strukturierten Befund mit Ampel-Einschätzung.

## Warum
Kardiologische Expertise ist im Rettungsdienst selten sofort verfügbar, die EKG-Interpretation ist zeitkritisch.

## Was am Ende stehen soll
- Foto aufnehmen oder Datei hochladen
- Strukturierter Befund (Hauptbefund, Parameter, Handlungshinweis)
- Ampel-Ausgabe und jederzeit sichtbarer Hinweis „Prototyp“

**Erfolgskriterium:** Demo mit mindestens einem Testfall, der komplett von Foto bis Befund durchläuft.

## So startet ihr
1. Oben auf **Code → Download ZIP** klicken und entpacken.
2. Im entpackten Ordner ein Terminal öffnen und `claude` eingeben.
3. `SPICKZETTEL.md` öffnen und mit Block 1 beginnen.

## Was in diesem Repo liegt
| Datei | Wofür |
|---|---|
| `SPICKZETTEL.md` | Umsetzungsplan für 8 Stunden, Block für Block |
| `CLAUDE.md` | Regeln, an die sich Claude Code hält |
| `daten/QUELLEN.md` | Offene EKG-Datensätze mit Lizenz |
| `daten/testfaelle/` | Fertige Test-EKGs (werden vor dem Hackathon ergänzt) |

## Stolpersteine
- Die Bildqualität entscheidet über die Analysequalität
- Die medizinischen Vorgaben für die KI zu formulieren ist die eigentliche ärztliche Kernarbeit
- Zugangsdaten dürfen nicht öffentlich sichtbar im Code stehen

## Für Erfahrene
- Vergleich: gerendertes EKG-Bild gegen abfotografierten Ausdruck
- Rückfrage-Funktion zum Befund
- Zwei Modelle auf denselben Testfällen vergleichen
