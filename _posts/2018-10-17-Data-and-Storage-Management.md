---
layout: post
title:  "Data and Storage Management"
ref: data_and_storage_management
date:   2018-10-16 07:00:00 +0100
categories: master
excerpt: Ausgehend von den aktuellen Anforderungen an die Massendatenspeicherung in Rechenzentren werden unterschiedliche Speicherarchitekturen und Konzepte für die Speichervirtualisierung erläutert. Diskutiert werden dabei u.a. eine Taxonomie der Speichervirtualisierung, Storage Area Networks (SAN), Network Attached Storage (NAS), Fiber Channel, iSCSI und virtuelle sowie globale Filesysteme (z.B. CIFS, NFS). Darüber hinaus werden Verfahren für die Gewährleistung einer hohen und langfristigen Verfügbarkeit der Daten (vgl. Backup, Replikation und Langzeitarchivierung) vermittelt. Zusätzlich werden zukünftige Anforderungen, die aus der Verarbeitung großskaliger Daten sowie dem Verbund von räumlich verteilten Speicherinfrastrukturen (vgl. Cloud Storage) resultieren, diskutiert. Aktuelle Herausforderungen bei der Planung und dem Betrieb von Speicherinfrastrukturen werden erläutert und Plattformen sowie Werkzeuge für deren Verwaltung vorgestellt. Den Abschluss der Vorlesung bildet die Betrachtung von externen Anforderungen an den Betrieb von Speicherinfrastrukturen beispielsweise durch den Datenschutz sowie der IT-Sicherheit.
lang: de
tags: lecture
---
<div style="background-color: #EAEFF4; border: 1px solid #b5aeb1; border-radius: 3px;  padding: 10px; margin-right: 10px">
    <strong>Vorlesung:</strong> <a href="https://campus.studium.kit.edu/ev/mNDK-kwFSjqvAXvMGVhBJQ">Data and Storage Management</a>, Vorlesung, 4 ECTS <br>
    <strong>Dozent:</strong> Prof. Dr. Bernhard Neumair  <br>
   <strong>ILIAS:</strong> <a href="https://ilias.studium.kit.edu/goto.php?target=fold_885971&client_id=produktiv">https://ilias.studium.kit.edu/goto.php?target=fold_885971&client_id=produktiv</a> <br>   
   <strong>Vorlesungswebsite:</strong> <a href="https://www.scc.kit.edu/bildung/11923.php">https://www.scc.kit.edu/bildung/11923.php</a> <br>   
   <strong>Klausur:</strong> mündlich, daher nach Vereinbarung <br>
</div>

## Organisatorisches

### Vorlesungen
- **17.10.2018**: nicht da gewesen
- **24.10.2018**: nicht da gewesen
- **31.10.2018**: Kapitel 2 Folie 25 - Ende; Kapitel 3 Folie 1 - 8 

### Material
Das Material der Vorlesung besteht aus:  
- **Folien**: Folien werden im ILIAS hochgeladen

### Klausur
Klausur findet mündlich statt

## Vorlesungsinhalt
### Introduction
in immer größerem Umfang daten gesammelt, immer kostengünstiger herzustellen → viel größere Messungen, Experimente → Daten kostbares Gut

**Daten**: "Collection of raw facts from which conclusions may be drawn"; more convenient from is digital data (increase processing capabilities;
lower cost of digital storage; affordable, faster communication technology)

**Kategorisierung von Daten**: 
- *Structured:* e.g. rows and columns
- *Unstructured:* 80% of enterprise information, e.g. PDFs, Documents, Web Pages, Invoices

**Information Lifecycle Management**: effective data management:  
Create → Access → Migrate → Archive → Dispose (Vgl. Abb. Kap 1 - 8)

Enabling Data-Intensive Computing: Data Analysis, Visualization, Experiment, Data Creation, Publications, Archive, Simulation.

**Datenanstieg**: Smarter System creating an information explosion; storage requirements growing 20-40% p.a., Information doubling ever 18-24 months, 
Storage butgets up 1-5% in 2010 → Information explosion meets budget reality;   
Clients struggling to keep up, top issues for storage managers:
- Managing Storage Growth ~55%
- Proper Capacity Forecasting and Storage Reporting ~35%
- Managing Costs ~30%
- Backup Administration and Management 20%
- Managing Compolexity ~20%  
Top Storage Initiatives:
- Tired Store Build-out
- Consolidation
- Technology Refresh
- Backup Redesgin
- Vitualization Adoption
- Improving Performance
- Archiving

**Key Requirements for Data Center Elements**: Data Integrity, Availability, Security, Performance, Scalability, Capacity → Manageability

**Critical Success Factors**: Managing Information Growth without Complexitiy:
- *Storage Efficiency:* Reduce Cost, improve performance, increase felxibility
- *Data Protection:* maintain access to information
- *Service Management:* improve service, beat expectations

**Storage Efficiency**: getting the most from storage resources
- *Tiered Storage:* automated tiered storage to maximize performance, reduce operation expenses; SSD to increase performance up to 300%;
cost reducing by migrating less critical data to less expensive media;
- *Consolidated Storage:* reduce administrative costs and improce cycle time, Scale out storage to manage billions of files from single consolidated 
system
- *Virtualized Storage:* quickly provision storage, increase flexibility; increate utilization of storage by up tp 30%; Reduce total cost of 
ownershipt (TCO) up to 66% by deploying automated, virtualized storage

**Data Protection**: Improving Service levels, beating Expectations
- *Visibility:* improve visibility to enable better forecasting, identify up to15% of allocated storage for reclamation, reuse
- *Control and Automation:* improve cycle time, reduce errors; increase administrator productivity by simpifying disk provisioning
- *Flexible Delivery Options:* flexible delivery options (e.g. cloud) an manages services; improve flexibility by moving processes and workloads to
external cloud environments

Hard Disk Performance (per GB) drops alarmingly: Sustained IO Rate per GB and hard disk generation 10k RPM (2005)

**Storage Media**: Predominant in datacenter:
- *Tape:* in robotic libraries
- *SATA 7kRPM:* Serial ATA → "dumb" disk electronics
- *3,5 FC 15kRPM:* Fibrechannel  → "intelligent" networkes SCSI disk controller
- *Flash SSD:* Solid State Device, NAND Flash

Trends Backup on SATA: 3,5" FC → 2,5" FC (FC = [FibreChannel](https://de.wikipedia.org/wiki/Fibre_Channel)) 

### Storage Access and Architectures
**Host**: Applications run on host; hosts range from simple laptops to compley server cluster; Physical Components: CPU, Storage (Disk device, internal 
memory), I/O device (Host to host communications, e.g. Network Interface Card NIC), Host to storage device communications (Host Bus Adapter HBA)  
Logical Components:
- *Application:* Inferface between User and Host, three-tired architecture (UI, Logic, Databases), data access classification:
    - Block-Level-access: data stored/retrieved in blocks
    - File-Level-access: data stored/retrieved by name and pathname
- *OS:* between application and hardware, controls environment
- *LVM (Logical Volumen Manager):* [Logical Volume Manager](https://wiki.ubuntuusers.de/Logical_Volume_Manager/), creates/controlls host level logical
storage (physical view ⇔ logical view, physical data blocks ⇔ logical data blocks), part of OS or third party  
Components: 
    - Physical Volumes: typically divided into contiguos equal-sized disk blocks
    - Volume Groups: one or more physical volumes form volume groups, LVM manages it as single entity, physical volumes can be added/removed, at least
    one disk group per OS
    - Logical Volumes
- *Device Drivers*: for device recognition, API to access, control devices, hardware dependent, OS specific
- *File System*: file is collection of related records/data stored as a unit, file system ist hierarchical structure of files (e.g. FAT32, NFTS, UNIX FS)
    
**Partitioning**: Physical Volume splitted into many Logical Volumes

**Concatenation**: Physical Volume united into one Logical Volume

**Files from/to Storage**: User (manages/configures) → Files (Reside in) → Files System Files (Mapped by a file system to) →
File System Blocks (residing in) → LVM Logical Extents (Mapped by LVM to) → Disk Physical Extents (Managed by disk storage subsystem)

**Connectivity**: Interaction between hosts, host and storage device; physical components: Bus, Port and cable

**Connectivity Protocol**:
- *Tightly connected entities:* central processor to RAM, storage buffers to controllers
- *Directly attached entities:* connected at moderate distance (e.g. host to storage)
- *Network connected entities:* networked host (e.g. NAS or SAN)

**Storage: Medias and Options**: 
- *Magnetic Tape:* low costs, long term data storage, limitations: sequential data access, single application access at a time, storage/retrieval overheads
- *Optical Disk:* distribution medium in small, single-user computing environments, limited capacity and speed, e.g. CD-ROM, DVD-ROM
- *Disk Drive:* most popular, large storage capacity, random read/write access, for performance intentive online application, 
$ Transfer Time = \frac{Block size}{Transfer rate} $

**Hard Disk Drive (HDD) Basics**: read/write cache hits ~1ms; physical disk I/O operations >5ms; limited number of I/O operations per second by:
- *Average Seek Time [ms]*: head movement to required track, typical 4-10ms
- *Rotation Latency [ms]*: disk platter spinning until first sector addressed passes under r/w heads; avg. time = half a rotation; typical: 2-4ms
- *Transfer Time [ms]*: read/write data sectors, 1 sector = 512 Byte; typical <16KiB

**Fundamental Laws Governing Disk Performance**:  arrival rate a
- *Little's Law:* Relationship between number of requests N in queue an response time R: $ N = a * R $ 
- *Utilization Law:* I/O controller utilization $ U = a*R_s $; $R_s$ is service time

**Native Command Queueing (NCQ)**: muss eingeschaltet werden; Frage: Wann geben wir commit, dass Schreiboperation erfolgreich war?
- wenn File im Cache → schlecht für Performance
- wenn File auf Platte → Leistung von Hersteller, bessere Performance, Head Verhalten in Hardware, paar 1000 Umdrehungen pro Minute

**Short Stroking**: Increasing HDD Performance, Approach to achieve maximum possible performance from HDD by limiting overall head movement and
average seek time; Implementation: only small portion of overall capacity, tracks on outer edge with higher data density; Disadvantage: large number of 
HDDS invoveld, onyl small portion os storage capacity used; typical for applications with high access densities with high random I/O rates, 
low response times but small amount of data

**Transaction Processing**: Buchungsprozesse, online, tausende Nutzer → Daten schlecht vorhersehbar, z.B. durch Sitzplatzbuchung, nur wenige bytes
die sich ändern; vorsicht beim Buffern z.B. Telefonie; Antwortzeit bei DBs typischerweise 2s → sehr niedrige response time, aber gleichzeitig bei
wenigen Datan hohe I/O Raten; OLTP = Online Transaction Process;  
*Latenz wichtig, Durchsatz wichtig!*

**Batch Jobs**: Nachts ausführbar, z.B. Berechnungen für Buchungen können nachts ausgeführt werden (Terminüberweisungen); ABER: Bewegen von vielen Daten, 
seriell geschrieben → I/O auch noch hoch, aber durch caching/prepatching handlebar → Durchsatz aber begrenzt
*Buffering möglich, Latenz egal!*

**Application I/O – Workload Performance Characteristics**:
- *Basic Workload Performance:* I/O rate [IOps] (transactions) or data rate [MBps] (throughput); Random access or sequential access;
Read:write ration; average I/O request size
- *Additional Workload Performance:* Read cache hit ratio, average response time

**Enterprise Flash Drives**: highest possible throughput per drive, no spinning magnetic media, no mechanical movement (→ no latency), Solid State enables
consisten I/O performance; very low latency per I/O, energy efficient storage design; based on Flash Solid State; 30 greater IOPS, less than 1 ms service time, 
better reliability

### Storage Infrastructures

**Redundant Array of Independent Disks (RAID)**: [Wikipedia](https://de.wikipedia.org/wiki/RAID): "Ein RAID-System dient zur Organisation 
mehrerer physischer Massenspeicher zu einem logischen Laufwerk, das eine höhere Ausfallsicherheit oder einen größeren Datendurchsatz erlaubt 
als ein einzelnes physisches Speichermedium."; performance limitation of disk drive, individual drive has certain life expectancy → RAID; Ziel von
RAID: geringe Ausfallwahrscheinlichkeit für Festplatten mit möglichst geringem Overhead, Erhöhung von Performance; Raid provides: increase capacity, 
higher availability (Ausfallsicherheit), increased performance  
*RAID Array Components:*
- RAID Controller
- Physical Array
- Logical Array
- Hard Disk  

*RAID implementations:*
- Hardware: usually specialized disk controller card; controls attached drives, arrays appear
to host as regular disk drive
- Software: "Firmware", runs on OS, performance CPU workload dependent, not supporting all RAID
levels  

*RAID Levels:*
- 0: Redundanz fehlt, nur Striped array, no fault tolerance, Beschleunigung ohne Redundanz, gesteigerte Transferraten, Platten in zusammenhängende Blöcke 
gleicher Größe aufgeteilt, Blöcke "reißverschlussartig" zu einer großen Platte angeordnet, Zugriffe auf Platten parallel möglich (→ Striping), chunk size 
meist 64kB
- 1: Disk mirroring, alle Daten auf zwei Festplatten gespiegelt, Kapaziät max so groß wie kleinste Platte, sehr einfach, 
- Nested RAID 0+1: Striping und Mirroring
- Nested RAID 1+0: Mirroring und Striping, Ein RAID-10-Verbund ist ein RAID 0 über mehrere RAID 1, Eigenschaften der beiden RAIDs kombiniert: 
Sicherheit und gesteigerte Schreib-/Lesegeschwindigkeit, mindestens vier Festplatten 
- 3: Parallel access array with dedicated parity disk, parity disk enthält Summeninformation zum Errechnen der verorenen Bits auf Datenplatte
- 4: Striped array, independent disks, dedicated parity disk; größere Datenblöcke der Paritätsinformationen, Datenübertragungsgeschwindigkeit durch
Datenübertragungsgeschwindigkeit der Paritätsplatte begrenzt, fest definierte Paritätsplatte
- 5: Striped array, independent disks, distributed parity, Nutzdaten auf alle Platten verteilt, Paritätsdaten gleichmäßig verteilt, Parallelisierung nicht
möglich
- 6: Striped array, independent disks, dual distributed parity, survives 2 erasures, parity block in different place each stripe  

*RAID definitions:*
- Strip size (Chunk, Stripe): e.g. 256 KiB
- Stripe (Stride) size: Capacity of full stripe
- Spare drive: Standby drive, in case of disk failure in an array
- Rebuild Time: duration of exposure until spare has migrated into failing array

*RAID 5 vs. RAID 10:* RAID 5, RAID 10 comparable peroformance regarding read operations, RAID5 better for large-block seuential writes, RAID 10 better
for small-block random writes; RAID 5 good choice for high availability, fewer writes than reads, RAID 10 fault-tolerant, performance critical, write sensitive
but high random write percentage

*Ende Vorlesung vom 7.11.2018*

**Components of Intelligent Storage Systems**: wenig "intelligent", unterstützt dabei große Anzahl an physical disks in unterschiedliche
RAID Systeme abzubilden; Vorteile: increased capacity, improved performance, easier data management, improved data availability/protection
- *Front End:* Configuration Richtung Netzwerk/Host
- *Cache:* write operations:
    - Write-through Cache: direktes Schreiben in den HS ("am Cache vorbei"), langsamer, in billigeren Systemen
    - Write-back Cache: Daten nicht direkt in den Speicher geschrieben, sondern in den Cache, Daten in HS und Cache sind inkonsistent, commit wird
     gegeben, wenn Daten im Cache sind, aufwändigere Technik (teurere Systeme) aber bessere Performance
- *Back End:* Configuration zu physical disks
- *Physical Disks:*

**Caching Algorithmen**: Least Recently Used (LRU)/ Least Recently Written (LRW), bessere Performance durch write-cache management

**Cache Data Protection**: protecting cache data against failure:
- *Cache mirroring:* writes to cache are held in two different memory locations on two different memory cards
- *Cache vaulting:* cache exposed to risk of uncommitted data → power failure: uncommitted data is dumped to dedicated set of drives (= vault
drives)

**Logical Units**: physical disks combined to logical units and deliver to host as unit; LUN = logical unit number; man 
"sieht" nach außen nur LU und nicht physikalische Disks, einfach um im laufenden system RAID systeme auszutauschen; 
LUN Masking Zugriffsrechtschutz; Zugriffe auf LUNs immer in Blöcken unabhängig von Repräsentation nach außen, "hinten" auf Disks immer Standard

**High-end Storage Systems**: for enterprises, large storage capacity, huge cache to service host I/Os, fault tolerance architecture, high scalability
Active-Active Configuration: Storage Array with two connections to host; Storage Array alles gedoppelt: Controller, Platten, Stromanschlüsse 
→ sehr hohe Ausfallsicherheit

**Mid-end Storage Systems**: less scalable, eine Verbindung active (darüber geht Host I/O) und eine passiv, welche dafür da ist, wenn aktive Verbindung
failed 

> high-end SS und mid-end SS Preisunterschied kommt hauptsächlich von teurer Software (Firmware)

### Storage Connectivity and Networking
**Direct Attached Storage (DAS)**: [Wikipedia](https://de.wikipedia.org/wiki/Direct_Attached_Storage): "an einen einzelnen 
Rechner angeschlossene Festplatten, die sich in einem separaten Gehäuse befinden"  
*Vorteile:* lokale Datenhaltung, schnelles Entwickeln fürkleine Umgebungen, einfacher Deploy, Zuverlässigkeit, 
niedrige Kosten und niedrige Komplexität  
*Probleme:* begrenzte Skalierbarkeit, Downtime bei Wartung, limitiertes Ressourcensharing

**Small Computer System Interface (SCSI)**: [Wikipedia](https://de.wikipedia.org/wiki/Small_Computer_System_Interface): "Familie von 
standardisierten Protokollen und Schnittstellen für die Verbindung und Datenübertragung zwischen Peripheriegeräten und Computern"  
*Adressierung:* SCSI initiator port and SCSI target port has SCSI port indetifier, logical unit is assigned a LUN within SCSI 
target device, LU has also LUN, SCSI target device with SAS target ports has device name  
→ *Address = Bus : Target ID : LUN*  
*Commands:* 
- Non-data commands (N): no data transferred
- write commands (W): data transferred from initiator to target, write data = Data-Out
- read commands (R): data transferred from target to initiator, read data = Data-In
- bidirectional commands (B): data transferred in both directions, Data-In and Data-Out

*Ende der Vorleseung vom 21.11.2018*
