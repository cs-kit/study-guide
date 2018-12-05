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
   <strong>Klausur:</strong> 21.2.2019 11:00 - 12:30 Uhr <br>
   <strong>Einordnung:</strong> Vertiefungsfach "Telematik", Profil "Datenintensives Rechnen" <br>
</div>

## Organisatorisches

### Vorlesungen
- **17.10.2018**: Organisatorisches und Foliensatz 1-1 bis 2-20
- **18.10.2018**: Foliensatz 2-20 bis 2-63
- **24.10.2018**: Foliensatz 2-64 bis 3-12 und Besprechung Homework 1
- **25.10.2018**: Foliensatz 3-13 bis 3-53
- **31.10.2018**: Foliensatz 3-54 bis 3-100
- **07.11.2018**: Foliensatz 3-101 bis 3-135
- **08.11.2018**: Foliensatz 3-135 bis 3-154, 4-1 bis 4-16
- **14.11.2018**: Foliensatz 4-17 bis 4-77, 5-1 bis 5-28
- **15.11.2018**: Foliensatz 5-29 bis 5-103
- **21.11.2018**: Foliensatz 5-104 bis 5-165
- **22.11.2018**: Foliensatz 5-166 bis 5-213; 6-1 bis 6-34
- **22.11.2018**: Foliensatz 7-1 bis 7-45

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
(da sonst hohe Latenz → schlecht bei z.B. VoIP kommt es sonst zu Verzögerungen), small tables (da sonst Speicher teuer)

**Forwarding**: part of data path; Forwarding table part of control path;  
Incoming data →  *IP-Processing*: check Headers of IP Packet (version number, valid header length, checksum); check TTL (decrement TTL); recalculate checksum)
→ *Lookup* (determine output port for packet, Fragmentation (?), Handle IP options (?)) → *Classification* (Priorization, differentiated treatment of packets) → (Queue) → Outgoing Data

#### Challenge: Line Speed
bandwidth demand increases (32% 2015-2016); 250 Tbit/s in 2016 → Link capacity has to increase  
memory is **not** keeping up with Moore's law; network bandwidth doubles every 17-18 months; DRAM/CPU bandwidth doubles every 26-27 months;
Router needs to keep up with line-speed for **all packet sizes**

*Example:* 1 Gbit/s line-speed, 1500 byte packets: $ t_{packet} = \frac  {12000 bit}{10⁹ \frac {bit}{s}} = 12 \mu s $;
 higher requirements for smaller packets; forwarding decision is overhead for every single packet  

Regarding TCP two types of segments:
- TCP segments that transport data e.b. 1500 bytes (Ethernet)
- TCP that are purely acknowledgements (min. 40 byte)
→ e.g only 3,2ns for 40 byte in a 100 Gbit/s environment  
Problem: Small packets are quite common, 50% of IPv4 packets smaller than 100 bytes

**Router Types**:
- *Core router:* used by service provider; large amound of aggregated traffic; high speed, reliability is essential (fast lookup, redundancy to increade reliability);
cost secondary issue (1-3 Mio. € per router)
- *Enterprise router:* connect end systems in companies, universities,...; provide connectivity to many end systems; support VLANs, firewalls,...; low cost per post, large number
of ports, ease of maintenance
- *Edge router (access router):* at *edge* of service provider; connectivity for customer (home, small business); support PPTP, IPsec, VPNs

#### Forwarding Table Lookup
**Prefix**: Identifies block of addresses; continous blocks of addresses per output port good
→ does not require a separate entry for each IP address (Scalability)

*Ende Vorlesung vom 17.10.2018*

**Longest Prefix Matching**: Multiple prefixes matching in the forwarding table to given destination? Select most specific prefix
(highest number of matching bits) → *longest prefix matching*; Challenge: Lookup in Line-Speed (can be long because TTL is decreased → checksum recalculated),
 Different approaches in software:

**Efficient Data Structures for Longest Prefix Matching**  
Requirements: fast lookup; low memory; fast updates (route changes occur frequently, data structure should support >> 100 updates/second)  
Variables: N = number of prefixes; W = length of prefix (W=32 for IPv4); k = length of stride

**Binary Trie**: Trie = tree-based data structure to store and search prefix information; Idea: bits in prefix to tell algorithm what branch to take; (vgl. Abb. 02-27)
- *Lookup speed* $ O(W) $, maximum of one node per bit in prefix
- *Memory requirement* $ O(N*W) $, prefixes stored as linked list starting from root, every prefix can have upt do W nodes
- *Updates* $ O(W) $  
Lookup speed with memory access time $ 10ns $ for 100 byte packets $ 2,5 Gbit/s $ → Optimization: Path Compression, Multibit Tries,...

**Path Compression**: one-child node waste memory → nothing stored, not required for branch decision → eliminate sequences → path compression; additional information
of next examined index; (vgl. Abb. 02-31)
- *Lookup speed* $ O(W) $, with no one-child nodes, number of nodes to search = length of prefix
- *Memory requirement* $ O(N) $, N entries for leaf nodes, N-1 for internal nodes → max 2N-1 entries
- *Updates* $ O(W) $  

**Multibit Trie**: match multiple bits at same time; reduce number of memory accesses; fixed strides multibit tries (strides = number of bits)
have same strides on each level, different level can have different strides; Problem: prefixes do not always match with strides → expand prefix to next available stride
(0* expands to 01* and 00*); choose prefix that is most specific; (vgl. Abb. 02-36)
- *Lookup speed* $ O(W/k) $
- *Memory requirement* $ O(2^k NW/k) $, max path length W/k, path composed of one level subtrees with $ 2^k $
- *Updates* $ O(W/k + 2^k ) $, search time $ O(W/k) $, modification $ 2^{k-1} $ entries

**Hash Tables**: goal: improve lookup speed → $ O(1) $, BUT: longest prefix match only with hash table does **not** work; use additional hash table instead (stores result of trie lookup);
check for each IP packet if entry in hash table exists if not → lookup; goof if addresses show "locality" characteristics

**Longest Prefix Matching in Hardware**  
Idea: Read information with single memory access, use destination IP as RAM address; waste of memory; required memor size grows expoentially with size of addresses;  

**Content-Addressable Memory (CAM)**: *RAM:* address → data; *CAM:* data → address (search all stored entries in single clock cycle,
very fast address lookups with address as search input); compare search input data with stored entries, priority encoder searches "first" match
- *Binary CAM:* static lookups
- *Ternary CAM:* with *Don't Care* State; allows longest prefix matching, prefixes stored sorted by length; very fast lookups; BUT: hight energy demands
(parallelization, every core required for every lookup), high cost/ low density, requires strict ordering → severe scalability limitations

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
 input buffer: FIFO at input; requirements S=1, Z= 1/2; Head-of-Line blocking (packet waiting but packet behind could be served); throughput N=2 → 75%, N → ∞ → 58,58%
 output buffer: FIFO at output; requirements: S=N, Z=1/(N+1); output buffer accepting packets N*S, input buffer at least one packet; throughput max 100%, usually 80-85%  
 distributed buffer: conflict resolution inside switch fabric, FIFO buffer per crosspoint; requirements: matrix structure, S=1, Z=1/2; no head-of-line blocking, higher memory than input/output   
 central: shared buffer for conflict resolution; Requirements: Z=1/2N, address memory for information of packets, control memory for parallelization
- *Backpressure:* signal overlaod back to input ports, input ports can reduce load
- *Parallel switch fabrics:* parallel transport of multiple packets to output ports, higher access sped required at output ports

*Ende Vorlesung vom 18.10.2018*

**Switch Fabric**: Basic Structures
- *Shared memory*
- *Bus/ring structure:* conflict-free access through time-division multiplexing, transmission capacity bus/ring (at least sum of all input ports),
easy support for multicast/broadcast, extensions limited, usually los number (approx. 16)
- *Crossbar:* each input connected to each output, n inputs, n outputs n² crosspoints; partial parallel switching possible, multiple packets for same output
→ Blocking → Buffering required; especially efficient with same sized packets
- *Multi-level switching networks:* switching states can set up multilevel connections (0 → $O_1$, 1 → $O_2$); Less wiring effort than crossbar, each input
connected with each output, not all connections at same time → internal blocking possible

### Internet Routing
#### Basics
**Control Path (Control Plane)**: Routing protocols, exchange of routing messages for route calculation

**Data Path (Data Plane)**: Lookup, Forwarding of IP packets (Layer 3)

**Routing Table**: Generated by routing protocol; Entries: mapping of dest. IP prefixes to next hop (IP address);
optimized for particular routing algorithm; Implemented in software → Performance not critical

**Forwarding Table**: Used for packet forwarding; Entries:  Mapping of IP prefixes to outgoing ports (interface ID, MAC address);
optimized for rlongest prefix matching; Uses (partially) dedicated hardware → Performance critical (Lookup in line speed)

> Anmerkung aus Vorlesung: Lookup findet in Schicht 3 statt, da es sich um IP Pakete handelt; Routing Protokolle liegen über SChicht

**Routing metric (cost, weight)**: used by router for routing decision; applied to link or overall path; e.g. Utilization, latency, data rate, number of hops
- *hop count*: distance between source and destination → number of hops on the way, limited range: 1-15 (16 = infinity); schlechte Maß, da Qualität der hops
(= Geschwindigkeit der Links), nicht betrachtet

**Routing policy**: routing decision based on policies; defined by networrk operator/owner; e.g. prefered routes over specific neighbors

**Distributed Adaptive Routing**: most commonly used; instance of protocol per router, exchange of routing information via routing messages; path
adaptions according to current network situation; *Path computation:* Network modeled as graph, Routers are nodes; Links are edges with metric

#### Autonomous Systems
**Autonomous System (AS)**: internet divided into AS; indetification over unique number (Autonomous Systems Number - ASN: earlier 16 bit, now 32 bit); avg.
path length 3,83;    
Properties: appears as single entity to the outside, uniform routing policy, typically uniform IGP;   
Advantages:
- *Operator autonomy:* separated administrative domains; increasing overhead with size of network
- *Scalability of routing protocols:* Routing Protocol *inside* AS, Routing protocol *between* ASes; choice of IGP, Hiding internal structure  

IANA (Internet Assigned Numbers Authority) delegates allocation to RIR (Regional Internet Registries); around 45.000 issued ASNs  

Classification of AS based on role:
- *Stub AS:* small organizations, mostly only regional, connected with exactly one provider, no transit traffic
- *Multihomed AS:* large enterprises, connected to several providers (→ Reliability), no transit traffic
- *Transit AS:* Provider, often global scope,

Classification based on "economic position/influence", no official mapping!
- *Tier 1:* (=Transit AS), do not buy transit, sell transit, peering with other Tier1s, e.g. Telekom
- *Tier 2:* big national and interregional AS, downstream of Tier1 ASes, sell transit to other ASes, employ peering, e.g. Vodafone
- *Tier 3:* small (regional) AS, downstream of Tier2 providers, do not sell to other ASes, sell to end customers, employ peering, e.g. Congstar

How ensure mutual reachability? Cooperation among autonomous systems?

**Transit**: Purchased connectivity, traffic exchange in both directions, only downstream AS must pay, Transit AS offers transit
- *Upstream:* provider (seller) of transit
- *Downstream:* customer (buyer)

Options for Connectivity: (Stub = Zugang)
- *Stub AS:* ein Zugang zum AS (und Rest des Internets), bei Ausfall keine Verbindung zum Internet
- *Multihomed stub AS:* zwei Zugänge, Umstieg bei Linkausfall
- *Multihomed AS:* zwei Transit Verbindungen

**Peering**: Direct connection, typically between ASes of same tier;
- *Private Peering:* no costs for traffic exchange; mostly only data traffic between privately peered AS, no transit in other ASes
→ Connectivity is not achieved; Advantages: benefits for both ASes (save transit costs), shorter data paths; Problems: direct connection complicated
(geographical distance), Full mesh of n ASes more than 1 billion connections!
- *Public Peering:* through Internet Exchange Points (IXP, central public authority for interconnection): neutral traffic forwarding on layer 2, monthly
fixed charges per port → expensive infrastructure, Different Peering policies:
    - Open
    - Selective: specific terms and conditions
    - Restrictive: no new peering relationships
    - No Peering

**Content Delivery Provider**: Goal: fast content delivery → locations close to Tier1 peering points

**Content delivery networt (CDN)**: connected over own routers, world wide network with own AS number, points of presence (PoP) spread over world
(access and core routers, customer connection through access router), load balancing at access router, low latencies

**Routing Protocols**:
- *Interior Gateway Protocol (IGP):* Routing inside an autonomous system, not visible to the outsides, different IGPs possible, metric-based
    - *Routing Information Protocol (RIP):* commonly used, distance vector algorithm
    - *Open Shortes Path First (OSPF):* commonly used, link state algorithm
    - *Intra-Domain Intermediate System to Intermediate System Routing Protocol (IS-IS):* ISO Standard, link state algorithm
    - *Enhanced Interior Gateway Routing Protocol (EIGRP):* CISCO, link state algorithm, based on RIP
- *Exterior Gateway Protocol (EGP):* Routing between autonomous systems; EGPs müssen einheitlich sein; policy-based; im Einsatz: *Border Gateway Protocol*

#### Roting Information Protocol (RIP)
**Routing Information Protocol (RIP)**: IGP, one of first routing protocols, very simple, little configuration; oberhalb von IP; application process
implements RIP, manages forwarding table; RIP sent over UDP → *not reliable*  
*Routing Messages:* exchange messages over UDP
- *Request Message:* complete routing table (partly)
- *Response Message:* response to query,
    - Regular Routing update: broadcasted every 30sec, not synchronized, entire routing table to neighbors, no refresh for at least 180s
    → in case UDP messages are lost, retry, hop count 16 → route is invalidated;  
    - Triggered Update: because of route change, not complete table; rate limitation to reduce load, randomized between 1 and 5 seconds, changes during period
    accumulated and sent in one message

#### OSPF: Open Shortest Path First
**Open Shortest Path First (OSPF)**: Interor Gateway Protocl, based on Link State, each router
needs to learn complete topology of network (nodes, links with costs), each router computes
shortes path (dijkstra), every router must have identical knowledge → otherwise inconsistent
paths; OSPF on top of IP → unreliable communication

**Routing metric:** each link associated with link costs, configured value, $Cost =
\frac{ReferenceBandwidth}{InterfaceBandwidth}, ReferenceBandwidth = 100Mbit/s (default)

**Link State Advertisement(LSA):** with information about neighbors and links; flood LSA to all
interfaces → router must have identival copy of LSA; Lifetime: MaxAge = 1 hour, LSRefreshTime = 30 min; if nothing changes, nothing needs to be reported
→ keep quiet, LSAs refreshed every 30mins, otherwise communication only needed in case of changes; min time between two consecutive LSAs 5 secs   
Structure:
- *Header:*
    - LS Age, Options, LS Type (Hello, link state advertisement, acknowledgement)
    - Version: OSPF Version: 2 for IPv$, 3 for IPv6
    - Type: Hello, link state advertisement, acknowledgement
    - RouterID: identifier of router that originated packet
    - AreaID
    - AUType and Authentication: option authentication, verifies that sending router belongs to same network
    - LSAs: if tye is LSA
- *Body:* variable
    - (Advertising Router Flags)
    - \#Links
    - Link ID
    - Link Data: type dependent
    - Type, \#ToS, Metric
    - ToS, 0, ToS Metric

Flooding: Goal: Link State databases must have identical content → need to be synchronized, following actions needed:
- ensure each LSA is received by every router → reliable flooding
- ensure each router consistently store (if LSA is newer → sequence number higher) or discard each LSA → fully deterministic comparison rules
- ensure that expired LSAs are pruned from link state databases

**Link State Database:** LSAs from all routers in network stored; for topology graph and routing table

**Hello Protocol:** establish, maintain logical adjacencies, ensure bi-direction communication
→ determines identity and liveliness of neighbors

*Workflow:* Router sends hello messages (own routerID, routerID of neighbors, dest. IP of message) periodically

**Areas**: AS grow rather large, LSA flooding and route computation overhead → do not scale; Concept: Divide AS into *areas*, Link state algorithms only within area, areas exchange
summary of information, typical size in area: less than 100 router → only router within area have same link state databases; Area 0 = backbone of AS, other areas directly connected to AS
via area border router, Inter-Area Forwarding through backbone area

**Area Border Router (ABR)**: connected to both areas, instance of OSPF for each area, generate summary LSAs, Handling summary of LSAs

On OSPF every router is pre-configured with: routerID (e.g. smallest IP address of its interfaces), Per-interface parameters (interface IP address, mask; interface output cost (metric))

**RIP vs. OSPF**

|         |     RIP       | OSPF  |
| ------------- |-------------| -----|
| **Algorithm**      | distance vector (limited metric selection and size, max path length of 15 hops | links state|
| **Messages**      | periodic updates every 30secs, even without changes     | updates only on change |
| **Resources**      | easier, less resources    | more complicate, more resources |
| **Usage** | somethimes in small networks   |  standard in large ASes, large networks divided into areas|

**ARPANET Routing Metric**: early routing metric versions based on delay; Problems: queue length can change significantly, metric may lead to routing oscillations, bandwidth not
considered  
Measuring Delay: $ t_v = (T_{out} - T_{in}) + t_a + t_s$ ; $T_{in}$: packet receiving time, $T_{}out $: sending first bit of packet, $t_a$: Ausbreitungsverzögerung (Kabelübertragungszeit),
$t_s$ = Sendezeit (Zeit um Paket komplett zu senden)  
Problem: measured delay good indicator *after* rerouting; experienced delay ony godd in case of low load  → route oscillations, low network utilization  
Routing Oscillation: hin und her zwischen Link A und Link B  
Improvement: during heacy load better take good paths than optimal paths: $ τ = \frac{k}{C(1-ρ)} ⇒ ρ = 1 - \frac{k}{Cτ} $ and smoothed utilization value:
$U(n + 1) = 0,5 ∗ ρ(n + 1) + 0,5 ∗ U(n)$ → damps oscillations
with: $τ$: average delay, $ρ$: measured utilization, $C$: link speed, $k$: average packet size, $U$: smoothed utilization

**Equal Cost Multipath (ECMP)**: multiple paths with lowest cost may exist; ECMP splits traffic *equally* between paths with lowest cost; allows load balancing; OSPF supports ECMP

**Traffic Engineering**: Goal: Performance optimization for networks; determine proper link weights (lieber 80% als 100% auf einem Link).

 - Usage of all resources
 - Performance requirements
 - Medium term goal: handle peaks of a usual day

Traffic engineering is monitoring and managing the existent resources and it is
not about adding new routers etc. Changes of the topology are made via the
routing protocol (OSPF supports this).

Traffic engineering is not new. Cellphone line providers already had such a
monitoring and routing management.

**Exterior Gateway Protocol (EGP):** large networks in AS usually only have
information about themselves, number of entries in routing table and amount of
exchanged routing information does not
scale, per AS at least one intermediate system with interface to another AS  
 Advantages:
 - *Scalability:* size of routing table depends on AS size, changes in routing tables only propagated within AS
 - *Autonomy:* routing can be controlled within own network, not the same routing protocols within AS necessary

**Border Gateway Protocol (BGP)**: most important EGP, basis of today's internet routing, worldwide usage;
Path Vector Protocol: Extension of distance vector approach, routing metric = paths (guarantee no loop exist),
routing/paths are based on policies (e.g. cheapest path, not over AS xyz),
routing not pre-determined; through smart address assignment, address ranges are summarized by single prefix → improves scalability  

The protocol has not been changed significantly since the first days in
comparison to changes made to TCP.


*Structure:*

- *External BGP (EBGP):* between routers of *neighboring* ASs; announcement, forwarding of path information; no internal AS details exchanged
- *Internal BGP (IBGP):* between BGP routers within AS; synchronization of BGP routers; Transit AS establish transit routes  

BGP calculates routes to prefixes from **other** ASs, IGP of local AS broadcasts routes to destinations **within** AS  
Possible approaches for routing with BGP and IGP:
- IGP distributes default routes: unknown address/prefix packets to BGP router by shortest path
- Publication of external routes via IGP: BGP router responsible for specific external prefixes
- IGP router also speaks BGP (IBGP)  
Sessions: Point-to-Point (via TCP between directly connected routers = neighbors, peers); hen-eg-problem, how to establish TCP connection?
→ IBGP: IGP of AS can be used   
→ EBGP: usually direct physical connection (no routing required), manual config  

*IBGP Connections:*
- Simple case: BGP routers fully meshed/directly connected, but then sessions must be kept alive, bad scalability
- Alternative 1: concentrate IBGP traffic in a single router = route reflector, has to maintain sessions, forwards messages, in practice more than one reflector → reliabilty
- Alternative 2: form hierarchies from sub ASes (AS confederations), implement more complex policies, confederation appears as a single AS

*BGP Messages:*
- OPEN: establish BGP connection to peer, TCP connection must alread exists!, authentication
- UPDATE: announcement of new / withdrawal of outdated path; only sent if new/better paths available. Theoretically there is an
  aggregation function but due to the splitting of IP regions, it can not be used a lot.
- KEEPALIVE: keeps connection alive in absence of update messages, acknowledgement for OPEN request
- NOTIFICATION: error message / tear down of BGP connection

*BGP Routing:* no predefined routing metric → policies → Routing Information Base (RIB): DB for received, dispatched routing information
- Incoming updates: Adj-RIB-In (Adjacency RIB Incoming), exists per peer, stores information received from peer
- Input Policy Engine: Filtering of information according to rules
- Decision-making Process: Selection of best route
- Loc-RIB: Local RIB, Routing Informaiton Base, actual routing table, only preferred routes, routes form *Forwarding Information Base (FIB)*
- Output Policy Engine: Filtering of information according to defined rules
- Outgoing updates: Adj-RIB-OUT (Adjacency RIB Outgoing), exists per peer, contains routes published to peer

*BGP Challenges:* maintaining scalability ( growth of routing tables, increasing dynamics), increased demands on internet, security problems

**Route Flap Damping**: Routes in routing table change more frequently → temporarily suppressing changes of unstable routes; penalty per update, penalty drops exponentially over time, can lead
to connectivity loss!

**Security Extensions for BGP**: to secure route information, authentication and authorization of senders, integrity protection and encryption, secured routing through IPSec and TCP mit MD5
- *soBGP (secure origin BGP):* from Cisco
- *S-BGP (secure BGP):* from BBN-Technologies

**Cleaning Center**: Redirect traffic to separate DDoS attack traffic and legitimate traffic, legitimate traffic routed back to AS → BUT: good position for "man in the middle" attacker

### Label Switching
#### Motivation
Issures related to IP based routing: Lookup complex, Shortest path routing, packet based

#### Flows
**Flows**: A flow is a sequence of packets traversing a network that share a set of header field values; Ip routing is special case flow based forwarding, concept also applicable to Ethernet
switching
- *Micro-flows:* single "connection", fine grained control, high number of flows possible
- *Macro-flows:* higher level of aggregation, several "connections", lower number of flows

**Flow based forwarding**: fundamental concept, indepentent of layers (can also span multiple layers), incorporates classic routing/forwarding concepts

#### Label Switching
**Types of Communication Networks:**
- *Packet Switching:* packets forwarded independent of each other, meta data required, expensive forwarding decision (e.g. IP)
- *Circuit Switching:* connection with fixed resource reservations, no meta data within data stream required (e.g. ISDN)
- *Virtual Switching:* connections without fixed resource reservation, packet efficiently forwarded on same path, inexpensive label-based
forwarding decision (e.g. MPLS)

> Label Switching: communication network, switched, packet-switched, connection-oriented (e.g. ATM, MPLS) → Label Switching
is combination of packet switching (packets forwarded individually, packets include metadata) and circiut switching (paths
for flows through network, simple forwarding)

**Implementation of Label Switching**: Switching at Layer 2 (instead of routing at layer 3), Labels (local Identification),
Virtual circiuts (Sequence of labels)

**Label**: Short unstructured identification of fixed length (no Layer 3 information, unique, only locally at correcsponding
switch, label swapping (mapping input - output label)), Virtual circuit (identified through sequence of labels at path)  
*Tranport:* Label must be transported within packet  
*Structure:* Layer 2 (Ethernet Head) \| Label \| Layer 3 (IP-Datagram) \| Data

**Label Switching Domain**:
- *Edge Devices:* at border of domain; add/remove labels, map flow to forwarding class, access control
- *Switching Device:* within domain; forwar packets based on label information, label swapping

**Multiprotocol Label Switching (MPLS)**: based on label switching, data plane optimization
- Fast Forwarding due to reduced amount of packet processing
- QoS support (guarantees on latency, capacity)
- Traffic engineering (load balancing)
- Virtual private networks (isolated traffic)
- mulitple networks support   
→ good Acceptance: on top of IP, separation between forwarding (label switching) and control (manipulation of label binding),
not limited on IP, support metrics, scales  
*Components:*
- Label-switching router (LSR): MPLS-capable IP router, can forward packets based on IP prefixes and MPLS labels
- Labeld edge router (LER): Router at edge of MPLS domain (LSR with non-MPLS capable neighbor is LER), classifies packets that enter MPLS
domain
- MPLS-Node: MPLS-capable intermediate system  
*Label:* Encapsulation between headers of Layer 2 and 3, Structure:
- Label 20 bit
- Exp: Bit for experimental usage, 3 bit
- S: Stack bit, 1 bit
- TTL: Time-to-live, 8 bit

**Forwarding Equivalence Class (FEC)**: class of packets, that should be trated equally (same path, same QoS), basis for
label assignment, MPLS-specific, synonym to *flow*; FEC mapping 5 Tupels: ToS, IP Source Address, IP Destination Address,
 Source port, Destination port → LSP/label
*Granularity*:
- coarse-grained: important for quick forwarding and scalability
- fine-grained: important for differentiated treatment of packets/flows

**Label Switched Path (LSP)**: Virtual connection, no resources reserved  
*Communication*: define FEC, distribute labels, establish LSP

**Label Switched Router (LSR)**:
- *Downstream LSR:* in direction of data flow
- *Upstream LSR:* against direction of data flow

**Types of Label Distribution:**
- *Unsolicited downstram:* generates label bindings as soon as it is ready to forward MPLS packets of the respective FEC
- *Downstram on demand:* Downstream router generates label binding on demand
- *Originally:* Label distribution protocol defined along with MPLS
- *De-facto:* RSVP-TE is used mostly

**Resource ReserVation Protocol (RSVP)**: bandwith reservation for end-to-end data streams, soft state principle (establish
session an signal that it is still alive), Scalablity issues!
- Path message: sender → receiver, find path, each hop recorded
- Resv message: receiver → sender, bandwidth reservation

**Resource ReserVation Protocol - Traffic Engineering (RSVP-TE)**: extension to RSVP, additional functionalities e.g. fast
reroute

**Virtual Private Networks (VPN)**: MPLS enables VPNs; here: renting guaranteed transmission capacities from a network provider  
*VPNs with Label Switching:* outer label identifies path to LER, inner label identifies VPN instance

**Traffic Engineering:** extension of Link State routing protocols (additional information needed, all nodes have global view
on network)

### Software Defined Networks (SDN)
> **Traditional IP Networks:** every router control and data plane functions, control is decentralized → Limitations! → SDNs
increase flexibilty and decrease dependencies on hardware

#### Basics and Architecture
**Characteristics of Software-Defined Networks**: Separation of control and data plane; control functionalities → SDN controller,
Data plane → simple packet processors (SDN switches), control plane has global network view (knows all switches, network topology),
network ist software-programmable (network applications), processing based on flows

**Basic Operation in SDNs**:
- Control functionality, SDN controller (e.g. Routing including routing table), SDN controller programs entries in flow table (protocol required!)
- Forwarding table on SDN switch (name here: *flow table*), for every incoming packet in SDN switch → suited entry in flow table needs to be
determined

**Flows**: Identified through match fields (e-g- IP address, port number)

**Flow table**: contains match fields, actions, ...; matches appropriate flow table entry, actions are applied to all packets that match

**Flow rule**: Decision of controller, described in form of match fields, actions, switches

**Flow Programming:**
- *Proactive flow programming:* rules programmed before first packet of flow arrives, no additional delay, loss og controller
connectivity does not disrupt traffic
- *Reactive flow programming:* rules programmed in reaction to receipt of first packet, setup time per flow, high overhead for
short lived flows, new flows cannot be installed if controller connectivity is lost

**Important Interactions**:
- Flow rule send to switch → new flow table entry (reactive and proactive)
- Packet forwarded to controller (primarily reactive)
- Packet re-injected to switch (primarily reactive)

**SDN Architecture**:
Planes:
- *Application Plane:* Network apps perform network control and management tasks, interacts via *northbound API* with control plane
- *Control Plane:* control tasks outsourced from data plane to logically centralized control plane, more complex tasks delegated to application plane
- *Data Plane:* packet forwarding/processing, SDN switches are simple, interacts via *southbound API* with control plane
Interfaces:
- *Northbound API:* controller ↔ network apps (exposes control plane functions to apps, abstract from details, apps can operate on consistent network view)
- *Southbound API:* controller ↔ switches (exposes data plane functions to controller, abstracts from hardware details)
- *Westbound API:* controller ↔ controller (synchronization of network state information)
- *Eastbound API:* interface → legacy infrastructures  
→ No widely accepted standard for north/westbound interfaces

#### SDN Workflow in Practice
**SDN programming primitives:** to assist with creating app, important areas:
 1. *to create, install flow rules:* app that implements flow rule decisions, programs flow table entries into switch
 ```javascript
    import ...

    // entry point to implement custom logic
    // called when control connection established
    // reference to switch as parameter
    onConnect(switch) {
        if (switch == S1) {
            r = Rule(); //data structure holding single flow rule, can be modified with function calls
            r.MATCH('IP_DST', '1.2.3.4'); //select packet based on certain criteria → here: IP address
            r.ACTION('OUTPUT'‚ 4); //specify what happens to matched packets in switch, e.g. m.ACTION(OUTPUT, 7),  m.ACTION(DROP)
            send_rule(r, switch); //install flow rule in switch, creates new flow table entry or overwrites existing one
        }
    }
```
→ creates a new flow rule, sends flow rule to S1
*Priorities:* if flow rules are overlapped
- no overlap: all packets can only be matched by one rule
- overlap: at least one packet could be matched by more than one rule  
→ need to define priorities: default priority=1, higher priorities overwrite rules with lower priority

 2. *react to data plane events:* controller API provide callbacks:
 - to react to control events (e.g onConnect(switch))
 - to deal with packets sent to controller (e.g. onPacketIn(packet, switch, inport)): called if packet was forwarded via *r.ACTION(CONTROLLER)*

 3. *inject individual packets:* handle individual packets (forward a packets, perform topology detection, active monitoring, answer ARP requests)
 - injects single packet (only!) into switch (e.g. send_packet(packet, switch, [rule])), if rule parameter present it
 does not create a new flow table entry
 - handle injection:
    1. inject and process packet in flow table (no usage of optional rule parameter), rule must be installed before injection, otherwise cycle
    2. inject and process packet with custom rule (usage of optional rule parameter), actions attached to packet, rule only used for this packet, flow
    table remains unchanged; → Advantages: more efficient (not creating flow table entries every time), Inconsistencies (if packets matching a rule, while
    network is in inconsistent state = renewing a rule)

**Multiple Flow Tables**: SDN support more than one flow table, expensive in hardware, specify table with *r.table(x)*  
*Benefits:* used to isolate flow rules from apps, logical separation between tasks

**Self-Learning Switches**: Goal: hinter welchem Port liegt welche IP-Adresse → kein Fluten notwendig
1. Switch receives packet and does not know destination address: floods packets, learn location
2. Switch reveices packet and know destination address: forwards packet  
→ possible with SDNs: Leaning Switch App

**Learning Switch Example**:
- *Naive Approach:* send all packets to controller, controller creates rules based on INPORT and MAC ADDRESS,
unknown des. address → flooding; Problem: Controller has no chance to learn ports
- *Version 2 (with delayed rule installation):* delay rule installation until dest. address was learned, Problem: still not learning enough
- *Version 3 (with more specific matching):* only matching dest. address not enought, use more specific matches, ensures all end systems can be learned
Problem: functional perspective good, but: not scalable/usable → amount of flow table entries can be large
- *Version 4 (with multiple flow tables):* separate flow tables for learning and forwarding, 2*N rules for N end systems

#### Open Flow
**OpenFlow**: southbound interface (interaction between controller and switches, logical architecture for SDN switches)
- *Ports:* represent logical forwarding targets, can be selected by output action, physical ports → hardware interfaces  
Reserved Ports:
    - ALL: flooding
    - IN_PORT: send packet back
    - CONTROLLER: send packet to controller
    - NORMAL: forwarding to vendor-specific switch implementation  
Logical Ports:
    - link aggregation: multiple interfaces combined to single logical port
    - transparent tunneling: traffic forwarded via intermediate switches
- *Flow Table:*
    - Match fields → mandatory
    - Priority → mandatory
    - Actions → mandatory
    - Counters: number of processed packets
    - Timeouts: max lifetime of flow, automatic flow removal
    - Cookies: marker value set by SDN controller
    - Flags: indicate how flow is managed, notifies controller if flow is automatically removed
- *Group Table:* definiert Rules für jede Gruppe von Flows, nicht für jeden Flow einzeln, group entries invoked from other tables via group
actions, referenced by unique group identifier, flow table entries can perform group actions during ingress processing,
effect of group processing depends on group type and action buckets
    - Action Buckets: per group zero or more action buckets, contains set of actions to execute
    - Group Types:
        - all: alle buckets in Gruppe wählen
        - indirect: einziges bucket in gruppe
        - select: ein bucket aus vielen der Gruppe wählen
        - fast failover: erstes bucket, das mit aktivem port verknüpft ist
- *Pipeline Processing:* multiple flow table chained to flow table pipeline, flow tables numbered in order, traversed by packets, processing
starts at flow table 0, only forward traversal, actions accumulated in action set,
    - ingress processing: packet processing starts with ingress processing, start at flow table 0, initial action set empty
    - egress processing

#### Power of Abstraction
> Abstraction is major reason for success in OS → similar goals for networking domain

Controller can provide different abstractions to network apps, Apps should not deal with low level/unnecessary details, abstract view
on network, OpenFlow is no suitable for SDN Abstraction

**FlowVisor**: Network slicing (simple form of virtualization), individual users get "own" network slice

#### SDN Challenges
**Controller Connectivity**: SDN required connectivity between controller ans switches, otherwise no exchange of control messages,
no updates in flow tables, no control of the network; Connectivity Modes:
- *Out-of-band:* extra Kabel; dedicated (physical) control channel for messages between controller and switch
- *In-band:* kein extra Kabel; control message use same channel as "normal" traffic, multiple apps can configure switch → both apps
can disable ports → no controller connectivity anymore

**Scalability**: requires powerful controllers, size/load of networks can easily overload control plane, important parameters:
number of remotely controlled switches, hosts/flows, messages

**Distributed Controllers**: reasons for distributed controllers: Scalability, Responsibilities, Reliability, Incremental
deployment; BUT: controller must have consistent knowledge → westbound interface to communicate

**CAP Theorem**: multiple controller cause same problems as in distributed system → CAP Theorem
- **C**onsistency: system responds identically to request no matter which node receives request (or not at all)
- **A**vailability: system always responds to request
- **P**artition tolerance: system continues to function even when messages are lost  
→ inherentes Problem, nicht möglich alle drei Punkte gleichzeitig zu erfüllen, nur zwei gleichzeitig möglich

**Flow Table Capacity**: SDN needs a lot more than 20.000 rules, fast processing requires TCAM (current hardware max. 20.000 entries) →
workarounds like caching, flow aggregation, optimized distribution

**Flow Setup Latency**: setting a new flow requires that a rule is generated at SDN controller and installed at switch → directly affects
control latency of network → clever placement of controller

*Ende der Vorlesung vom 21.11.2018*

#### Tools
**OpenDaylight**: SDN Controller, Java-based, focus on network programmability, OpenDaylight Architecture: zwischen UI, Network apps und
Controller

**Virtual Switches**: core component in data centers #VMs >> #physical servers, #Virtual Ports >> #physical ports → one
virtual switch per physical server → "virtual" Top-of-Rack switches, e.b. Open vSwitch

### Network Function Virtualization
#### Network Functions
**Middlebox**: device on data path, between source and destination end system, performs functions other than normal, standard functions
of IP router

**Network Function**: functionality of middlebox, executed on data path

**Network Address Translation (NAT)**: connects a realm with pricate addresses to external realm with globally unique addresses,
Problem: private address not usable for routing in internet → exchange globally unique and private address when packets traverse network boundaries

**Firewall**: monitors and controls incoming and outgoing traffic  
*Packet inspection*:
- Shallow packet inspection: decisions based on header fields only (bis Layer 4)
- Deep packet inspection: inspect content of higher layer protocols (e.g malware detection)

*Processing:*
- Stateless: every packet inspected independently of other packets
- Stateful: keeps state between packets

**Web Cache**: provides additional storage on data path, temporarily caches content provided by remote server →reduces time for content
delivery → CDNs capitalize on well-placed caches → multiple middleboxes at different locations in network → Problems with middleboxes:
fast, but inflexible, closed source, static wiring, ...

**Network Function Virtualization (NFV)**: ideas of cloud computing (implement network functions in software, use virtualization technology);
Traditional middlebox with caching functionality → (Softwarization) → Caching functionality implemented in software → (Virtualization) →
Executed on hardware  
*Benefits*:
- Resource sharing
- Agility and flexibility
- Rapid deployment
- Reduced costs

*Main Building Blocks:*
- Virtualized Network Functions (VNFs): network functions provided in sofware
- NFV Management and Orchestration (MANO): Lifecycle management of VNFs and network services
- NFV Infrastructure (NFVI): Provides hardware, software and network resources for VNFs, can contain multiple Points of Presence, SDN used
to transparently reroute flows to PoPs

**Network Service**: Network services combine multiple network functions

**Point of Presence (PoP)**: small data centers, located at different points in infrastructure

#### Virtualization
**Virtualization**: provides software abstraction layer between hardware and OS and apps running on VM → offers standardized platform for
applications  
*Hypervisor:* abstraction layer ist referred to as *hypervisor* (resource broker between hardware and VM, tranlates I/Os from VMs to physical
server devides, allows multiple OSs to coexist on a single physical host, allows live migration on VMs and other hosts)
- *Type 1 Hypervisor*: runs directly on hardware (high performance, strong isolation between VMs), synchronized access of VMs to hardware
- *Type 2 Hypervisor*: runs on top of host OS (executed as app in user space), VMs provide virtual hardware to guest OS  

*Container-based:* single kernel provides multiple instances (containers) of same host OS (no hypervisor involved, isolation enforced
by host OS kernel, apps in containers executed by host OS), kernel synchronizes access of containers to hardware

#### Service Function Chaining
**Service Function Chain (SFC)**: ordered set of network functions (specifies ordering contrains that must be applied to flows), enables creation
of composite network services

**MPLS-based SFC**: Services classifiers select appropriate service function chains, service function forwarders deliver packet to network
functions

### Internet Congestion Control
#### Basics
**Shared (Network) Resources**: general problem: multiple users use same resource, high
level objective with respect to networks (provide good utilization of network resources and
acceptable performance for users) → Buffer or Drop?

**Congested Router**: Assumption: no cumulative acks, all packets same length; Input interface
receives 4 times more traffic than can be forwarded on output interface → 75% of packets
discarded

**Buffer**: Router need buffers to cope with temporary traffic bursts, packets caan not be 
transmitted immediately → buffer, buffer full → packets dropped; buffers add latency, FIFO 
queues, end-to-end latency of packets:
- Propagation delay
- transmission delay
- queueing delay (überwiegt in vielen Fällen)

**"ursprüngliches" TCP**: Connection establishment:3-way handshake (full duplex connection),
 connection termination: 4 way handshake (separately for each direction of transmission), data
 transfer: byte-oriented sequence numbers, go-back-N (positive cumulative acks, timeout), flow 
 control
 
**Congested Internet**: drastic performance reduction of TCP (1986) → series of congestion
collapses, goodput reduced about several orders of magnitude, routers dropped 10% of packets

**Throughput:** amount of network layer data delivered in a time interval (pre-tax), 
aggregation of data flows *through* router/link

**Goodput:** "application-level" throughput (after-tax), amount of application data delivered 
in a time interval, retransmission doesn't count, packets dropped not counted, what 
application receives, traffic at network level might be higher

**Knee**: Load reaches network capacity, goodput stops increasing, buffers build up, end-to-end 
latency increases → Network is *congested*

**Cliff**: traffic load increases beyond cliff, packets start to be dropped, goodput
decreased → *Congestion collapses*

→ Initial TCP standard: entit simply doesn't kow state of network, adjustment of sending
rate if TCP stream to capacity of network not possible

**Improved TCP Versions**: Goal: estimate available network capacity to avoid overload 
situations, limit traffic instroduced to network accordingly; Traffic Sources: 
Receive feedback from network, apply congestion control → system control and optimization 
problem

**Congestion avoidance**: keep traffic load around knee

**Congestion control**: prevent system from going over cliff

→ Location of knee changes (difficult to predict): total network load and traffic pattern
matters → typical distributed optimization problem

**Optimization Criteria**: Network N with data sources, data rate of data source i: $r_i(t)$
- *Efficiency:* bottleneck link of source (link with lowest data rate), capacity C of bottleneck, 
set of sources that use the bottleneck link $A_i$: $\sum_{j in A_i} r_i(j)$ (But: how are
data rates distributed among sources?)
- *Fairness:* fair allocation (all sources get equal allocation): $F(r_i,...,r_N) = 
\frac]{(\sum r_i)²}{N(\sum r_i²)}$, F = [0,1], totally fair = 1, totally unfair $= \frac{1}{N}$
- *Convergence:* Responsiveness (Speed with wich $r_i$ gets to equilibrium at knee after starting
from zero), Smoothness (Oscillation arond equilirbium at steady state)
- *Distributedness:* congestion control should operate in distributed manner (no central control, 
with complete knowledge, no need to know number of currently active sources)

#### Types of Congestion Control
**Window-based Congestion Control**: Congestion Control Window CWnd: max number of 
unacknowledged packets allowed per data stream, assumes each packet is acknowledged by
receiver, basic window mechanisms compares to sliding window, adjust sending rate of source
to bottleneck capacity → self-clocking

**Rate-based Congestion Control**: controls sending rate, implemented by timers (define
inter packet intervals), Problem: no cut off mechanism; e.g. UDP for audio/video streaming

#### TCP-Tahoe
**Mechanisms**: used for congestion control:
- Slow Start
- Timeout
- Congestion avoidance
- fast retransmit 

**Congestion Signal**: Retransmission timeout, Reception of duplicate acks → begin of slow 
start

> Must be valid: *LastByteSent - LastByteAcked ≤ min{cWnd, RcvWnd}

**TCP Tahoe Algorithm**: AIMD (additive increade, multiplicative decrease), Additive
increase of CWnd after receipt of acknoledgement, multiplicative decrease of CWnd if
packet loss is assumed; SSTresh (Slow Start Threshold)
- CWnd < SSThresh and ACKS received: slow start, CWnd += 1
- CWnd ≥ SSThresh and ACKS received: congestion avoidance, Cwnd += 1/CWnd
- Timeout or 3 duplicate ACKS: slow start, CWnd = 1 MSS, SSTresh = max(FlighSize/2 * MSS)

**Fast Retransmit**: not every segment received out-of-order means congestion, wait until
retransmisson timer expires, then retransmit, BUT to be faster: retransmission after
receipt of specific number of duplicate ACKS e.g. 3

#### Analysis of Improvements
After observing Congestion Collapses the following mechanisms were introduced to the original TCP:
- Slow-Start 
- Round-trip time variance estimation
- Exponential retransmission timer backoff
- dynamic window sizing on congestion
- more aggressice reciever achknoledgement policy

→ packet conversation: keep TCP connection stable and achieve network stability

**Self-Clocking**: is valid for any window-based system (TCP uses window-based flow control)   
*Basic Assumption:* Complete flow control window in transit (TCP: receive window RcvWindow), 
Bottleneck link with low data rate on path to receiver   
*Basic scenario:* graue Kästchen = Pakete, Pakete vom schnellen Link auf langsamen Link geschickt → Auswirkung auf Sendezeit (da
abhängig von Datenrate) → muss durch Bottleneck und braucht länger → *Inter Packet Gap* heißt Lücke die dadurch entsteht, bis 
neues Packet sich durch Bottleneck gequetscht hat. Dieser wird recht groß und man wird ihn nichtmehr los. Packete werden
im Zeitraum des Inter-Packet-Gaps weitergeschickt. Ziel ist es Zustand zu erzielen und zu halten.

**Three Ways for Packet Conservation to fail**
*1) Connection does not get to equilibrium*
**Slow Start** brings TCP connection into equilibrium if connection has just started or restart after assumption of congestion.
The idea of slow start is to no send the complete receive windoe (flow control) immediately, in case it is larger than
the buffer at the bottleneck, then it would drop segments. Gradually increase number of segments that can be send without receiving
an ACK   
*Approach:* Apply congestion window in addition to receive window, minimum of congestion and receive window can be sent (
Congestion Window: CWnd[MSS], Receive Window: RcvWindow[Byte]), new connection or congestion assumed: reset congestion window: CWnd = 1, 
incoming ACK for sent (not retransmitted) segment: increase congestion window by one → exponential grows of CWnd

About MSS: refers to payload, that can be send in TCP segment that consist of TCP header (max. 60 bytes) and payload. With
IPv4 at least MSS of 536 byte must be supported

