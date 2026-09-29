### 1. Schutzziele der Informationssicherheit

**Aufgabe:** Nenne die drei Schutzziele und erkläre sie.

| Schutzziel          | Bedeutung                                        |
| ------------------- | ------------------------------------------------ |
| **Vertraulichkeit** | Nur berechtigte Personen haben Zugriff.          |
| **Integrität**      | Daten werden nicht unerlaubt verändert.          |
| **Verfügbarkeit**   | Daten und Systeme sind da, wenn ich sie brauche. |
|                     |                                                  |

**Aufgabe:** Erkenne das verletzte Schutzziel im Beispiel.

- Ein Mitarbeiter ohne Berechtigung liest Gehaltsdaten.
  → **Vertraulichkeit** ist verletzt.
- Ein Angreifer ändert Rechnungsbeträge.
  → **Integrität** ist verletzt.
- Der Server fällt aus. Niemand kann arbeiten.
  → **Verfügbarkeit** ist verletzt.

> [!tip] Merkhilfe
> **CIA** = Confidentiality, Integrity, Availability

---

### 2. Schutzbedarf

**Aufgabe:** Nenne die Stufen des Schutzbedarfs.

- **normal**
- **hoch**
- **sehr hoch**

**Aufgabe:** Ordne die Information dem Schutzbedarf zu.

| Information | Schutzbedarf |
|---|---|
| öffentliche Firmenbroschüre | normal |
| interne Kundendaten | hoch |
| Gehaltsdaten | hoch / sehr hoch |
| medizinische Daten | sehr hoch |

> [!warning] Wichtig
> Nur die Tabelle lernen reicht nicht. In der Prüfung gibt es eine Situation. Ich muss den Schutzbedarf **begründen**.
> Frage dazu: *Wie groß ist der Schaden, wenn etwas passiert?*

---

### 3. Schadensszenarien

**Aufgabe:** Beschreibe, was passiert, wenn …

| Fall | Betroffenes Schutzziel |
|---|---|
| Daten werden gestohlen (Datenleck) | Vertraulichkeit |
| Daten werden verändert | Integrität |
| System ist nicht erreichbar | Verfügbarkeit |
| Daten gehen verloren | Verfügbarkeit (und oft Integrität) |

**Regel:** Schaden → betroffenes Schutzziel

---

### 4. Bedrohung, Schwachstelle, Risiko

**Aufgabe:** Erkläre die drei Begriffe.

| Begriff | Bedeutung |
|---|---|
| **Bedrohung** | Eine mögliche Gefahr von außen. |
| **Schwachstelle** | Ein schwacher Punkt im System. |
| **Risiko** | Möglicher Schaden durch eine Bedrohung. |

**Aufgabe:** Ordne den Satz dem richtigen Begriff zu.

- Der Server hat ein Betriebssystem ohne Updates.
  → **Schwachstelle**
- Ein Hacker versucht, den Server anzugreifen.
  → **Bedrohung**
- Durch den Angriff könnten Firmendaten gestohlen werden.
  → **Risiko** / Schadensszenario

> [!tip] Merkhilfe
> Schwachstelle = *Tür ist offen*
> Bedrohung = *Einbrecher kommt*
> Risiko = *Einbrecher nimmt etwas mit*

---

### 5. Technische und organisatorische Maßnahmen (TOM)

**Aufgabe:** Ordne die Maßnahme zu: technisch oder organisatorisch?

**Technische Maßnahmen**

- Firewall
- Antivirus / Endpoint Protection
- Verschlüsselung
- Backup
- MFA (Multi-Faktor-Authentifizierung)
- Zugriffskontrolle
- Updates / Patches
- VPN

**Organisatorische Maßnahmen**

- Passwortregeln
- Berechtigungskonzept
- Schulungen
- Sicherheitsrichtlinien
- Notfallplan
- Datenschutzrichtlinien
- regelmäßige Backups als fester Prozess

**Aufgabe:** Wähle die passende Maßnahme zum Problem.

| Problem | Maßnahme |
|---|---|
| Fremde lesen Daten | Zugriffskontrolle, Verschlüsselung |
| Server hat Sicherheitslücken | Updates / Patches |
| Daten sind weg | Backup |
| Zugang mit gestohlenem Passwort | MFA |
| Mitarbeiter klicken auf Phishing | Schulung |

---

**Aufgabe:** Erkläre die Begriffe kurz.

- **Authentifizierung** = Wer bist du?
- **Autorisierung** = Was darfst du?
- **Passwort vs. MFA** = MFA nutzt mehr als einen Nachweis (z. B. Passwort + Code).
- **Rollen und Berechtigungen** = Jeder Mitarbeiter bekommt nur die Rechte für seine Rolle.
- **Need-to-know-Prinzip** = Jeder erfährt nur das, was er für seine Arbeit braucht.
- **Backup-Grundlagen** = Kopien der Daten an einem anderen Ort speichern.
- **Physische Sicherheit** = Schutz vor Ort, z. B. Schloss, Zutrittskontrolle, Serverraum.
- **Social Engineering** = Angreifer täuschen Menschen, um an Daten zu kommen.
- **Phishing** = Falsche E-Mails oder Webseiten stehlen Zugangsdaten.
- **Malware** = Schadsoftware (Viren, Trojaner usw.).
- **Ransomware** = Schadsoftware, die Daten verschlüsselt und Geld verlangt.
- **Updates / Patchmanagement** = Sicherheitslücken regelmäßig schließen.

---


## ✅ Kurz-Check

- [ ] Ich kann die 3 Schutzziele erklären.
- [ ] Ich erkenne das Schutzziel in einem Beispiel.
- [ ] Ich kann den Schutzbedarf begründen.
- [ ] Ich kann Bedrohung, Schwachstelle und Risiko unterscheiden.
- [ ] Ich kann zu einem Problem eine passende Maßnahme nennen.
- [ ] Ich weiß, was technisch und was organisatorisch ist.
