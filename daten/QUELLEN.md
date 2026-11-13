# Datenquellen EKG-AI

## Im Repo
| Ordner | Inhalt | Herkunft und Lizenz |
|---|---|---|
| `beispielbilder/` | 4 fertige 12-Kanal-EKG-Bilder zum sofortigen Ausprobieren: 2 sauber gerendert, 2 mit handschriftlichen Notizen | Beispieldaten aus [ECG-Image-Kit](https://github.com/alphanumericslab/ecg-image-kit) (BSD-3-Clause), erzeugt aus PTB-XL-Aufzeichnungen (CC BY 4.0) |
| `beispielbilder/referenz.csv` | Je Bild: PTB-XL-Nummer, Diagnose-Codes und Befundtext des Datensatzes | aus der PTB-XL-Tabelle |
| `testfaelle/` | Platz für die eigentlichen Testfälle (8 Fälle, 2 Kontrollen, `referenz.csv`) | werden vor dem Hackathon ergänzt |

**Wichtig:** Alle vier Beispielbilder zeigen Normalbefunde. Sie eignen sich, um den Ablauf von Foto bis Befund zu testen, aber nicht, um die Erkennung kritischer Befunde zu prüfen. Dafür sind die Testfälle da.

## Weitere offene Quellen (nur verlinkt)
| Quelle | Inhalt | Lizenz laut Anbieter | Hinweis |
|---|---|---|---|
| [PTB-XL (PhysioNet)](https://physionet.org/content/ptb-xl/) | 21.837 12-Kanal-EKGs von 18.869 Personen mit Diagnose-Codes (SCP) | CC BY 4.0 | Signaldaten, keine Bilder. Für Fotos erst als Bild rendern. |
| [ECG-Image-Kit](https://github.com/alphanumericslab/ecg-image-kit) | Werkzeug, das aus EKG-Signalen realistische Papier-EKG-Bilder erzeugt | BSD-3-Clause | Für Teams mit Python-Erfahrung. |
| [ECG-Image-Database (arXiv 2409.16612)](https://arxiv.org/abs/2409.16612) | 35.595 EKG-Bilder mit echten Scan- und Fotoartefakten, erzeugt aus PTB-XL und Emory-Daten | siehe Veröffentlichung | Datensatz der PhysioNet Challenge 2024. Gut für den Realitätstest. |

## Empfehlung für den Hackathon
- 8 Fälle plus 2 Kontrollen reichen: 5 zum Verbessern, 3 Blind-Fälle.
- Kontrollen: ein Foto ohne EKG und ein unscharfes oder angeschnittenes EKG. Erwartet wird GRAU.
- Für den Realitätstest 2 bis 3 Bilder vom Bildschirm oder Ausdruck abfotografieren.
- Die Diagnosen in `referenz.csv` sind die Labels des Datensatzes und nicht von uns bestätigt. Das Medizin-Team bewertet am Bild.

## Bei Verwendung angeben
Wagner P, Strodthoff N, Bousseljot R-D, et al. PTB-XL, a large publicly available electrocardiography dataset. Scientific Data 7, 154 (2020). Dazu der Verweis auf PhysioNet und die Lizenz CC BY 4.0.
