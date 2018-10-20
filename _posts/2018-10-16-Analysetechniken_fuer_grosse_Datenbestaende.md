---
layout: post
title:  "Analysetechniken für große Datenbestände"
ref: analysetechniken_fuer_grosse_datenbestaende
date:   2018-10-16 07:00:00 +0100
categories: master
excerpt: Techniken zur Analyse großer Datenbestände stoßen bei Anwendern auf großes Interesse. Das Spektrum ist breit und umfasst klassische Branchen wie Banken und Versicherungen, neuere Akteure, insbesondere Internet-Firmen oder Betreiber neuartiger Informationsdienste und sozialer Medien, und Natur- und Ingenieurswissenschaften.
lang: de
tags: lecture
---
<div style="background-color: #EAEFF4; border: 1px solid #b5aeb1; border-radius: 3px;  padding: 10px; margin-right: 10px">
    <strong>Vorlesung:</strong> <a href="https://campus.studium.kit.edu/ev/vACNcrMpRvCbVANs7qJ92Q">Analysetechniken für große Datenbestände</a>, Vorlesung, 5 ECTS <br>
    <strong>Dozent:</strong> Klemens Böhm  <br>
   <strong>ILIAS:</strong> <a href="https://ilias.studium.kit.edu/goto_produktiv_crs_883316.html">https://ilias.studium.kit.edu/goto_produktiv_crs_883316.html</a> <br>   
   <strong>Vorlesungswebsite:</strong> <a href="http://dbis.ipd.kit.edu/2629.php">http://dbis.ipd.kit.edu/2629.php</a> <br>   
   <strong>Videos:</strong> <a href="https://opencast.informatik.kit.edu/engage/ui/index.html?e=1&p=1&epFrom=a4ded4cb-24cf-4372-aa1f-7ae4c7f16091">https://opencast.informatik.kit.edu/engage/ui/index.html?e=1&p=1&epFrom=a4ded4cb-24cf-4372-aa1f-7ae4c7f16091</a> <br>   
   <strong>Klausur:</strong> mündlich, daher nach Vereinbarung <br>
   <strong>Einordnung:</strong> Vertiefungsfach "Informationssysteme", Profil "Datenintensives Rechnen" <br>
</div>

## Organisatorisches

### Vorlesungen
- **16.10.2018**: Organisatorisches und Foliensatz 1-1 bis 2-36

### Material
Das Material der Vorlesung besteht aus:  
- **Folien**: Folien werden im ILIAS hochgeladen
- **Übungsblättern**  
Inhaltlich sind keine Veränderungen zum Vorjahr geplant, unter Umständen aber durchaus möglich

### Übungen
Es gibt insgesamt 5 Übungen, hauptsächlich schreiben von Programmen in R, Übungsblätter gibt es zwei Wochen vor
dem Übungstermin zum Download, Musterlösung wird in VL besprochen, Übungsaufgaben sind sehr wichtig

### Praktikum
Es gibt im Sommersemester das zugehörige Praktikum "Analysetechniken für große Datenbestände", die VL wird
vorausgesetzt, zwei Datensätze anhand eine eigene Analyse der Daten stattfinden soll, wenn man teilnehmen möchte
muss man das letzte Übungsblatt bearbeiten und abgeben -> sozusagen Anmeldung für Praktikum wenn das gut bearbeitet wurde

### Klausur
Die Klausur soll mündlich stattfinden (wenn Kursgröße das zulässt), Prüfungstermin kann man im Sekretariat des Lehrstuhls 
durch ausfüllen eines Formulars ausmachen, dabei gibt man den präferierten Monat der Prüfung an (z.B. April 2019).
Inhaltliche Fragen: SQL, Frage oft "Nenne ein Beispiel, aber nicht aus der Vorlesung"

## Vorlesungsinhalt
### Einleitung
**Worum geht es in der Vorlesung?**  
Erkennen von Zusammenhängen in Datenbeständen, die:
- **nichttrivial**: nicht offensichtlich
- **implizit**: belegbar durch Daten, Daten sollen Zusammenhang implizieren
- **potentiell nützlich**: keine/kaum Überlappung von Ergebniselementen/zuvor nicht bekannt  

Absicht hinter dem Herausfinden der Datenbestände entweder *wissenschaftlicher
(Publikationen)* oder *kommerzieller (Geld) Natur*. Herausforderung also *neue, nützliche* Zusammenhänge 
herauszufinden. Dabei sind die Datenbestände oft *sehr groß* und mit *komplexer innerer Struktur*.

**Wichtige Data-Mining Probleme**  
- **Association Rules**: Suche nach starken Regeln, Assoziationsanalyse z.B. im Warenkorb von Kunden 
(finden von *Frequent Item Sets*) mit dem Ziel eine Vorhersage zu treffen; Probleme: Performance, 
zu viele (ähnliche) Association Rules -> quantitative Angaben (wie oft wird ein Produkt 
mit einem anderen Produkt zusammen gekauft), zeitlichen Verlauf (nur wenn Item unmittelbar nacheinander gekauft 
wurde, nicht z.B. 3 Monate später) berücksichtigen, aber auch geeignete Sprache verwenden, um das ganze zu 
Beschleunigen.
- **Clustering, Outlier Detection**: Identifizieren von Gruppen in Datenmengen, die ähnliche Eigenschaften
besitzen, nah beieinanderliegen z.B. Kundengruppen; nicht zu einem Cluster gehörende Datenobjekte bezeichnet 
man als Outlier, d.h. Datenobjekte, die sich graphisch dargestellt, weit von den "gehäuften" Datenpunkten 
entfernt sind. Attribute unterscheiden sich z.B. Zahlen, Aufzählungstyp (Gruppen wie z.B. Haarfarbe) oder 
Mengenwertigkeit. Cluster können in einem Datenbestand unterschiedliche Form, Dichte und Größe besitzen.  
*Unsupervised:* vorab nicht bekannt welche Cluster es geben wird und wo ihre Grenzen verlaufen 
-> abhängig vom Datensatz  
*Supervised:* Klassenzugehörigkeit des Trainingsdatenbestandes vorher bekannt
- **Klassifikation**:  Einteilung von Datenobjekten in Klassen mit dem Ziel anhand von n Attributen das
n+1te Attribut vorherzusagen. Als Grundlage Trainingsmenge von welchen alle n+1ten Attribute bekannt sind.   
Viele unterschiedliche Ansätze, unter anderem:  
*Linearer Classifier:* Gegeben n Attribute x, Schwellenwert T (Score), n Gewichte w, Datensatz ist in Klasse, 
gdw. *x * w > T*, Gewichtung entscheidet über Klasse, große Gewicht = wichtige Attribute, 
kleine Gewichte = unwichtige Attribue, hat ein Attribut keine Auswirkung auf die Klassifizierung kann es mit 
negativen Gewichten versehen werden; sinnvoll für reelwertige, boolsche Attribute  
*1-Rules:* sehr einfaches Vorhersageverfahren, betrachtet jedes Attribut für sich, anfangs auch jeden 
Attributwert, häufigste Klasse ist diejenige, die vorhergesagt wird. Attribut mit kleinster Fehlerquote wird
als Grundlage für Vorhersage gewählt. (Vgl. 1 - 29), einfaches, schlichtes Modell mit hoher Fehlerrate, reicht
für manche Anwendungsfälle aus  
*Overfitting*: zu kleinteiliges Modell, das zu sehr auf den Trainingsdatenbestand zugeschnitten ist und daher
im Allgemeinen schlecht performt  

**Frage: Geben Sie Beispiele für Anwendungsgebiete, in denen Clustering anwendbar ist?**  
Typen von Studierenden (z.B. fleißige, faule, gute Studenten, schlechte Studenten)

**Frage: Skizzieren Sie ein Szenario aus den Naturwissenschaften, in dem Klassifikation 
sinnvoll einsetzbar ist.**  
Beispiel aus Vorlesung *Predictive Maintenance*, Vorhersage für Motoren bzw. alle komplexen technischen
Systeme, wann/welcher Schadensfall eintritt, dabei false positives oder false negatives möglich. Zwei 
Herangehensweisen:   
*datenorientiert*: wenn aktueller Systemstand kristischem Zustand ähnelt, dann Alarm; Voraussetzung, dass 
System sich in Zukunft so verhält, wie in Vergangenheit (d.h. nicht unter menschlichem Einfluss stehen), 
ausreichend Trainingsdaten vorhanden sind, zusammenbringen von Messdaten und vorherzusagenden Daten, 
Infrastruktur muss relevante Phänomene erfassen.  
*modellorientiert*: Experte formuliert "Alarmzustände" per Hand
Bei Betrachtung der Testdaten wird unterschieden:  
*statisch:* jeder Zeitpunkt wird isoliert betrachtet   
*dynamisch:* zeitliche Entwicklung wird berücksichtigt -> *Change Detection* entweder univariat (Zeitreihe
eindimensional) oder multivariat (von zwei Dimensionen abhängig, Vektor) 

Im Allgemeinen ist es nicht ausreichend Analyseverfahren zu verwenden, sondern zudem die Daten aufzubereiten
und in die Umgebung einzubetten. Außerdem ist es nciht offensichtlich, welche Daten wie zu analysieren sind.

*Ende der 1. Vorlesung vom 16.10.2018*  

**Prüfungsfrage: Was ist Overfitting?**
Zu feinteilige Betrachtung der Trainingsdaten -> performen, funktionieren nicht in Realität

**Prüfungsfrage: Was ist Change Detection? Wie unterschieden sich multivariate 
von univariaten Datenströmen?**
Bei dynamischer Betrachtung von Daten, d.h. Zeitpunkte werden in relation zueinander betrachtet, ist Change
Detection die Festellung, ob von Zeitpunkt t1 zu Zeitpunkt t2 eine Veränderung der Attributwerte 
stattgefunden hat. Dabei ist univariate Change Detection eindimensional und multivariate Change Detection
mehrdimensional (z.B. ein Vektor)

### Statistische Grundlagen
#### Beschaffenheit der Daten
**Kategorisierung der Daten**  
Kategorische Werte (Qualitative Konzepte)
- *Nominal:* Keine natürliche Anordnunge der Werte (z.B. Farben, Namen)
- *Ordinal:* Anordnung existiert (z.B. klein < mittel < groß)

Numerische Werte (Zahlen)
- *Diskret:* endliche Anzahl möglicher Werte (z.B. ganze Zahlen aus [0,100])
- *Kontinuierlich:* unendlich viele mögliche Werte (z.B. reelle Zahlen aus [0,100])

**Dimensionalität der Daten** 
- *eindimensional (univariat)* z.B. Alter 10, 51, 38 
- *multidimensional (multivariat)* z.B. x-y-Koordinaten (1;0), (4;8)
- *hochdimensional* z.B. Kundenrepräsentation in e-Commerce Firma
- *Daten ohne Dimension* z.B. Strings, Mengen

**Metrische Daten**: Daten ohne Dimension, deren Objektabstand sich aber berechnen lässt. Für diese 
Daten gilt in metrischen Räumen gegeben mit Domäne M, Metrik d für alle Objekte p,q,r aus M:
- Symmetrie: d(p,q) = d(q,p)
- Definitheit: d(p,q) = 0 <-> p = q
- Dreiecksungleichung: d(p,r) <= d(p,q) + d(q,r)

#### Einfache deskriptive Statistiken
**Aggregate**: Kombinieren alle Werte eines Attributs zu einem skalaren Wert, z.B. count, sum, min, max, avg, 
manche Aggregate sind parallelisierbar, andere nicht. Eine Aggregatsfunktion heißt *self-maintainable*, wenn
nach einer Änderung der Daten, der neue Wert der Aggregatsfunktion aus dem Alten berechnet werden kann. 
z.B. min; min war 3, jetzt ist kommt 2 -> ist 2 < 3 -> dann ist 2 neues minimum. ABER: min ist nicht
self-maintainable bezüglich des Löschens. Wenn 2 gelöscht wird, kann ich nichtmehr sagen, was das kleinste
Element danach war. Besseres Beispiel daher: count(). 
Klassifizierung von Aggregatsfunktionen:
- *distributiv:* Funktion F kann erst auf Teildaten angewandt werden und anschließend existiert eine 
Funktion G mit der aus den Teilergebnissen, das Endergebnis berechnet werden kann. z.B. min, max, count 
(Definition 2 - 9)
- *algebraisch:* Funktion G kann auf Teildaten angewandt werden, und liefert ein M-Tupel zurück, 
das wiederum mit einer anderen Funktion H am Ende das gleiche liefert wie eine Funktion F direkt 
auf die gesamten Daten angewandt. z.B. avg. *Beispiel:* Zum Berechnen des Durchschnitts einer
Datenmenge, kann man auch aus Submengen ein Tupel mit der Anzahl der Elemente (count) und deren Summe
(sum) zurückgeben. Aus diesem Tupel kann man nun den Durchschnitt berechnen. (Definition 2 - 9)
- *holistisch:* keine Parallelisierung möglich, keine Beschränkung des Speicherbedarfs für Sub-Aggregate,
z.B. häufigsterWert(), median(); Beispiel: häufigsterWert() ist holistisch, da die einzelnen häufigsten
Werte pro Submenge nicht aussagekräftig sind, sondern nur eine Liste Auskunft darüber gibt, welcher Wert
*insgesamt* am häufigsten Auftritt, Länge der Liste abhängig von Anzahl der Daten.

**Frage: Warum ist häufigster Wert holistisch?**  
siehe oben

**Frage: Welcher Aggregatsfunktion lässt sich Trucated Average (Richter, höchste und niedrigste Note wird
getrichen und daraus der Durchschnitt berechnet)**  
Algebraisch. Man berechnet mit Funktion G vier Werte: Anzahl Richter, Summe der Noten, höchste Note pro
Scheibe, niedrigste Note pro Scheibe. Daher das Zwischenergebnis ist ein M-Tupel mit M=4. Aus diesem
Zwischenergebnis kann die Endnote berechnet werden. Aus unterschiedlichen Schichten kann nun der gesamt 
höchste/niedrigste Wert gestrichen werden und anschließend den Trucated Average berechnen.  

**Prüfungsfrage: Was ist der Zusammenhang zwischen Aggregatsfunktionen und self-maintainability?**
?

**Prüfungsfrage: Warum ist Median holistisch?**
Weil der Median der Wert ist, der in der Mitte steht ist. Das heißt es müsste jeweils eine
 sortierte Liste ausgegeben werden, und anschließend aus der Anzahl der Elemente der mittlere
 Wert berechnet werden. Da die einzelnen Schichten aber nur intern sortiert sind kann man
 keinen Schluss darauf ziehen, wie der Median des gesamten Datensatz aussieht.

**(gewichtetes) arithmetisches Mittel**: ugs. "Durchschnitt", **Summe / Anzahl**, Klassifikation *algebraisch*, 
nur für numerische Daten

**Midrange**: Mitte des tatsächlichen Wertebereichs, **(max - min) / 2**  

**Median**: Mittlerer Wert, d.h bei sortierten Werten, der Wert der in der Mitte liegt. Bei ungerader Anzahl
der Durchschnitt der beiden Werte in der Mitte, Klassifikation *holistisch*, auf numerische und ordinale Daten
anwendbar (z.B. klein - mittel - groß).

**Modalwert / Modus**: Wert der im Datenbestand am häufigsten Vorkommt, für nominale, ordinale Daten,
schwierig ei kontinuierlichen Daten. Wenn jeder Wert nur einmal vorkommt ist Modus nicht definiert.

**Quartile**: Q1 = oberste 25%, Q3 = oberste 75%, IQR ("Inter-Quartile Range") = Q3 - Q1

**Außreißer**: Werte die mehr als 1,5 * IWR von Q1 nach unten bzw von Q3 nach oben abweichen.

**Boxplots**: Zur Darstellung von min, Q1, median, Q3 und max

**Varianz**: Maß für die Größe der Abweichung von einem Mittelwert (Definition 2 - 18)

**Standardabweichung**: Quadratwurzel der Varianz

**Histogramme**: Zeigt Häufigkeit mit der die einzelnen Werte auftreten, Kompression in "Buckets",
Probleme: ungeeigent für viele Dimensionen, keine Antwortverfeinerung (Antwortverfeinerung = 
je länger Daten betrachtet werden, desto genauer ist deren Auswertung) 
- *Equi-Width-Histogramm:* Breite aller Buckets gleich, Breite = Intervall der Attributwerte
- *Equi-Depth-Histogramm:* Tiefe aller Buckets gleich, Tiefe = Summe der Häufigkeiten  

**Entropie**: gibt an, wie zufällig die Daten verteilt sind, Maß für Unordnung (Definition 2-24),
negative Summe aus relativer Häufigkeit und statistischer Signifikanz, gibt an wie überraschend
 ein Ergebnis ist, p=1 keine Überraschung (minimal), maximal wenn pi=pj; Entropie ist 
 abhängig von der Anzahl der Werte d.h. nicht normalisiert
 kleine Zahl = kleine Entropie = kleine Überraschung
 große Zahl = große Entropie = große Überraschung
 Joint-Entrpoie für mehr als eine Variable
 
 
#### Wahrscheinlichkeitstheorie
**Wahrscheinlichkeitsmaß**: P erfüllt die folgenden Axiome:
- *Nichtnegativität:* P(a)>=0
- *Triviales Ereignis:* P(Ω)=1
- *Additivität:* Für alle a,b ∈ F und a ∩ b = ∅ (disjunkt): P(a ∪ b) = P(a) + P(b)

**Multivariate Verteilung**: Wahrscheinlichkeitsverteilun bei mehrdimensionalen 
Zufallsvariablen; P(X = a, Y = b) = Wahrscheinlichkeit, P(X,Y) = multivariate 
Wahrscheinlichkeitsverteilung, P(X) und P(Y) Randverteilungen

**Unabhängigkeit**: Verteilung einer Zufallsvariable ist nicht anders, wenn Wert einer
anderen Zufallsvariable bekannt ist

**Erwartungswert**:  Zahl, die die Zufallsvariable im Mittel annimmt (Definition 2 - 36)

**Varianz**: mittlere quadratische Abweichung vom Erwartungswert, Streuungsmaß (Definition 2 - 36)

*Ende der 2. Vorlesung vom 16.10.2018*  

## Übung




