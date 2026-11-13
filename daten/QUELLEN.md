# Datenquellen EKG-AI

## Im Repo
| Ordner | Inhalt | Herkunft und Lizenz |
|---|---|---|
| `mendeley_ekg_bilder/` | 928 Bilder von 12-Kanal-EKGs realer Patientinnen und Patienten in vier Unterordnern: `normal` (284), `myokardinfarkt` (239), `zustand_nach_myokardinfarkt` (172), `abnormaler_herzschlag` (233). Dazu `uebersicht.csv`. | Khan AH, Hussain M. ECG Images dataset of Cardiac Patients. Mendeley Data, Version 2 (2021). [doi:10.17632/gwbz3fsgp8.2](https://doi.org/10.17632/gwbz3fsgp8.2), CC BY 4.0 |
| `testfaelle/` | 8 fertige Testfälle `Fall01.jpg` bis `Fall08.jpg` aus dem Mendeley-Datensatz, mit neutralen Dateinamen. `referenz.csv` nennt je Fall die Klasse und ob er zum Verbessern (Tuning, Fall 1 bis 5) oder zum Blind-Test (Fall 6 bis 8) gehört. | Zufällige Auswahl aus `mendeley_ekg_bilder/` |
| `beispielbilder/` | 4 sauber gerenderte EKG-Bilder (Normalbefunde), 2 davon mit handschriftlichen Notizen | Beispieldaten aus [ECG-Image-Kit](https://github.com/alphanumericslab/ecg-image-kit) (BSD-3-Clause), erzeugt aus PTB-XL (CC BY 4.0) |

Die Dateien im Mendeley-Ordner wurden nur umbenannt, damit sie sich leichter verarbeiten lassen: aus `MI(84).jpg` wurde `MI_084.jpg`. Kürzel: `MI` Myokardinfarkt, `PMI` Zustand nach Myokardinfarkt, `HB` abnormaler Herzschlag, `Normal` Normalbefund.

## Was ihr über den Mendeley-Datensatz wissen müsst
- **Herkunft:** Aufgenommen am Ch. Pervaiz Elahi Institute of Cardiology in Multan, Pakistan. Laut den Autoren enthalten die Bilder keine persönlichen Angaben. Es sind dennoch EKGs echter Menschen, also sorgfältig damit umgehen.
- **Labels sind grob:** Es gibt nur vier Klassen. „Abnormaler Herzschlag“ ist keine Diagnose, sondern ein Sammelbegriff. Eine Einzelbefundung je EKG fehlt. Das Medizin-Team bewertet am Bild.
- **Vorsicht, Abkürzung:** Eine Untersuchung des Datensatzes beschreibt, dass Bilder der Infarkt-Klasse teils rote Markierungen tragen. Eine KI kann daran die Klasse erkennen, ohne das EKG zu lesen. Prüft eure Testfälle darauf und nennt es in den Limitationen.
- **Kontrollen fehlen:** Zwei Kontrollbilder macht ihr selbst, ein Foto ohne EKG und ein unscharfes oder angeschnittenes EKG. Erwartet wird GRAU.

## Weitere offene Quellen (nur verlinkt)
| Quelle | Inhalt | Lizenz laut Anbieter | Hinweis |
|---|---|---|---|
| [PTB-XL (PhysioNet)](https://physionet.org/content/ptb-xl/) | 21.837 12-Kanal-EKGs von 18.869 Personen mit Diagnose-Codes (SCP) und Befundtext | CC BY 4.0 | Signaldaten, keine Bilder. Deutlich feinere Labels als der Mendeley-Datensatz. |
| [ECG-Image-Kit](https://github.com/alphanumericslab/ecg-image-kit) | Werkzeug, das aus EKG-Signalen realistische Papier-EKG-Bilder erzeugt | BSD-3-Clause | Für Teams mit Python-Erfahrung. |
| [ECG-Image-Database (arXiv 2409.16612)](https://arxiv.org/abs/2409.16612) | 35.595 EKG-Bilder mit echten Scan- und Fotoartefakten | siehe Veröffentlichung | Datensatz der PhysioNet Challenge 2024. |

## Empfehlung für den Hackathon
- Mit den 8 Testfällen arbeiten. Die Blind-Fälle 6 bis 8 bleiben bis zum Schluss ungesehen.
- Wer mehr Fälle will, zieht weitere aus `mendeley_ekg_bilder/`, legt aber vorher fest, welche Blind-Fälle sind.
- Für den Realitätstest 2 bis 3 Bilder vom Bildschirm oder Ausdruck abfotografieren.

## Bei Verwendung angeben
Khan AH, Hussain M. ECG Images dataset of Cardiac Patients. Mendeley Data, V2, 2021. doi:10.17632/gwbz3fsgp8.2 (CC BY 4.0). Für die Beispielbilder zusätzlich: Wagner P et al. PTB-XL. Scientific Data 7, 154 (2020).
