---
layout: post
title:  "Algorithmen II"
ref: algorithmen_II
date:   2018-09-04 07:00:00 +0100
categories: master
excerpt: Diese Lehrveranstaltung soll Studierenden die grundlegenden theoretischen und praktischen Aspekte der Algorithmentechnik vermitteln. Es werden generelle Methoden zum Entwurf und der Analyse von Algorithmen für grundlegende algorithmische Probleme vermittelt sowie die Grundzüge allgemeiner algorithmischer Methoden wie Approximationsalgorithmen, Lineare Programmierung, Randomisierte Algorithmen, Parallele Algorithmen und parametrisierte Algorithmen behandelt.
lang: de
tags: lecture
---
<div style="background-color: #EAEFF4; border: 1px solid #b5aeb1; border-radius: 3px;  padding: 10px; margin-right: 10px">
    <strong>Vorlesung:</strong> <a href="https://campus.studium.kit.edu/ev/LSwjSOYfRp6QN-PKh4W42Q">Algorithmen II</a>, Stammmodul, 6 ECTS <br>
    <strong>Dozent:</strong> Peter Sanders  <br>
    <strong>Übungsleitung:</strong> Sebastian Lamm, Demian Hespe  <br>
   <strong>Vorlesungswebsite:</strong> <a href="http://algo2.iti.kit.edu/AlgorithmenII_WS18.php">http://algo2.iti.kit.edu/AlgorithmenII_WS18.php</a> <br>   
   <strong>Klausur:</strong> 19.2.2019 13:00 - 15:00  <br>
   <strong>Nachklausur:</strong> (noch unklar)  <br>
  
</div>

## Organisatorisches

### Vorlesungen
- **15.10.2018**: Organisatorisches und Foliensatz 1-1 bis 1-19
- **16.10.2018**: Dozent krank, VL wird von Übungsleiter gehalten (Foliensatz 2, hat Nummerierung 3): 3-1 bis 3-23
- **22.10.2018**: 1-20 bis 1-32; Wdh. Foliensatz 2; (Foliensatz 3 hat Nummerierung 2) 2-1 bis 2-65
- **23.10.2018**: 2-10 bis 2-27 und Übung 1
- **29.10.2018**: 2-28 bis Ende Kapitel 3
- **30.10.2018**: 4-1 bis 4-22, Übung 2
- **05.11.2018**: 4-23 bis Ende Kapitel 4; 5-1 bis 5-25
- **06.11.2018**: 5-12 bis 5-19, Übung 3
- **12.11.2018**: 5-20 bis 5-61
- **13.11.2018**: 5-61 bis 5-68, Übung 4
- **19.11.2018**: 5-68 bis Ende Kapitel 5, 6-1 bis 6-2
- **20.11.2018**:

### Material
Das Material der Vorlesung besteht aus:  
- **Folien**: Folien mit einer Chilischote am oberen Rand sind *nicht prüfungsrelevant*
- **Übungsblättern**
- **Buch**: *Algorithms and Data Structures — The Basic Toolbox*, K. Mehlhorn, P. Sanders, Springer 2008, macht ca. 40% der Vorlesung aus, vor allem empfehlenswert, 
wenn man Algorithmen I nicht am KIT oder gar nicht gehört hat.
- **Skript**: ergänzende Informationen die nicht im Buch stehen

### Übungen
Die Übungen finden jeweils in der zweiten Hälfte der Dienstagsvorlesung statt. Die Übungsblätter erscheinen 14-tägig jeweils am Dienstag. 
Die Mustelösung kommt 9 Tage später und wird in den Übungen nicht besprochen. Die Bearbeitung der Übungsblätter ist freiwillig und wird wärmstens Empfohlen (na klar).
Das erste Blatt erscheint am 23.10.2018.

### Klausur
Die Klausurbearbeitung beträgt 120 Minuten und es darf ein doppelseitig handbeschriebenes DIN A4 Blatt mitgenommen werden.


## Vorlesungsinhalt

### Algorithm Engineering
> Algorithm Engineering ist eine umfassenendere Sicht auf die Algorithmik und liefert eine bessere Kopplung zu Anwendungen, als die 
Algorithm Theory.

**Algorithm Theory:** Das Problem in der Umsetzung von Algorithmen liegt zwischen Theorie, Praxis und interdiziplinären Felden.
- *Theorie*: Model -> Design -> Analysis -> Performance Guarantees
- *Practice*: Implementation -> Applications
- *Other Disciplines*: Publications? Money?
  Die Schwierigkeit liegt darin, die großen Kluften zwischen diesen Gebieten zu überwinden.

*Beispiele:*
- Komplexe theoretische Algorithmen lassen sich oft durch "einfache" FOR-Schleifen implementieren
- fortgeschrittene Datenstrukturen lassen sich durch Arrays implementieren
- Kontanten werden in der Laufzeitberechnung vernachlässigt, machen in Realität aber 42% der Effizienz aus

**Algorithmics as Algorithm Engineering**: Den Zusammenhang von Theorie und Praxis kann man sich besser als Kreislauf vorstellen, 
bei welchem Model, Design, Analysis, Implementation und Experiment ineinander übergehen und zusätzlich interdisziplinäre Forschung mit einbeziehen.

**Realistic Models**: Vorsichtige Definition von Modellen, die sowohl in der Theorie funktionieren, als auch auf realen Maschinen laufen können.

**Design**: algorithm that work well in practice; simplicity, reuse, constant factors, easy instances

**Analysis**: constant factors matter, beyond worst case analysis → practical algorithms might be difficult to analyze

**Implementations**: Sanity check for algorithms; Challenges in semantic gaps: abstract algorithms ↔ C++ ↔ hardware

**Experiments**: sometimes good instead of analysis, rather too much than too little output data, reproducibility (10 years!); need a possible outcome 
that fasifies a hypothesis; 

**Quality Criteria**: new algorithms must be good (really good, not only with "toy data"); show through comparision old - new algorithm: use same data, 
benchmarks, quality and speed, real world data if possible, many different inputs if possible

### Fortgeschrittene Datenstrukturen
Anmerkung: Foliensatz 02 trägt die Nummerierung 3

**Prioritätslisten**: [Wikipedia](https://de.wikipedia.org/wiki/Vorrangwarteschlange): "Den Elementen, die in die Warteschlange gelegt werden, 
wird ein Schlüssel mitgegeben, der die Reihenfolge der Abarbeitung der Elemente bestimmt.", 
Operationen: insert, extractMin, remove, decreaseKey (=Priorität erhöhen)

**Adressierbare Prioritätslisten**: Elemente in Prioritätsliste können verändert werden* → zur Identifikation des zu verändernden Elements adressierbar,
z.B. remove nicht nur mit oberstem Element möglich; Operationen in Prioritätslisten: build, size, insert, min, deleteMin, remove*, decreaseKey*, merge* 
(*neu ggü einfachen Prioritätslisten);
Anwendungen: Dijkstra, Greedy-Algorithmen ([Wikipedia](https://de.wikipedia.org/wiki/Greedy-Algorithmus): "schrittweise den Folgezustand auswählen, 
der zum Zeitpunkt der Wahl den größten Gewinn bzw. das beste Ergebnis verspricht")

**Heap-Eigenschaft**: Wurzel eines Teilbaums muss immer kleiner sein als seine Kindknoten (→ min-heaps; max-heaps gibt es aber auch)

**Wald heap-geordneter Bäume**: nicht nur einen Baum → ganzer Wald = Menge an Bäumen; kein Binärbaum, Knoten kann mehrere Kinder haben  
Operationen:
- *Cut:* Teilbaum eines Baumes, als eigenen Baum in den Wald einfügen (Knoten der Wurzel werden soll: parent := null)
- *Link:* Verknüpfen zweier Bäume a,b; wenn a < b → b Teilbaum von a: $ union(a,b): link(min(a,b), max(a,b)) $

**Pairing Heaps**: Operationen:
- *insertItem(h: Handle):* Einfügen eines neuen Baums für Handle h; $ O(1) $
- *newTree(h: Handle):* Einfügen eines neuen Elements in den Wald mit Handle h, zur effizienten Ausgabedes kleinsten Elements Pointer aktualisieren, 
wenn eingefügtes Element kleiner als bisheriger min
- *decreaseKey(h: Handle, k: Key):* Update Key des handles, wenn sich key verkleinert, unklar ob Baum noch heap-Eigenschaft erfüllt, deshalb: 
ist Element Wurzel → update und fertig, wenn *keine* Wurzel → cut; unbewiesen: $ O(log log n) ≤ T ≤ O(log n) $ → sehr schnell in Realität   
- *cut(h: Handle):* Herausschneiden aus Baum: Entfernen des gesamten Teilbaum und einfügen als neuen Baum in Wald (newTree(h)); 
update des minPointers (minPtr)
- *deleteMin : Handle:* Element m auf das minPtr zeigt wird aus Wald entfernt → muss root sein, das kleinste Element kann nicht unterhalb eines Baumes sein, 
alle Kinder von m werden als neue Teilbäume in Wald eingefügt; paarweise Vereinigung der Wurzeln, Vergleiche Wurzeln von nebeneinanderstehenden Bäumen und
hänge das größere Element unten an; $ O(log n) $
- *merge(c: addressablePQ):* aus zwei Heaps einen Heap bilden; kleinere minPtr wird für neuen Heap übernommen; Vereinigung der Wälder der Heaps; 
Ursprungswald := ∅; $ O(1) $  

Repräsentation: Wurzeln in doppelt verketteter Liste; zwei Varianten (Vgl. Foliensatz 2 Abb 3-10); Pointer auf linken bzw. rechten Sibling, weil sonst 
Parent alle Pointer auf Kinder halten müsste
- Variante 1: | parent | data | left sibling | right sibling | one child | → einfacher, mehr Speicherplatz
- Variante 2: | data | parent or left sibling | right sibling | one child | → spart Platz, etwas komplizierter

**Fibonacci-Heaps**: Wichtige Begriffe:
- *Rang:* direkte Anzahl Kinder
- *Verinigung nach Rang:* Unnion nur für gleichrangige Wurzeln (Union by Rank)
- *Markieren:* Knoten die ein Kind verloren haben
- *Kaskadierende Schnitte:* Schneide markierte Knoten (mehr als 2 Kinder verloren)  

Armotisierte Komplexität: $ O( o + d log n)$ für d=#deleteMin, o=#otherOps,  n = maxAnzahlKnoten

Repräsentation: wie Variante 1, plus Rank, Markierung zusammen mit data speichern

Operationen:
- *deleteMin : Handle:* Element m auf das minPtr zeigt wird aus Wald entfernt → muss root sein, das kleinste Element kann nicht unterhalb eines Baumes sein, 
alle Kinder von m werden als neue Teilbäume in Wald eingefügt; solange ein a,b ∈ forest existiert, für das gilt rank(a) = rank(b) →  Vereinigung von a und b,
inkrement Rang der verbliebenen Wurzeln, update  minPt und return minPtr; Analyse: $ O(maxRank) = O(log n)  $ (Beweis siehe Foliensatz 02 Abb. 3-16), 
maxRank logarithmisch, $ 2^k + 1 × insert, 1 × deleteMin → rank k $, Binomialbäume haben Struktur, dass Teilbäume von allen Rängen darunter enthalten sind
→ Problem: durch Rausschneiden ergeben sich kleine aber hochrangige Bäume → Kaskading Cuts in Fibonacci Heaps
- *Union-by-Rank:* Roots haben Rang, Array mit Länge des größten Rangs, jedes Element wird im Array an Stelle seines Rangs gehängt, ist Feld besetzt, 
werden Elemente vereint (der größe nach aneinander gehängt), dadurch verändert sich Rang und Baum muss an anderer Stelle im Array eingesetzte werden, ist 
dieses wieder besetzt muss wieder Vereinigt werden,... (vgl Foliensatz 02 Abb. 3-15); Analyse: $ O(AnzahlUnions + AnzahlForest)$
- *Cascading Cuts/Kaskadierenden Schnitte:* in decreseKey kein normaler cut, sondern cascadingCut(h): wenn h keine Wurzel ist, p := parent(h), unmark wenn
markierung, cut, wenn p marked dann cascadingCut(p), else mark p; Beweis, dass kaskadierende Schnitte maxRank logarithmisch halten (vgl. Foliensatz 02: 3-19)

Name Fibonacci-Heaps: Bekannt, dass i-te Fibonacci-Zahl $ ≥ 1.618^i $, exponentiell in i → ein Baum mit Rank i enhält exponentiell viele Knoten → nur
logarithmisch viele Ranks, z.B. v mit rank(v) = i enthält $ ≥ F^{i+2} = 1.618^i+2 $ Elemente → logarithmische Zeit für deleteMin 
(Beweis auf Foliensatz 02: 3-21)

*Ende der Vorlesung vom 16.10.2018*

### Fortgeschrittene Graphenalgorithmen
**Kürzeste Wege**: Graph mit Knoten V und Kanten E, Kostenfunktion c und Anfangsknoten s; Gesucht Länge $ \mu (v)$ des kürzesten Pfads von s nach v →
Pfad mit der kleinsten Summe aus den Kosten der Kanten; zwei Knotenarrays: d[v] (vorläufige Distanz von s nach v;  $ d[v] ≥ \mu (v)$), 
parent[v] (Vorgänger von v auf Pfad von s nach v);  
*Initialisierung:* $ d[s] = 0, parent[s] = s; d[v] = ∞, parent[v] = ⊥ $ (⊥ = Bottom Symbol, undefined)  
*Kanten relaxieren:* falls $ d[u] + c(u,v) < d[v] → d[v] := d[u] + c(u,v) $ und $ parent[v] := u  $
*Pseudocode von Dijkstra:*
{% highlight python %}
initialize d, parent
all nodes are non-scanned
while ∃ non-scanned node u with d[u] < ∞
    u := non-scanned node v with minimal d[v]
    relax all edges (u,v) out of u
    u is scanned now
{% endhighlight %}
d ist anschließend optimale Entfernung und parent zugehörige Wege; v erreichbar, es wird irgendwann gescannt; v gescannt $ \mu (v) = d[v]$  

*Laufzeit:* $T_{Dijkstra} = O(m · T_{decreaseKey} (n) + n · (T_{deleteMin} (n) + T_{insert} (n)))$ mit 
[Fibonacci-Heapprioritätslisten](https://de.wikipedia.org/wiki/Fibonacci-Heap) (Wikipedia: "Elemente mit festgelegter Priorität 
in beliebiger Reihenfolge effizient im Heap gespeichert werden können und stets ein Element mit höchster Priorität 
entnommen werden kann."), wenn zudem m hinreichend groß (m > log log n), dominiert m die Laufzeit und hinterer Teil nichtmehr relevant
 $T_{DijkstraFib} = O(m · 1 + n · (log  n + 1)) =
 O(m + n  log  n)$ → ABER: konstante Faktoren sind größer als bei binären Heaps  
 
*Laufzeit im Durchschnitt:* maximal m decreaseKey Operationen (eine pro Kante) → Erwartungswert der Laufzeit ist Durchschnitt: 
$ E[Anzahl decreaseKey-Operationen] = O(n log \frac {m} {n}) $  → $ E[T_DijkstraBHeap] = O(m + n log log \frac {m} {n} log n) $, bei
dichten Graphen sogar lineare Laufzeit ($ m = Ω(n log n log log n)$)

*Ende der Vorlesung vom 22.10.2018*

*Präfixminimum:* Zum Beweis, dass die Anzahl decreseKey Operationen in $ O(n log \frac {m} {n}) $ laufen: Ansehen der eingehenden Kanten von v, 
 in der Reihenfolge in der sie gescannt wurden, decrese Key findet statt, wenn $ μ(u_i) + c(e_i) < min (μ(u_j) + c(e_j))$; wenn aber $ μ(u_i) ≥ μ(u_j) $,
 (Wege zu $u_i$ kürzer sind als zu $u_j$) für j < i muss das *Präfixminimum* gelten: $ c(e_i) < min_{j<i} c(e_j) $ → es findet decreaseKey bei 
 Bearbeitung von $e_i$ statt; nur Abschätzung (sonst sehr schwierig, da Reihenfolge der $u_i$ unbekannt), es kann z.B. garkein decreaseKey kommen;
 Da erstes Minimum zu insert führt gilt: $ ≤ H_k − 1 ≤ (ln k + 1) − 1 = ln k $ erwartete decreaseKeys 
 *Präfixminima einer Zufallsfolge:* Da Folge zufällig permutiert, ist jede Zahl mit der gleichen Wahrscheinlichkeit die kleinste: bei i Zahlen $ \frac{1}{i}$    
  
Ziel: Dijkstras Algorithmus schneller zu machen, dafür bereits angesehen: Fibonacci-Heaps (schlecht bei decreaseKey, im average-Case nicht so wichtig; ABER:
auch Betrachtung des Worst-Case). Daher nochmal Prioritätslisten ansehen:
                                                                                                                        
**Monotone ganzzahlige Prioritätslisten**: bei ganzzahligen Schlüsseln gut und ausnutzen, dass deleteMin immer monoton steigende Werte liefert → weitere
Verbesserung von Dikjstras Algorithmus möglich; sehr viel eingesetzt in Praxis (nicht nur Dijkstra);

**Bucket-(Priority)-Queue:** zahlen in sehr engem Bereich zu repräsentieren (Ring um settled nodes); zyklisches Array B mit Länge C+1, 
jeder Arrayeintrag enthält doppelt verkettete Liste von prioriy-queue Einträgen, alle Einträge in Bucket haben gleiche Priorität, 
Knoten mit Distanz d[v] wird in B[d[v] mod(C+1)] gespeichert  
*Initialisierung:* C+1 leere Listen, min = 0
*Operationen in Bucket Queues:*
- insert(v): v wird in B[d[v] mod(C+1)] eingefügt; Analyse: $O(1)$
- decreseKey(v): entfernen von v und neu einfügen in B[d[v] mod(C+1)] mit neuem Key; Analyse: $O(1)$
- deleteMin: anfangen bei B... (im moment das Minimum gespeichert), falls leer inkrement min, solange bis nicht leerer Bucket gefunden (sonst geht nicht weil
Queue leer) → hier Monotonizität wichtig: wenn Schlüsselwerte sinken können, müsste man "rückwärts schauen" können → extra Kosten; Analyse: im Worst-Case
muss man einmal durch die Queue also $ O(nC) $ oder $ O(n+maxPathLength) $

**Radix-Heaps**: Array von -1 bis k Buckets ($ K = 1 + ⌊log_2 C⌋ $); min ist zuletzt aus Q entfernte Distanz; für jeden Knoten v gilt 
$ d[v] ∈ [min, . . . , min +C] $; nun hat man C mögliche Schlüssel, aber nur log C mögliche Buckets → wie abbilden? → "Bitfummelei" :D 
Beispiel: C=9, binär 1001 → K=4; Vergleich binär min und binär v → suche erste Stelle an der sie sich unterscheiden. Spezialfall: bei keinem 
Unterschied in B[-1]; Unterscheiden sie sich an einer größeren Stelle als K → B[K]; sehr schnell zu berechnen mit Maschinenbefehl XOR → Unterschiede
werden zur 1, gleiche Zahlen zur 0 → suche nun höchstwertige 1 in Ergebnis (Operation *msd(a,b)* = "most significant difference")
- *deleteMin:* wenn B[-1] nicht leer, steht min dort; sonst suche erstes nicht leere Bucket, suche in der Liste dieses Buckets B[i] das min und schiebe 
es nach B[-1] → neu "aufräumen" mit msd-Formel in B[i] (nur B[i], alle anderen nicht betroffen) → return B[-1]; Analyse: $ O(K+|B[i]|)$    

*Ende der Vorlesung vom 23.10.2018*

*Vergleich Djkstra:*
- Dijkstra: $ T_{Dijkstra} = O(m · T_{decreaseKey} (n) + n · (T_{deleteMin} (n) + T_{insert} (n))) $
- mit Radix-Heaps: $ T_{DijkstraRadix} = O(m + n · (K + K)) = O(m + n · log C) $

**All-Pairs Shortest Paths**: kürzeste Pfade für alle Paare bestimmen, negative Kosten erlauben, aber keine negativen Kreise;
Verschiedene Möglichkeiten:
- n mal Bellman Ford: $ O(n²m) $  
- Knotenpotentiale: $ O(nm+n²logn) $ 

**Knotenpotentiale**: Knoten bekommen Potentiale (von "potentieller Energie" in Physik, z.B. mit Elektroauto bergab fahren hat negatives Kantengewicht 
→ kann über Potential ausgedrückt werden); Potentiale definierten *reduzierte Kosten*, Kosten finden gleiche küzeste Pfade (genaue
Definion der Potentiale egal): Durch aufsummieren der Potentiale (erst positiv, dann negativ) ergibt sich $ ̄c(e) = pot(u) + c(e) − pot(v) $ (+ und - hebt sich auf
es bleibt nurnoch erster und letzter Knoten);  
*Einfügen eines Hilfsknotens s:* von Knoten s aus Kanten zu allen Knoten einführen, die Kosten 0 haben. Anschließend [Bellman-Ford](https://de.wikipedia.org/wiki/Bellman-Ford-Algorithmus)
 zur kürzesten Pfade Berechnung; definiere $ pot (v) := μ(v) $ für alle v → nun alle Kosten *nicht negativ* und Dijkstra kann verwendet werden, warum sind alle Kanten positiv:
 - Keine negativen Kreise, pot(v) = wohldefiniert → lässt sich durch Bellman-Ford "herausschneiden"
 - Für beliebige Kanten gilt: $ μ(u) + c(e) ≥ μ(v) $  → $ c̄(e) = μ(u) + c(e) − μ(v) ≥ 0 $
*Analyse:* s hinzufügen $O(n)$; Postprocessing (zurück zu ursprünglichen Kosten): $ O(n²) $; n mal Dijkstra dominiert  → $ O(n(m + n log n)) = O()nm + n^2 log n) $  
*Distanz zu Zielknoten:* 
- Bidirektionale Suche: abwechselnd s und t, Vorwärtssuche auf G, Rückwärtssuche auf G' (= umgedrehte Kantengewichte), bei jedem Schritt kürzeste
Distanz speichern: $ d[s,t] = min(d[s,t], d_{forward} [u] + d_{backward} [u]) $; Abbruchkriterium: Suche scannt Knoten, der in anderer Richtung bereits gescannt wurde: $ d[s,t] ⇒ μ(s,t)$
- A*-Suche: Scanne Knoten möglichst nah an t, Funktion $f(v)$ schätzt $μ (v,t)$: $ pot(v) = f(v)$ und $ c̄(u,v) = c(u,v) + f(v) − f(u) $;  
 f(v) benötigt folgende Eigenschaften:
    - Konsistenz (reduzierte Kosten nicht negativ): $c(e) + f(v) ≥ f(u) ∀e = (u, v)$
    - wird t aus Q entfernt wenn f(t) = 0 und $ f(v) ≤ μ (v,t) ∀v ∈ $
    
### Anwendungen von DFS
**Tiefensuche (Depth-First-Seacht, DFS)**: [Tiefensuche](https://de.wikipedia.org/wiki/Tiefensuche) "Pfad vollständig in die Tiefe beschritten, bevor abzweigende Pfade beschritten werden"; 
Algorithmus:
{% highlight python %}
unmark all nodes; init      //dfsPos = 1 : 1...n; finishingTime = 1 : 1...n

foreach s ∈ V do
    if s is not marked then
        mark s          // make s a root and grow
        root (s)        // a new DFS-tree rooted at it;  dfsNum [s]:= dfsPos ++
        DFS (s, s)

Procedure DFS (u, v : NodeId )      // Explore v coming from u.
    foreach (v, w) ∈ E do
        if w is marked then traverseNonTreeEdge (v, w)
        else
            traverseTreeEdge (v, w)         // dfsNum [w]:= dfsPos ++
            mark w
            DFS (v, w)
            backtrack (u, v)        // return from v along the incoming edge; finishingTime[v]:= dfsPos ++

{% endhighlight %}

**Starke Zusammenhangskomponenten (SCC)**: fundamental Eigenschaft von Graphen, zur Anwendung, Analyse und Vereinfachung von Graphen benötigt. Relation ↔* besagt, u ist zusammenhängend mit
v, wenn es einen Pfad von u nach v gibt und einen Pfad von v nach u → man kann in beide Richtungen gehen, Relation ist Äquivalenzrelation, definiert Relationsklassen: jede Teilmenge ist wiederum
 stark zusammenhängend, beliebige Knoten in Teilmenge können sich gegenseitig erreichen; bei *Zusammenschrumpfen* des Graphen (=jede Zusammenhangskomponente durch neuen Knoten ersetzen, 
 entstehender Graph = *Schrumpfgraph*), dann entsteht ein *gerichteter Azyklischer Graph*

### Maximum Flows und Matchings
**Network**: [Network](https://de.wikipedia.org/wiki/Fl%C3%BCsse_und_Schnitte_in_Netzwerken#Netzwerk); directed weighted graph, source node $s$ and sink node $t$, s has no incoming edges, 
t no outgoing edges, weight $c_e$ is nonnegative capacity of edge $e$

**Flows**: [Fluss](https://de.wikipedia.org/wiki/Fl%C3%BCsse_und_Schnitte_in_Netzwerken#Fluss); Funktion f die Netzwerk einen nichtnegativen Flusswert zuweist  
Bedingungen:
- *Kapazitätskonformität:* Flusswert auf Kante ist max. so groß wie Kapazität der Kante
- *Flusserhalt:* in jeden Knoten muss genau so viel "hineinfließen" wie "herausfließen"

**Cuts**: [Schnitt](https://de.wikipedia.org/wiki/Fl%C3%BCsse_und_Schnitte_in_Netzwerken#Schnitt); echte Teilmengen S und T der Knoten in Netzwerk mit $s \in S$ und $t \in T$; 
Kapazität des Schnittes ist Summe der Kapazitäten der Kanten von S nach T

> Wert von Max-Flow = min. Kapazität eines s-t-Cuts

**Max-Flow Berechnung**: 
- *Linear:* Flussvariablen $x_e$ für jede Kannte, Fluss pro Kante hat max. Kapazität, eingehende Fluss = ausgehender Fluss, maximiere ausgehende Kanten vom Startknoten s aus
- *Augmenting Paths:* finde Pfad von s nach t, sodass Kante noch Kapazität übrig hat, sättige Kante mit kleinster übriger Kapauität, passe Kapazitäten an (erstelle *Residualgraph*) und wiederhole
 
**Residual Graph**: [Residualnetzwerk](https://de.wikipedia.org/wiki/Fl%C3%BCsse_und_Schnitte_in_Netzwerken#Residualnetzwerk); Das Residualnetzwerk mit Residualgraphen $G_f$, Fluss $f$ und 
Residualkapazitäten $u_f$ zeigt restliche Kapazitäten des Netwerks an; Residualgraph besitzt gleiche Knotenmengen wie G und besteht aus den von $f$ nicht ausgelasteten Kanten und ergänzt
Rückkanten (für $f(e) > 0$), und Kanten (wenn $f(e) < c(e)$)

**Augmenting Paths**: Pfad p von s nach t finden, sodass jede Kante $e$ nonzero residual capacity hat

**Ford Fulkerson Algorithmus**: [Algorithmus](https://de.wikipedia.org/wiki/Algorithmus_von_Ford_und_Fulkerson) zu Bestimmung des Maximalen Flusses; am 
Besten Beispiel auf Wikipedia anschauen

**Max-Flow-Min-Cut Theorem**: *max-flow = min-cut*; offensichtlich: *any-flow ≤ max-flow ≤ min-cut ≤ any-cut*; Theorem gilt
für beliebige Flussnetzwerke, wenn alle ≤ zu = werden, Beweis: (S, T) flow = (S, T) cut capacity ⇒ (S, T) flow = max-flow = min-cut

**Blocking Flows:** $f_b$ ist ein Blockierender Fluss, wenn alle Kanten $e$ von $f_b$ gleich der Kosten von $e$ sind: 
$∀ paths p = \langle s,...,t\rangle: ∃e ∈ p : f_b(e) = c(e)$

**Dinitz-Algorithmus**: [Algorithmus](https://de.wikipedia.org/wiki/Algorithmus_von_Dinic)
*DinitzMaxFlow:* berechnet MaxFlow, Rückwärtsbreitensuche von t nach s, solange
ein Pfad von s nach t existiert, füge Kante von u nach v in den Layer Graph L ein, mit der Distanz $d(v) = d(u)-1 $; ausgehend von t haben also alle Knoten
die direkt von t erreichbar sind die d = 1, t selbst 0, usw. dadruch entsteht ein layer graph (Schichtengraph), in dem alle Knoten mit dem selben 
Abstand zu t einer Schicht angehören; finde einen Blocking Flow $f_b$ in L, vergößere den Fluss f um den eben gefundenen blocking flow $f_b$  
*blockingFlow:* langer Algorithmus, besteht aus 3 Teilen: breakthrough, extend, retreat, loop solange bis return Blocking flow $f_b$ wenn v=s 
- breakthrough: δ = minimale Residualkapazität von Kanten im Graph
- extend: pushe Knoten w auf p
- retreat: delete last edge  

Analyse: $O(m+nm) = O(nm)$, d(s) erhöht sich pro Runde min. um 1, streng polynomiell: O(mn²), O(mn log n) min dynamic tree, at most 
$ 2 \sqrt{m} $BF computations $O((m+n)\sqrt{m}$

*Unit Capacity:* min{indegree(v), outdegree(v)} = 1

*Matching:* ungerichteter Graph G=(V,E) mit M ⊆ E, gdw. (V,M) max grad ≤ 1; M ist maximal wenn $\nexists e ∈ E \ M : M ∪ {e} $ ist matching;
M hat maximale Kardinalität $\nexists matching M': \|M'\| > \|M\|$

**Preflow**: Fluss für den Eingangskanten größer sein dürfen als Ausgangskanten: $ excess(v) := inflow - outflow ≥ 0 $; Knoten (nicht s,t) ist
*aktiv* wenn excess > 0

**Preflow-Push Algorithms**: Familie von Algorithmen; maintain approximation d(v) of BFS distance from v to t in $G_f$
- Invariante 1: $d(t) = 0$
- Invariante 2: $d(s) = n$
- Invariante 3: no steep edges $ ∀(v, w) ∈ E_f: d(v) ≤ d(w) + 1 $  

*Edge Directions:*
- steep: d(w) < d(v) − 1
- downwards: d(w) < d(v)
- horizontal: d(w) = d(v)
- upwards: d(w) > d(v)

*Analyse:* $O(n²m)$

*Ende Vorlesung vom 13.11.2018**

**FIFO Preflow push**: Wie kann Anzahl nicht-saturierender Pushes verringert werden? → FIFO besser als Stack  → $O(n³)$

> Grundsätzlich gilt : $n ≤ m$ mit Knoten n und Kanten m, da ansonsten Knoten isoliert wären und für den Fluss nicht betrachtet werden müssten.

**Highest Level Preflow Push**: verbessert Dinitz weiter: Knoten, die möglichst weit weg sind werden bearbeitet, "Fluss sammelt sich unten an, bevor man ihn
wegschiebt", select active nodes, that maximize $d(v)$, with bucket priority queue, not monotone, relabels pay for scan operations → highest level preflow
push finds a max flow in $O(n²\sqrt{n})$  
still better: with aggressive local relabeling and global relabelling and special treatment of nodes with $d(v) ≥ n$ → no node can connect to t across an empty
level

### Randomisierte Algorithmen

> **Randomisierte Algorithmen** verwenden Zufall(sbits) zur Beschleunigung/Vereinfachung von Algorithmen

**Las Vegas Algorithmen**: Ergebnis immer korrekt, Laufzeit ist Zufallsvariable (z.B. quicksort, hashing)

**Monte Carlo Algorithmen**: Ergebnis mit bestimmer Wahrscheinlichkeit p inkorrekt, k-fache Wiederholungen machen Fehlerwahrscheinlichkeit
exponentiell klein $p^k$

**Permutationseigenschaft**: Sortiertheit

**Sortieren - Ergebnisüberprüfung (Checking)**: Überprüfung ob Vektor1 eine Permutation von Vektor' ist, durch Polynom berechnen  (Differenz der Werte 0) wenn
Vektoren permutiert; Polynom q kann höchstens n Nullstellen haben, Auswertung an zufälliger Stelle $x in F$, $p(q!= 0 und q(x) = 0) ≤ \frac{n}{\|F\|}$
→ Körper F muss möglichst groß gewählt werden; Monte-Carlo → Verkleinern von p durch mehrfache Durchführung

*Ende Vorlesung vom 19.11.2018**



## Übung
### Übung 1
**Amortisierte Analyse:** [Amortisierte Laufzeitanalyse](https://de.wikipedia.org/wiki/Amortisierte_Laufzeitanalyse) wurde in Algorithmen I behandelt. Im
Gegensatz zur allgemeinen Laufzeitanalyse wird der Worst-Case in mehreren Durchläufen des Algorithmuses analysiert. Ziel ist es die durchschnittliche 
obere Schranke im Worst-Case zu bestimmen, da in z.B. teure Operationen nur selten auftreten.

**Kontomethode:** [Account-Methode](https://de.wikipedia.org/wiki/Account-Methode): Verfahrensweise der armotisierten Laufzeitanalyse; wichtig: bei 
Tokenerzeugung darf es keine Zyklen geben!

**Kontomethode mit Fibonacci-Heaps:** 
- *Insert:* Erzeuge neuen Baum mit Element zum einfügen, füge ihn den Wurzeln hinzu, ggf. min Pointer anpassen; erstelle Union-Token 
(je Wurzel ein Union-Token); insert kostet konstante Zeit
- *deleteMin:* siehe Übungsfolie 1

### Übung 2
**Spezielle Priority Queues**: monoton, ganzzahlig; Bedingungen: 
- positive, ganzzahlige Schlüssel
- neue/geänderte Schlüssel ≥ minmale Schlüssel
- maximales Schllüsselinkrement C (bezogen auf min. Schlüssel)

**Bucket Queues**: zirkuläre Liste aus Buckets, Variable min, init min = 0; C Schlüsselinkremente → #Buckets |B| = C + 1
- *insert:* Einfügen in B[key mod(C+1)]; Laufzeit: $O(1)$
- *deleteMin:* Entfernen aus B[min mod(C+1)] oder aus erstem nicht-leeren Folgebucket; Laufzeit: $O(C)$
- *decreaseKey:* Verschieben von altem in neues Bucket; Laufzeit $O(1)$   
→ Abstand min-Element und max-Element maximal C → ansonsten geht einfürgen nicht; vgl. *Spezielle Priority Queues*-Bedingungen; Problem sonst, dass man kleinste Element finden, obwohl noch
kleineres Element in Queue vorhanden

**Radix Heaps**:  Liste aus Buckets, Variable min; C Schlüsselinkremente →  #Buckets $ |B| = K + 2 = (\lfloor log C \rfloor)  + 1 ) + 2 $ z.B. mit C = 9 → 6 Buckets; maximal können pro Bucket[i]
$max(1,2^i)$ verschiedene Werte in Bucket stehen
- *Bucket[i]:* i = min(msd(min, key), K)
- *Bucket[k]:* Overflow Bucket 
- *Bucket[-1]:* min  
Vorgehen:
- *insert:* Einfügen in Bucket B [min( msd(min, key), K)]; Laufzeit: $O(log C)$ → da wenn min entfernt wird, alle Elemente verschoben werden müssen, erstellen nach Kontomethode bei insert
bereits genug Token um verschieben zu "bezahlen"
- *deleteMin:* min = minimaler Schlüssel (aus Bucket i), Elemente aus Bucket i verschieben, Entfernen aus Bucket B [− 1 ]; Laufzeit: $O(log C)$
- *decreaseKey:* Verschieben von altem in neues Bucket; Laufzeit $O(1)$  
→ Warum Formel [min( msd(min, key), K)]? → bei min Änderung potentiell alle Buckets zu verändern → schlechte Laufzeit und man muss nicht alle Elemente verschieben, d.h. armotisierte 
Laufzeit Erklärung funktioniert nicht

**Average Case Analyse für Minimale-Spannbäume (MST)**: Minimaler Spannbaum ist Baum aus Graph, der nur Kanten aus Graph verwendet, alle Knoten miteinander verbindet und Kanten sollen
minimales Gewicht haben; Jarnik-Prim Algorithmus:
- Wähle beliebigen Startknoten s
- Füre Knoten v zu MST mit kleinstem Abstand d[v]  
Analyse: m Kanten, mit zufällig geordneten Gewichten → wie oft wird decreaseKey im Durchschnitt ausgeführt? → Nachbarn durchnummerieren, in Reihenfolge in der sie zu MST hinzugefügt
wird, wann muss Kante relaxiert werden → Distanz an v ist größer als Kante die sich nun ergeben hat → DecreaseKey wird dann ausgeführt, wenn d[v] > d[über neu hinzugefügte Kanten]  
Wie oft passiert das? → $ E( M_k ) = H_k $ → $ O ( n ln \frac{m}{n}) $

### Übung 3
**Dijkstras Algorithmus**: nicht-negative Kantengewichte, vorläufige Distanzen in Priority Queue d, unterscheidet zwischen
erreichten Knoten und gescannten Knoten

**Bidirektionale Suche**: Beschleunigung, zweimal Dijkstra ausführen (Vorwärtssuche s → t auf G, Rückwärtssuche von t → s auf $G^r$ mit umgekehrten
 Kanten); Vorgehen: einen Schritt Vorwärtssuche, einen Schritt Rückwärtssuche, Abbruch wenn ein Knoten von beiden Suchen gescannt (nicht nur erreicht); 

**A\*-Suche**: Dijkstra in Richtung t gesteuert, Potentialfunktion pot ordnet jedem Knoten reele Zahl zu; Vorgehen entwerder reduzieren der
Kantengewichte $$ \bar{c}(u, v) := c(u, v) + pot(v) − pot(u)$ **oder** modifizieren der Schlüssel $\bar{d}[v] : = d[v] + pot(v)$; gültige Potentialfunktion:
- untere Schranke für Distanz zum Ziel t: $ pot(u) ≤ \mu(u,t) $
- nicht-negative reduzierte Kantengewichte: $ \bar{c}(u, v) := c(u, v) + pot(v) − pot(u) ≥ 0 $
- t hat potential 0
Woher Potentialfunktionen? Sollen Schätzung für tatsächliche Distanz sein, z.B. Manhattan-Distanz, Euklidischer Abstand
A*-Suchen Möglichkeiten:
- Suche mit reduzierten Kantengewichten
- Suche mit geänderten Schlüsseln in Priority Queue
- Suche mit Landmarks: Kompormiss, berechne Potentiale für einige Knoten, bei konkreter Anfrage wähle Landmark hinter dem Ziel, Landmarks immer
korrekt dank Dreicksungleichung (oben definierte Potentialfunktionseigenschaften müssen gegeben sein), Algorithmus kann langsam sein (z.B. Suche
in  falscher Richtung)

**Starke Zusammenhangskomponenten**: 
Nomenklatur:
- *oNodes:* Stack, offene Knoten
- *oReps:* Stack, Repräsentaten der offenen Komponenten
- *aktive Knoten:* Knoten die während dfs markiert, aber noch nicht finished, kein Backtracking
- *offene SCCs:* enthält nur aktive Knoten und keine abgeschlossenen Knoten
- *abgeschlossene SCCs:* alle Knoten finished (markiert), backtracking gemacht
- *Repräsentanten der SCC:* Knoten mit kleinster dfsNumber (Reihenfolge der Knotenabarbeitung bei Tiefensuche)  in SCC   

Invarianten:
- *Invariante 1:* Keine Kanten von geschlossenen in offene Komponenten.
- *Invariante 2:* Offene Komponenten liegen auf Pfad.
- *Invariante 3:* Repräsentanten partitionieren offene Komponenten bzgl. dfsNum.

**Floyd-Warshall Algorithmus**: kubischer Algorithmus, berechnet transitive Hülle

**Floyd-Warshall Algorithmus und SCCs**: Transitive Hülle einer SCC ist ein vollständiger Graph, betrachte Schrumpfgraph, 
deutlich schneller: #SCC³ < n, Eintrag pro SCC

### Übung 4
**Residualgraph**: Verwalten von Restkapazitäten, Modellierung und Erkennung von Gegenflüssen, keine 0 Gewicht Kanten, Flüsse
über Kanten und Gegenkanten erlaubt
- *Restkapazität:* $c^f(e) = c(e) − f(e)$
- *Fluss:*  $c^f(e^{rev}) = f(e)$

**Dinitz Distanz Label**: geben Distanz im Residualgraphen zur Senke t an, Rückwärtsgerichtete Breitensuche → Layered Graph

**Dinitz Blocking FLow**: “Auf jedem Weg durch den Graphen mindestens  eine Kante bis zur maximalen Kapazität ausgelastet ist”,
Berechnung auf Schichtgraph, kein Rückfluss möglich; Berechnung basiert auf Tiefensuche von s aus:
- extend: gehe einen Knoten näher ans Ziel (Schichtgraph)
- retreat: Sackgasse gefunden, gehe zurück, lösche Kante
- breakthrough: Tiefensuche hat Senke erreicht, lösche saturierte Kanten
*Analyse*: $O(nm)$