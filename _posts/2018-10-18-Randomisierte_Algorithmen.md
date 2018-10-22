---
layout: post
title:  "Randomisierte Algorithmen"
ref: randomisierte_algorithmen
date:   2018-10-16 07:00:00 +0100
categories: master
excerpt: Randomisierte Algorithmen sind nicht deterministisch. Ihr Verhalten hängt vom Ausgang von Zufallsexperimenten ab. Diese Idee wurde erstmals von Rabin durch einen randomisierten Primzahltest bekannt. Inzwischen gibt es für eine Vielzahl von Problemen randomisierte Algorithmen, die (in dem einen oder anderen Sinne) schneller sind als deterministische Verfahren. Außerdem sind randomisierte Algorithmen mitunter einfacher zu verstehen und zu implementieren als 'normale' (deterministische) Algorithmen.
lang: de
tags: lecture
---
<div style="background-color: #EAEFF4; border: 1px solid #b5aeb1; border-radius: 3px;  padding: 10px; margin-right: 10px">
    <strong>Vorlesung:</strong> <a href="https://campus.studium.kit.edu/ev/DNKzFgy4QEiQ5AIZebdp7A">Randomisierte Algorithmen</a>, Vorlesung, 5 ECTS <br>
    <strong>Dozent:</strong> Thomas Worsch <br>
   <strong>Vorlesungswebsite:</strong> <a href="http://liinwww.ira.uka.de/~thw/vl-rand-alg/index.html">http://liinwww.ira.uka.de/~thw/vl-rand-alg/index.html</a> <br>   
   <strong>Klausur:</strong> mündlich, daher nach Vereinbarung <br>
   <strong>Einordnung:</strong> Vertiefungsfächer "Parallelverarbeitung","Algorithmentechnik", Profil "Datenintensives Rechnen" <br>
</div>

## Organisatorisches

### Vorlesungen
- **18.10.2018**: Organisatorisches und Foliensatz 1-1 bis 2-27

### Material
Das Material der Vorlesung besteht aus:  
- **Folien**: Folien werden auf Veranstaltungswebsite hochgeladen, Literatur ist im Skript vermerkt
- **Übungsblättern**  
Inhaltlich sind keine Veränderungen zum Vorjahr geplant, unter Umständen aber durchaus möglich

### Übungen
Die Übungen finden innerhalb der Vorlesungen nach Bedarf und meistens am Ende eines Kapitels statt

### Klausur
Klausur mündlich, per E-Mail melden, einen Zeitraum von 2/4-Wochen angeben in dem man Zeit hat

## Vorlesungsinhalt
### Einleitung
#### Grundsätzliches
Aufweichung des klassischen Alogorithmenbegriff für *randomisierte Algorithmen*; Bereitstellen
eines *zufälligen Wertes*; keine *eindeutige Festlegung* der Elementarschritte; 
 deterministischer Algorithmus der neben Input noch eine Zufallsvariable erhält  
 
 **ABER**: im Unterschied zu nichtdeterministischen Verfahren ist definiert mit 
 welcher Wahrscheinlichkeitwelcher Schritt als nächstes gewählt wird.  
 Alle Sichtweisen haben gemeinsam: *bei gleicher Eingabe können verschiedene Berechnungen 
 stattfinden*   
  
 Für eine festgehaltene Eingabe kann im Allgemeinen das *Ergebnis*, die *Laufzeit* und der 
 *Speicherplatzbedarf* nicht genau angegeben werden; Interesse Erwartungswerte herauszufinden.
 
 **Problem bei randomisierten Algorithmen**: Risiko falsch zu berechnen, aber 
 Fehlerwahrscheinlichkeit kann gering gehalten werden.  
 
 **Optimierungsalgorithmen**: Berechnung dauert uU zu lange; bessere Laufzeit mit 
 randomisierten Algorithmen, die aber uU das dlasche Ergebnis liefern. 
  
**Warum randomisierte ALgorithmen?** Lösung randomisiert oft schneller und leichter zu 
implementiert; manchmal sogar deterministisch nicht lösbar -> Preis dafür 
Fehlerwahrscheinlichkeit

#### Einige Schlagwörter
Standartmethoden zum generieren von Zufallbits:
- **Fingerabdrücke**: kompakte Repräsentationen großer Daten, durch zufällige Komponenten 
kann man erreichen, dass identische Fingerabdrücke auf identische Ausgangsdaten hinweisen
- **Zufälliges Auswählen und Umordnen**: durch zufällige Auswahl von Teilmengen, kann man
durch Zufall Ausreißer, die z.B. eine schlechte Laufzeit verursachen umgehen.
- **Überfluss an Zeugen**: Auswahl eines Elements, z.B. in einem Kreis ist durch 
deterministischen Algorithmus sehr schwer, obwohl Auswahl groß, daher durch Zufall einen
auswählen
- **Vereitelung gegnerischer Angriffe**: TODO
- **Lastbalancierung**: randomisierte Lastverteilung für parallele Algorithmen
- **Schnell mischende Markovketten**: TODO
- **Isolierung und Symmetriebrechung**: bei verteilter Umgebung kann Zufall eingesetzt werden
um unterschiedliche Ergebnisse bei Ausführung des gleichen ALgorithmuses erzielen

Weitere Aspekte im Zusammenhang mit randomisierten Algorithmen:
- **prohabilistische Methode**: Werkzeug um Existenz von gewissen Objekten nachzuweisen, durch
Zeigen, dass bei randomisiertem Algorithmus die Wahrscheinlichkeit auf gewisses Objekt zu 
stoßen größer 0 is.
- **randomisierte Komplexitätsklassen**: Komplexitätsklassen für randomisierte Algorithmen

### Erste Beispiele
#### Randomisierte Identitätstest
Vergleich zweier großer Objekte, nicht durch gesamte Struktur sondern durch "Fingerabdruck". 
Es wird angenommen, dass unterschiedlicher Fingerabdruck = unterschiedliches Objekt, aber 
Gleichheit von Fingerabdrücken = Gleichheit von Objekten *kann* auch falsch sein.

Drei Matrizen A,B und C; Frage: Ist AB = C? Durch Ausmultiplizieren beste derzeit mögliche
Laufzeit $ \mathcal{O}(n^{2{,}3727}) $; Prohabilistische Methode von Freivalds (1977) mit 
$ \mathcal{O}(n²) $ und einer Wahrscheinlichkeit von $ 1-2^{-k} $ richtig.   

{% highlight python %}
r ← Vektor von n unabhängigen Zufallsbits  
x ← Br
y ← Ax
z ← Cr
if (y ≠ z) then
    return NO
else
    return YES
fi
{% endhighlight %}

Überprüfung statt Gleichheit nur ob $ A(Br) = Cr$; Werte $y = A(Br)$ und $ z = CR $ als 
Fingerabdrücke verwendet. Es gilt $ P(ABr = Cr) <= 1/2 $; Algorithmus liefert definitiv 
richtiges Ergebnis, wenn Ergebnis *Nein*, Algorithmus kann falsches Ergebnis liefern, wenn 
Ergebnis *Ja*; nicht eindeutig z.B. wenn r der Nullvektor ist. Fehlerwahrscheinlichkeit 1/2
weil wenn Algorithmus *Ja* dann kann es entweder stimmen, oder nicht.  

**Fehlerwahrschenlichkeit**: Drücken der Fehlerwahrscheinlichkeit durch Auswählen aus 
Werten anstatt 2 -> $ P(ABr = Cr) <= 2^{-k} $; k Wiederholungen des Algorithmus nur dann am
Ende JA, wenn alle Einzelversuche auch JA, da Produkt der Wahrscheinlichkeiten

#### Vergleich von Wörtern
Vergleich von Wörtern A und B, wenn diese an unterschiedlichen Orten liegen. Klar 
Lösung deterministisch durch Übertragung der Wörter; mit probabilistischem Algorithmus
Laufzeit von $ \mathcal{O}(log n) und Fehlerwahrscheinlichkeit kleiner gleich 1/n.

{% highlight python %}
p ← Primzahl; zufällig gleichverteilt aus denen kleiner oder gleich n² ln n² ausgewählt 
a ← 
b ← Ax
if (a mod p = b mod p) then
    return YES
else
    return NO
fi
{% endhighlight %}



## Übung




