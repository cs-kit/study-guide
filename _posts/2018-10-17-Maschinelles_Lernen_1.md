---
layout: post
title:  "Maschinelles Lernen 1 - Grundverfahren"
ref: maschinelles_lernen_1
date:   2018-10-17 07:00:00 +0100
categories: master
excerpt: Das Themenfeld Wissensakquisition und Maschinelles Lernen ist ein stark expandierendes Wissensgebiet und Gegenstand zahlreicher Forschungs- und Entwicklungsvorhaben. Der Wissenserwerb kann dabei auf unterschiedliche Weise erfolgen. So kann ein System Nutzen aus bereits gemachten Erfahrungen ziehen, es kann trainiert werden, oder es zieht Schlüsse aus umfangreichem Hintergrundwissen.
lang: de
tags: lecture
---
<div style="background-color: #EAEFF4; border: 1px solid #b5aeb1; border-radius: 3px;  padding: 10px; margin-right: 10px">
    <strong>Vorlesung:</strong> <a href="https://campus.studium.kit.edu/ev/_qIONru0So6lB_y2FMgGxg">Maschinelles Lernen 1 - Grundverfahren</a>, Vorlesung, 3 ECTS <br>
    <strong>Dozent:</strong>Prof. Dr.-Ing. Rüdiger Dillmann<br>
   <strong>ILIAS:</strong> <a href="https://ilias.studium.kit.edu/goto.php?target=crs_884298&client_id=produktiv">https://ilias.studium.kit.edu/goto.php?target=crs_884298&client_id=produktiv</a><br>   
   <strong>Videos:</strong> <a href="">TODO</a>, technische Probleme: ersten beiden VL fehlen<br>   
   <strong>DIVA Videos:</strong> <a href="https://mediaservice.bibliothek.kit.edu/#/details/DIVA-2017-548">WS 17/18</a> nur im KIT-Netz<br>  
   <strong>Klausur:</strong> schriftlich, 11./12./13.2.2018, wird noch bekanntgegeben <br>
   <strong>Einordnung:</strong> Vertiefungsfach "Anthropomatik und Kognitive Systeme", Profil "Datenintensives Rechnen", Robotik, KI... <br>
</div>

## Organisatorisches

### Vorlesungen
- **17.10.2018**: Organisatorisches und Foliensatz 1-1 bis 1-59
- **24.10.2018**: Wiederholung von Kapitel 1, Foliensatz 2
- **30.10.2018**: Wiederholung von Kapitel 2, Foliensatz 3
- **06.11.2018**: Foliensatz 4 [Neuronale Netze](#vl4)
- **13.11.2018**: Foliensatz 5

### Material
VL wird aufgezeichnet. Das Material wird auf ILIAS zur Verfügung gestellt. Die Suche der Verantstaltung
funktioniert nicht. Daher muss man manuell suchen. Dafür geht man bei "Organisationseinheiten" zu den
Wirtschaftswissenschaften und sucht dort die Vorlesung. Das Passwort wurde in der Vorlesung mitgeteilt.

### Übung
Übung findet montags alle zwei Wochen von 14:00 bis 15:30 statt (Sport R007). Beginn des Übungsbetriebes
 am 29.10. Ist für Wirtschaftswissenschafler Pflicht,
für Informatiker freiwillig. Vor erster Übung sollte Python am eigenen Laptop installiert werden.
Dazu wird auf [diese Anleitung](https://git.scc.kit.edu/snippets/236) verwiesen.

Aufbau der Übungseinheiten:
- **29.10.2018**: Übung 01 Einführung: Python, Jupyter Notebook, Numpy, Pandas, Matplotlib, etc.
- **19.11.2018**: Übung 02 Neuronale Netze
- **26.11.2018**: Übung 03 Klassifikation und Regression
- **10.12.2018**: Übung 04 Reinforcement Learning
- **14.01.2019**: Übung 05 HMM und Bayes
- **28.01.2019**: Übung 06 Unüberwachte Lernverfahren

### Klausur
Die Klausur findet schriftlich statt. Termin noch unklar, 11./12./13.2.2018, wird noch bekanntgegeben.

## Vorlesungsinhalt
### Einführung und Überblick
**Intelligenz**: viele widersprüchliche Definitionen, bereits 1021 von Psychologen, Kontext (im technischen
Sinne) oft eingeschränkt; mögliche Komponenten: Denken und Problemlösen, Lernen und Erinnern, Sprache,
Wissen abspeichern und übertragen, Kreativität und Bewusstsein, Überleben in komplexen Welten, rezeptive und
motorische Fähigkeiten (Robotik)

**Lernen**: Lernen von Entscheidungen, Aktionsfolgen, Beschreibungen, Modellen; Entwicklung motorischer und
kognitiver Fähigkeiten durch Anweisung oder Training; Neuorganisation/Umorganisation/Transformation von Wissen

**Lernendes System**: in der Lage unbekannte Eigenschaften eines Prozesses/seiner Umgebung durch schritweises,
wiederholtes Handeln und Beobachten zu erfassen; mit gewonnener Erfahrung Vorhersagen treffen, klassifizieren,
Entscheidungen treffen mit Ziel optimales Systemverhalten zu erzielen oder Leistung zu steigern.  
Komponenten eines Lernenden Systems (vgl. Abb 1-30):
- *Informationsquelle*
- *Lernendes Element*: Was und wie wird gelernt? Wie wird das genutzt? Inferenz?
- *Wissensbasis*: Wie kann Wissen/Hypothesen repräsentiert werden?
- *Ausführendes Element*: Was und wie wird gelernt? Wie wird das genutzt? Inferenz?

**Maschinelles Lernen**: System lernt aus Erfahrung E im Hinblick auf Klasse von Aufgaben T und Performanzmaß P, wenn
Leistungen bei Aufgabe aus T mit P durch Erfarhgung E steigt; generiert ein/mehrere Lösungshypothesen H;

**Inferenz**: bezeichnet den Vorgang eines Algorithmus aus Fakten und Vermutung (korrekte) Schlüsse zu ziehen.

*Ziel:* Hypothesen finden, Interferenz ermöglichen; Hypothesen beschreiben ein Modell, z.B. Diskriminatives Modell (Klassifikation),
Generatives Modell (Beschreibung/Erzeugung von Daten), Probabilistisches Modell (Schließen auf Zufallsvariablen), Markovsches Entscheidungsmodell
(Bestimmen von Aktionsketten)

**Deduktiver Schluss**: Aus A folgt B, es gibt Folge von Regeln um B abzuleiten ⇔  $ A → B $   
Beispiel: "Alle Menschen sind sterblich.", "Sokrates ist ein Mensch." → "Sokrates ist sterblich."

**Abduktion**: H folgt aus Hintergrundwissen B und Beobachtungen D abduktiv ⇔ $ B ∪ H ↦ D $
Beispiel: "Alle Menschen sind sterblich.", "Sokrates ist sterblich." → "Sokrates ist ein Mensch."

**Induktiver Schluss**: Hypothese H folgt induktiv aus Menge D von Grundbeispielen und Hintergrundwissen D ⇔
$ B ∪ H ↦ D, B ↛ D,  B ∪ D ↛ ¬H $, **Vorsicht**: Aus Hypothesen sind einzelne Beispiele ableitbar, aber nicht umgekehrt!
Mit ausreichenden Beispielen: "Sokrates ist ein Mensch.", "Sokrates ist sterblich." → "Alle Menschen sind sterblich."

**Wissensrepräsentationen**: verschiedene Möglichkeiten Wissen zu repräsentieren:
- *Assoziierte Paare*
- *Parameter in algebraischen Ausdrücken*
- *Entscheidungsbäume*
- *Formale Grammatiken*
- *Produktionsregeln*
- *Formale logikbasierte Ausdrücke*
- *Graphen und Netzwerke*
- *Probabilistische Graphische Modelle*
- *Frames, Schemata, Semantische Netze*
- *Prozedurale Kodierung*
- *Taxonomien*
- *Markov-Ketten*

**Historie**:
- *Beginn und Enthusiasmus (1955-1968):* Lernen ohne Wissenstrukturen, Auswendiglernen und Lernen als Suche,...
- *Depression (1969-1976):* Symbolisches begrifforientiertes Lernen,...
- *Renaissance (1976-1986):* erste erfolgreiche Anwendung, Neuronale Netze, Statistisches Lernen,...
- *Maturität - Reife (1986-...):* Reinforcement Learning, Deep Learning, Kombination induktiver und deduktiver Verfahren,...
- *Heute:* Betrachtung komplexerer realer Anwendungen, Verbesserung/Erweiterung der Grundverfahren

**Lernen als Prozess**: (vgl. Abb 1-48)
1. Identifikation der Lernaufgabe
2. Initiale Wissenakquisation
3. Vorverarbeitung/Segmentierung/Generierung von Trainingsdaten
4. Konfigurierung des Lernverfahrens
5. Initialer (offline) Lernprozess
6. Bewertung des erlernten Wissens
7. Wissensanapassung/-verfeinerung/-erweiterung

**Einordnungskriterien von Lernverfahren**:
- *Typ der Inferenz:* induktiv ⇔ deduktiv
- *Ebenen des Lernens:* symbolisch ⇔ subsymbolisch (z.B. Matrixmultiplikation)
- *Lernvorgang:* überwacht ⇔ unüberwacht
- *Beispielumgebung:* inkrementell (mit neuen Daten Stück für Stück weiterlernen) ⇔ nicht inkrementell
- *Umfang der Beispiele:* umfangreich ⇔ gering
- *Hintergrundwissen:* empirisch ⇔ axiomatisch

### Induktives Lernen
**Induktion**: Prozess des *plausiblen* Schließens vom Speziellen zum Allgemeinen; wahrheitserweiternd, Generierung neuter Hypothesen;

**Deduktion**: Prozess des *korrekten* Schließens vom Allgmeinen zum Speziellen; wahrheitserhaltend, Ableiten neuer Reglen/Fakten

**Induktive Lernverfahren**: beispiel Konzeptlernen  (min Anpassungen)
Gegeben:
- *Instanzraum/Merkmalsraum* $X$:
- *Trainingsmenge* $D$:
- *Zielkonzept/Sollausgabe* $c(...)$: Untermenge von Objekten/Ereignissen, Boolsche Funktion
- *Hypothesenraum* $H$:

Gesucht:
- *Hypothese* $h$: jede Hypothese, die Zielfunktion über genügend große Menge von Trainingsbeispielen gut approximiert, wirds Zielfunktion auch
bei unbekannten Beispielen gut approximieren.

*Konzeptlernen:* induktives Lernverfahren, schließen auf Boolean-wertige Funktion asu Trainingsbeipielen ihres Inputs und Outputs

**Definitionen im Hypothesenraum**:
- *Konsistenz:* keine negativen Beispiele werden positiv klassifiziert
- *Vollständigkeit:* alle positiven Beispiele werden positiv klassifiziert  
→ Vozugskriterium: konstistent + vollständig


<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/C1cI7wUUg6M" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

**Versionsrau (Version Space)**: Versionsraum ist Untermenge von Hypothesen in H, die mit Trainingsbeispielen *konsistent* und *vollständig* sind  
parallele Anwendung von *Suche vom Allgemeinen zum Speziellen* (Ausgangspunkt allgemeinste Hypothese, neg. Beispiele: Spezialisierung,
 pos. Beispiele: nicht betrachtet) und *Suche vom Speziellen zum Allgemeinen*  (Ausgangspunkt spziellste Hypothese, pos. Beispiele: Verallgemeinerung,
 neg. Beispiele: nicht betrachtet)  
 Spezifischste Hypothese = Allgemeinste Hypothese, wenn alle Beispiele konsistent, korrekte Hypothese im Hypothesenraum enhalten, *Probleme:* bei
 fehlerhaften Trainingsdaten (Rauschen), Zielkonzept nicht von Hypothesenrepräsentation abgedeckt, disjunktive Begriffe, konsistente Beispiele nötig

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/TlkMkC64XpE" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

**Induktiver Bias**: Induktives Lernen erfordert Vorannahmen = **Inductive Bias**, je strenger Vorannahmen, desto mehr unbekannte Beispiele können
klassifiziert werden, z.B. Version Space: Zielkonzept in H repräsentierbar, Specific-to-General: alle Instanzen negativ, soland nicht Gegenteil
bekannt.
Beispiel: Ockham's razor

**Bias (Vorzugskriterium)**: Vorschrift nach der Hypothesen gebildet werden
- *Hypothesenraumbias*: h in beschränktem Hypothesenraum
- *Präferenzbias*: h mit höchste Präferenz in geordnetem Hypothesenraum  

→ Problem: es existiert keine Funktion h, die konsistent mir Trainingsbeispiele ist, z.B. bei verrauschten Trainingsdaten  
→ Lösung: Anpassen des Hypothesenraumbias (gute Klassifikation aber Overfitting), Anpassen des Präferenzbias (wähle h, dass möglichst viel
richtig klassifiziert, mögliche Missklassifikation)

### Lerntheorie
**Lernmaschine**: lernende Maschine mit *Hypothesenraum* ${h_\alpha: \alpha ∈ A}$ und  Lernverfahren (Methode $\alpha_{opt}$ mit Hilfe von
Lernbeispielen zu finden) → Entscheidungsmodell $M_{opt}$

**Probleme beim Lernen**:
- *Statistisches Problem:* "zu großer" Hypothesenraum, für Trainingsdaten mehrere gleich gute Hypothesen (bis vor fünf Jahren wäre noch die
  pauschale Antwort gewesen, dass man gemäß Occam's Razor die einfachere der beiden Hypthosen wählt)
- *Komplexitätsproblem:* nicht garantierte optimale Lösung im Hypothesenraum, Gefahr einer suboptimalen Lösung
- *Repräsentationsproblem:* Zielfunktion nicht genügend gut approximiert

**Fehler**: reale Fehler nicht berechenbar ($ \int $) → empirischer Fehler schätzbar ($ \sum $);
mögliche Fehler: Lerndaten → Lernfehler, Verifikationsdaten → Verifikationsfehler, Testdaten → Generalisierungsfehler

**Fehlerminimierung**: definiere $h_a$, finde beste $\alpha_{opt}$ durch iterative Minimierung des empirischen Lernfehlers $E_D(h_{\alpha}), z.B. durch Gradientenabstieg (Gradient
muss berechenbar oder abschätzbar sein)

**Overfitting**: zu starke Spezialisierung der Maschine auf Lernbeispiele ("auswendig Lernen"); Lernfehler fällt, Testfehler steigt → Generalisierung fällt; Erklärung: Lerndatenmenge und
Testdatenmenge unterschiedlich; Lösung: Lernprozess durch Verifikationsfehler steuern, Lernprozess im "richtigen Moment" stoppen, richtige Wahl und Suche der optimale Hypothesen

**Modellgüte bestimmen**: je nach Aufgabenstellung unterschiedliche Methoden:
- *Klassifikation:* Anzahl richtiger/falscher Klassifizierungen  
- *Regression:* Entfernung zu Schätzungsziel  
- *Unüberwachtes Lernen:* wie gut werden Daten abgebildet → schwierig  
- *Reinforcement learning:* wie gut passt Aktionsfolge  → keine allgemeinen Metriken

**Klassifikation**: Unterscheidung von vier Ergebnisklassen:
- *True Positive (TP):* korrekte Klassifikation positiver Instanzen
- *True Negative (TN):* korrekte Klassifikation negativer Instanzen
- *False Positive (FP):* falsche Klassifikation positiver Instanzen (typische Verwendung)
- *False Negative (FN):* falsche Klassifikation negativer Instanzen  

*Konfusionsmatrix:* Wunschergebnis hohe Werte auf Diagonale, wenige FP und FN; horizontal = Vorhersage, vertikal = tatsächliche Klasse

|               |     Ja        | Nein  |
| ------------- |-------------  | ----- |
| **Ja**        |  TP           | FN    |
| **Nein**      |  FP           | TN    |

*Metriken:*
- Klassifikationsfehler: möglichst klein $\frac{errors}{total} = \frac{FP+FN}{TP+FN+FP+TN}$
- Güte: = 1-Fehler $\frac{correct}{total} = \frac{TP+TN}{TP+FN+FP+TN}$
- False Positve Rate (FPR) / False Alarm Rate (FA): möglichst klein $FPR = \frac{FP}{FP+TN}$
- False Negative Rate (FNR) / Miss Rate (MR): möglichst klein $FNR = \frac{FN}{TP+FN} = 1 - TPR$
- Genauigkeit (Precision): möglichst hoch $P = \frac{TP}{TP+FP}$
- True Positve Rate (TPR) / Recall / Positive Rückmeldung: möglichst hoch $TPR = R =\frac{TP}{TP+FN} = 1 - FNR $
- F1-Maß: Harmonisches Mittel zwischen Precision und Recall. Möglichst hoch $F_1  =\frac{2}{\frac{1}{R}+\frac{1}{P}}$

Durch Kombination von Metriken Auswahl der besten Hypothese möglich,
z.B.

 - TPR/FPR-Graph auch **ROC** [Receiver operating characteristic(https://en.wikipedia.org/wiki/Receiver_operating_characteristic) genannt
 - Precision-Recall-Graph

**Cross-Validierung:** Modell statistisch auswerten, mit Teil der Daten evaluieren → Modell gut oder schlecht?;
Vorgehen: Teile Daten wiederholt in Lern- und Validierungsdaten auf, bestimme gute Hypothese, berechne Metriken
 → wiederhole n mal "n-fold-cross-validation"

 Resultat: Die Varianz der Daten variiert über die Aufteilungen, dadurch würde
 eine instabile Lernmaschine identifiziert werden. Solche Maschinen sind nicht
 wünschenswert.

**Bootstrap:** Wie mit einfachen Verfahren mehr erreichen?
Zufälliges Ziehen der Beispiele mit Zurücklegen, Modellbestimmung & Parameter, Wiederholen...
bestimme Mittelwert, Varianz des Modells;

> "Das Bootstrapping-Verfahren, oder Bootstrap-Verfahren (selten Münchhausenmethode), ist in der Statistik eine Methode des Resampling. Dabei werden wiederholt Statistiken auf der Grundlage lediglich einer Stichprobe berechnet. Verwendung finden Bootstrap-Methoden, wenn die theoretische Verteilung der interessierenden Statistik nicht bekannt ist."

https://de.wikipedia.org/wiki/Bootstrapping-Verfahren

**Bagging** (Bootstrap aggregation)
Variante Bagging: verwende mehrere Lernmaschinen → Kombination der Lernmaschinen
und dann Mehrheitsentscheid der einzelnen Maschinen

**Boosting für Klassifikation**: Kombination "schwacher" Modelle, um gutes Modell zu erhalten

**Adaptive Boosting / AdaBoost**: Iteratives Erstellen eines komplexen Klassifikators in k Stufen,
Ziehen von Lernbeispielen enstprechend definierter Gewichte; mit neuer Lernmenge
wird mit Hilfe eines Lernverfahrens nächster Klassifikatior bestimmt.

Adaptive Boosting (1996): Man versucht iterativ besser zu werden. Also wählt man
als Trainingsdaten für den nächsten anzutrainierenden Klassifikator die
Daten, die von den bisherigen Modellen falsch klassifiziert wurden.
Dann kann man ein **Ensemble** aus den Modellen erstellen, wobei es auch
eine "Sicherheitsmetrik" gibt.

Gutes Beispiel: Kaskadierung von **Viola & Jones (2001)**:
Sie haben Gesichterkennung mit Haar-like Filtern gemacht.

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/uEJ71VlUmMQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Das Cascading ist interessant, weil folgendes passiert:
Erster Klassifikator hat precision 0.99 und recall 0.3. Wenn man zehn
solcher Klassifikatoren hintereinanderreiht, dann bekommt man precision = 0.99^10 ~= 0.9
 und recall = 0.3^10 ~= 0.00.

**General Adversarial Networks (GAN)** (auch Turing-Lernen) profitiert vom
Boosting.

**Probably Approximate Correct**:

> "Kann man mit einfacher Lernmaschine ein gegebenes Konzept lernen?" Den Fehler
approximiert man auf ein epsilon. PAC Stichprobenkomplexität: Wie viele Lerndaten
brauche ich, um das Problem zu lösen?

Aus Menge X von Instanzen mit Länge n, Konzept C, Hypothesenraum H und Lerndatenmenge D kann keine korrekte Hypothese gefunden werden, aber eine ε-genaue:
$E_D(h) ≤ ε, 0 < ε < \frac{1}{2}  $ (Approximate Correct); Wert kann mit Wahrscheinlichkeit δ $1 - δ, 0 < δ < \frac{1}{2}$ gefunden werden; Anzahl benötigter Lerndaten:
$ m ≥ \frac{1}{ε}(lm\frac{1}{δ} + ln|H|)$   
→ je größer gewünschte Sicherheit, je kleiner zulässige Fehler, je größer Hypothesenraum → umso größer Anzahl benötigter Daten

Eigentlich ist das eine schöne Sache, aber es geht leider nur bei einfachen
Lernmaschinen.

**Vapnik-Chervonenkis (VC) Dimension**: ist maximale Anzahl von Datenpunkten die von der Hypothese beliebig separiert werden können; eine Hypothese h separiert die Daten D wenn zwei
Untermengen definiert werden können: ${x|h(x) = 0 } $ und ${x|h(x) = 1 } $; Beispiel: Hypothesenraum durch Geraden separiert, maximal 3 Werte durch Geraden spariert (nur wenn Aufteilung egal);
Allgemein: Hyperebenen in $R^n ⇒ n+1 $ separierte Werte

"bessere PAC-Strichprobenkomplexität"

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/puDzy2XmR5c" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**"Korrektes Lernen":** Vapnik

 - Kapazität so gering wie möglich
 - Optimierung so gut wie möglich
 - Trainingsdaten so repräsentativ und viele wie möglich

**Abschätzung des Testfehlers**: Lernerfolg abhängig von Kapazität der lernenden Maschine (so gering wie möglich), Optimierungsmethode (so gut wie möglich), Lernbeispiele (so viele wie möglich,
repräsentativ)

**Prof: Man bekommt die obere Schranke des Fehlers nicht nur durch
Reduktion des empirischen Fehlers des Modells hin, sondern auch durch:**

**Structural Risk Minimization**: finde Maschine $VC(h_a)$, Beispiele $N$ und Minimum des empirischen Fehlers $\alpha$: $ min_{H_n} (E_{emp} (h_a)+ \sqrt (... \frac{VC(h_{\alpha})}{N} ...)) $   
Strukturiere Hypothesenraum, Iteriere über Teile des Hypothesenraum, Suche Minimum für $E(h_{\alpha}), stoppe wenn Summe minimal; Berechnung VC Dimension schwer, rechenintensiv

> "SRM ist Meta-Algorithmus: Wie bekommt man strukturell aufsteigende Kapazität
über Hypothesenraum? Zum Beispiel AdaBoost implementiert SRM:
Kapazität steigt mit jedem neuen Klassifikator. Auch SVM macht das implizit."

**Das schien dem Professor sehr wichtig zu sein!**

GAN generieren neue Lernbeispiele, dadurch wird N in der VC-Ungleichung größer
und die obere Schranke geht nach unten.

Der Professor verweist auf Tom Mitchells Buch "Machine Learning" und
auf das erste Kapitel von Vapniks "Statistical Learning Theory"

Für die Klausur sollte man wissen:

 - Strukturelles Risiko
 - Vapnik-Chervonenkis grobe Entwicklung
 - PAC grundsätzliche Aussage

### <a name="vl4"></a> Neuronale Netze
**Künstliche Neuronale Netze (KNN)**: externe Eingabe → Gewichtsbelegung → Propagierungsfunktion → Aktivierungsfunktion → Ausgabe  
Einsatzfelder:
- *Klassifikation und Mustererkennung:* Diagnose, Spracherkennung, Schrifterkennung, Bilderkennung
- *Funktionsapprocimierung/Regression:* Kontinuierliche Abbildung, Steuerung, Vorhersage
- *Musterervervollständigung:* Bilderzeugung, generative Modelle, Kodierung, Komprimierung

**Perzeptron**: Anlehnung an natürliche Wahrnehmung,
Perceptron realisiert Trennhyperebene (in $R²$ eine Gerade), Gewichte definieren (stellen Normale dar),
Gegeben Positive und Negative“ Daten $(P,N)$ erfolgt eine Entscheidung durch gewichtete Summe → Skalarprodukt mit dem Nomalenvektor, *Lernen = Anpassen der Gewichte →
Gesucht wird die beste Trennhyperebene*

<a title="By Mayranna [CC BY-SA 3.0 (https://creativecommons.org/licenses/by-sa/3.0)], from Wikimedia Commons"
href="https://commons.wikimedia.org/wiki/File:Perceptron_moj.png"><img width="512" alt="Perceptron moj"
src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/8c/Perceptron_moj.png/512px-Perceptron_moj.png"></a>

*Lernalgorithmus:*  
{% highlight python %}
Gegeben Lerndatenmenge P ∪ N    
Erzeuge der Gewichtsvektor w zufällig  
While Zähler < Schwellenwert:  
    Wähle ein Trainingsbeispiel x in P ∈ N zufällig  
    If x ∈ P:  
        If w * x > 0 (korrekt klassifiziert):  
            dann tue nichts  
        Else w * x ≤ 0:  
            Setze w ← w + x  
    Else x ∈ N:  
        If w * x < 0 (korrekt klassifiziert):  
            dann tue nichts  
        Else x ∈ N und w * x ≥ 0:  
            Setze w ← w – x  
    If alle x richtig klassifiziert:  
        Break,  
    Update Zähler  
{% endhighlight %}

*Grenzen des Perzeptron Lernalgorithmus:* $\|w\| >> \|x\|$: sehr langsame Anpassung, Normierung nötig, Worst Case antiparallele Vektoren → Gradientenabstieg → differenzierbare Aktivierungsfunktion

Ein Perzeptron hat niedrige Kapazität → Zusammenschalten von Neuronen ("Perzeptronen") kann man Kapazität erhöhen

**Kernel Methode**: lineare Trennung durch Kernel Methode realisierbar, Lineare Trennung im transformierten Raum führt zu komplexer Trennung im Ursprungsraum

**Multi Layer Neural Network**: mehrere versteckte (innere) Schichten, Lernverfahren mit Backpropagation-Algorithmus, nichtlineare Aktivierungsfunktionen in Neuronen

**Nichtlineare Aktivierungsfunktionen**:
- *Sigmoid:* $f(x) = \frac{1}{1+e^{-x}}, \frac{\partial f}{\partial x} = f(x)(1-f(x))$
- *Tangens Hyperbolicus:* $f(x) = tanh(x), \frac{\partial f}{\partial x} = (1+f(x))(1-f(x))$
- *ReLU:* $f(x) = max(0,x), \frac{\partial f}{\partial x} = \begin{cases} 1 & x > 0 \\\\ 0 & \text{sonst} \end{cases}$
- *LeakyReLU:* $f(x) = \begin{cases} x & x > 0 \\\\ \alpha x & x \leq 0 \end{cases}, \frac{\partial f}{\partial x} = \begin{cases} 1 & x > 0 \\\\ \alpha & \text{sonst} \end{cases}$

**Backpropagation Algorithmus**: Aus Menge T von Trainingsbeispielen als Eingangs/Ausgabevektor, Lernrate $\mu$, Netztopologie finde Gewichtsbelegung W die T korrekt wiedergibt, Vorgehen
mittels Gradientenabstieg

**Anpassen der Gewichte**:
- Lernen aus Einzeldaten (Pattern learning): Anpassung nach jedem Lernbeispiel, schnelles Lernen (kein "echter" Gradientenabstieg, aber gute Approximation)
- Lernen aus Teilmengen (mini batch learning): kleine Lernmenge mit Zurücklegen, gutes Lernen (kein "echter" Gradientenabstieg, aber gute Approximation)
- Epochenlernen(epoch learning): Mittelung der Gewichtsänderung über alle Beispiele, Anpassung nachdem Beispiele propagiert wurden, echter Gradientenabstieg, nicht Ausreißeranfällig

**Optimierungen des Gradientenabstiegs**:
- *Resilient Propagation (RPROP):* Implementiert normierte Schrittweite und Lernratenanpassung, Beschleunigung auf flachem Plateau, langsames Anpassen im Minimum → schnelle Konvergenz (In den 90ern am KIT entstanden)
- *Adaptive Moment Estimation (Adam):* Angepasste Lernraten für jeden Parameter,
pro Parameter werden gleitende Schätzer für Mittelwert und Varianz mitgeführt, Implizites Momentum und
Anpassung an die Varianz der Gradienten.
**Vorteil ggü. RPROP:** Abstiegskurve wird geglättet, was bei realen Daten wichtig ist
- *Xavier – Initialisierung:* Verringerung des Vanishing- und Exploding-Gradients durch optimierte Initialisierung

**Topologieauswahl**: Anzahl Neuronen pro Schicht zur Anzahl von Lerndaten wichtig,
Schichten stark abhängig von Zielfunktion, ABER: zu viele Neuronen, zu wenig Lerndaten → Overfitting;
Gleichzeitiges Trainieren des NN und finden der optimalen Topologie:
 - großes Netzwerk verkleinern und am auswendig lernen hindern
   → Weight Decay, Weight Elimination = Bestrafen von großen W durch Verwendung erweiterter Fehlerfunktion
    "optimal brain damage"
 - kleines Netzwerk vergrößern und erweitern bis es Daten lernt
    - Meiosis Netzwerke: Aufspaltung von Neuronen
    - Cascade Correlation: dort neues Neuron einführen, wo der Fehler am größten ist

**Cascade Correlation**: Initialisiere 2 schichtiges Netz, Festlegen der Abbruchkriterien, Trainieren, solange E(w) kleiner als Fehlerschranke: Neuron einfügen,
Neuron trainieren, Netz trainieren   
*Vorteile:* nur eine Ebene zum selben Zeitpunkt trainiert, schnell, inkrementelles Training, iterative Anpassung des Netzes
*Nachteile:* spezielle Architektur → schwer Güte zu bestimmen, nicht anwendbar bei komplexen Architekturen

**Dropout**: Umsetzung von Bagging (bootstrap aggregation): k Modelle trainiern auf Daten (mit Zurücklegen), Mittelung der Ergebnisse der Modelle, Ziel: Erwartungswert des Fehlers reduzieren;
bei sehr großen Netzen → viele Netze lernen → overhead; Daher: approximative, implizite Umsetzung → Maskierung/Inaktivierung von Neuronen beim Lernen → auf allen Subnetzen gleichzeitg lernen,
Lernen mit jeweils aktiven Neuronen
**Wichtig:** Nach dem Trainieren muss man die Gewichte skalieren. Zum Beispiel
bei einem Dropout von 50% müssen die Gewichte halbiert werden, da sie sonst
wenn alle Neuronen aktiv sin ein doppelt so großes Ergebnis liefern im Vergleich zu Trainingphase.
**Bemerkung:** Das funktioniert, weil jedes Model im Ensemble seine eigene
Fehleroberfläche hat und das Mittel könnte besser sein als nur eine einzelne.

**Exploding/Vanishing-Gradient Problem**: je weiter Schicht von Ausgabeschicht entfernt,
desto kleiner werden Gradienten, falls Gewichtsmatrizen klein sind, ergeben sich viele kleine Werte,
die miteinander multipliziert werden, Update im Gradientenabstiegsverfahren lässt Gewichte der unteren Schichten praktisch unverändert und Training konvergiert nicht zu guter Lösung; falls
Gewichtsmatrizen groß sind, ergeben sich viele große Werte, die miteinander
multipliziert werden, explodierende Gradienten können Lernen instabil machen, NN kann nciht aus Trainingsdaten
lernen.

 - **Gradient Clipping**: Gradienten während Backpropagation einschränken, dass sie Schwellwert nicht überschreiten
 - **Gradient Norm**:
 - **Residual Learning**: Optimierung durch zusätzliche Verbindungen über Schichten hinweg, stärkere Rückpropagierung des Fehlers in untere Schichten

**Early Stopping**: Bei Gefahr des Overfittings Training abbrechen; in Intervallen von n Trainingszyklenn wird geprüft ob der Testfehler p mal aufeinanderfolgend größer wird

**Label smoothing**: Miteinberechnen, dass die Labels der Daten nur zu $1 - \epsilon$
richtig sind.

**Auswahl repräsentativer Trainingsbeispiele**:
- *Lerndaten* → Anpassung der Gewichte
- *Testdaten* → Testen des Fehlers und Overfitting
- *Verifikationsdaten* → Feststellen der Generalisierung  
→ Gute Verteilung nötig, aber unbekannt

**Einsatz von MLNN**:
1. *Entwurf:* subsymbolische Repräsentation der Ein-/Ausgabe, Trainingsdatenauswahl, Verfahrensauswahl, Topologieauswahl, Parametereinstellung
2. *Auswahl des Lernverfahrens:* Optimierungsmethode, Initliasisierung, Lernansatz
3. *Lernfortschritt (Gewichtsanpassung):* Overfitting testen
4. *Training & Verifikation (Test)*

### Convolutional Neuronale Netze
**Erste künstliche Ansätze**: Architektur von Verarbeitungsschritten, pro Schritt zwei Komponenten, erste reagiert auf Bereich zuvor (Lernen),
zweite komprimiert den Bereich (Informationskomprimierung)

**Faltung**: = Convolution, hier diskrete Faltung, bekannt aus Bildverarbeitung: Kantenfilter, Bildglättung, Bildschärfung;
Beispiel in Vorlesung: $m×m$ Eingabebild + $n×n$ Filter → $m_{neu}×m_{neu}$ mit $m_{neu} = m - n + 1$

**Warum CNNs**: Bild mit m*m Pixel: pro Neuron m*m Gewichte → ungünstiges Verhältnis Parameter : Lernaufgabe → nicht sinnvoll lern/berechenbar;
Beispiel Gesichtserkennung: ähnliche Features werden mehrfach gelernt, da jedes Feature für jedes receptive fiesld unabhängig gelernt wird

**Unterschied NN / CNN**: Im NN sind die Gewichte von einem Layer zum anderen, im CNN nur eine Kante zwischen Layer

**Feature Maps**: Form, in der Daten von Layer zu Layer übertragen werden; jedes Layer enthält als Eingabe r Feature Maps (m×m),
im Input Layer ist Feature Map ≡ Eingabebild; Featgures Maps zwischen zwei Layern = *Tensor*

**Pooling Layer**: Zusammenfassung kleiner Bildbereiche, Größe nach Zweck und Größe des Eingabebildes gewählt, verschiedene
Strategien:
- Max Pooling: Maximum wird gewählt
- Mean Pooling: Mean wird gewählt
- Stochastic Pooling: stochastische Auswahl abhängig von Aktivierung  

→ lokale Translationsinvarianz, Invarianz gegen leichte Veränderung, Verzerrung, Datenreduktion

**Convolution Layer**: Anwendung von Faltungsoperationen auf Eingabe, Eingabe: Feature Maps von vorherigen Layer ($m×m$),
 Ausgabe: Feature Maps des Layers (entstanden durch Faltung der Eingabe $m×m$ mit k Filtern $n×n×q$)
→ Eingabe: $m×m$ → k Filter $n×n×q$ → Ausgabe $m_{neu}×m_{neu}×k$ mit $m_{neu} = \frac{(m-n)}{s}+1$ mit s = Stride/Schrittgröße
Stride muss zur Größe der Eingabe passen, bei Pooling Layern meist 1; ConvLayer mit Stride erreicht Reduktion durch ASulassen,
Max Pooling betrachtet alle Werte bei Reduktion, bei ConvLayer größer 1×1 → Randbetrachtung notwendig: Informationsverlust bei Faltung,
Beheben:
- *don't care:* Berechnung des inneren Bereichs, Reduktion der Ergebnisgröße
- *Padding:* stabilisiert Größenverlauf der Layer, auffüllen der verlorenen Zeilen/Spalten, Varianten: Zero Padding (
Auffüllen mit 0), Nearest Padding (Duplizieren der Randpixel), Reflect Padding (Matrix nach außen spiegeln); ohne Padding
gehen Informationen am Bildrand sukzessive verloren, in jedem ConvLayer ohne Padding, große Filter beschleunigen Problem,
Pooling mit großen p auch; mit Padding Gefahr, dass Strukturinformationene entstehen die im Eingabebild nicht waren

**Activation Layer**: nichtlineare Aktivierung, in CNNs: ReLU, normalerweise nach ConvLayer
Aktivierungsfunktionen:
- *ReLU*: $f(x) = max(0,x), \frac{\partial f}{\partial x} = \begin{cases} 1 & x > 0 \\\\ 0 & \text{sonst} \end{cases}$
- *Leaky ReLU (LReLU)*: $f(x) = \begin{cases} x & x > 0 \\\\ 0.01 x & x \leq 0 \end{cases}, \frac{\partial f}{\partial x} = \begin{cases} 1 & x > 0 \\\\ \alpha & \text{sonst} \end{cases}$
- *PReLU (Generalisierung von LReLU)*: $f(x) = \begin{cases} x & x > 0 \\\\ \alpha x & x \leq 0 \end{cases}, \frac{\partial f}{\partial x} = \begin{cases} 1 & x > 0 \\\\ \alpha & \text{sonst} \end{cases}$
- *ELU (Exponential Linear Unit)*: $f(x) = \begin{cases} x & x > 0 \\\\ \alpha(e^x-1) x & x \leq 0 \end{cases}, \frac{\partial f}{\partial x} = \begin{cases} 1 & x > 0 \\\\ \alpha & \text{sonst} \end{cases}$

**Features**: CNN lernt Features für bestimmte Domäne, Feature Detektoren in Filtern der Convolutional Layer, Gewichte werden durch Gradienten
abstieg gelernt, Features eines Layers basieren auf Ausgaben der Features des vorherigen Layers,

**Gewichte**: Gewichte in CNNs werden nur in Filtern gelernt,
Methoden zur Initialisierung:
- *Random Initialization:* zufällig
- *Fixed Feature Extractor:* Übernahme der Gewichte aus trainiertem Netz, fixieren in Feature Extraction Schicht
- *Fine-Tuning:* Übernahme der Gewichte aus trainiertem Netz, geringe Lernrate für ausgewählte Schihten
- *Pretrained Initialization:* Übernahme der Gewichte aus trainiertem Netz nut zur Initialisierung, normale Lernrate für ausgewählte Schichten

> CNNs werden besser, da Rechenkapazität ständig wächst, immer größere Datensätze verfügbar, bessere CNN Architekturen

**Fully Connected Layer**: v.a. bei Klassifikation, Anzahl der Neuronen im letzten Layer korrespondiert zu der Anzahl an
Klassen, die Netz unterscheiden soll

**Fully Convolutional Networks (FCN)**: größere Eingabebilder möglich als bei Fully Connected CNNs, Fully Connected Schichten
in Convolutional Schichten konvertiert

**Ausgaben der FCN**:
- Fully Connected CNN (Klassifikationsnetz): Wahrhscheinlichkeitswert pro Klasse
- Fully Convolutional Network: Wahrhscheinlichkeitskart pro Klasse (gibt p an und Bereich in dem Bild zur Klasse gehört)

### Support Vector Machine (SVM)
**Support Vektor Methode**: Hypertrennebene finden, sodass Mengen A und B geteilt werden (Klassifikation). Ziel ist es die beste
Trenngerade zu finden, sodass der Rand (Abstand Gerade zu den Elementen der Ebene) maximal wird (Generalisierung)

**Trennhyperebene**: Normalenvektor $\vec{w}$ beschreibt Gerade durch Ursprung, senkrecht zu $\vec{w}$ verlaufen Trennhyperebenen, welche die
Gerade $\vec{w}$ an einer Stelle schneiden, der Abstand der Schnittstelle zu Urpsung ist $b$: $\vec{w}\vec{x} + b = 0$  
*Rand*: ist Abstand zwischen den nächsten Datenpunkten jeder Klasse $\frac{\vec{w}(x_⁻x_2)}{\|\vec{w}\|}$  
*Normierung:* $\vec{w}\vec{x}+b = +1 $ bzw $\vec{w}\vec{x}+b = -1 $ → maximaler Rand (Abstand zwischen zwei Klassen): $\frac{2}{\|\vec{w}\|}$  
*Optimale Hyperebene:* Abstand $\frac{1}{\|\vec{w}\|}$ zum nächsten Punkt und Abstand $\frac{2}{\|\vec{w}\|}$ zwischen zwei Klassen  
*Optimierungsproblem:* = Minimierungsproblem von $\|\vec{w}\|²$ um $\frac{2}{\|\vec{w}\|}$ zu maximieren unter der Randbedingung, dass die
Daten auch korrekt klassifiziert werden; Vapnik: Lernmaschine mit kleinsten möglichen VC-Dimension (= gültiger Hypothesenraum), falls
Klassen linear trennbar  
*Primäres Optimierungsproblem:* Lagrange Methode, Finde den (eindeutigen) Sattelpunkt $L_p$ der Funktion mit den positiven Lagrange-Multiplikatoren
$\vec{\alpha}=(\alpha_1, ..., \alpha_n)$ mit $\alpha_1, ..., \alpha_n \geq 0$, Minimum von L bezüglich $\vec{w}b$, Maximum von L bezüglich
$\alpha_1, ..., \alpha_n$  
*Duales Optimierungsproblem:* Duale Lagrange Gleichung $W(\alpha)$, duales Optimierungsproblem unter der Randbedingung dass Summe der
$y_i\alpha_i = 0 $ und $\alpha_i \geq 0$ → Vorteile nurnoch von $\alpha_i$ abhängig und damit einfacher zu lösen

**Support Vektoren**: Vektoren, die am nächsten zur Trennhyperebene liegen (wichtige Vektoren für Lernmaschine); die meisten (Sattelpunkt)
Bedingungen sind erfüllt → $\alpha_i = 0$; $\vec{w}$ ist Linearkombination weniger Support Vektoren

**Soft Margin**: "Aufweichen der Ebene" um einen "weichen Rand", erlaube geringer Zahl von Missklassifikationen, höhere Generalisierung,
indem Randbedingung um den Wert der Schlupfvariable $\xi \geq 0$ erweitert wird → d.h. Datenpunkt kann auch leicht neben Gerade auf
"falscher Seite" liegen   
*Regulierungsparameter $C$ (Größe des Randes)*:
- *$C$ groß:* wenig Missklassifikationen
- *$C$ klein:* maximaler Rand  
Folge für Support Vektoren $\vec{x_i}$ mit $\alpha_i > 0$:
- $\alpha_i < C$: Support Vektor liegt am Rand, Abstand zur Trennhyperebene ist $\frac{1}{\|\vec{w}\|}$
- $\alpha_i = C$:
    - Fehlklassifikation wenn $\xi_i > 1$
    - richtig, wenig Abstand (margin error): $0 < \xi_i \leq 1$
    - Rand Vektor (margin vetctor): $\xi_i = 0$

**Nichtlineare Kernel-Methoden**: Transformiere Daten in anderen Raum und löse dort linear (Klassifikation: lineare Trennung); meist
Transformation in höher dimensionalen Raum, Problem: Transformation oft rechenintensiv:  
*Kernel-Trick:* wenn Daten als Skalarprodukt, Transformation nicht nötig, implizites Rechnen im höher dimensionalen Raum → Lösung
im Ursprungsraum; Kernel-Funktion: $K(\vec{x}, \vec{y}) = \phi(\vec{x})\phi(\vec{y})$  
*Kernel-Funktionen:* Skalarprodukt, Polinomial, Radiale Basis-Funktionen (RBF), Sigmoid

**Version Space für SVM**: Randbedingung für korrekte Klassifikation/gültige Trenngeraden; jeder Datenpunkt definiert Hyperebene
im Hypothesenraum, gültige $\vec{w}$ jeweils in reduziertem Hypothesenraum → Suche nach $\vec{w}$ mit maximalen Abstand zu allen
Hyperebenen der Datenpunkte → Mittelpunkt der Hyperkugel; bei Suche über Trennhyperebene wird implizit Structural Risk Minimization
durchgeführt → korrektes Lernen ist Mittelpunkt der verbleibenden Hyperkugel

**SVM Architektur**: Ähnlichkeit zu NNs? → lernen Gewichte, Kernel, hidden-Layer; ABER: sonst nichts: Optimierung, mathematischer
Hintergrund

**SVM Erweiterungen**:
- Einer-gegen-Alle: $k$ SVMs (pro Anzahl k an Klassen), Abstimmungsverfahren
- Einer-gegen-Einen: $\frac{k(k-1)}{2}$ SVMs, Abstimmungsverfahren
- Mehrfachzugehörigkeit: $k$ SVMs (pro Anzahl k an Klassen), Abstimmungsverfahren
- k-class SVM (Watkins): gemeinsames Optimierungsverfahren, kein Abstimmungsverfahren (→ schlecht, schlechte Performance)

**Probabilistische Sicht auf SVMs**: Interpretation des Abstandes der Trennhyperebene als Klassifikationswahrscheinlichkeit, Alternative:
Maximierung der Klassifikationswahrscheinlichkeit des Randes

**Dichte-Träger-Schätzung**: Funktion f, die für "kleine Region" (enthält die meisten Lernbeispiele), Wert > 0, sonst Wert $\leq$ 0
(Ähnlichj zum Clustering im unüberwachten Lernen), Abstand $\vec{w}$ zum Ursprung soll maximal sein, Trennung der Lernbeispiele vom
Ursprung im transformierten Merkmalsraum

**Kernel Perceptron**: einfacher Algorithmus, als Kernel Methode realisierbar, lineare Trennung im transformierten Raum für zu
komplexer Trennung im Ursprungsraum

**Pro SVM**:
- Optimale Hyperebene → gute Lernergebnisse
- optimale VC-Dimension → korrektes Lernen
- hochdimensionale Daten → schnelle Auswertung
- Entscheidung anhand Randregion getroffen

**Kontra SVM**:
- Vorverarbeitung extern nötig (kein "tiefes" Lernen)
- speicher- und rechenaufwändig
- Anzahl Support Vektoren abhängig von Problem und Parameter
