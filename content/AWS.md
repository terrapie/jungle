## 26.05.2026

![[Pasted image 20260526120839.png]]

![[Pasted image 20260526102714.png]]
z.B. https://contabo.com/de/


**⚙️ vCPU *(Virtual CPU)***

**Das ist kein Hosting-Typ – das ist eine Einheit.**

CPU = Prozessor (das „Gehirn" des Computers). vCPU = ein **virtueller** Prozessor-Kern.

Wenn ein vServer sagt: *„2 vCPU"* → du bekommst **2 virtuelle Rechenkerne**. Mehr vCPU = schneller, mehr kann gleichzeitig laufen.

##### ☆ skillbuilder.aws ☆ AWS Cloud Practitioner Essentials ☆ AWS Cloud Quest ☆
https://skillbuilder.aws/learn


![[Pasted image 20260526110333.png]]

![[Pasted image 20260526110946.png]]


*Aufgabe Modul 1 im Skill Builder*

*Was ist eine AWS Region, eine Verfügbarkeitszone = AZ = Availability Zone  
und was ist ein Data Center?*

*Was sind AWS Edge Locations?*

**Cloud Computing in der Praxis: Wir erklären Cloud Computing**  

https://www.youtube.com/watch?v=NoABtadYfxo&t=13s

**CLOUD (COMPUTING) einfach erklärt**  

https://www.youtube.com/watch?v=ehg1CjYH3Mg&list=PLK9Fkt4sz0MkPrMNNntru8E1p8tGU9m31&index=12

**Regionen und Availability Zones**  

https://aws.amazon.com/de/about-aws/global-infrastructure/regions_az/


---

### Was ist Cloud Computing?

Cloud Computing ist die bedarfsabhängige Bereitstellung von IT-Ressourcen über das Internet zu nutzungsabhängigen Preisen. Statt physische Rechenzentren und Server zu erwerben, zu besitzen und zu unterhalten, können Sie über einen Cloud-Anbieter wie Amazon Web Services (AWS) nach Bedarf auf Technologie-Services wie beispielsweise Rechenleistung, Speicher und Datenbanken zugreifen.

### Modell der geteilten Verantwortung

![[Pasted image 20260526161315.png]]

Sicherheit und Compliance stellen eine geteilte Verantwortung zwischen AWS und dem Kunden dar. Dieses geteilte Modell bedeutet für den Kunden eine Arbeitsentlastung, da die Komponenten des Hostbetriebssystems und der Virtualisierungsebene von AWS ausgeführt, verwaltet und gesteuert werden und zudem für die physische Sicherheit der Standorte gesorgt wird, an denen die Services ausgeführt werden. Der Kunde ist für das Gastbetriebssystem und dessen Verwaltung (einschließlich Updates und Sicherheitspatches), für andere damit verbundene Anwendungssoftware sowie für die Konfiguration der von AWS bereitgestellten Firewall für die Sicherheitsgruppe verantwortlich. Kunden sollten sich gut überlegen, welche Services sie auswählen, da ihre Zuständigkeiten von den genutzten Services, von deren Integration in ihre IT-Umgebung sowie von den geltenden Gesetzen und Vorschriften abhängen. Die Art und Weise dieser geteilten Verantwortlichkeit gewährleistet die Flexibilität und Kundenkontrolle, durch die die Bereitstellung ermöglicht wird. Wie im Diagramm unten ersichtlich wird diese Differenzierung der Verantwortlichkeit häufig als „Sicherheit der Cloud“ im Gegensatz zu „Sicherheit in der Cloud“ bezeichnet.


### AWS Global Infrastructure

The AWS Cloud spans 123 Availability Zones within 39 Geographic Regions, with announced plans for 7 more Availability Zones and 2 more AWS Regions in the Kingdom of Saudi Arabia, and Chile.


### AWS-Infrastrukturangebote

#### Regionen

Bei AWS sprechen wir oft von Regionen, einem physischen Standort, an dem wir Rechenzentrums-Cluster betreiben. Eine logische Gruppe von Rechenzentren heißt bei uns Availability Zone. Jede AWS-Region besteht aus mindestens drei isolierten und physisch getrennten AZs innerhalb eines geographischen Bereichs. Im Gegensatz zu anderen Cloud-Anbietern, die eine Region oft als einzelnes Rechenzentrum definieren, bietet das Konzept mehrerer AZs pro AWS-Region klare Vorteile. Jede AZ verfügt über unabhängige Stromversorgung, Kühlung sowie physische Sicherheit und ist über redundante, extrem latenzarme Netzwerke verbunden. AWS-Kunden, die den Schwerpunkt auf hohe Verfügbarkeit legen, können ihre Anwendungen in mehreren AZs ausführen, um eine noch höhere Fehlertoleranz zu erzielen. AWS-Infrastrukturregionen entsprechen den höchsten Sicherheits-, Compliance- und Datenschutzstandards.

AWS ist weltweit an mehr Standorten vertreten als alle anderen Cloud-Anbieter. Um dies und eine weltweite Serviceabdeckung zu gewährleisten, eröffnet AWS regelmäßig neue Regionen. AWS-Standorte finden sich in zahlreichen geografischen Regionen, unter anderem in Nordamerika, Südamerika, Europa, China, Asien-Pazifik und im Nahen Osten.

#### Availability Zones

Eine Availability Zone (AZ) ist ein oder mehrere diskrete Rechenzentren mit redundanter Stromversorgung, Vernetzung und Konnektivität in einer AWS Region. Mithilfe dieser Availability Zones (AZs) können Sie Produktionsanwendungen und Datenbanken betreiben, die verfügbarer, fehlertoleranter und skalierbarer sind, als dies von einem einzigen Rechenzentrum aus möglich wäre. Alle AZs in einer AWS-Region sind mit einem Netzwerk mit hoher Bandbreite und niedriger Latenz über eine vollständig redundante, dedizierte Metro-Glasfaser-Leitung miteinander verbunden, die einen hohen Durchsatz und eine niedrige Latenz zwischen den AZ ermöglicht. Der gesamte Datenverkehr zwischen AZs wird verschlüsselt. Die Netzwerkleistung ist ausreichend, um eine synchrone Replikation zwischen AZs zu erreichen. AZs vereinfachen das Partitionieren von Anwendungen für hohe Verfügbarkeit. Wenn die Partition einer Anwendung auf mehrere AZs verteilt ist, sind Unternehmen besser vor Naturereignissen wie Stromausfällen, Blitzeinschlägen, Tornados, Erdbeben usw. isoliert und geschützt. Die AZs sind physisch durch eine große Entfernung, vieler Kilometer, von jeder anderen AZ getrennt, obwohl alle innerhalb von 100 km voneinander liegen.

https://aws.amazon.com/de/about-aws/global-infrastructure/regions_az/

---
## 27.05.2026

### AWS Well-Architected Framework
ist ein Leitfaden von Amazon Web Services, der Best Practices und Designprinzipien für den Aufbau sicherer, leistungsfähiger, zuverlässiger und kosteneffizienter Cloud-Architekturen beschreibt.

Die **6 Säulen des AWS Well-Architected Framework**:

1. **Operational Excellence** – Betrieb und Überwachung von Systemen optimieren
2. **Security** – Daten, Systeme und Assets schützen
3. **Reliability** – Ausfallsicherheit und Wiederherstellung gewährleisten
4. **Performance Efficiency** – Ressourcen effizient einsetzen
5. **Cost Optimization** – Kosten minimieren ohne Qualitätsverlust
6. **Sustainability** – Umweltauswirkungen der Cloud-Nutzung reduzieren


*Welche Formen der Skalierung gibt es bei AWS?*  
*z.B. ich habe eine EC2-Instanz (vServer) und dieser ist zu langsam geworden.*

### Formen der Skalierung

**Vertical Scaling (Scale Up)** → Du nimmst deinen einen Server und machst ihn stärker – wie ein Auto mit einem größeren Motor ausstatten.

**Horizontal Scaling (Scale Out)** → Du fügst einfach mehr Server hinzu – wie statt einem Kassierer drei Kassen gleichzeitig öffnen.

**Elastic Load Balancing (ELB)**
Stell dir vor, du hast 3 Server – der Load Balancer steht davor und verteilt die eingehenden Anfragen gleichmäßig auf alle drei.
→ Kein Server wird überlastet, und wenn einer ausfällt, leiten die anderen den Traffic weiter.
Kurz: **Verkehrsregler für Server.** 🚦


*Was ist AWS Lambda und wofür könnte man dieses nutzen?*  

### AWS Lambda
ist ein Dienst, bei dem du **Code ausführst ohne einen Server zu verwalten** – AWS kümmert sich um alles im Hintergrund.

Du zahlst nur, wenn der Code tatsächlich läuft.

**Beispiele:**
- Bild wird hochgeladen → Lambda verkleinert es automatisch
- Bestellung kommt rein → Lambda schickt eine Bestätigungs-E-Mail
- Bestimmte Uhrzeit → Lambda startet automatisch einen Bericht
Kurz: **Code on demand – kein Server, kein Stress.** ⚡


*Was ist ein Container und warum nehme ich keine vServer?*

Ein Container ist wie ein **Päckchen**, das deinen Code + alle benötigten Abhängigkeiten enthält – läuft überall gleich, egal auf welchem System.

![[Pasted image 20260527104648.png]]

Kurz: vServer = ganzes Haus mieten. Container = nur ein Zimmer nutzen. 🏠

---
## 28.05.2026


AWS Outposts nutzt du, wenn du AWS-Infrastruktur und AWS-Services **im eigenen Rechenzentrum oder vor Ort** betreiben willst — aber trotzdem mit der AWS-Cloud verbunden bleiben möchtest.


*Was ist und wie funktioniert ein Content Delivery Network (CDN) ?*

### Was ist ein CDN?

Ein CDN ist ein **weltweites Netzwerk von Servern**, das Inhalte näher zum Nutzer bringt.

**Wie funktioniert es?**

Ohne CDN:
> Nutzer in Tokyo → fragt Server in Frankfurt → langsam 🐢

Mit CDN:
> Nutzer in Tokyo → fragt nächsten CDN-Server in Tokyo → schnell ⚡

Die Inhalte (Bilder, Videos, HTML) werden auf vielen Servern weltweit **zwischengespeichert (gecacht)**.

Bei AWS heißt der CDN-Dienst: **Amazon CloudFront** 🌍

- CDN speichert statische Inhalte (Bilder, Videos, CSS) auf Servern weltweit
- Ohne CDN: alle Nutzer verbinden sich mit deinem einen Server (z.B. Frankfurt)
- Mit CloudFront: Inhalte werden automatisch global verteilt – unabhängig von deiner gewählten Region
- Statische Inhalte werden **gecacht**, dynamische Inhalte werden **schneller übertragen**
- CDN verteilt nur **deine** Inhalte – nicht die Daten der Kunden

### Point-to-Site vs. Site-to-Site

**Point-to-Site VPN** Ein einzelner Nutzer (z.B. du zuhause) verbindet sich sicher mit dem Firmennetzwerk. → **1 Person ↔ Netzwerk**

**Site-to-Site VPN** Zwei ganze Netzwerke werden miteinander verbunden (z.B. Büro Berlin ↔ Büro München). → **Netzwerk ↔ Netzwerk**

### Security groups and Network ACLs

![[Pasted image 20260528120323.png]]

**Stateful vs Stateless:**

- **Stateful** (Security Group) – Antwort kommt automatisch durch, keine extra Regel nötig
- **Stateless** (ACL) – Antwort braucht eine eigene Regel, sonst blockiert ✋

Kurz: Security Group = Türsteher am Server, ACL = Türsteher am Stadtviertel 🏘️

![[Pasted image 20260528121632.png]]

*AWS Skillbuilder bis Modul 5 - Globale Netzwerke (also bis DNS)*

*Was ist ein DNS-Server?*
