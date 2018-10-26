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

## 3. Vorlesung

Hörsaal Akustik -> abgerundete Kanzel (Schallreflektion zum Publikum wie in
  evangelischen Kirchen)
Glatter Linoleumboden, glatte Tafel => reflektieren Schall -> Schall kommt dann
unterschiedlich schnell beim Ohr des Hörers an und ergibt einen "Verschmierungs"-Effekt.

An den Wänden und der Decke sind Lochblenden zwischen denen sich der Schall
verfangen kann. Menschen absorbieren Schall sehr gut.

An der Decke des Hörsaals, der auch für Videoaufnahmen genutzt wird, befinden
sich Grenzflächenmikrofone, um Fragen des Publikums aufnehmen zu können.
Es handelt sich um ein spezielles Mikrofon auf einer Plexiglasscheibe.

=> Warnung: Aufnahmetechnik ist sehr wichtig für Erfolg bei Spracherkennung

**Lombard-Effekt**
Bei Blaupunkt wurde eine Freisprecheinrichtung für Autos entwickelt, die das
Signal des Autoradios aus der Sprachaufnahme herausrechnen kann, wodurch das
Radio bei Telefonaten im Auto an bleiben kann, jedoch nicht am anderen Ende
der Leitung gehört wird.
Es hat sich herausgestellt, dass die Tester des Systems vollkommen anders
gesprochen haben als normal, weil sie sich der lauten Umgebung angepasst haben.

**Homonyme:** Gleichklänge von Wörtern mit unterschiedlicher Bedeutung
  - Homographene: Man schreibt sie sogar gleich, z. B. Schloss, Schloss
  - Homophone: Sie klingen gleich, aber sie werden unterschiedlich geschrieben,
    z. B. bis und Biss, Verse <-> Ferse

Mehrdeutigkeiten von Sätzen: "Time flies like an arrow" (Time flies like an arrow. Fruit flies like a banana.)

Spracherkennung ist Mustererkennung. Klasse ist der komplette Satz.

Folie 13: Datenübertragung ist bei 30.000 bps, aber durch Redundanz und unnützes Signal werden
die 50.000 bps aufgefüllt.

Schichtenarchitektur aus Modell funktionieren nicht so top-down wie dargestellt,
es existieren Beeinflussungen und Feedbackschleifen.

"Flugzeuge schlagen nicht mit den Flügeln und Autos haben keine Beine"


Gaumensegel macht den Nasenraum zu. Harter Gaumen und Zähne sind passive
Artikulatoren. Impulse/Radstöße (aus der Vorlesung Kognitive Systeme) sind gut
geeignet um Zerhackung des Luftstroms aus der Lunge durch die Stimmbänder zu
modellieren.
-> Impulszug wird moduliert

**Bernoulli-Effekt**
Medium (Gas,Flüssigkeit) strömt durch begrenzten Kanal.

1. Die Strömungsgeschwindigkeit eines Moleküls passt sich seiner Umgebung an
   -> der Rand des Kanals bewegt sich garnicht, daher ist außen die Flussgeschwindigkeit
      geringer
2. Durch die unterschiedlichen Flussgeschwindigkeiten entsteht ein Unterdruck in
   der Mitte. -> Dieser Unterdruck zieht die Stimmlippen zusammen.

Das Zusammenziehen und Öffnen durch den Druck aus der Lunge wiederholt sich sehr
oft pro Sekunde. Vergleichbar mit einem Luftballon, den man zum Quitschen bringt.

Pulmonische Sprache (pulmo = Lunge) macht fast alle menschlichen Sprachen aus,
es gibt aber Ausnahmen (für uns verständliches Beispiel: Amis/Engländer machen Gluk-Gluk
  um Säufer zu imitieren mit dem Gaumen)

Die Frequez des Öffnen und Schließens der Stimmbänder ergibt die Stimmhöhe.
Eine hohe Frequenz macht einen höheren Ton. (fälschlicherweise denken manche,
  dass es mit der Größe des Vokaltraktes zusammenhängt, dieser Zusammenhang
  besteht aber nur über die Größe der Stimmbänder; Mann Testosteron größere
  Stimmbänder -> Sichtbarkeit des Kehlkopfes -> niedrigere Frequenz Stimme)

Langoroskop (Kamera in Rachen)  + Stroposkoplicht (Subsamplingder Bildrate)
-> Aufnahmen von Stimmbändern

Mitlaute v.s. Selbstlaute

Vokale sind immer stimmhaft = Stimmbänder schwingen

Definition: **Phon**
Kleinster Bestandteil der Spreche, der wahrgenommen wird. Der Mensch glaubt
zumindest, dass da etwas ist, auch wenn manchmal im Signal nichts spezielles da ist
(vergleiche mit Pausen)

Phonetiker und Linguisten nutzen die menschliche Wahrnehmung als Forschungsbasis

-> Optische Täuschungen zeigen, dass die Wahrnehmung getäuscht und interpretiert
   ist

Durch das exakte Scannen des Hirns können sog. Nuklei aufgenommen werden, die
soetwas wie eine Taktrate haben. Diese Takte sind im Vielfachen (zum Beispiel
  Nucleus A ist doppelt so schnell wie B) miteinander getaktet
  -> Wiederum eingeschlossen in größere Nuklei, die mitunter einen Taktschlag
     pro 15-20 Millisekunden haben -> Das würde bedeuten, dass auf dieser
     Millisekundenebene gar nichts zuverlässig verarbeitet wird -> Theorie: Phone existieren nicht.

Lippenform: Flach oder rund
Zungenspitze: Dorsum Linguae

Vokalviereck: Bestimmung eines Vokals durch Position des dorsum linguae und der
Öffnung der Lippen. Zwei Buchstaben pro Position. Der rechte ist mit runden Lippen.

Diphtonge wandern durch das Viereck im Laufe der Artikulation. Monophtonge nicht.
Vokale können auch nasal ausgesprochen werden: Franzosen

Einordnung der Konsonanten:

 - Art der Artikulation
 - Ort der Artikulation
 - Stimmbändereinsatz (Hand an Stimmbänder halten um zu spüren, z. B. "b" vs "p")

"Pf" ist zum Beispiel ein Phon. Es ist nicht "P" und "f" sondern zusammen wahrgenommen.

Mit wenigen Monaten können Kinder alles hören und über die Zeit lernt man dann,
dass manches kein sinnvolles Signal ist oder nicht unterschieden werden muss,
dann fängt man an, diese Unterschiede nicht mehr zu hören.
Das sorgt für ein schwierigeres Erlernen von Fremdsprachen, wenn man älter ist,
zum Beispiel russische Muttersprachlerin "Jochen" und "Johann" klingen, wegen des
fehlenden Verständnis für ein aspiriertes "H", gleich.

## 4. Vorlesung

Offene Konfiguration des Vokaltraktes: Vokal (vowel)
Geschlossene: Konsonant

IPA = International Phonetic Alphabet
herausgegeben von der International Phonetic Association

Alle bekannten Sprachlaute der Welt sollen durch ein eindeutiges Alphabet
beschrieben werden können, damit man alle Sprachen so schreiben kann, wie sie
klingen, wie Noten in der Musik.

Bei den Vokalen gibt es zwei Symbole, die stehen alleine und zwischen zwei Knoten.
Die gibt es nur gerundet. Die grauen können theoretisch artikuliert werden,
existieren aber in keiner Sprache.

Aus dem Audiosignal kann man offensichtlich nicht die Konfiguration des Vokal-
traktes oder ähnliches ableiten. Daher misst man mit Metallplättchen im Mund,
die man elektromagnetisch prüfen kann.
Es gibt auch noch den Laryngograph ([electroglottograph](https://en.wikipedia.org/wiki/Electroglottograph)),
dieser misst von außen am Kehlkopf.
Man kann auch den Luftdruck in und außerhalb des Mundes messen, um Unterschiede
bei plosiven o. Ä. zu quantifizieren.

Die gepulsten Luftströme der pulmonischen Sprache werden dann durch die Formung
des Mundes moduliert. Die unterschiedlich großen Räume durch die der
Schall hindurch muss, können als **Helmholtz-Resonator** modelliert werden.
Der Helmholtz-Resonator ist eine Röhre, in der sich Wellen ausbreiten.

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/PoEyIJx3uM0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

IPA Konsonanten: links stehen jeweils die stimmlosen und rechts die stimmhaften Konsonanten.
Zum Beispiel p, b. Die lila hinterlegten Zellen sind unmöglich zu artikulieren.
Leere, weiße Zellen wären möglich, aber sind noch nicht in menschlicher Sprache
gefunden worden. Der Großteil der gesprochenen Sprachen ist jedoch nicht
durch Linguisten oder Phonetiker erforscht worden. (Es gibt sehr viele kleine
  Sprachen)

**Diakritika:** Kleine Zeichen zur Modifikation des IPA, zum Beispiel Hochkomma
für Aspiration oder Doppelpunkt nach Vokal für Streckung (W**e**k, w**e**g) [vɛːɕ], [vɛk]

Die ersten paar Kapitel des IPA Handbuchs führen nochmal besser in dieses Thema
ein.

### Phoneme

Ein Phonem ist die kleinste bedeutungsunterscheidende Einheit einer menschlichen
Sprache.

Das **Phon** ist unabhängig von einer spezielle Sprache; ein Phonem hingegen nicht.

Wie findet man Phoneme? Für Laien: Unterscheidung zweier Wörter durch Tausch
eines Phons, zum Beispiel "Haus" und "Maus".

Austauschbare Laute, die die Bedeutung erhalten, heißen **Allophone**.
Beispiel: "Chemie", "Schemie". Das schließt aber nicht auf alle Phone, zum Beispiel
gibt es trotzdem Unterscheidungen, wie  "Rauch", "Rausch".
Weiteres Beispiel ist das gerollte und ungerollte "R" im Deutschen.

Jedes Phon ist entweder Phonem oder Allophone und letzere können auch wieder zu
Phonemen zusammengesetzt werden. "Monophon" <-> Allophon

Weiteres Beispiel: Im Japanischen klingen "R" und "L" gleich, daher wissen
Japaner oft nicht, was genutzt werden soll, wenn sie eine Sprache sprechen in
der "r" und "l" keine Allophone sind. Prinzipiell können sie aber schon "R" und "L"
differenziert sprechen, es ist nur nicht nötig im Japanischen.

Die Phoneme sind nicht eindeutig definierbar. Gegenstand von Diskussionen
zwischen Linguisten und Phonologen. Für Informatiker ist das nicht so wichtig.
Eher die Frage, ob das Phonem geeignet ist für die Spracherkennung.
Zum Beispiel: Wenn ein sehr diskutiertes Phonem (glotaler Stopp bei ...) nur
drei mal in 10 Stunden sprache annotiert wurde, dann ist es aus einer probabilistischen
Sicht nicht so wichtig. Praktisch heißt das, dass man sie ignoriert und hofft,
dass sich minimale Paare aus dem Kontext unterscheiden lassen.

Bei jeder Sprache gibt es neue Phänomene. Zum Beispiel Klicks oder nasale Vokale
im Französischen. Oder tonale Sprachen.

**Tonale Sprachen:** Beim Englischen, wo man früher sehr viel geforscht hatte, war
und ist die "Tonhöhe" (-> besser Grundfrequenz nennen) uninteressant.
Im Mandarin sind sie aber bedeutungsunterscheidend. Dort gibt es fünf Töne:
steigend, fallend, bergförmig, flacher Ton und unbetonter Ton.
Beim Kantonesischen sind es sogar 8 Töne + der flache Ton = 9.
In afrikanischen Zulu-Sprachen wird es noch mehr, denn dort ändert sich die
Tonhöhe mit der Stelle des Wortes im Satz...

### Physik Wellen

Schall ist eine Longitudinalwelle. Kleine Auffrischung von Schulwissen:

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/eyO1UlrPqIQ" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Ruhe Luftdruck auf NN 1013 mbar (Millibar).

Schalldruck: Wechseldruck in Pascall ($ {N \over m^2}  [Pa] $), der zum Ruhedruck
hinzukommt. Der leisteste hörbare Schall hat einen Schalldruck von 1e^-5 Pa.
Die Schmerzgrenze für den Menschen liegt bei 63 Pa. -> 10 Milliarden mal größer als das Leiseste
=> großer dynamischer Umfang

Schall kann als eine Überlagerung von sinoiden Wellen modelliert werden.

T = Dauer für eine Schwingung
Frequenz f = 1/T [Hz]

James Clerk Maxwell hat die Theorie aufgestellt, die elektromagnetische Wellen
vorstellt. Deren Existenz wurde durch Hertz nachgewiesen (1/s ist 1 Hz):

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/b2cVLHozb9k" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Schall breitet sich mit begrenzter Geschwindigkeit (abhängig vom Medium) aus.
Wellenlänge $ l = {c \over f} $

Dazu ein kleines Video, das den Zusammenhang zwischen elektromagnetischen
Wellen und deren Frequenz illustriert:

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/7WXW2bBWBEg" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

**Schalldruckpegel**: $ L_{p} = 10 log_{10} ( { \tilde{p}^2 \over p_{0}^2 } ) [dB] $
  oder $  L_{p} = 20 log_{10} ( { \tilde{p} \over p_0} ) [dB]  $.

Wobei $\tilde{p}$ der vorzeichenbereinigte Schalldruck und $p_0$ der Referenzdruck $2 * 10^{-5} Pa$.
Ursprünglich wurde letzteres für die Hörschwelle bei 1 kHz gehalten. Jetzt leicht
anders, aber man passt die Referenz nicht mehr an, daher kann es zu zu negativen
Werten in niedrigen Bereichen kommen, da: $log(x) < 0$ für x kleiner 1.

Die Wahl des Logarithmus spiegelt auch das menschliche Empfinden beim Schall,
da er nicht linear als lauter empfunden wird.

dezi Bell gibt es auch bei Elektromagnetismus, daher nutzt man in der Akustik noch
ein angehängtes "A" für "Akustisch": **dB (A)**

| Referenz                                                             | Ungefährer Schalldruck [dB (A)]        |
|----------------------------------------------------------------------|----------------------------------------|
| $P_{}$                                                               | 0                                      |
| Kühlschrank                                                          | 40                                     |
| Schreien                                                             | 65                                     |
| Konzert (ab hier beginnt das Gehör Schaden zu nehmen)                | 120                                    |
| Gewehrschuss (ab hier beginnt Schmerzgrenze)                         | 140                                    |
| Raketenstart                                                         | 180                                    |

Man beachte, dass die Schmerzgrenze leider erst nach der Schadensgrenze beginnt.

**Schallenergie:** Zusammensetzung aus kinematischer und potentieller Energie.
Modellannahme: Luftteilchen, die an fiktivem Punkt mit einer fiktiven Feder
verbunden sind. "Aufziehen" und "Zurückschwingen" (siehe Erklärung zu Helmholtz
  Resonator)

Energie wird Schall zugewiesen. Schalldruck und Energie verhalten sich unterschiedlich
bezüglich der Distanz.

 - $E ~ { 1 \over r^2 }$: die Energie verhält sich umgekehrt, quadratisch
   proportional zum Radius
 - $P ~ { 1 /over r}$: der Druck hingegen umgekehrt linear proportional

 Die Schallwelle breitet sich als Kugel aus -> Oberfläche der Kugel -> quadratische Abnahme der Energie
 ???

### Das Ohr

Ohrmuschel dient als Empfänger.

Druck auf Trommelfell von außen unterschiedlich. Die Longitudinalwelle wird
am Trommelfell in eine mechanische Bewegung übertragen.
Über Steigbügel, Hammes und Amboss findet dann eine Verstärkung des Signals
auf eine kleinere Fläche statt. **Ovales Fenster**
Dieses Ovale Fenster überträgt die mechanische Bewegung in eine
[Wanderwelle](https://de.wikipedia.org/wiki/Wanderwelle) auf die
Flüssigkeit innerhalb der geschlossenen **Schnecke (latein Cochlea)**.
Es handelt sich um eine stehende Welle.

Die Schnecke wird nach hinten immer schmaler. Dadurch findet sich zu jeder Frequenz
ein Abschnitt der Cochlea mit einer passenden Resonanzfrequenz. Das heißt, es
gibt dort besonders starke Wechseldrucke. Salopp: "Es schwappt dort besonder
viel Wasser hin und her".

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/WeQluId1hnQ" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Ungefähr: Diese Resonanz wird übertragen und an der basal membran auf die Haarzellen
übertragen, welche dann das Signal in elektrische Reize überführen.

Mehr Infos: https://de.wikipedia.org/wiki/H%C3%B6rschnecke

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/HgZURbqJPUo" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Effekte:

 - Es ist nicht immer nur ein Resonanzbereich aktiv
 - Schwingungen überlagern sich

 => komplexe Muster

**Aktivierung eines Neurons:** Es gibt ein Mindesniveau zum Aktivieren eines
Neurons. Davor feuert es nicht, sondern regeneriert sich nur. Aktivierungspotential.
Die notwendige Zeit zum Aktivieren eines Neurons ist länger als die Dauer, einer
Schwingung eines Haars an der Cochlea.
Daraus folgt, dass der Mensch Schallwellen nur beschränkt genau auflösen kann.
Es gibt also Frequenzunterschiede, die kann der Mensch nicht hören.
-> pychoaktive Effekte
Diese "Lücke" wird zum Beispiel bei der Codierung von MP3 verwendet, um die
Datenrate reduzieren zu können.


![](/assets/images/Aktionspotential.png)

https://de.wikipedia.org/wiki/Aktionspotential
