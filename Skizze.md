2026-05-02

#### Outline

Wie wäre es, einen groß angelegten Versuch mit KI zu wagen? Wie folgt: 

Wir möchten gerne **xxx** mit SNA-Methoden auswerten. Alle erforderlichen Software-Komponenten sollen automatisch durch eine KI erstellt werden.

Aus heutiger Sicht umfasst das System die folgenden Komponenten:
- ein **Corpus Maker** zur Auswahl der jeweils relevanten Texte bzw. Textabschnitte,
- einen **Text-to-Graph Generator** zur Erzeugung von Graph aus den ausgewählten Texten bzw. Textabschnitten,
- ein **Statistics Modul** zur Erzeugung von statistischen Kenngrößen und Diagrammen,
- ein **Evaluator** zur Erzeugung von zusammenfassenden Texten,
- ein übergeordnetes **Dashboard** zur Steuerung des Gesamtablaufs.

Diese minimalen Architektur-Anforderungen sollen der KI in einem Prompt mitgeteilt werden. Die Funktionen der Komponenten werden weiter unten noch etwas genauer spezifiziert. Über ihre innere Struktur werden allerdings keine weiteren Angaben gemacht. 
###### - Corpus Maker
Hier wird festgelegt, wie der Forscher aus den vorhandenen Texten einen Korpus erstellen kann: 
- Auswahl der Texte bzw. Textabschnitte  
- Bereinigen des Textes
- NLP-Funktionen
- Knoten und Kanten von Graphen
###### - Text-to-Graph Generator
Hier wird festgelegt, wie die Graphen aus den Knoten und Kanten erzeugt werden:
- Knoten und Kanten properties
- Styling der Knoten und Kanten
- Visualisierung
###### - Statistics Module
Hier wird festgelegt, welche statistischen Größen berechnet werden sollen.
###### - Evaluator
Hier können zusammenfassende Texte oder sogar Forschungsergebnisse abgerufen werden. 

#### Was ist xxx? 
Das ist die große Frage.

- Mobi Dick: https://www.gutenberg.org/cache/epub/2701/pg2701.txt
- Rezepte von Johann Lafer: https://lafer.de/pages/rezepte