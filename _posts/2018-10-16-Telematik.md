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


*2) Sender injects new packet before an old packet has exited*

**Retransmission Timer**:   
*Assumption:* Complete receive window in transit
- Alternative 1: ACK received, segment delivered and thus exited network → conversation of packets fulfilled
- Alternative 2: Retransmission timer expired. Segment is dropped in the network → conversation of packets fulfilled;
segment is delayed but not dropped → conversation not fulfilled → to short retransmission timeout causes connection to leave equilibrium   

→ Good estimation of Round Trip Time essential for a good timer value
- too small: unnecessary retransmissions
- too large: slow reaction to packet losses

*Estimation of Round Trip Time (RTT)*: RTT = wann kommt nächste Quittung an? → timer-based measurement, timer resolution up to 500ms, 
requirements regarding timer resolutions vary (e.g. high resolution in high performance data center) 
- SampleRTT: time interval between sending a segment and reception of ACK, single measurement, retransmissions ignored (ACK can not be
associated with segment)
- EstimatedRTT: smoothed value across a number of measurements, observation: measured values can fluctuate heavily

→ apply exponential weighted moving average (EWMA), influence of each value becomes gradually less as it ages, unbiased estimator for 
average value: *EstimatedRTT = (1-$\alpha)\*EstimatedRTT+ $\alpha$\*SampleRTT* (Typical $\alpha$ = 0,125)

*Retransmission Timeout (RTO)*: RTO = $\beta$ * EstimatedRTT 

*Estimation of Deviation*: Goal: avoid observed occasional retransmissions; Observations: Variation of RTT can greatly increase in higher
loaded networks: Deviation = (a-$\gamma$) \* Deviation + $\gamma$ \* \|SampleRTT - EstimatedRtt\|

*Improved Retransmission Timeout (RTO)*: RTO = $\beta$ * EstimatedRTT  RTO = EstimatedRTT + $\beta$ * Deviation (Typical $\beta = 4, $\gamma$=0,25)
→ Observation: Differences between RTT and RTO are smaller

*Multiple Retransmissions*: 
- Problem 1: How large should timer interval be between two subsequent retransmissions of same segment? →
*Exponential backoff* after each new retransmission RTO doubles (RTO = 2*RTO), maximum value should be applied (≥ 60 seconds)
- Problem 2:To which segment does received ACK belong (original or retransmission)? → *Karn's Algorithm*: ACKs for
retransmitted segments are not included into calculation of EstimatedRTT and Deviation, timeout value is set to value calculated
by backoff algorithm until ACK of non-retransmitted segment received

> Timeouts are importatant to keep TCP connection in equilibrium, to avoid unnecessary retransmissions. Carefully tuned timers are important 
(apply EWMA and consider deviation)

**Congestion Avoidance**:
Consider *multiple* concurrent TCP streams → how to adapt available path capacity?
Under the assumption that the TCP connection operaties in quilibrium, a packet loss is with high probability
caused by a newly started TCP connection (new connection requires resources on bottleneck router/link). Therfore
the load on existing TCP connections has to be reduced.

*Congestion signal:* signals TCP senders that congestion is occurring or is about to occur (uses ACKs). An implicit
congestion signal needs no support from network. A missing ACK indicates a congestion situation (retransmission timeout). 
Duplicate ACKs are also used as congestion indication.

*Additive increase/multiplicative decrease (AIMD):* Strategy to adjust traffic load 
- Multiplicatively decrease load in case a congestion signal was experienced. The Retransmission Timeout is
CWnd = y * CWnd with 0 < y < 1 (TCP Tahoe: y = 0.5)
- Additively increase load in case of no congestion signal is applicable. ACK received: CWnd += 1/CWnd

**Additive increase Multiplicative decrease**: is a general feedback control algorithm that is applied to congestion control.
- Additive increase od data rate until congestion
- Multiplication decrease of data rate in case of congestion signal 

(img AIMD.png)

*Asumptions:* explicit network feedback (increase/decrease load), system operates near the knee, system operation is 
synchronous and in discrete time steps

*Fairness:* network with two sources that share a bottleneck link with capacity C, Goal bring system close to optimal point (c/2)
- Efficiency Line: $r_1 + r_2 = C$ holds for all points on the line, points under the line reflect an underloaded system (→ increase rate),
points above the line reflect an overloaded system (→ decrease rate)
- Fairness Line: All sources with fair allocation ($r_1 = r_2$), multiplying with b does not change fairness. 
Jain's fairness index: $F(r_1, r_2) = \frac{(r_1 + r_2)²}{2(r_1² + r_2²)}$
- Optimal Operating point: Intersection of efficiency line and fairness line
(img AIMD-fairness.png)

**TCP Fairness**: TCP connections compete for network resources. Goal all TCP connections receive equal share of bottleneck resource 
(non-zero). If n TCP connections share the same bottleneck it would be fair if each connection receives 1/n-th of the bottleneck capacity.
Both TCP connections have the same RTT and use the same MSS. Lost TCP segments are also detected instantly. 

TCP Fairness refers to TCP connections. Therefore a user can open *multiple TCP connections* concurrently to *get more capacity*.
Furthermore the ACK generation of the receiver can influence resource allocation. A "greedy" receiver can send several ACKs, 
can send ACKs faster than it receives segments and can send duplicate ACKs.   
It is possible to open congestion window faster and consequently get more resources allocation. Inconsistencies of the TCP
specification can cause this: TCP sequence number countrs bytes, congestions window counts segments → Attack would be impossible
if congestion window also counted bytes.   

(img send-acks-fairness1.png)

The receiver acknowledged each segment in several pieces and congestion window opens fast (increases per received ACK)
The sender can also send ACKs faster/before data is received. Packet losses are unlikely, receiver anticipates successfull reception, since
ACKs are not a proof for receip of corresponding data. To solve this it requires changes in the protocoll or increasing loss possibility
of ACKs makes attack unprofitable.

(img send-acks-fairness2.png)

#### TCP Reno
The TCP Reno concept differentiates between *Major congestion signal* (timeout of retransmission timer)
 and *minor congestion signal* (receipt of duplicate ACKs). The difference of TCP Tahoe in case of minor congestion
 signal is that Reno doesn't reset to slow start (duplicate ACKs mean successful delivery of segments) and does *fast recovery*
 (controls sending of new segments until receipt of non-duplicate ACK). Major congestions signal still cause a slow start.
 
**Fast Recovery**: is started on a receipt of a specified number of duplicate ACKs (usally 3). The idea ist that new segments should
continue to be send, even if packet loss is not yet recovered. The network load is reduced by halving the congestion window.
The first missing segment is fast retransmitted. 

**Differences to TCP Tahoe:** in congestion avoidance. 
- Timeout: slow start SSTresh = max(FlightSize/2, 2*MSS), CWnd = 1
- Fast recovery (3 dup Acks): retransmission of oldest unacknowledged segment 

**Evolution of Congestion Window**: (img congwindreno.png)

**TCP Fairness**: Sending identical ACKs multiple times causes interpretation of duplicate ACKs (one segment has left network →
new one should be sent). TCP Reno is sending duplicate ACKs before/without receiving new segments. The sender sends a new segment
per received duplicate ACK. The self clocking continues and the congestion window grows. Remedy: retransmission timeout and reset
congestion window.

(img reno-fairness.png)

#### Periodic Model
For TCP Performance assesment interesting metrics:
- *Throughput:* Data that can be transferred in a certain time interval
- *Latency:* Experienced Delay while sending data

**Variables for analysing TCP**:
- X: Transfer rate measured in segments per time interval
- N: Number of segments
- A: Duration of a cycle
- RTT: Rount trip time [s]
- p: Loss probability of a segment
- MSS: Maximum segment size [bit]
- W: Value of a congestion measure in #MSS
- E[z]: Expeted value of variable z
- O: total amount of data to transfer [bit]
- D: data rate measured in bit per second [bit/s]

Under the assumption of a long-term steady state behavior of TCP (without slow start, linear CWnd → Congestion avoidance), a constant RTT and W,
periodically occuring losses that are detected through ACKs (no timeouts) and without retransmissions the progress of the congestion
window will be analysed. W is the value of the congestion window right before the packet loss is detected.

(img peridic-model.png)

The data rate when the segment loss occurs is $D = \frac{W MSS}{RTT}$, so a time of $\frac{w}{2} \cdot RTT$ is needed until congestions 
window reaches W again. Therefore the average data rate of a TCP connection is $D = \frac{0,75 W MSS}{RTT}$

**Round**: A Round starts with the sending of W segments. After sendig these W segments, the sender cannot send any further segments before
receiving an ACK. This ACK marks the end of the current round and the beginning of the next round. The duration of a round corresponds to the RTT
and is independent of the window size, but the time to send a complete window is shorter than RTT.

**Cycle**: A Cycle are (several) rounds until a segment loss is detected. After a loss, the next cycle starts.

(img round-cycle.png)

The minimal value of a congestions window is $\frac{W}{2}$ and it opens by one segment per round. That means the duration
of a cylcle is $\frac{W}{2} \cdot RTT$ and the number of delivered segments per cylce are $N = \frac{1}{p}$. 
The average transfer rate is $X = \frac{N}{t}$. The *Inverse Square-Root p Law* says that the intensity is inversely 
proportional to the square of the distance from the source of that physical quantity, which means: $X = 1,22 \frac{1}{RTT \sqrt{p}}$

#### Active Queue Management
In the simple queue management a full buffer means, that the next segment must be dropped (tail drop). The problem here
is the synchronization. Segment of several TCP connections are dropped more or less at the same time.

**Active Queue Management (AQM)**: The network gives an implicit notification of an arising congestion and reacts before
the queue gets overloaded. Routers can then drop segments before queue is completely filled up. The decision which segment
will be dropped is *random* that ensures more fairness. Consequently the average queue occupancy decreases and congestion
can be detected early. 

*Random Early Detection (RED)*: is an AQM algorithm. It does not drop segments if the queue occupancy is < $q_{min}$ and 
does drop all segments if the occupancy is ≥ $q_{max}$. For $q_{min}$ ≤ queue occupancy < $q_{max}$ the probability of
dropping an incoming signal is linearly increasing with the queue occupancy.   
RED ist implemented in many routers/switches but rarely used. New AQM Algorithms are currently in development.

*Explicit Congestion Notification (ECN)*: ist eine Erweiterung des Netzwerkprotokolls TCP/IP zur Überlastkontrolle. 
Mittels ECN kann ein Router durch eine einfache Markierung eines Bits (genauer 2 bit) im IP-Header eine drohende Überlast mitteilen.
ECN is based on queue occupandy and requires active queue management. The notifications must be issued before queue
is completely filled up. To *notify* congestion, the IP datagram is marked but not dropped and then forwarded to the
receiver. To *react* to the notified congestion, the sender receives the marked IP datagram and can then adjust congestion
control window accordingly. The notification takes place on layer 3 (IP).

(img ecn.png)

### Ethernet Evolution
#### Aloha, Slotted Aloha
**Aloha**: was the first media access control (MAC) protocol for packet-based, wireless networks. MAC ensures time multiplex,
variable and random access. No previous sensing of medium an no announcement of intended transmission is possible. The access
to the medium is asynchonous. Therefore collisions are possible. 

(img collision-aloha.png)

*Collision detection:* 
- Explicit: Confirmation of collision through higher layers, requires an additional communication channel
- Implicit: is used by aloha over satellite. The Satellite broastcasts received packets to all, the sending station
receives packet again after one RTT and can then check its correctness.

*Reaction to collisions:* is a Retransmission of the packets, but this should not introduce another collision. That's why the
exact time of retransmission is *randomized*. After a certain amount of collisions, the sending is aborted.

*Evalutation:* A collisions occurs if a previous packet from another sender has not been send completely 
of another system starts sending before transmission is done. With N active systems in the network, the probability p 
that a system starts sending, the probability that a collision occurs is $(1-p)^{N-1}$ and the probability for
a successfull transmission by any system $Np(1-p)^{2(N-1)}$. This is resulting in a maximum utilization $U_{max} = 0,18$

**Slotted Aloha**: works like Aloha but uses time slots and a synchronized access only at the beginning of the time slog. It has
on average less collisions than normal Aloha. 

(img slotted-aloha-coll.png)

*Evalutation:* There are N active systems in the network. Each system starts to send with a probability p, so N-1 systems 
are not sending with a probabiliy of $(1-p)^{N-1}$. So the successful transmission of any system is $Np(1-p)^{N-1}$
The maximum utilization is $U_{max} = 0,36$

#### CSMA-based Approaches
**Carrier Sense Multiple Access (CSMA)**: is a media access control method that ckecks if the medium is free before starting to
send, so it is "listening before talking".
- *CSMA/CD (Collision Detection):* The sending station can detect collisions by listening (usage e.g. Ethernet)
- *CSMA/CA (Collision Avoidance):* The sending station assumes collisions when ACK is missing (usage e.g. WLAN)

#### Ethernet-Variants
**Original Ethernet (IEEE 802.3)**: uses MAC (time multiplex, variable, random access) and CSMA/CD with exponential backoff 
(Stauauflösungsmechanismus in Ethernet. Wird von Stationen im Ethernet eine Kollision erkannt, beenden diese Stationen ihre 
Sendung und versuchen sofort oder nach einer Slot-Time erneut ihre Sendung über das Ethernet zu übertragen.) The network 
topology was originally a bus topology with a data rate of 10 Mbit/s. Ethernet was wire based with a coaxial cable. The
standard consists of Layer 1 and Layer 2a (MAC Protocol).

*CSMA/CD-based approach:* checks the medium, which is considered to be free if there is no activity detected for 96 bit times (=
Inter Frame Space). CSMA/CD is 1-persistent (Wenn das Medium als besetzt erkannt wird, wird geprüft, bis es frei wird; wenn frei, 
wird gesendet (mit Wahrscheinlichkeit 1, d. h. immer)). The sender is doing collision detection. On detecting a collision, 
the sending will be aborted and a jamming signal (Übertragung des anderen gezielt kaputt machen, damit er merkt, 
dass eine Kollision stattgefunden hat und Daten kaputt sing) will be sent (length 48 bit). Exponential backoff is for 
repeated transmissions.

*Collision detection:* The sender is detecting a collision. This must happen before transmission is finished. The minimum 
duration for sending is the doubled maximum propagation delay of the medium. If the frames are shorter and therefore the sending time
it is not possible to detect a collision reliably (only CSMA, not CSMA/CD). To enforce the minimal frame length, the frame is
extended by the padding field (PAD).

(img ethernet-frames.png)

*Utilization:* Under the Assumption that the Ethernet protocol works perfect without any interferences or errors and without
an overhead or processing time the maximum utilization is $U_{max} = \frac{throughput}{data rate} =\frac{1}{1+a}$. The parameter
a is used for performance evaluaion $a = \frac{propagation delay}{transmission delay}$. Two types of time intervals can be 
discriminated:
- Transmission intervals: 1/(2a) time slots
- Collision intervals: collision or no transmissions

(img ethernet-utilization.png)

**Fast Ethernet (IEEE 802.3u)**: was introduced 1995 with a data rate of 100 Mbit/s (switchable between 10Mbit/s and 100 Mbit/s and 
automatic negotiation (protocol for automatic seletection of technical communication settings)), a star network topology (half duplex
and duplex links), medium access control (CSMA/CD for halb duplex links) that uses the same design as ethernet frames (collision detection
has to be possible) and a modified encoding.

*Congestion and Flow Control:* With faster interfaces and switches as a central component, switches can be the performance bottleneck and frames are
temporarily buffered (buffer full → frame has to be dropped). Loss recovery is done at transport layer (TCP) which is not performant.
Since buffer overflow and frame loss happens on layer 2, the resource bottleneck should be handled there. *Backpressure* is a workaround
for half duplex links. It enforces collision, CSMA/CD detects the collision and the sender aborts sending and repeats the frame (backoff).
This might cause a long delay.   
 Furthermore backpressure pretends the medium is used and sends a potentially correct bit sequenece, CSMA/CS notices that the medium is
 used and the sender is watining for the medium to be free. This is an implicit flow control. But it's not possible with
 duplex links, since no CSMA/CD is used.    
 
**Ethernet (IEEE 802.3x)**: A *pause function* was standardized to stop sending on receiving a pause frame and implicitly continue after
a pause time that was given in the pause frame (multiple time for sending 512 bit) or explicitly continue when receiving a pause
frame with time=0. This does not solve longer overload in the network and only deals with short, local overload on a single link.

The pause function is a part of the newly introduced sublayer *MAC control* (Layer 2). All MAC control frames terminate on the MAC 
control sublayer or are generated by it. All other frames are passed from/to higher layers.

(img mac-control-frame.png)

Components should discover automatically which data rate/enconding is possible for the communication. The *Auto-negotiation function*
is between the end systems and a central node (hub, switch) to exchange 16-bit long messages to encode possible configurations.
It is transmitted as a sequence of tact and data pulses. The *Auto-negotiation function* is not for variants using glass fiber.

**1 Gigabit/s-Ethernet (IEEE 802.3z, IEEE 802.3ab)**: Is almost the same Ethernet as standardized in IEEE 802.3u except the data rate 
 which has been upgraded to 1 Gbit/s but is still adjustable between 10Mbit/s and 100Mbit/s. Using half duplex links with
 a data rate of 1 Gbit/s makes it difficult to ensure collision detection with CSMA/CD. Therefore it it possible to either restrict
 the network size (max segment length of 10m) or change the minimum frame rate (efficient for a small amount of data). Since these
 changes are still not good enough, new concepts has been established:
 - *Carrier extension:* ensures collision detection on fast links. It is increasing the transmission without increasing the 
 minimum length of the frames. The length of the time slot is not as long as the minimum length of a frame (minimum frame length: 512 Bit, 
 new time slot length: 512 byte). 
 
 (img carrier-extension.png)
 
 - *Frame bursting:* transmits short frames efficiently. Stations are permitted to send burst of frames directly following each other.
 The first frame has an extension if required (might be required for collision detection), the following frames are following (last
 frame has to start after at most 8192 Bytes) 
 
 (img frame-bursting.png)
 
 **10 Gigabit/s-Ethernet (IEEE 802.3ae (glass fiber), IEEE 802.3an (twisted pair))**: Important characteristics of 
 10 Gigabit/s- Ethernet are a data rate of 10 Gbit/s, only point-to-point connections and only full duplex. It does no longer
 support old legacies like half duplex or hubs, CSMA/CD, no frame bursting or carrier extension and it does not require a MAC
 protocol. Jumbo frames with 9014 byte payload can be enabled optionally. It is the physical layer for locale networks (LANs) and 
 wide area networks (WANs). But it still requires improved coding mechanisms (interference becomes more problematic, signal-noise-ratio
 determines achievable data rate) and becomes technically challenging.
 
 **40/100 Gigabit/s-Ethernet (IEEE 802.3ba)**:40 or 100 Gigabit/s Ethernet is the fastes generation of Ethernet. It supports
  distances up to 40km and a multilane distribution (multiple parallel channels, different physical wires or different frequencies) and
  a virtual lane (distribute data stream over number of virtaul lanes)
  
  
#### Spanning Tree
**Bridges**: connect local networks (LANs) on layer 2. The filter function detaches
intra-network traffic in one LAN from inter-network traffic to other LANs, this increases
network capacity of big networks.

(img bridges.png)

There are two types of bridges:
- *Source-Routing bridges:* End systems add forwarding information in send packets. The 
Bridges forward the packet based in this information. Sending packets is not transparent for
the end system, it has to know the way.
- *Transparent bridges:* The local forwarding decision takes place in each bridge. (
Forwarding information is store in the forwarding table). The end system is not involved in
forwarding decisions (existence of bridges is transparent for end systems). For each network
interface exists an own layer 1 and a MAC instance.

(img transp-bridge.png)

**Spanning-Tree Algorithm**: To ensure the network is established as a loop-free topology (packets must no loop endlessly)
 we use the *Spanning-Tree* Algorithm. To Forward packets, the switches have to learn the
 location of end systems (and store it in forwarding tables). The forwarding table is then
 used for filtering and forwarding of packets.
 
 The *Spanning Tree* Algorithm organized the bridges as a tree topology (no loops possible), 
 where nodes are bridges or LANs and edges are connections between interfaces and LANs. In
 case the resoureces are not used optimally, it can be that bridges are not in the tree.
 Forwarding of packets is onl possible along the tree.
 
 (img example-network.png)
 
 *Requirements* for using the bridge protocol:
 - *Group address* to address al bridges in the network (MAC address)
 - *Unique bridge identifier* per bridge in the network
 - *Unique interface identifier* per interface in each bridge
 - *Path costs* for all interfaces of a bridge
 
 In the *Spanning Tree* Algorithm bridges send special packets, so called *Bridge Protocol
 Data Units (BPDUs). It contains the identifier of the sending bridge, the identifier of 
 the bridge that is assumed to be the root bridge and path costs of the sending bridge
 to the root bridge.
 
 *Implementation of Spanning Tree*: Determine the root bridge, then determine the root 
 interfaces for each bridge (calculate path costs to the root bridge, select the interface
 with the lowest costs) and then determine the designated bridge for each LAN (loop free). 
 A LAN can have multiple bridges. Select the bridge with the lowest costs on the root interface 
 (designated bridge, resolve equal costs over bridge identifier). The designated bridge is
 responsible for the forwarding of packets. Other bridges in the LAN will be deactivated
 (affected interfaces set to blocked).  
 Initially bridges have no topology information. Therefore all bridges think they are the
 root bridge (periodically sending BPDUs with itself as root bridge). As soon as the bridge
 receives a BPDU with a smaller bridge identifier it no longer assumes itself as the 
 root bridge (but the bridge with the smaller identifier). When it receives another BPDU
 wit an even smaller identifier, then this bridge is the new root bridge. If the bridge
 notices that it is not the designated bridge, it is no longer forwarding BPDUs.  
 The Algorithm is in a stable phase, if the root bridge periodically sends BPDUs (only
 active bridges forwar BPDUs), no more BPDUs are received (bridge again thinks its the 
 root bridge, algorithm starts again), after stabilization packets are forwarded over the 
 respective ports (based on forwarding table).
 
 (img st-impl1.png st-impl2.png st-impl3.png st-impl4.png)
 
 *Forwarding of packets*: The forwarding table contains the information required for forwarding, 
 link destination address, outgoing port and timer, as well as static, created by network 
 administrator and dynamic entries, learned and forgotten during operation (Learning
 through incoming packets, forgetting based on timer (soft-state)). Packets with local
 destinations are not forwarded over the bridge to separate the traffic and increase 
 scalability.  
 If the bridge is receiving a packet with a *known destination*, that means the destination
  is identified by destination MAC address in the packet and matches an existing enstry in 
  the forwarding table, the packet will be sent over the respective port.   
  If the bridge is receiving a packet with a *unknown destination*, the packets will be 
  flooded, that means it is sent over all ports except the input port and the bridge learns
  the location of the source system by identifying the source MAC address in the packet and
  creating a new entry in the forwarding table. The source system needs to be reachable 
  over the input port.
  
  (img forwarding-sptr-ex.png)
  
  **Rapid Spanning Tree Protocol**: (Wikipedia)[https://de.wikipedia.org/wiki/Rapid_Spanning_Tree_Protocol]:
  "Das Rapid Spanning Tree Protocol (RSTP) ist ein Netzprotokoll, um redundante Pfade in 
  lokalen Netzen zu deaktivieren, bzw. im Bedarfsfall (Ausfall einer Verbindung) wieder zu 
  aktivieren.
  Werden beim STP beim Ausfall einer Netzkomponente (Switch, Bridge etc.) noch sämtliche 
  Verbindungen unterbrochen, bis die neue Topologie berechnet ist, so fallen beim RSTP nur 
  die Pfade aus, die über die defekte Komponente liefen. Ansonsten bleiben die bisherigen 
  Pfade bestehen, bis die Berechnung der neuen Topologie beendet ist. Die Umschaltung auf 
  die neue Topologie erfolgt dann sehr schnell. Häufig können die nicht-ausgefallenen 
  Verbindungen weiter bestehen bleiben, da lediglich einige zusätzliche Ports freigeschaltet
   werden, die zuvor wegen Redundanz deaktiviert waren.
   
   Two new types of port states:
   - *Alternate Ports* are ports with the best alternative path to the root bridge.
   - *Backup Ports* are also ports with alternative paths to a network that already has a
   connection. The bridge has two ports which connect to the same network.
   
   Every bridge sends *peridic BPDUs* (Hello-Timer = 2s) to the next hierarchy level in the
   tree. In case of a failure of a neighbor there are no BPDUs for 3 times.
   
   Different types of ports:
   - *Edge port:* Only end systems are connected (no loops possible)
   - *Point-to-Point port:* full duplex (only connects to  neighbors)
   - *Shared port:* connects to a network (no fast switching possible)
   
   (img rsp-ex.png)

#### Real time Ethernet
Ethernet is a cheap technology and therefore used in manny new use cases (Industy automation, 
vehicles, music industry). Real time Ethernet is in these use cases not possible.
     
**Time-Triggered Ethernet (TT-Ethernet)**: is used in control tasks for e.g. wind wheels and
vehicles. Requirements are support of time-triggered real time communication (collision free
sending), support of a data rate based communication and compatibility to normal Ethernet.

TT-Ethernet defines three *traffic classes*:
- time controlled, high priority frames (time-triggered)
- rate limited data streams (rate-constrained)
- best-effort traffic: normal Ethernet frames, only send and relayed if no higher priority
frames are available

(img tt-eth-classes.png)

**EtherCAT**: is an Ethernet for control automation. Its topology is a logical ring, it needs
hardware changes and efficient handling of small data packets. It allows very time critical
applications.

**Audio Video Bridging (AVB)**: is used for broadcasting, events (concerts, statium) and
vehicles. It need time synchronization between AVB stations (< 1ms) and hardware changes.

### Data Center Networking
#### High-Level View

**Data Center** typically has a large number of compute servers with virtual machine support
and extensive storage facilities. It uses off-the-shelf commodity hardware devices (
handelsübliche Hardware-Geräte) like switches with small buffers and a huge amount of servers
(> 100.000). These devices fail regularly. Furthermore they should be extensible without 
massive reorganization, need to be reliable (requires redundancy) and highly performant 
(100Tbit/s, low latencies).

(img dc-simpl.png)

*Top-of-Rack Switches (ToR)* are Ethernet switches that connect servers within a rack. 
Switches typically have small buffers. A rack has 42-48 rack units per rack.

(img tor.png)

*Challenges* are to maintain *scalability*, to maximize throughput while minimizing latency
and cost. In case of failure to guarantee data integrity and service availability. Enhance
power efficiency and reduce operational costs.

A *Data Center Network* interconnects data center servers with each other and connects the
data center to the internet. There are *two types of traffic*: Between external clients and 
internal servers and between internal servers. *Border routers* connect the internal network
of the data center to the internet.

*Routing/Forwarding within a Data Center* requires for example network efficiency, no
forwarding loops, a quick failure detection.

(img dc-forwarding.png)

**Typical Services**

**Infrastructure as a Service (IaaS)**: providing virtual computing resources or virtual
network resources by cloud providers.

**Platform as a Service (PaaS)**: allows customers to manage services (e.g. web apps) with
leased platforms from cloud providers without owning physical resources.

**Software as a Service (SaaS)**: providing software services as needed. Customers do not
need to purchase software licenses.

**Storage as a Service (StaaS)**: providing storage and sharing infrastructure by cloud
provider.

#### Network Topology
The Tree-Based Topology is often used in data centers.

(img tree-based.png)

**Traffic Types**
*East-west traffic* is between internal servers and server racks. It is the result of internal
applications like MapReduce and storage data movements.

*North-south traffic* traffic between external cliens and internal servers.  It is is the 
result of external requests from the internet. North-south traffic may cause east-west 
traffic.

**Fat Tree Networks**

**Fat-Tree Networks**: is a tree structure in which branches nearer the top of the 
hierarchy are "fatter" (thicker, higher bandwidth) than branches further down the hierarchy.
It is a solution for the problem that switches only have a limited number of ports but we want
to connect a large number servers with it.

(img fat-tree-ex.png)

But in this topology switches need different numbers of ports and switches with high numbers
of ports are more expensive. The *k Pod Fat Tree* (below 4 pod fat tree) resolves this through
creating "pods" (Hülle, Gehäuse) around switches. Each switch has k ports. To avoid re-numbering
of IP addresses when topology changes the entire topology uses layer 2 forwarding.

(img 4podfat.png kpodfatnumb.png)

*Address Assignment*: for the private IPv4 address block 10.0.0.0/8
- Pods: enumerated from left to right [0,k-1]
- Switches in a pod: IP address *10.pod.switch.1*
    - edge switches are enumerated from left to right [0, k/2 -1]
    - enumeration continues with aggregation switches from left to right [k/2, k -1]
- End hosts: IP address *10.pod.switch.ID*
    - Based on the IP Address of the connected edge switch
    - IDs are assigned to hosts from left to right starting at 2
- Core swiches: IP address *10.k.x.y*
    - k: number of pods
    - x: starts at 1 and increments every k/2 core switches
    - y: enumerates each switch in a block of k/2 core switches from left to rigt (starting 
    with 1)
    
(img address-ex-pod.png)

*Advantages* of k Pod Fat Trees are the identical switches, cheap commodity (handelsübliche)
switches can be used and multiple equachl cost paths between any hosts. A *disadvantage* is
the high cabling complexity.

**Load Balancer** distributes traffic to servers and also collects traffic from servers. It
provides NAT-like functions like translating private into public address spaces and hiding
internal structure to the outside. The hierarchical topology supports scalability and
redundant devices and links to increase reliability but it has many points of failure.

(img load-balancer.png)

**Clos Network**

A **Clos Network** is a multi-rooted tree that allows forming a large switch out of smaller
switches. Referred to as (m,n,r) switch with number of switches in the middle stage m, 
number of input/output ports n and number of input/output switches r.

(img clos.png)

In clos networks has three different levels of switches.
But clos networks are not limited to three levels. A recursive construction of clos networks 
with odd number of switches is possible through  replacing the middle switches with a three
level clos network. A Clos network is non-blocking if m ≥ 2n - 1.
 
Three layers of switches:
- *Input switches:* ToR swithes directly connected to servers
- *Middle switches:* Aggregation switches directly connected to ToR switches
- *Output switches:* Intermediate switches connected to the aggregation switches

#### Ethernet within Data Centers
Ethernet as a "fabric" for data centers has to cope with a mix of different traffic types and
therefore needs *Prioritization*. **Priority Code Point (PCP)** is a field of the VLAN tag for
traffic differentiation. But it is not enough for bandwidth reservation.

**Data Center Bridging**

**Data Center Bridging** is a unified, Ethernet-based solution for a wide variety of data
center aplcations. It is extending Ethernet with the following four functions.

*Priority-based Flow Control* is an extension of flow control via PAUSE frame. Eight priority
levels are introduced using the VLAN tag (eight virtal links on one physical link). The 
pause time can be individually selected for each priority level that allows differentiated
quality of service.

*Enhanced Transmission Selection* is introducing priority groups (PGs) to allow
bandwidth reservation. It guarantees a minimum data rate per PG. Unused capacity is usable by
other PGs.

*Congestion control on Layer 2*: The Quantatized Congestion Notification (QCN) protocol 
estimates of the strengthof the congestion (Detection) and sends a feedback to congestion 
source via a special frame (Notification). The source can limit the transmission rate similar
to TCP (decrease transmission rate multiplicative and increase it again additive)

*Data Center Bridge Exchange* Protocol (DCBX) detects the capabilites of the network and 
configueres the neighbors through sending periodic broadcasts to the neigbor, 
for example to enable priority-based flow control.

**Alternatives to Spanning Tree**

To gain more flexibility, in terms of network topology and usage 
and a better utilization of the total available capacity, data centers are using 
*routing algorithms in Layer 2*.   
The basic Procedure consists of two parts:
*Intermediate-System-to-Intermediate-System (IS-IS) protocol* uses link state rounting, 
doesn't rely on IP address and supports multipath.  
The use of *tunneling* is encapsulated within the domain and adds a new header with addresses
that is used for forwarding.

(img l2f.png)

*Alternative Concepts*

*Shortest Path Bridging (SPB)*: Every bridge in the LAN calculated shortest paths using MAC
address tabes. If the target is not known yet, the packet is forwarded via the shortest path 
tree. The packets are encapsulated in the LAN (MAC-in-MAC).

*Transparent Interconnection of Lots of Links (TRILL)*: Routing Bridges implement TRILL. 
Each Routing Bridge is calculated in the LAN, the shortest routes to all Routing Bridges is
stored in a tree. These trees are sed for traffic with multiple destination. Forwarding
of the frame if target is unknown. The forwarding information base is quite small because it
only contains Routing Bridges and no end systems.

#### TCP within Data Centers
For the use of TCP in Data Centers, relevant properties are:
- low round trip times
- incast communication: servers answer to the client at the same time (synchronized)
- multiple patchs
- mix of long and short-lived flows
- virtualization
- ethernet as a "fabric"
- commodity switches

The *goals* are simultaneous support for low delays and high throughput, high utilization of
the infrastructure and low cost. At the same time data center should have the option to an
administrative control, homogenous components, backwards compatibility and seperation of 
traffic.

*TCP Reno* is *not suitable* because of the requirement of large buffers and high end-to-end 
delay. Most TCP concepts for congestion control in data centers require changes is end systems
and switches.

**Incast Problem in Data Centers**

**TCP-Incast Problem**: Incast ist a many-to-one communication pattern. It is common in 
applications such as web search and analytics. A Request is distributet to multiple servers
which are responding almost synchronously. The total numver of responses can overwhelm small
buffers in switches.

(img tcp-incast.png)

**Packet loss in Ethernet switches**: Ports often share buffers because individual answers may 
be small. That's why larger number of responses can overload a port, high background traffic
on the same port as incast or on a different port than incast can cause *packet losses*. 
Losses cause *TCP retransmission timeouts* and no further data can be received. Duplicate
ACKs cannot be generated.

(img tcp-retrans.png)

**Barrier Synchronization and Response Time**: A client has a TCP connection to each of the
servers involved. Requests are sent synchronously to the servers which respond almost
synchronously. The application needs answers from all servers before the next query. The
consequence is that the slowest TCP connection determines the efficiency of the application. 
This effect, that the affected TCP instance must wait for the retransmission timeout, 
is called *Barrier Synchronization*. In this time the link is not used. The result are
long periods where the TCP connection cannot transfer data and the application is blocked.

To prevent these problems a *smaller minimum retransmission timeout* (ms → µs) and the
*desynchronization* in case of a full buffer as well as randomization to desynchronize 
retransmissions might be helpful.

#### Data Center TCP 
**Data Center TCP (DCTCP)**: achieves high burst tolerance, low latencies and high throughput
with commodity switches. DCTCP works with low utilization of queues without reducing the
throughput. DCTCP achieves the goal through responding to the strength of the congestion
and not to its presence if congestion occurs. The response based on presence would be too
strong in data center. Buffer underflow and a low throughput would be the result.

*Explicit Congestion Notification (ECN)* is a very simple active queue management. If an
element is in the queue > k the CE-Bit will be set.  
DCTCP sets the ECN echo flag only in ACKs for segments that were marked with *Congestion
Experienced*.

*Benefits of DCTCP*:
- *Incast:* If the queue is build up over multiple RTTs, DCTCPs early reaction will help. If
the number of small flows is too large, no congestion controll will help to prevent segment
loss.
- *Building the queue:* DCTCP reacts if the queue is longer than k. For bursts there is
more buffer space available.
- *Buffer pressure:* Queues of loaded ports are kept small. The mutual influence among ports
is reduced.