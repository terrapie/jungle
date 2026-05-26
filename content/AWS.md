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

Cloud Computing in der Praxis: Wir erklären Cloud Computing
https://www.youtube.com/watch?v=NoABtadYfxo&t=13s

CLOUD (COMPUTING) einfach erklärt
https://www.youtube.com/watch?v=ehg1CjYH3Mg&list=PLK9Fkt4sz0MkPrMNNntru8E1p8tGU9m31&index=12

Regionen und Availability Zones
https://aws.amazon.com/de/about-aws/global-infrastructure/regions_az/


## Modul 1

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

#### Local Zones

[AWS Local Zones](https://aws.amazon.com/de/about-aws/global-infrastructure/localzones/) bringen Rechenleistung, Speicher, Datenbanken und andere ausgewählte AWS-Services näher an die Endnutzer. Mit lokalen AWS-Zonen können Sie Ihren Endnutzern ganz einfach anspruchsvolle Anwendungen mit Latenz im einstelligen Millisekundenbereich bereitstellen, darunter die Erstellung von Medieninhalten, Echtzeit-Gaming, Reservoir-Simulationen, Electronic Design Automation und Machine Learning.

Jeder Standort einer lokalen AWS-Zone ist eine Erweiterung einer AWS-Region, in der Sie Ihre latenzanfälligen Anwendungen mit AWS-Services wie Amazon Elastic Compute Cloud, Amazon Virtual Private Cloud, Amazon Elastic Block Store, Amazon File Storage und Amazon Elastic Load Balancing in geografischer Nähe zum Endnutzer betreiben können. AWS Local Zones bieten eine sichere Verbindung mit hoher Bandbreite zwischen lokalen Workloads und denen in der AWS-Region, sodass Sie eine nahtlose Verbindung zu allen regionalen Services über dieselben APIs und Toolsets herstellen können.

#### AWS Outposts

[AWS Outposts](https://aws.amazon.com/de/outposts/) bieten native AWS-Services, Infrastruktur und Betriebsmodelle für praktisch jedes Rechenzentrum, jede Co-Location oder jede On-Premises-Einrichtung. Sie können dieselbe(n) AWS-APIs, Tools und Infrastruktur On-Premises und in der AWS Cloud verwenden, um ein wirklich konsistentes Hybrid-Erlebnis zu liefern. AWS Outposts sind für vernetzte Umgebungen konzipiert und können zur Unterstützung von Workloads verwendet werden, die aufgrund von geringer Latenz oder lokalen Datenverarbeitungsanforderungen lokal bleiben müssen.

#### Services

AWS bietet eine breite Palette an globalen cloudbasierten Produkten wie Computing, Speicher, Datenbanken, Analytik, Netzwerke, Machine Learning und KI, Mobilgeräte, Entwickler-Tools, IoT, Sicherheit, Unternehmensanwendungen und vieles mehr. 

Die folgenden Kernservices sind in allen Region-Einführungen enthalten: Access Analyzer, Amazon API Gateway, AWS AppConfig, AWS Application Auto Scaling, Amazon Application Recovery Controller, Amazon Aurora, AWS Batch, AWS Certificate Manager (ACM), AWS Cloud Map, AWS CloudFormation, AWS CloudTrail, Amazon CloudWatch, Amazon CloudWatch Events, Amazon CloudWatch Logs, AWS CodeDeploy, AWS Config, AWS Database Migration Service (AWS DMS), AWS Direct Connect, Amazon DynamoDB, Amazon EC2 Auto Scaling, Amazon EKS, Amazon Elastic Container Registry, Amazon Elastic Container Service, Elastic Block Store (EBS), Elastic Compute Cloud (EC2), Elastic Load Balancing (ELB), Amazon ElastiCache, Amazon EMR, Amazon EventBridge, AWS Fargate, AWS-Servicestatus-Dashboard, AWS Identity & Access Management (IAM), AWS Key Management Service (AWS KMS), Amazon Kinesis Streams, AWS Lambda, AWS-Managementkonsole, AWS Marketplace, Amazon OpenSearch Service, AWS PrivateLink, Amazon Redshift, Amazon Relational Database Service (Amazon RDS), Amazon Route 53, AWS Secrets Manager, AWS Security Token Service (AWS STS), Service Quotas, Amazon Simple Notification Service (Amazon SNS), Amazon Simple Queue Service (Amazon SQS), Amazon Simple Storage Service (Amazon S3), Amazon Simple Workflow Service (Amazon SWF), AWS Site-to-Site VPN, AWS Step Functions, AWS Support, AWS Systems Manager (SSM), AWS Trusted Advisor, Amazon Virtual Private Cloud (VPC), AWS X-Ray

Darüber hinaus werden die folgenden Services in der Regel innerhalb von 12 Monaten nach dem Start einer neuen Region eingeführt: Amazon Athena, AWS Backup, Amazon CloudFront, Amazon Cognito, AWS Control Tower, AWS DataSync, AWS Directory Service, EC2 Image Builder, Amazon Elastic File System (Amazon EFS), Amazon Kinesis Data Firehose, Firewall Management Service (FMS), Amazon FSx, AWS Glue, Amazon GuardDuty, AWS IAM Identity Center, AWS Lake Formation, AWS License Manager, Amazon Managed Service für Apache Flink (MSF), Amazon Managed Streaming für Kafka (MSK), Amazon MQ, AWS Organizations, AWS Private Certificate Authority, AWS Resource Access Manager (RAM), AWS Resource Groups, Amazon SageMaker, AWS Security Hub, AWS Shield Advanced, AWS Storage Gateway, AWS Transfer Family, AWS Transit Gateway, AWS WAF

Kunden haben die Möglichkeit, ihr Interesse an der Bereitstellung in ihrer lokalen Region mitzuteilen, Service-Roadmap-Informationen anzufordern oder Einblicke in die Serviceunabhängigkeit (unter der NDA) [durch die Kontaktaufnahme zu dem jeweils zuständigen AWS-Vertriebsmitarbeiter](https://aws.amazon.com/de/contact-us/?p=ugi) zu erhalten.