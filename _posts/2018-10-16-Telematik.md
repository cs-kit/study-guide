---
layout: post
title:  "Telematik"
ref: telematik
date:   2018-10-16 07:00:00 +0100
categories: master
excerpt: Die Vorlesung behandelt Protokolle, Architekturen, sowie Verfahren und Algorithmen, die u.a. im Internet für die Wegewahl und für das Zustandekommen einer zuverlässigen Ende-zu-Ende-Verbindung zum Einsatz kommen. Neben verschiedenen Medienzuteilungsverfahren in lokalen Netzen werden auch weitere Kommunikationssysteme, wie z.B. das leitungsvermittelte ISDN behandelt. Die Teilnehmer sollten ebenfalls verstanden haben, welche Möglichkeiten zur Verwaltung und Administration von Netzen zur Verfügung stehen.
lang: de
tags: lecture
---
<div style="background-color: #EAEFF4; border: 1px solid #b5aeb1; border-radius: 3px;  padding: 10px; margin-right: 10px">
    <strong>Vorlesung:</strong> <a href="https://campus.studium.kit.edu/ev/G6hOdkEyRGaMJ98tdLHvGw">Telematik</a>, Stammmodul, 6 ECTS <br>
    <strong>Dozent:</strong> Prof. Dr. Zitterbart <br>
   <strong>ILIAS:</strong> <a href="https://ilias.studium.kit.edu/goto_produktiv_crs_880989.html">https://ilias.studium.kit.edu/goto_produktiv_crs_880989.html</a> <br>   
   <strong>Vorlesungswebsite:</strong> <a href="http://telematics.tm.kit.edu/tm.php">http://telematics.tm.kit.edu/tm.php</a> <br>   
   <strong>Videos:</strong> <a href="">TODO</a> <br>   
   <strong>Klausur:</strong> 21.2.2019 11:00 - 12:30 Uhr <br>
   <strong>Einordnung:</strong> Vertiefungsfach "Telematik", Profil "Datenintensives Rechnen" <br>
</div>

## Organisatorisches

### Vorlesungen
- **17.10.2018**: Organisatorisches und Foliensatz 1-1 bis 2-20
- **18.10.2018**: Foliensatz 2-20 bis 2-63

### Material
Das Material der Vorlesung besteht aus:  
- **Folien**: Folien werden im ILIAS hochgeladen, Passwort wurde in der Vorlesung mitgeteilt
- **Übungsblättern**  
Inhaltlich werden Grundlagen der Rechnernetze vorausgesetzt, Inhaltlich geht es um Technologien des Internets;
Kein spezielles Bucht auf dem VL aufbaut, da gute Standardwerke. Folien auf Englisch um Inhalt einheitlich zu
halten; VL wird durch Pingo, Kahoot und Homework interaktiv gestaltet; 
Ende der Vorlesung voraussichtlich bereits ca. 16./17.1.2019

### Übungen
Homework wird jeweils in der zweiten Hälfte der VL besprochen, das Blatt dazu gibt es in der Regele "bisschen" früher;
teilweise mit Programmieraufgaben, keine komplette Musterlösung nur Ergebnis.

### Klausur
Klausur ist schriftlich; am 21.2.2019 von 11:00 bis 12:30; Fragen in Deutsch, Antworten auf Deutsch und Englisch möglich

## Vorlesungsinhalt
### Introduction
**Internet:** largest system build by mankind; Critical Infrastructure e.g. critical infrastructures (water, electricity) depend on the internet;  
rapid development (less than 50 years):
- early 60s: vision of networked computers
- 1969: first packet-switched network with four nodes
- early 70s: architectural concept for interconnection (TCP, IP)
- since 90s: commercialization
- since around 2005: software-defined networks
- today: ubiquituous, critical infrastructure
 
**Internet of Things (Robots):** Sensors collecting data about us and environment (Eyes and Ears); Processors, Storage and Cloud processing data (Brain); 
Actuators affecting environment (Hands and Feet);

### Router
#### Basic Functionalities
**Intermediate Systems**: Forward data from input ports to output ports; Forwarding task of data path; may operate on different layers:
- *Layer 1* (Physical Layer, Bitübertragungsschicht) - *Hubs* (schicken an alle Anschlussports)
- *Layer 2* (Data Link Layer, Sicherungsschicht) - *Bridges* (entscheiden anhand MAC-Adressen)
- *Layer 3* (Network Layer, Vermittlungsschicht) - *Routers* (entscheiden anhand IP-Adressen)

**Routing**: determines path that packet follows; part of control path; requires routing algorithms and protocols;

**Forwarding table**: enthält mindestens pro Eintrag Netzadresse/Subnetzmaske (bzw. Prefixlänge), next hop, Metrik (Gewichtung, Präferenz des Weges);
Informationen welcher Value im Paket, welchem Link entspricht;

**Router**: main task: lookup in forwading table, forwart data from input to output ports; goals: forwarding in line speed (Geschw. des Links soll eingehalten werden), short queues
(da sonst hohe Latenz -> schlecht bei z.B. VoIP kommt es sonst zu Verzögerungen), small tables (da sonst Speicher teuer)

**Forwarding**: part of data path; Forwarding table part of control path;  
Incoming data ->  *IP-Processing*: check Headers of IP Packet (version number, valid header length, checksum); check TTL (decrement TTL); recalculate checksum) 
-> *Lookup* (determine output port for packet, Fragmentation (?), Handle IP options (?)) -> *Classification* (Priorization, differentiated treatment of packets) -> (Queue) -> Outgoing Data

#### Challenge: Line Speed
bandwidth demand increases (32% 2015-2016); 250 Tbit/s in 2016 -> Link capacity has to increase  
memory is **not** keeping up with Moore's law; network bandwidth doubles every 17-18 months; DRAM/CPU bandwidth doubles every 26-27 months;
Router needs to keep up with line-speed for **all packet sizes**

*Example:* 1 Gbit/s line-speed, 1500 byte packets: $ t_{packet} = \frac  {12000 bit}{10⁹ \frac {bit}{s}} = 12 \mu s $;
 higher requirements for smaller packets; forwarding decision is overhead for every single packet  

Regarding TCP two types of segments:
- TCP segments that transport data e.b. 1500 bytes (Ethernet)
- TCP that are purely acknowledgements (min. 40 byte)
-> e.g only 3,2ns for 40 byte in a 100 Gbit/s environment  
Problem: Small packets are quite common, 50% of IPv4 packets smaller than 100 bytes

**Router Types**:
- *Core router:* used by service provider; large amound of aggregated traffic; high speed, reliability is essential (fast lookup, redundancy to increade reliability); 
cost secondary issue (1-3 Mio. € per router) 
- *Enterprise router:* connect end systems in companies, universities,...; provide connectivity to many end systems; support VLANs, firewalls,...; low cost per post, large number
of ports, ease of maintenance
- *Edge router (access router):* at *edge* of service provider; connectivity for customer (home, small business); support PPTP, IPsec, VPNs

#### Forwarding Table Lookup
**Prefix**: Identifies block of addresses; continous blocks of addresses per output port good 
-> does not require a separate entry for each IP address (Scalability)

*Ende Vorlesung vom 17.10.2018*

**Longest Prefix Matching**: Multiple prefixes matching in the forwarding table to given destination? Select most specific prefix 
(highest number of matching bits) -> *longest prefix matching*; Challenge: Lookup in Line-Speed (can be long because TTL is decreased -> checksum recalculated),
 Different approaches in software:

**Efficient Data Structures for Longest Prefix Matching**  
Requirements: fast lookup; low memory; fast updates (route changes occur frequently, data structure should support >> 100 updates/second)  
Variables: N = number of prefixes; W = length of prefix (W=32 for IPv4); k = length of stride

**Binary Trie**: Trie = tree-based data structure to store and search prefix information; Idea: bits in prefix to tell algorithm what branch to take; (vgl. Abb. 02-27)
- *Lookup speed* $ O(W) $, maximum of one node per bit in prefix 
- *Memory requirement* $ O(N*W), prefixes stored as linked list starting from root, every prefix can have upt do W nodes
- *Updates* $ O(W) $  
Lookup speed with memory access time $ 10ns $ for 100 byte packets $ 2,5 Gbit/s $ -> Optimization: Path Compression, Multibit Tries,...

**Path Compression**: one-child node waste memory -> nothing stored, not required for branch decision -> eliminate sequences -> path compression; additional information 
of next examined index; (vgl. Abb. 02-31)
- *Lookup speed* $ O(W) $, with no one-child nodes, number of nodes to search = length of prefix
- *Memory requirement* $ O(N) $, N entries for leaf nodes, N-1 for internal nodes -> max 2N-1 entries
- *Updates* $ O(W) $  

**Multibit Trie**: match multiple bits at same time; reduce number of memory accesses; fixed strides multibit tries (strides = number of bits) 
have same strides on each level, different level can have different strides; Problem: prefixes do not always match with strides -> expand prefix to next available stride
(0* expands to 01* and 00*); choose prefix that is most specific; (vgl. Abb. 02-36)
- *Lookup speed* $ O(W/k) $
- *Memory requirement* $ O(2^k NW/k) $, max path length W/k, path composed of one level subtrees with $ 2^k $
- *Updates* $ O(W/k + 2^k ) $, search time O(W/k), modification $ 2^k-1 $ entries

**Hash Tables**: goal: improve lookup speed -> $ O(1) $, BUT: longest prefix match only with hash table does **not** work; use additional hash table instead (stores result of trie lookup);
check for each IP packet if entry in hash table exists if not -> lookup; goof if addresses show "locality" characteristics

**Longest Prefix Matching in Hardware**  
Idea: Read information with single memory access, use destination IP as RAM address; waste of memory; required memor size grows expoentially with size of addresses;  

**Content-Addressable Memory (CAM)**: *RAM:* address -> data; *CAM:* data -> address (search all stored entries in single clock cycle, 
very fast address lookups with address as search input); compare search input data with stored entries, priority encoder searches "first" match
- *Binary CAM:* static lookups
- *Ternary CAM:* with *Don't Care* State; allows longest prefix matching, prefixes stored sorted by length; very fast lookups; BUT: hight energy demands
(parallelization, every core required for every lookup), high cost/ low density, requires strict ordering -> severe scalability limitations

#### Router Architecture
**Generic Router Architecture**
- *Network Interfaces*: Access to attached networks; Layer 1, Layer 2 functionalities; basic functions of IP
- *Routing Processor*: Routing protocol, management functionality
- *Switch fabric*: "Backplane", realizes internal forwarding  
Conflicting Design goals: high efficiency (line speed, low delay) vs. low cost; Blocking (e.g. packets arriving at the same time, going to same port)

**Frage: TODO, irgendwas mit Blocking???** Schicht 3. Schicht 2 nicht, da IP-Paket bereits aus Schicht 2 "herausgeholt"; Indirekt aber Schicht 4, weil darin Schicht 3 Paket transportiert
**Frage: Gibt es bei Verlust eine Sendewiederholung auf Schicht 4?** Ja & Nein. Abhängig von Protokoll. TCP wird wiederholt, UDP nicht.

**Blocking**: Packets are blocking each other, prevent blocking:
- *Overprovisioning:* circuits in switch fabric faster than input ports
- *Buffering:* queue packets until resources available (network interface or switch fabric), possible buffer places (N input, output ports, storage M, speedup S, cycle time Z):   
 input buffer: FIFO at input; requirements S=1, Z= 1/2; Head-of-Line blocking (packet waiting but packet behind could be served); throughput N=2 -> 75%, N -> ∞ -> 58,58%
 output buffer: FIFO at output; requirements: S=N, Z=1/(N+1); output buffer accepting packets N*S, input buffer at least one packet; throughput max 100%, usually 80-85%  
 distributed buffer: conflict resolution inside switch fabric, FIFO buffer per crosspoint; requirements: matrix structure, S=1, Z=1/2; no head-of-line blocking, higher memory than input/output   
 central: shared buffer for conflict resolution; Requirements: Z=1/2N, address memory for information of packets, control memory for parallelization
- *Backpressure:* signal overlaod back to input ports, input ports can reduce load
- *Parallel switch fabrics:* parallel transport of multiple packets to output ports, higher access sped required at output ports

*Ende Vorlesung vom 18.10.2018*


## Übung




