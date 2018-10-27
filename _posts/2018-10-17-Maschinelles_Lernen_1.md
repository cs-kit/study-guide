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

## Übung
