---
layout: post
title:  "Buch: Artificial Intelligence - A Modern Approach"
ref: ai_book
date:   2018-10-15 07:00:00 +0100
categories: master
excerpt: Summary of the standard book on Artificial Intelligence by Russel and Norvig.
         I try to read 5 - 10 pages every day.
lang: de
tags: book
---

AIMA (abbrev.) ist [online verfügbar](http://aima.cs.berkeley.edu/) und in der KIT Bibliothek.

## Intelligenz
... macht den Menschen aus (homa "sapiens"). Bei AI geht es nicht
nur darum zu verstehen, wie Intelligenz beim Menschen funktioniert, sondern
auch eigene Intelligenz zu "bauen".

Der Begriff AI wird seit 1956 geprägt.

### Was ist AI?

Rational bedeutet, dass ein Aktor tut, was zu seinem Wissenstands richtig ist.
Die unterschiedlichen Strömungen können wie folgt unterteilt werden:

<table>
  <tr><td>Menschlich denkend</td><td>Rational denkend</td></tr>
  <tr><td>Menschlich handelnd</td><td>Rational handelnd</td></tr>
</table>

#### Acting humanly

Turing Test (1950)
Fragen per Brief stellen -> Antworten per Brief bekommen -> entscheiden, ob es
sich um einen Menschen oder einen Roboter handelt

Total Turing Test ist eine Erweiterung bei der auch ein Videosignal und Interaktion
durch das Reichen von Gegenständen möglich ist.

Folgende Bereiche wären nötig, um eine Maschine zu bauen, die den Turing Test
bestehen könnte:

 - Natural Laguage Processing (NLP)
 - Knowledge Representation (store knowledge and things which were heard)
 - Automated Reasoning (infer behaviour/an answer from knowledge)
 - Machine Learning (Adapt to changes and extrapolate patterns)
 - Robotics (Interact with the physical world)
 - Computer Vision (Perceive the visual world)

Auch wenn der Test nach all den Jahre immernoch herausfordernd ist, war er nie
wirklich das Zentrum der Forschung. Vergleich mit dem Bau des Flugzeugs.
Irgendwann hat man aufgehört das Flugverhalten der Taube nachgeahmt und aufgehört
ein Gerät mit Flügelschlag bauen zu wollen.

#### Thinking humanly

Cognitive Sciences

"Program thinks like humans"

Wie denkt der Mensch? Wir wissen es nicht. Herausfinden kann man es durch:

- Introspektion: Versuchen Gedanken wahrzunehmen bei sich selbst
- Bildgebende Verfahren beim Menschen
- Psychologische Experimente

INPUT A -> AI -> OUTPUT B
INPUT A -> HUMAN -> OUTPUT C

Wenn B ähnlich C, dann könnte man vermuten, dass der Prozess in der AI
ähnlich dem des Menschen ist.

Notiz: Gute Ergebnisse machen eine AI nicht menschlich im Denken, denn es geht
um den Vergleich der beiden Leistungen. Von dem Abgleich hat man in Computer
Vision profitiert.

#### Logik

(Rational denkend)

Syllologismus: "Sokrates ist ein Mensch. Menschen sind sterblich. Sokrates ist ein Mensch."

Ab 1965 ist die Logik mächtig genug, um jedes lösbare Problem theoretisch zu
lösen. Jedoch ist es in der Praxis so, dass bei großen Suchräumen die Suche
sehr lange dauert und eine Lösung nicht von einem Scheitern abzugrenzen ist durch
die Suchzeit.

"Logicist tradition" will AI so bauen, dass sie rational denkt.
Die Probleme dabei sind:

 - Zu großer Suchraum (wo soll man anfangen?)
 - Schwierig informelles Wissen in formelle Logik zu überführen.
  100%-Wahrscheinlichkeiten sind in der Realität selten (->fuzzy?)

#### Acting rationally

Agent = Handler (latein agere)
Rationaler Agent = rationales Handler

Korrekte Schlussfolgerung (Inferenz) bildet nicht die komplette Rationalität ab.
Instintives Handeln (wie zum Beispiel Reflexe) sind auch ohne logisches Schlussfolgern
wertvoll. Manche Entscheidungen können nicht für richtig oder falsch befunden werden,
generell ist aber trotzdem ein Handeln nötig.
=> Inferenz ist nicht alles -> rationales Handeln besserer Ausgangspunkt für AIMA

Rationalität ist gut wissendschaftlich definiert und kann besser erarbeitet werden
als das Denken oder Handeln eines Menschen, was immer mit Spekulieren zu tun hätte.

In der Realität ist für kaum eine Augabe die Zeit, alle nötigen Berechnungen
durchzuführen (vergleiche Schach mit Sport). Dieses Thema nennt sich
beschränkte Rationalität ("limited rationality").

### Foundations of AI

Die folgenden Gebiete sind die Ursprünge von AI.

#### Philosophy

Wo und wie funktioniert Denken? Wie entsteht Handeln?

Artistoteles mit seinen Syllologismen. Viele Maschinen und Ideen von früher.
DaVinci...

Rationalismus.
Dualismus: Gehirn und Seele...
Materialismus: Es geht ohne Seele.

Empirie: Wissen durch Erforschung mit den Sinnen (nicht nur theoretische Gedanken)
Induktion: Regeln erlernen durch das wiederholte Beobachten vom Zusammenspiel
den Regeln unterworfener Objekte.

Logischer Positivismus: Alles ist erklärbar und durch logisches Inferieren ableitbar.
(Kombination aus Ratiionalismus und Empirismus)


#### Mathematics

 - Mit Logik rechnen können: Algorithmen, Rechenmaschinen
 - Wahrscheinlichkeitstheorie

 Incompleteness theorem: Es gibt am Grunde (genauso wie bei Zahlen) eine kleine
    Menge von Annahmen, die man treffen muss. (Goedel) -> Es gibt Funktionen,
    die sind nicht berechenbar (andere Interpretation)

-> Turing: Berechenbarkeit. Halteproblem, Turing & Church thesis

Die theoretische Berechenbarkeit ist aber in der Realität nicht passend. Die
Frage muss sein, was kann in annehmbarer Zeit berechnet werden: Tractability

-> NP-completenes, exponential time?

-> Man könnte für manche Probleme vielleicht die richtige Lösung finden, aber
der Algorithmus ist in seiner Laufzeit nicht kontrollierbar.
Daher benötigt man Heuristiken! Wahrscheinlichstheorie! Pascal, LaPlace, Fermat,
Bernoulli, Bayes

#### Economics

Wie bekommt man das beste Ergebnis bei geringstem Einsatz. Wirtschaftliches Handeln
im Kontext von Staaten und die Spieltheorie.

Utility, Decision theory...

Von Neumann macht Computer und Analyseketten. Wichtige Überschneidung Markow-Ketten.

Nobelpreis für "satisficing" -> Modelle liefern Ergebnis, das ist "gut genug"
und nicht perfekt -> menschenähnlicher


#### Neuroscience

Ist die Wissenschaft über Gehirn und Neuronen. Es wurden immer mehr Zusammenhänge
und Funktionsweisen von Körperteilen und Fähigkeiten mit Orten im Hirn
verortet, aber es gibt noch zu viele Rätsel. Wie funktionieren Erinnerungen,
das Ersetzen von Funktionsbereichen bei Ausfällen...

Neuronen erforschen. EEG, fMRI.


#### Psychology

Wie denken und verhalten sich Menschen und Tiere?

Helmholtz mit seinem Schüler in Leipzig maßgebend. Etablierung schwierig.
Introspektion wurde nicht als wissenschaftlich angesehen durch den "behaviourism",
der mentale Prozesse als Ergebnis akzeptiert.

Änderte sich dann aber (Cognitive Psychology). behaviourism hatte bei Tieren
Erfolg, aber nicht bei Menschen.

Helmholtz hat ein Buch über das visuelle System geschrieben, das immernoch als
Standardlektüre gilt.


#### Computer Engineering

Die Maschinen wurden dann wirklich gebaut um den zweiten WK herum.
Programmiersprachen, Komplexitätsberechnung, schnellere Hardware.

Der Supercomputer kommt nicht in allen Fällen an das menschliche Gehirn heran.
Vor allem zu wenige Cores, auch wenn man nicht sagen kann, was ein menschlicher
Core ist.





#### Control Theory and cybernetics

Control theory will Error einer Zielfunktion minimieren, was AI auch tut. Homeostatic sollte eine
physikalische Schaltung des Hirns mit Feedbackschleifen ermöglichen.

Wie kann man einen Roboter bauen, damit die KI mit der Realität interagieren kann.

#### Linguistics

Moderne Linguistik entsteht zusammen mit KI. Zwei Monate bevor am MIT die Arbeit
an AI beginnt, gibt es eine Konferenz auf der Chomsky ein wichtiges Paper über
Sprache vorstellt. Es geht um Berechenbarkeit etc.

Natural Language Processing ist eine Gemeinsamkeit genauso wie Computational Linguistics.
Erst ab den 60ern wird klar, wie schwierig das Verstehen von Sprache wirklich ist.
