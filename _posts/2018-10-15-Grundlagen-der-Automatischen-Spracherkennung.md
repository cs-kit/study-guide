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

## 2. Vorlesung

### Nachteile der Spracherkennung:

- Umgebungen, in denen nicht gesprochen werden kann (Theater, laute Umgebung):
  Es gibt auch lautlose Spracherkennung: Ultraschalle am Kinn, Muskel EEG, Hirnströmungen
- Entferntes Mikrofon: Ergebnis sind dann sehr schlecht und sie werden mehr als
  linear schlechter mit der Distanz

>Beispiel zur Distanz: Google Homepod. Veröffentlichung von Google: Eigene Mitarbeiter
produzieren eine höhere Wortfehlerrate als normale Nutzer, weil sie kompliziertere
Befehle ausführen wollen (20% vs 8%). Das liegt daran, dass einfachere Aufgaben
"Wie wird das Wetter?" leichter zu verstehen sind und nicht alle Nuancen des
Satzes benötigen im Gegensatz zu "Bestelle mir das rote Pucky-Fahrrad von Amazon
für meine Tochter".

In einem realen Projekt muss immer die erste Frage sein: "Wo kann ich das Mikrofon anbringen?"
Wenn die Antwort nicht nah genug am Mund ist, dann ist es schon ein schlechtes Zeichen.
Beispiel im Auto: 30 cm in der Deckenverkleidung ist schon problematisch.
Beim Live-Transkribieren im europäischen Parlament (wo der Dozent wohl schon einmal
  mit dem Lötkolben die Mikrofonkabel angezapft hat), war es wichtig, keine
  Hintergrundgeräusche im Audiosignal dazugemischt zu bekommen.

Das Audiosignal von alten Kampfjets kam über den Kehlkopf früher, weil es einfach
zu laut war. Heute hat man die Mikrofone vorne in der Maske.

Die Hintergrundgeräusche sind dabei immer ein Problem. Bei Autos hat man das so
gelöst, dass man einen neuen Datensatz von Stimmaufnahmen mit Autogeräuschen im
Hintergrund erstellt hat.

### Taxonomie Sprache

Hier geht es um language.

Künstliche Sprache, zum Beispiel eine kontextfreie Grammatik mit festem Vokabular.
Der Nutzer muss geschult werden. Das kann man nur mit Arbeitnehmern machen.

Normalen Anwendern kann man keine Schulung zumuten, das heißt, man möchte
**Spracherkennung natürlicher Sprache**.

Man unterscheidet bei natürlicher Sprache drei Schwierigkeitsstufen:

1. Gelesene Sprache (Vorlesen eines bereits existierenden Textes, um System zu testen)
2. Geplante Sprache (Vortragen einer Rede im Bundestag sollte zwar geplant sein,
  aber frei gesprochen sein)
3. Ungeplante Sprache (Konversationen. Und die werden immer schwieriger je
  kodifizierter die Kommunikation ist, was bei engen Beziehungen der Sprecher
  der Fall ist, zum Beispiel in einer Familie)

### Taxonomie für Sprache und Spracherkennung

- Sprecherabhängig: Dialekte, Akzente werden darüber bedacht, dass das System
  auf einen Sprecher eintrainiert wird. Alte Diktiergeräte musste man 15-Minuten
  antrainieren, indem man ihnen einen bestimmten Text vorlaß. Andere Personen
  konnten das Gerät dann nicht benutzen.
  Wenn sich die Umgebung (Teppich statt Parkett) oder das Mikrofon verändert hat,
  dann funktionierten diese Systeme schnell nicht mehr.
- Geschlossene Sprechermenge, zum Beispiel in einem Parlament. Da hat man viele
  Trainingsdaten und kann sich auf jede Person einstellen.
- Sprecherunabhängig: Das gewünschte System
- Größe des Diskurs: Dialog versus Gruppengespräch -> unerwartete Wörter
  - domänenlimitiert: Sehr große Domäne (Parlament)
  - domänenunabhängig: Gibt es noch nicht wirklich (ist streitbar wie groß eine Domäne sein kann)
- Sprecherverhalten:
  - kooperativ: Sprecher kennt das System nicht, will aber dass es funktioniert
  - unkooperativ: Beispiel Telekom-Kundenhotline, man will gar nicht erkannt werden,
    wenn man sich beschwert
  - Vertraut: Menschen adaptieren sich im gegenseitigen Gespräch (Spiegelneuronen),
    das gleiche Phänomen passiert auch bei Mensch und Maschine. Es werden sogar
    neue Wörter erfunden (Studie über das Bestellen eines Mobilfunkvertrages in
    fremder Sprache)
- Äußerungsart:
  - Isolierte Wörter
  - Phrasen
  - Kontinuierliche Sprache

Frage: Wie funktioniert die Trennung von Kontinuum in isolierte Wörter?

**Achtung!** Der natürlichste Gedanke wäre, dass man sich einen Satz von unten
nach oben (Phonem für Phonem) zusammenbaut, **aber das ist genau, wie die
guten Systeme nicht funktionieren.**

Es wird mit dem ganzen Satz begonnen und der wird dann zerlegt. Von oben nach
unten. (Monolithischer Block)
Es werden quasi alle Sätze einmal probiert und für jeden Satz gibt es eine
Wahrscheinlichkeit, circa: "Wie hätte dieser Satz geklungen, wenn er
die vorliegende Audioaufnahme gewesen wäre."

Dabei fallen dann wiederum quasi als Nebenprodukt Wort- und Phonemgrenzen ab.

Frage: Hat man bei Satzgrenzen wieder das gleiche Problem?

Antwort: Ja. Da kommt man etwas in tricksen mit Mathe. Ansätze basiernd auf
neuronalen Netzen können das umgehen, sind aber noch nicht so gut...

Spracherkennung ist schwer, weil die menschliche Sprache sehr variant ist:

 - Signalebene: Kein Mensch kann ein Wort zwei mal artikulieren und es produziert
   das gleiche Signal. Akustik, Umgebung, Mikrofone haben auch Einfluss auf das Signal.
 - Phonetische Ebene: Kein Mensch spricht ein Phonem gleich aus. Alle Menschen
   haben eine unterschiedliche Sprache, Dialekte, Sprachfehler...
 - Linguistische Ebene: Mensch ist sehr kreativ. Variation der Sätze ist sehr
   hoch. Analyse der Texte aus dem Wall Street Journal. Mit jeder Ausgabe gab
   es neue Wörter, das menschliche Gehirn lernt diese einfach dazu und erschließt
   sie sich. Der Computer ist noch nicht so adaptiv.

Frage: Ist Betonung ein Problem?

Antwort: Verlauf der Grundfrequenz ist ein besserer Ausdruck. Bei Deutsch und
Englisch relativ irrelevant, wird teilweise ignoriert.

**Experiment zum McGurk-Effekt:** Immer gleiches Audioschnipsel wird über
Video von unterschiedlichen Lippenbewegungen gelegt und die Menschen hören
unterschiedliches, weil der Mensch indirekt Lippen lesen kann.

Ein Komilitone im Raum hatte den Effekt nicht. Mögliche Begründung, weil er
als Kind die Fähigkeit aufgrund seiner Sehschwäche nicht aufbauen konnte.

Auf bei Japanern funktioniert das nicht. Unwahrscheinliche Erklärung ist aufgrund
fehlenden Blickkontaktes. Wahrscheinlicher ist, dass die sichtbaren Feature
(Lippen, Kinn, Spitze der Zunge) nicht hilfreich sind für das Japanische.







## Math formulae

Test your LaTeX for mathjax on http://mathurl.com/

 $ \zeta(s) = \sum_{n=1}^\infty \frac{1}{n^s} $

test

 $$  \frac{
   \sum_{i=1}^{N}{(x_{i}-{{x}})^{2}}
}
{N-1}
 $$


## Syntax highlighting

{% highlight python %}

def test_this(name):
    print("hello", name)
    return name

a = test_this("Yo")

{% endhighlight %}
