# Datenquellen EKG-AI

Die fertigen Test-EKGs kommen in den Ordner `testfaelle/` neben dieser Datei (8 Fälle, 2 Kontrollen, `referenz.csv`). Sie werden vor dem Hackathon ergänzt.

| Quelle | Inhalt | Lizenz laut Anbieter | Hinweis |
|---|---|---|---|
| [PTB-XL (PhysioNet)](https://physionet.org/content/ptb-xl/) | 21.837 12-Kanal-EKGs von 18.869 Personen mit Diagnose-Codes (SCP) | CC BY 4.0 | Signaldaten, keine Bilder. Für Fotos erst als Bild rendern. |
| [ECG-Image-Kit](https://github.com/alphanumericslab/ecg-image-kit) | Werkzeug, das aus EKG-Signalen realistische Papier-EKG-Bilder erzeugt | siehe Projektseite | Für Teams mit Python-Erfahrung. |
| [ECG-Image-Database (arXiv 2409.16612)](https://arxiv.org/abs/2409.16612) | 35.595 EKG-Bilder mit echten Scan- und Fotoartefakten, erzeugt aus PTB-XL und Emory-Daten | siehe Veröffentlichung | Datensatz der PhysioNet Challenge 2024. Gut für den Realitätstest. |
| [PTB-XL-Image-17K](https://doi.org/10.5281/zenodo.18197519) | 17.271 synthetische 12-Kanal-EKG-Bilder aus PTB-XL | siehe Zenodo-Seite | Sehr groß, nur einzelne Bilder entnehmen. |

## Empfehlung für den Hackathon
- 8 Fälle plus 2 Kontrollen reichen: 5 zum Verbessern, 3 Blind-Fälle.
- Kontrollen: ein Foto ohne EKG und ein unscharfes oder angeschnittenes EKG. Erwartet wird GRAU.
- Für den Realitätstest 2 bis 3 Bilder vom Bildschirm oder Ausdruck abfotografieren.
- Die Diagnosen in `referenz.csv` sind die Labels des Datensatzes und nicht von uns bestätigt. Das Medizin-Team bewertet am Bild.

## Bei Verwendung angeben
Wagner P, Strodthoff N, Bousseljot R-D, et al. PTB-XL, a large publicly available electrocardiography dataset. Scientific Data 7, 154 (2020). Dazu der Verweis auf PhysioNet und die Lizenz CC BY 4.0.
