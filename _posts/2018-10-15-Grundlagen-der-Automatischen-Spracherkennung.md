---
layout: post
title:  "Grundlagen der Automatischen Spracherkennung"
ref: basics_asr
date:   2018-10-15 07:00:00 +0100
categories: master lecture
excerpt: Gesprochene Sprache in eine Folge von Wörtern überführen
lang: de
tags: lecture
---

## 1. Vorlesung

Link zu den [Folien](https://ilias.studium.kit.edu/goto.php?target=file_884805_download&client_id=produktiv) der ersten Vorlesung.

### Organisation

Webseite: [http://isl.ira.uka.de](http://isl.ira.uka.de)

Videos von WS17/18 auf DIVA: [DIVA Videos](https://mediaservice.bibliothek.kit.edu/#/details/DIVA-2017-518)

WS 2013/2014 auf Youtube: [Playlist](https://www.youtube.com/playlist?list=PLfk0Dfh13pBMPGYh-vP9c6rSwkYcTUFo3)

[Ilias-Kurs](https://ilias.studium.kit.edu/goto.php?target=crs_884802&client_id=produktiv)

Mündliche Klausur: Anmeldung über das Sekretariat (per E-Mail).

### Literatur

- Xuedong Huang, Alex Acero, Hsiao-Wuen Hon:  Spoken Language Processing
  *sehr umfangreich. Mehr drin als in der Vorlesung. Schön.*
- A. Waibel, K. F. Lee: Readings in Speech Recognition
  *älter, aber zwei gute Paper.*
- F. Jelinek: Statistical Methods of Speech Recognition
  *klein, oberflächig, gutes Material zu Sprachmodellierung*
- Schukat-Talamazzini: Automatische Spracherkennung
  *PDF verfügbar*
- Ivica Rogina: Sprachliche Mensch-Maschine-Kommunikation
  *unvollständig. Download Ilias*

**Eindrücklicher Hinweis darauf, dass die Literatur zu lesen ist!** Die Folien alleine reichen definitiv nicht aus.

"Unterschätzen Sie das nicht!"

### Definition

Automatic Speech Recognition (ASR):

Definition:
    Automatische Umwandlung menschlicher, gesprochener Sprache in die dazugehörige Wortsequenz in maschinenverarbeitbarer Form.

Häufig fälschlicherweise als Voice-Recognition bezeichnet.

Menschliche, gesprochene Sprache ist auf Englisch: *speech*

*Language* hingegen umfasst auch Text, Gestik, Tonhöhe...

Bei ASR geht es weder um die Tonhöhe noch ob Sprecher männlich oder weiblich etc. Auch die Semantik ist in der Definition nicht enthalten. Natural/Spoken Language Understanding versucht Semantik zu erfassen.

Frage: Wie kann man Wörter korrekt niederschreiben ohne den Sinn zu kennen?

Antwort: Das geht nicht wirklich. Die immer gleichen Fehler passieren.

**Lücke:** Es gibt eine Lücke zwischen gesprochener Sprache und der Veschriftung. Zum Beispiel Satzzeichen. Diese sind nicht im "Signal" enthalten, der Mensch imaginiert sie sich hinzu. Sowetwas braucht die Maschine quasi auch.

Anmerkung zu den Satzzeichen: Pausen markieren nicht pauschal Satzgrenzen. Es gibt sogar Studien, die zeigen, dass mehr als die Hälfte von Pause innerhalb von Sätzen gemacht werden. (Das berühmte "Äääh" von Boris Becker.)

### Anwendungsgebiete

- Diktat (überall wo man nicht schnell genug tippen kann, Hände beschäftigt)
- Untertitel für Filme (-> Durchsuchbarkeit von Videos)
- Sprachsuche, Spionage, Überwachung
- Assistenzsysteme (Blinde, Taube, körperlich Eingeschränkte)
- Pick-To-Voice-Systeme: Amazonlogistiker im Lager geben und Empfangen Befehle per Headset beim Packen von Paketen

Anmerkung: Gesprochene Sprache ist zeitlinear -> die wenigsten Menschen können diktieren.

**Was sind gute Anwendungsgebiete:**

 - Geschwindigkeit von Eingabe erhöhen (Sprache > Stenographie > Tippen)
 - Bei Verhinderung der Hände etc.
 - Schon gelerntes Werkzeug - "natürliche Art der Eingabe" (vgl. Programmieren eines alten Videorecorders)
 - Mikrofone sind billig, leicht und klein
 - Zusätzlicher Kanal (Sprache und Knöpfe, Ausfallsicherheit)





## Math formulae

Test your LaTeX for mathjax on http://mathurl.com/

 $ \zeta(s) = \sum_{n=1}^\infty \frac{1}{n^s} $


## Syntax highlighting

{% highlight python %}

def test_this(name):
    print("hello", name)
    return name

a = test_this("Yo")

{% endhighlight %}
