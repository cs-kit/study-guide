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
