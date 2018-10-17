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
*1-Rules:* sehr einfaches Vorhersageverfahren
*Overfitting*:


## Übung




