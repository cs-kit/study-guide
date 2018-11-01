---
layout: post
title:  "Verteiltes Rechnen"
ref: verteiltes_rechnen
date:   2018-10-17 07:00:00 +0100
categories: master
excerpt: Die Vorlesung "Verteiltes Rechnen" gibt eine Einführung in die Welt des verteilten Rechnens mit einem Fokus auf Grundlagen, Technologien und Beispielen aus Grid, Cloud und dem Umgang mit Big Data.
lang: de
tags: lecture
---
<div style="background-color: #EAEFF4; border: 1px solid #b5aeb1; border-radius: 3px;  padding: 10px; margin-right: 10px">
    <strong>Vorlesung:</strong> <a href="https://campus.studium.kit.edu/ev/U8oAm94VRIyvtcN-9RuTmg">Verteiltes Rechnen</a>, Vorlesung, 4 ECTS <br>
    <strong>Dozent:</strong>Prof. Dr. Achim Streit<br>
   <strong>ILIAS:</strong> <a href="https://ilias.studium.kit.edu/goto_produktiv_crs_873428.html">https://ilias.studium.kit.edu/goto_produktiv_crs_873428.html</a><br>   
   <strong>Vorlesungswebsite:</strong> <a href="https://www.scc.kit.edu/bildung/11926.php">https://www.scc.kit.edu/bildung/11926.php</a> <br>   
   <strong>Klausur:</strong> schriftlich, Termin noch unklar <br>
   <strong>Einordnung:</strong> Vertiefungsfach "Telematik" und "Parallelverarbeitung", Profil "Datenintensives Rechnen" <br>
</div>

## Organisatorisches

### Vorlesungen
- **17.10.2018**: Organisatorisches und Foliensatz 0-1 bis 0-32
- **24.10.2018**: Foliensatz 1-1 bis 1-34
- **31.10.2018**: Foliensatz 2-1 bis 2-33

### Material
Die Vorlesungsfolien werden im ILIAS hochgeladen. Sämlichte Literatur befindet sich im Skript. Die Vorlesung
findet auf Deutsch statt, die Folien sind auf Englisch.

### Klausur
Die Klausur findet schriftlich statt und dauert 60min. Termin noch unklar, grober Zeitraum Februar/März.
 Zudem ob Klausur auf Deutsch oder Englisch gestellt wird.

## Vorlesungsinhalt
### Opening
**Distributed Computing**: Definitionen aus [Wikipedia](https://en.wikipedia.org/wiki/Distributed_computing):
Components *interact* with each other to *achieve a common goal*; use of distributed systems to *solve computational problems*;
no clear distinction between *concurrent computing*, *parallel computing* and *distributed computing*.   
Definition in *Vorlesung*: Distributed Computing is about *systems* (hard- and software) that *work together*, *geographical distance*, 
problem *solving environment for benefit of their users*; e.g. Web Services, Grid Computing, Cloud Computing

**Metacomputing**: logical integration of several, independent supercomputer via high-performance WAN connections; aggregation of main
memory capacity, computing power → solve big problems, too big for one supercomputer (grand challenge problems e.b. clima simulations)

**Grid**: Term as analogy to electric power grids; Grids harness distributed resources to provide scalable, secure and high-performance mechanisms for discovering resources, negotiating 
the access to resources, using remote resources; share resources and work together e.g. scientific collaborations;  
 Checklist for Grids:
- Coordinates resources that are *not subject to centralized control* (user desktop vs. central computing; addresses securtiy, payment,...)
- Using *standard, open, general-purpose protocols and interfaces* (authentication, authorization, access, resource discovery)
- Deliver *non-trivial qualities of service* (response time, throughput, availability, security, co-allocation; 
utility of combined systems must be greate than sum of its parts)

**Big Data**: Definition by Doug Laney: **V**olume, **V**elocity, **V**ariety; often extended by **V**alue and **V**eracity (=Vertrauenswürdigkeit); 
Important also Privacy, Preservation and Sustainability;  
Scientific Big Data only possible due to extraordinary performance of *Grid Computing*

**Cloud Computing**: no single answer; e.g. Wikipedia: ubiquitous, convenient, on-demand networt access to shared pool of 
configurable computing resource;
- *Scalable:* partitioning of compley workflows in adaptive infrastructures
- *Flexible:* variety of workloads (consumer, business)
- *Fully-automatic:* resources on demand
- *Business modell:* utility computing, pay-per-use, pay-as-you-go
- *Service oriented architecture:* dynamic procision of resources via web services interfaces
- *Virtualisation:* arbitrary, customer-desired view on resources; location and type of resources transparent for user  
→ **Web Services + Virtualisation = Cloud Computing**

Unterscheidung Grid Computing - Cloud Computing:
> **Grid Computing:** nicht kommerziell, jeder bring Ressourcen ein; früher große Grid-Infrastrukturen → heutzutage nichtmehr da für kommerzielle Anbieter
kein Gewinn; Grid Computing für wissenschaftliche Zwecke, keine zentrale Kontrolle; z.B. GritKA  
**Cloud Computing:** agil, eingach zu nutzen, vor allem aber schnell; z.B. AWS

### Introduction
#### Distributed Systems & Middleware
> A **Distributed Systems** is a collection of independent computers, appear to user as single coherent system,autonomy of individual computers, 
single-system view

not visible for user if individual computer or distributed system; interaction with DS in uniform, consistent manner; 
should be **scalable**, **extensible** (Systeme auch herausnehmbar, können ausfallen) and **fault tolerant**; Grid infrasturcture is highly dynamic 
distributed system offering non-trivial qualities of service   
Examples: DesktopGrid (workstations not in use, single 
file system, commands typed locally → executed on available machines; act like single-processor time-sharing system), World Wide Web (simple, 
consistent and unifrom model of distributed documents, publishing documents via URL)    

Goals of Distributed Systems:
- **Connecting users and resources**: 
    - *Access*: to remote resources e.g. hardware, software, services 
    - *economical:* sharing supercomputer 
    - *collaboration and exchange of information*
    - *security mechanisms:* access to trusted users, accepting only secure resources 
    - *billing and accounting:* billing = Preis, Rechnung, nur mit accounting = Sammeln von Nutzerdaten, aber accounting ohne billing möglich
- **Transparency**:  
    - *Access:* hide **differences in data representation** e.g byte order, **how** accessing resource
    - *Location:* hide **where** resource is located
    - *Concurrency:* hide that resource may be shared with **competitive users**, consistency still important
    - *Failure:* hide **failure and recovery**
- **Openness**: 
    - *Access*: Protocols (specify format), Interfaces (specify syntax) and Semantics (hard to specify; informal e.g. comments) to standardize rules 
    how to access functionality
    - *Interoperability:* implementations should work together through each others interface specifications
    - *Portability:* implementation should run on different systems implementing the same interfaces
    - *Flexibility:* easy configuration of system with different components
- **Scalability**:
    - *Size:* large number of users/resources; main bottleneck: centralization
    - *Geographical extent:* main bottleneck: latency of wide-area, syncronous, unreliable communication e.g. transatlantic
    - *Administrative domains:* no trust, restrictions make systems more complex; → establish a trust relationship (e.g. certificates)
   
*Ende der Vorlesung vom 17.10*
    
#### Web Services
> A **Web Service** is a *new middleware technology* for *machine-to-machine* interaction, can be accessed through *web protocols* (e.g. http),
 provides an *interface* (web API), typically *registered*, located through registry, *loosely coupled connections* between systems

Web Services are not for users, only connection technology, behind the scenes, users should not know that they are using Web Services, form
basis of modern Grids  
Advantages of Web Services:
- Loosely coupled
- Platform independent (datatypes as XML)
- Language independent
- Self-describing (WSDL, XML-Schema)
- coexistence with firewalls 
- separation of interface definitions from their embodiment
- simplicity and extensibility
Disadvantages of Web Services:
- data conversion overhead (from and back to XML)

*Examples for Web Services:*
- Models and metamodels: Web Services Resource Frameword (WS-RF)
- Service description and metadata: Web Services Description Language (WS-DL) 

**Web Service Description Language (WSDL)**: defines message syntax for invocation and response of WS (messages part of data layer); WSDL is XML-document;
**WSDL is not used during communication!**, web service provider exposes its WSDL file; currently WSDL 1.1
Three parts:
- *What a service does:* operations with parameters, return type
- *How to access service:* data formats, protocols
- *Where a service is:* protocol-specific network address  
*WSDL Tooling:* WSDL interface provided by service provider, machine readable; stub, skeleton can for communication parts can be automatically created 
→ concentrate on logic, contents

**Extensible Markup Language (XML)**: Defines generic syntax to mark up text with tags; human- and machine-readable; XML is trimmed
down version SGML, HTML is SGML application  
*Well formed* XML:
- start/end tag
- may nest, but may not overlap
- exactly one root element
- attributed values are quoted
- within one element no two attributes with same name
- no comments or processing instructions inside tags
- no unescaped illegal characters

#### Web Services Resource Framework (WSRF)
Service interfaces often need stateful interaction between sclients and service, WSRF defines a generic framwork for modeling and 
accessing stateful resources using Web services → XML document to describe state of resource, Specifications of WSRF:
- **WS-Resource**: defines WS-Resource as combination of resource and Web Service to access resource
- **WS-ResourceProperties (WSRF-RP)**: defines messages to query or update property values
- **WS-ResourceLifetime (WSRF-RL)**: defines messages to detroy resource, monitor lifetime
- **WS-ServiceGroup (WSRF-SG)**: to form variety of collections of services
- **WS-BaseFaults**: set of information that my appear in fault messages
(siehe Folien 1-34)

*Ende der Vorlesung vom 24.10*

### Grid
**Grid**: internet infrastructure; harnessing (nutzbar machen) distributed ressources, provide
scalable, secure, high-performance mechanisms; enables scientific collaborations (virtual
organizations) to share ressources; Grid ist Analogie zu "Electric powe grid"; Konzept bereits seit 1965 bekannt

**Grid Checklist**: <span style="color: red">Prüfungsfrage in Altklausuren!</span>  

|         |     Grid       | Cloud  |
| ------------- |-------------| -----|
| **Control**      | keine zentrale Kontrolle, keine Kontrolle über andere Standorte des Grids | zentrale Kontrolle, Anbieter mit wirtschaflichem Interesse (z.B. Amazon) |
| **Protocols & Interfaces**      | standardisierte, offene, general-purpose Protokolle (Authentication, Authorization, Resource Discovery, Access      |   keine standardisierten Interfaces, Hinterrund ist "vendor"-Login (Kundenbinding, kein einefacher Umstieg auf die Konkurrenz) |
| **Quality of Service** | nicht-triviale Dienstgüte (response time, throughput, availability, securtiy, co-allocation); Kombination der Systeme muss Mehrwert liefern      |  triviale Dienstgüte |

**Meta-Computing**: logische Integration unabhängiger, heterogener, paralleler Computer
mit high-performance WAN Verbindungen zu einem System; verteilen einer Anwendungen über
mehrere Supercomputer; kann Probleme (schneller) lösen, die mit einem Supercomputer 
nicht lösbar sind; Fokus aufs Rechnen alleine

**Klassifikation von Grids**: by resource type shared/technology used
- *Compute Grids*: access to computational resources, classification by hardware:  
    - Desktop Grids
    - Server Grids
    - HPC/Cluster Grids
- *Data Grids*: transparent, secure, high-performance access to federated data sets (flat-file, relational, streaming data)
- *Peer-to-peer Grids*: storage capacity of individual computer workstation shared
- *Collaborative Grids*: resource is human expertise, human interaction across geograophical distances

Klassification organizal/geographic range: Department Grids, Enterprise Grids, Global Grids, Utility Grids, Service Grids

#### Architecture
**Anatomy of Grids**: middleware architecture, layered protocol stack; follows *hourglass model* 
(= small set of core abstractions to allow diverse application to be mapped onto diverse set of resources); e.g. APIs, SDKs
(vgl. Abb. s.18, Kapitel 2.0-2.1); Hourglass Neck = Resource & Connectivity in Protocol Stack  
Layers: bottom up
- *Fabric Layer:* sharing of resources, resource-specific operations; Enquiry Mechanisms, Management Mechanisms
- *Connectivity Layer:* core communication protocols, authentication protocols
- *Resource Layer:* sharing of single resources, information protocols, management protocols
- *Collective Layer:* coordinates multiple resources, directory services, co-allocation, scheduling, brokering services, data replication

**Physiology of Grids**: service-oriented architecture based on Web Services technology: *Open Grid Services Architecture (OGSA)* =
standardized framework; includes set of basic interfaces to access state of resource

**Open Grid Services Architecture Capabilites**:
- *Resource management services:* management of resources themselves, resources in grid, OGSA infrastructure
- *Security services:* Authentication, Authorization, Audit, non-repudiation, Privacy and secure conversations
- *Self-management services:* Monitoring, fault-tolerance, self-healing, analysis and projection
- *Information services:* Naming, Logging, Monitoring, Message delivery   
→ Framework for grid structures
