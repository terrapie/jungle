
## 🔥 1. IPv4

**IPv4-Adresse** = 32 Bit, 4 Zahlen (0–255), getrennt mit Punkt.
Beispiel: `192.168.10.25`

Eine IP-Adresse hat **zwei Teile**:
- **Netzanteil** = in welchem Netz bin ich?
- **Hostanteil** = welches Gerät bin ich in diesem Netz?

Die **Subnetzmaske** zeigt, wo der Netzanteil endet.

### Wichtige Adressen

| Name | Bedeutung |
|---|---|
| Netzwerkadresse | Erste Adresse im Netz. Kein Gerät darf sie haben. |
| Broadcastadresse | Letzte Adresse im Netz. Geht an **alle** Geräte. Kein Gerät darf sie haben. |
| Hostadressen | Alles dazwischen. Diese bekommen die Geräte. |

### Private IP-Adressen (nur im eigenen Netz, nicht im Internet)

| Bereich                       | Präfix           | Klasse |
| ----------------------------- | ---------------- | ------ |
| 10.0.0.0 – 10.255.255.255     | `10.0.0.0/8`     | A      |
| 172.16.0.0 – 172.31.255.255   | `172.16.0.0/12`  | B      |
| 192.168.0.0 – 192.168.255.255 | `192.168.0.0/16` | C      |

Sonderadressen:
- `127.0.0.1` = **Loopback** (mein eigener PC)
- `169.254.x.x` = **APIPA** (kein DHCP erreichbar, siehe unten)

---

## 🔥 2. Subnetting

### Präfix und Subnetzmaske

**Präfix** `/24` = 24 Bit gehören zum Netz.

| Präfix | Subnetzmaske | Blockgröße | Hosts |
|---|---|---|---|
| /24 | 255.255.255.0 | 256 | 254 |
| /25 | 255.255.255.128 | 128 | 126 |
| /26 | 255.255.255.192 | 64 | 62 |
| /27 | 255.255.255.224 | 32 | 30 |
| /28 | 255.255.255.240 | 16 | 14 |
| /29 | 255.255.255.248 | 8 | 6 |
| /30 | 255.255.255.252 | 4 | 2 |

**Formel für Hosts:**

```
Hosts = 2^(32 − Präfix) − 2
```

Die **−2** sind Netzwerkadresse und Broadcastadresse.

Beispiel /26: 2^(32−26) = 2^6 = 64 → 64 − 2 = **62 Hosts**

> [!tip] Merken
> z.B. /27 -> 27 x 1
> 11111111.11111111.11111111.11100000
> 5 x 0 -> 2^5 = 32 - 2 = 30 Hosts

### Netzwerk- und Broadcastadresse bestimmen (Schritt für Schritt)

1. Präfix → Blockgröße aus der Tabelle nehmen.
2. Die Netzadressen zählen in Blockgröße-Schritten: 0, 64, 128, 192 …
3. Schauen: In welchem Block liegt die Host-Zahl?
4. **Netzwerkadresse** = Anfang vom Block.
5. **Broadcastadresse** = Ende vom Block (nächster Anfang − 1).
6. **Hostadressen** = alles dazwischen.

**Beispiel 1:** `192.168.10.77 /26`

- Blockgröße = 64
- Blöcke: 0–63, 64–127, 128–191, 192–255
- 77 liegt im Block 64–127
- Netzwerkadresse: `192.168.10.64`
- Broadcastadresse: `192.168.10.127`
- Hosts: `192.168.10.65` bis `192.168.10.126` (62 Hosts)

**Beispiel 2:** `10.5.20.130 /25`

- Blockgröße = 128
- Blöcke: 0–127, 128–255
- Netzwerkadresse: `10.5.20.128`
- Broadcastadresse: `10.5.20.255`
- Hosts: `10.5.20.129` bis `10.5.20.254` (126 Hosts)

> [!tip] Merken
> Beispiel 2: 10.5.20.130 /25
> 11111111.11111111.11111111.10000000
> 2^7 = 128
> Erster Teil -> 0 - 127 dann 128 bis (127 + 128 = 255)
> 130 liegt in 128 - 255 Teil, also:
> Netzwerkadresse -> .128
> Broadcastadresse -> .255
> Hosts dazwischen

### Sind zwei Geräte im selben Netz?

Beide müssen **dieselbe Netzwerkadresse** haben.

`192.168.10.25 /26` und `192.168.10.70 /26`
- Erstes Gerät: Block 0–63
- Zweites Gerät: Block 64–127
- → **Nicht** im selben Netz. Sie brauchen einen Router.

### Netz in Subnetze teilen

Aufgabe: `192.168.1.0 /24` in **4 Subnetze** teilen.

- 4 Subnetze = 2 Bit mehr → `/26`
- Blockgröße 64
- Subnetze:
  - `192.168.1.0 /26` (Hosts .1 – .62, Broadcast .63)
  - `192.168.1.64 /26` (Hosts .65 – .126, Broadcast .127)
  - `192.168.1.128 /26` (Hosts .129 – .190, Broadcast .191)
  - `192.168.1.192 /26` (Hosts .193 – .254, Broadcast .255)

> [!tip] Merken
> in 2 Subnetze teilen -> +1 Bit
> in 4 Subnetze teilen -> +2 Bits, usw.
> 11111111.11111111.11111111.00000000 /24
> 11111111.11111111.11111111.11000000 /26
> 2^6 = Blockgröße 64
> .64 Netzwerkadresse +64 = 128 -> nächste Netzwerkadresse, usw.
> 

### Welches Präfix brauche ich?

Aufgabe: Ich brauche **50 Hosts**.

- /27 hat nur 30 Hosts → zu klein
- /26 hat 62 Hosts → **passt**

Immer das **kleinste** Netz nehmen, das noch reicht.

---

## 🔥 3. IPv6

- **128 Bit** (IPv4: 32 Bit)
- **8 Blöcke**, jeder Block hat 4 Hexadezimal-Zeichen
- Getrennt mit **Doppelpunkt** (IPv4: Punkt)
- Hexadezimal = Zeichen `0–9` und `a–f`

Beispiel (ausgeschrieben):

```
2001:0db8:0000:0000:0000:0000:0000:0001
```

### Verkürzen (2 Regeln)

1. **Führende Nullen** in jedem Block weglassen.
2. **Eine** Folge von Null-Blöcken durch `::` ersetzen.

```
2001:0db8:0000:0000:0000:0000:0000:0001
→ 2001:db8:0:0:0:0:0:1        (Regel 1)
→ 2001:db8::1                 (Regel 2)
```

> [!warning] Achtung
> `::` darf nur **einmal** in einer Adresse stehen.
> Nehmen, wenn möglich, die **längste** Null-Folge.

### Wieder ausschreiben

`fe80::1` → Es fehlen Blöcke. Insgesamt müssen es 8 sein.

```
fe80::1
→ fe80:0000:0000:0000:0000:0000:0000:0001
```

Trick: Blöcke zählen. Was fehlt, sind Null-Blöcke. Jeder Block braucht 4 Zeichen.

### Wichtige Adresstypen

| Typ | Beginn | Bedeutung |
|---|---|---|
| Link-Local | `fe80::/10` | Nur im eigenen Netz. Hat jedes Gerät automatisch. |
| Globale Adresse | `2000::/3` (meist `2001:…`) | Im Internet nutzbar. |
| Loopback | `::1` | Mein eigener PC |

### IPv4 ↔ IPv6

| | IPv4 | IPv6 |
|---|---|---|
| Länge | 32 Bit | 128 Bit |
| Schreibweise | Dezimal | Hexadezimal |
| Trennzeichen | Punkt | Doppelpunkt |
| Adressen | ca. 4,3 Milliarden (zu wenig) | extrem viele |
| Broadcast | ja | **nein** |

Kurz: IPv6 gibt es, weil IPv4-Adressen **knapp** sind.

---

## 🔥 4. OSI-Modell

7 Schichten. **Von oben nach unten:**

| Schicht | Name | Beispiele |
|---|---|---|
| 7 | Anwendung | HTTP, HTTPS, DNS, DHCP |
| 6 | Darstellung | Verschlüsselung, Datenformate |
| 5 | Sitzung | Verbindung starten / beenden |
| 4 | Transport | TCP, UDP, Ports |
| 3 | Vermittlung | IP-Adresse, **Router** |
| 2 | Sicherung | MAC-Adresse, **Switch** |
| 1 | Bitübertragung | Kabel, Signale, Hub |

> [!tip] Eselsbrücke (von 7 nach 1)
> **A**lle **D**eutschen **S**tudenten **T**rinken **V**erschiedene **S**orten **B**ier

### Das musst du zuordnen können

- MAC-Adresse → **Schicht 2**
- Switch → **Schicht 2**
- IP-Adresse → **Schicht 3**
- Router → **Schicht 3**
- TCP / UDP → **Schicht 4**
- DNS / DHCP / HTTP → **Schicht 7**
- Kabel, Hub → **Schicht 1**

### Datenpakete haben Namen

| Schicht | Name |
|---|---|
| 4 | Segment |
| 3 | Paket |
| 2 | Frame |
| 1 | Bits |

---

## 🔥 5. Netzwerkkomponenten

| Gerät | Aufgabe |
|---|---|
| **Switch** | Verbindet Geräte **im selben Netz (LAN)**. |
| **Router** | Verbindet **verschiedene Netze** (z. B. LAN ↔ Internet). |
| **Access Point** | Gibt WLAN-Zugang. |
| **Netzwerkkarte (NIC)** | Verbindet den PC mit dem Netz. |
| **Modem** | Verbindung zum Provider. |
| **Firewall** | Kontrolliert den Datenverkehr (erlauben / blockieren). |

### Hub ↔ Switch

| Hub | Switch |
|---|---|
| Schicht 1 | Schicht 2 |
| Sendet Daten an **alle** Geräte | Sendet Daten nur an das **Zielgerät** |
| Langsam, unsicher | Schneller, besser |
| Veraltet | Standard heute |

Der Switch lernt die MAC-Adressen der Geräte und merkt sie sich.

### Router ↔ Switch

| Switch | Router |
|---|---|
| Arbeitet mit **MAC-Adressen** | Arbeitet mit **IP-Adressen** |
| Verbindet Geräte im **gleichen** Netz | Verbindet **verschiedene** Netze |
| Schicht 2 | Schicht 3 |

---

## 🔥 6. Netzwerkgrundkonfiguration

Ein PC braucht 4 Werte:

```
IP-Adresse:       192.168.10.25
Subnetzmaske:     255.255.255.0
Standardgateway:  192.168.10.1
DNS-Server:       192.168.10.1
```

| Wert | Wofür? |
|---|---|
| **IP-Adresse** | „Adresse" des PCs im Netz |
| **Subnetzmaske** | Zeigt, welcher Teil das Netz ist |
| **Standardgateway** | Ausgang in andere Netze (meist der Router) |
| **DNS-Server** | Macht aus Namen eine IP-Adresse |

> [!warning] Häufiger Fehler in Aufgaben
> Das Gateway muss **im selben Netz** liegen wie der PC.
> Wenn nicht → PC kommt nicht ins Internet.

---

## 🔥 7. DHCP

**DHCP** verteilt Netzwerk-Einstellungen **automatisch**.

DHCP gibt dem Client:
- IP-Adresse
- Subnetzmaske
- Standardgateway
- DNS-Server

### DORA (4 Schritte)

| Schritt | Wer? | Was? |
|---|---|---|
| **D**iscover | Client | „Ist hier ein DHCP-Server?" (an alle) |
| **O**ffer | Server | „Ich biete dir diese IP an." |
| **R**equest | Client | „Ja, ich nehme diese IP." |
| **A**cknowledge | Server | „Okay, die IP gehört dir." |

Wichtig:
- Die IP gilt nur für eine Zeit (**Lease Time**).
- Mit **Reservierung** bekommt ein Gerät immer dieselbe IP (z. B. Drucker).

### 🔥 APIPA

Wenn ein PC **keine** Antwort vom DHCP-Server bekommt, gibt er sich selbst eine Adresse:

```
169.254.x.x
```

> [!tip] Prüfungsfrage
> „PC hat 169.254.x.x" → **DHCP-Server nicht erreichbar**.
> Mögliche Gründe: Kabel ab, DHCP-Server aus, Switch kaputt.

---

## 🔥 8. DNS

**DNS** = Domain Name System.
Macht aus einem **Namen** eine **IP-Adresse**.

```
www.example.de
      ↓
93.184.216.34
```

- Vorgang heißt **Namensauflösung**.
- Der **DNS-Server** kennt die Zuordnung.
- Ohne DNS: Internet geht nur mit IP-Adressen (Namen gehen nicht).
- Test mit `nslookup`.

Typische Fehlersuche:
- `ping 8.8.8.8` geht, aber `ping www.google.de` geht nicht → **DNS-Problem**.

---

## 🔥 9. Netzwerkbefehle (Windows)

| Befehl | Was macht er? |
|---|---|
| `ping` | Testet: Antwortet das Gerät? Gibt es eine Verbindung? |
| `ipconfig /all` | Zeigt die Netzwerk-Einstellungen vom PC (IP, Maske, Gateway, DNS, MAC, DHCP) |
| `ipconfig /release` | Gibt die IP-Adresse zurück |
| `ipconfig /renew` | Holt neue IP vom DHCP-Server |
| `ipconfig /flushdns` | Löscht den DNS-Zwischenspeicher |
| `nslookup` | Prüft DNS (Name → IP) |
| `arp -a` | Zeigt die ARP-Tabelle (IP ↔ MAC) |
| `tracert` | Zeigt den Weg der Pakete (alle Router unterwegs) |

### Fehlersuche in dieser Reihenfolge

1. `ping 127.0.0.1` → Funktioniert meine Netzwerkkarte / mein TCP/IP?
2. `ping <eigene IP>` → Stimmt meine Konfiguration?
3. `ping <Gateway>` → Komme ich zum Router?
4. `ping 8.8.8.8` → Komme ich ins Internet?
5. `ping www.google.de` → Funktioniert DNS?

Wo es **zum ersten Mal** nicht mehr geht, liegt der Fehler.

### Ping-Meldungen

| Meldung | Bedeutung |
|---|---|
| Antwort von … | Verbindung okay |
| Zeitüberschreitung | Keine Antwort (Gerät aus, Firewall, Fehler) |
| Zielhost nicht erreichbar | Kein Weg zum Ziel (z. B. falsches Gateway) |

---

## 🟠 10. MAC-Adresse und ARP

**MAC-Adresse**
- Feste Hardware-Adresse der Netzwerkkarte
- 48 Bit = 6 Blöcke in Hexadezimal
- Beispiel: `00-1A-2B-3C-4D-5E`
- Die erste Hälfte zeigt den **Hersteller**
- Schicht 2

**IP-Adresse**
- Kann sich ändern
- Schicht 3

**ARP** (Address Resolution Protocol)
- Findet die **MAC-Adresse** zu einer **IPv4-Adresse** im lokalen Netz.
- Ablauf: PC fragt an **alle**: „Wer hat die IP 192.168.10.1?" → Das Gerät antwortet mit seiner MAC.
- Ergebnis steht in der ARP-Tabelle (`arp -a`).

---

## 🟠 11. Netzwerk-Topologien

| Topologie | Aussehen | Merkmal |
|---|---|---|
| **Stern** | Alle Geräte an **einem Switch** | Heute Standard. Ein Kabel kaputt → nur ein Gerät fällt aus. Switch kaputt → alles fällt aus. |
| Bus | Alle an **einem** Kabel | Veraltet. Kabel kaputt → alles fällt aus. |
| Ring | Geräte im Kreis | Selten |
| Baum | Mehrere Sterne verbunden | Große Netze |

Am wichtigsten: **Stern**.

---

## 🟠 12. Ethernet

- **Ethernet** = Standard für kabelgebundene Netze (LAN)
- Stecker: **RJ45**
- Kabel: **Twisted-Pair** (verdrillte Adernpaare)
- Maximale Länge: **100 m**

| Kabel | Geschwindigkeit (ungefähr) |
|---|---|
| CAT5e | 1 Gbit/s |
| CAT6 | 1 Gbit/s (bis 10 Gbit/s auf kurzer Strecke) |
| CAT6a / CAT7 | 10 Gbit/s |

Übertragungsgeschwindigkeiten:
- Fast Ethernet: **100 Mbit/s**
- Gigabit Ethernet: **1 Gbit/s**

> [!info] Du musst nicht alle IEEE-Standards auswendig lernen.

---

## 🟠 13. Netzwerkmedien

| Medium | Vorteile | Nachteile |
|---|---|---|
| **Kupfer** (Twisted-Pair, RJ45) | Billig, einfach | Störanfällig, max. 100 m |
| **Glasfaser** (LWL) | Große Entfernung, sehr schnell, **keine** Störung durch elektromagnetische Felder | Teurer |
| **WLAN** | Kabellos, praktisch | Alle teilen sich das Medium, langsamer, Störungen, Sicherheit wichtig |

WLAN kurz:
- Frequenzen: 2,4 GHz (weiter, langsamer) und 5 GHz (schneller, kürzere Reichweite)
- Name vom WLAN = **SSID**
- Sicherheit: **WPA2 / WPA3** (WEP ist unsicher)

---

## 🟠 14. TCP und UDP

| | TCP | UDP |
|---|---|---|
| Verbindung | **verbindungsorientiert** | **verbindungslos** |
| Zuverlässig | Ja | Nein (keine Garantie) |
| Reihenfolge | Wird kontrolliert | Nicht kontrolliert |
| Geschwindigkeit | Langsamer | **Schneller** (weniger Overhead) |
| Beispiele | Webseiten, E-Mail, Dateien | Video-Streaming, Telefonie, DNS |

Ports (Türen für Dienste):

| Dienst | Port |
|---|---|
| HTTP | 80 |
| HTTPS | 443 |
| DNS | 53 |
| DHCP | 67 / 68 |
| FTP | 21 |
| SSH | 22 |
| SMTP (E-Mail senden) | 25 |
| RDP (Remote Desktop) | 3389 |

---

## 🟠 15. Netzwerkprotokolle (nur diese!)

| Protokoll | Aufgabe | Schicht |
|---|---|---|
| **IP** | Adressierung, Weg finden | 3 |
| **ICMP** | Fehlermeldungen, `ping` | 3 |
| **ARP** | IP → MAC | 2 / 3 |
| **Ethernet** | Übertragung im LAN | 1 / 2 |
| **TCP** | Sichere Übertragung | 4 |
| **UDP** | Schnelle Übertragung | 4 |
| **DNS** | Name → IP | 7 |
| **DHCP** | Automatische IP | 7 |
| **HTTP / HTTPS** | Webseiten (HTTPS = verschlüsselt) | 7 |

---

## 🟠 16. Übertragungsrate und Übertragungszeit

Wichtig: **1 Byte = 8 Bit**

```
Zeit = Datenmenge (in Bit) ÷ Übertragungsrate (in Bit/s)
```

**Beispiel:** 500 MB über 100 Mbit/s.

1. MB → Mbit: 500 × 8 = 4.000 Mbit
2. Zeit = 4.000 Mbit ÷ 100 Mbit/s = **40 Sekunden**

> [!warning] Achtung bei Einheiten
> - `MB` = Megabyte
> - `Mbit` = Megabit
> - Großes **B** = Byte. Kleines **bit** = Bit.
> - Erst alles in dieselbe Einheit umrechnen!

---

## 🟡 17. Client-Server ↔ Peer-to-Peer

| Client-Server | Peer-to-Peer (P2P) |
|---|---|
| Ein zentraler **Server**, viele **Clients** | Alle Geräte sind gleich |
| Zentrale Verwaltung, sicherer | Kein Server nötig, einfach |
| Für Firmen | Für sehr kleine Netze |

## 🟡 18. Servertypen

| Server | Aufgabe |
|---|---|
| Fileserver | Speichert Dateien |
| Printserver | Verwaltet Drucker |
| Webserver | Stellt Webseiten bereit |
| Datenbankserver | Speichert Datenbanken |
| DNS-Server | Namen → IP |
| DHCP-Server | Verteilt IP-Adressen |

## 🟡 19. LAN / WAN / WLAN

- **LAN** = lokales Netz (z. B. Firma, Zuhause)
- **WAN** = großes Netz über weite Strecken (z. B. Internet)
- **WLAN** = kabelloses lokales Netz

## 🟡 20. Backup

| Art | Was wird gesichert? | Sichern | Zurückholen |
|---|---|---|---|
| **Vollbackup** | Alles | Langsam, viel Platz | Einfach (nur 1 Backup) |
| **Inkrementell** | Nur Änderungen seit dem **letzten Backup** (egal welche Art) | Schnell, wenig Platz | Langsam (alle Backups nötig) |
| **Differentiell** | Alle Änderungen seit dem **letzten Vollbackup** | Mittel | Mittel (Voll + letztes Diff) |

## 🟡 21. RAID (nur kurz)

> [!info] Seit 2025 nicht mehr Pflicht in der AP1. Nur kurz anschauen.

| RAID | Idee |
|---|---|
| RAID 0 | Schneller, **keine** Sicherheit |
| RAID 1 | Spiegelung, 1 Platte darf ausfallen |
| RAID 5 | Mindestens 3 Platten, 1 darf ausfallen |

## 🟡 22. Stromversorgung / Green-IT

```
Energie (kWh) = Leistung (kW) × Zeit (h)
Kosten (€)    = Energie (kWh) × Preis pro kWh
```

**Beispiel:** Gerät mit 200 W, 24 h am Tag, 30 Tage, 0,30 €/kWh.

1. 200 W = 0,2 kW
2. 0,2 kW × 24 h × 30 Tage = 144 kWh
3. 144 kWh × 0,30 € = **43,20 €**

Green-IT Ideen:
- Energiesparende Geräte kaufen
- Geräte ausschalten, Standby vermeiden
- Server zusammenlegen (Virtualisierung)

## 🟡 23. Kurz erklärt

- **Rechenzentrum** = Gebäude mit vielen Servern (Strom, Kühlung, Sicherheit, Ausfallschutz).
- **Strukturierte Verkabelung** = Ordentliche, feste Verkabelung im Gebäude in 3 Bereichen: Gelände (Primär), Gebäude (Sekundär), Etage (Tertiär).

---

## ✅ Lern-Checkliste

### 🔥 Muss ich können
- [ ] Subnetting-Tabelle (/24 bis /30) auswendig
- [ ] Netzwerk-, Broadcastadresse und Hosts berechnen
- [ ] Privaten IP-Bereiche kennen
- [ ] IPv6 kürzen und wieder ausschreiben
- [ ] Link-Local `fe80::/10` kennen
- [ ] 7 OSI-Schichten in richtiger Reihenfolge
- [ ] Switch / Router / MAC / IP / TCP / DNS den Schichten zuordnen
- [ ] Switch, Router, Access Point, Firewall erklären
- [ ] IP, Maske, Gateway, DNS erklären
- [ ] DHCP mit DORA erklären
- [ ] APIPA `169.254.x.x` erkennen
- [ ] DNS erklären
- [ ] `ping`, `ipconfig /all`, `nslookup`, `arp -a` erklären

### 🟠 Wichtig
- [ ] MAC ↔ IP, ARP
- [ ] Topologien (vor allem Stern)
- [ ] Ethernet, RJ45, Twisted-Pair, CAT
- [ ] Kupfer / Glasfaser / WLAN
- [ ] TCP ↔ UDP
- [ ] Protokoll-Tabelle
- [ ] Übertragungszeit berechnen

### 🟡 Kurz anschauen
- [ ] Client-Server / P2P
- [ ] Servertypen
- [ ] LAN / WAN
- [ ] Backup-Arten
- [ ] Stromkosten berechnen
