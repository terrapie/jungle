
## 🔴 1. Datenbanken

**Aufgabe:** Erkläre die Grundbegriffe.

| Begriff | Bedeutung |
|---|---|
| **Datenbank** | System, das Daten geordnet speichert. |
| **Tabelle** | Daten in Zeilen und Spalten. |
| **Datensatz** | Eine **Zeile** in der Tabelle. |
| **Attribut / Feld** | Eine **Spalte** in der Tabelle. |

**Beispiel: Tabelle Kunden**

| KundenID | Name | Ort |
|---|---|---|
| 1 | Müller GmbH | Marl |
| 2 | IT GmbH | Essen |

- Zeile 1 (`1, Müller GmbH, Marl`) = ein **Datensatz**
- Spalte `Ort` = ein **Attribut**

---

## 🔴 2. Primärschlüssel

**Aufgabe:** Was ist ein Primärschlüssel? Welche Regeln gelten?

Der **Primärschlüssel** (Primary Key) erkennt einen Datensatz **eindeutig**.

Beispiel: `KundenID`

**Regeln:**

- **eindeutig** (kein Wert doppelt)
- **möglichst unveränderlich**
- **nicht NULL** (nie leer)

---

## 🔴 3. Fremdschlüssel

**Aufgabe:** Was ist ein Fremdschlüssel? Wozu braucht man ihn?

Der **Fremdschlüssel** (Foreign Key) **verbindet Tabellen**.

- Tabelle **Kunden** → `KundenID` (Primärschlüssel)
- Tabelle **Aufträge** → `KundenID` (Fremdschlüssel)

So weiß man, **welcher Kunde zu welchem Auftrag gehört**.

> [!tip] Merkhilfe
> Primärschlüssel = Ausweis in der eigenen Tabelle.
> Fremdschlüssel = Verweis auf eine andere Tabelle.

---

## 🔴 4. Beziehungen

**Aufgabe:** Nenne die Beziehungsarten. Welche ist am wichtigsten?

| Beziehung | Bedeutung |
|---|---|
| **1:1** | Ein Datensatz gehört zu genau einem anderen. |
| **1:n** | Ein Datensatz gehört zu vielen anderen. |
| **n:m** | Viele gehören zu vielen. |

**Am wichtigsten: 1:n**

Beispiel: Ein Kunde kann mehrere Aufträge haben.
→ **1:n**

---

## 🔴 5. SQL – Grundlagen

**Aufgabe:** Erkläre die wichtigsten SQL-Befehle.

### SELECT

Alle Daten aus einer Tabelle anzeigen:

```sql
SELECT * FROM Kunden;
```

### WHERE

Nur bestimmte Datensätze anzeigen:

```sql
SELECT *
FROM Kunden
WHERE Ort = 'Marl';
```

→ Nur Kunden aus Marl.

### ORDER BY

Ergebnis sortieren:

```sql
SELECT *
FROM Kunden
ORDER BY Name;
```

### INSERT, UPDATE, DELETE

| Befehl | Bedeutung |
|---|---|
| **INSERT** | Daten **hinzufügen** |
| **UPDATE** | Daten **ändern** |
| **DELETE** | Daten **löschen** |

> [!info] Wichtig
> Du musst kein SQL-Profi sein. Du musst einfache Abfragen **lesen und verstehen**.

---

## 🔴 6. JOIN

**Aufgabe:** Erkläre, was ein JOIN macht.

Ein **JOIN** verbindet Daten aus **mehreren Tabellen**.

**Tabelle Kunden**

| KundenID | Name |
|---|---|
| 1 | Müller |
| 2 | Schmidt |

**Tabelle Aufträge**

| AuftragID | KundenID |
|---|---|
| 101 | 1 |
| 102 | 1 |
| 103 | 2 |

Ergebnis: Müller → Auftrag 101 und 102.

**Aufgabe:** Nenne die zwei wichtigsten JOINs.

| JOIN | Was macht er? |
|---|---|
| **INNER JOIN** | Zeigt nur Datensätze, die in **beiden** Tabellen passen. |
| **LEFT JOIN** | Zeigt **alle** aus der linken Tabelle. Auch wenn rechts nichts passt. |

Beispiel LEFT JOIN: Ein Kunde ohne Auftrag wird trotzdem angezeigt.

---

## 🔴 7. Datenformate

**Aufgabe:** Nenne wichtige Datenformate und wofür man sie nutzt.

| Format | Nutzung |
|---|---|
| **CSV** | Tabellen-Daten (einfacher Text, Trennzeichen) |
| **XML** | Strukturierte Daten mit Tags |
| **JSON** | Daten zwischen Anwendungen (z. B. API) |
| **XLSX** | Excel-Datei |

> [!info] Wichtig
> Verschiedene Systeme nutzen verschiedene Formate.
> Darum muss man Daten oft **umwandeln**.

---

## 🔴 8. Datenqualität

**Aufgabe:** Nenne die Kriterien der Datenqualität.

| Kriterium | Frage |
|---|---|
| **Vollständigkeit** | Fehlen Daten? |
| **Richtigkeit** | Sind die Daten korrekt? |
| **Konsistenz** | Passen die Daten zusammen? |
| **Aktualität** | Sind die Daten auf dem neuesten Stand? |
| **Eindeutigkeit** | Gibt es Duplikate? |
| **Plausibilität** | Sind die Werte sinnvoll? |

**Aufgabe:** Erkenne das Problem im Beispiel.

- Zweimal `Müller GmbH` in der Datenbank
  → **Duplikat** (Eindeutigkeit)
- Telefonnummer fehlt
  → **Vollständigkeit**
- Preis: `-999999 €`
  → **Plausibilität**

---

## 🔴 9. Datenvalidierung

**Aufgabe:** Was ist Datenvalidierung? Nenne Beispiele.

**Datenvalidierung** prüft, ob Daten bestimmte **Regeln** einhalten.

| Feld | Regel |
|---|---|
| Alter | 0 bis 120 |
| PLZ | genau 5 Ziffern |
| E-Mail | passendes Format (z. B. mit `@`) |
| Preis | größer oder gleich 0 |

---

## 🔴 10. Datenverarbeitung

**Aufgabe:** Nenne den Ablauf der Datenverarbeitung.

**Erfassen → Speichern → Verarbeiten → Auswerten → Ausgeben**

| Schritt | Bedeutung |
|---|---|
| **Erfassen** | Daten holen oder eingeben |
| **Speichern** | Daten ablegen |
| **Verarbeiten** | Daten bearbeiten oder berechnen |
| **Auswerten** | Daten analysieren |
| **Ausgeben** | Ergebnis zeigen (z. B. Bericht, Dashboard) |

---

## 🔴 11. Softwareentwicklung

**Aufgabe:** Nenne die Phasen der Softwareentwicklung.

**Anforderung → Planung → Entwicklung → Test → Dokumentation → Einführung / Wartung**

| Phase | Was passiert? |
|---|---|
| **Anforderung** | Was soll die Software können? |
| **Planung** | Wie und wann setzen wir es um? |
| **Entwicklung** | Die Software wird gebaut. |
| **Test** | Die Software wird geprüft. |
| **Dokumentation** | Alles wird beschrieben. |
| **Einführung / Wartung** | Die Software geht in Betrieb und wird gepflegt. |

---

## 🔴 12. Anforderungen

**Aufgabe:** Erkläre den Unterschied zwischen funktionalen und nicht-funktionalen Anforderungen.

| Art | Frage | Beispiel |
|---|---|---|
| **Funktional** | **WAS** soll das System tun? | Das System soll Rechnungen erstellen. |
| **Nicht-funktional** | **WIE** soll das System arbeiten? | Das System soll in 2 Sekunden antworten. |

> [!warning] Klassische Prüfungsfrage
> Frage dich immer: **Was?** (funktional) oder **Wie?** (nicht-funktional).

---

## 🔴 13. Testen

**Aufgabe:** Nenne die Testarten und erkläre den Unterschied.

| Test | Was wird geprüft? |
|---|---|
| **Modultest / Unit-Test** | Ein einzelner Baustein |
| **Integrationstest** | Arbeiten die Bausteine **zusammen**? |
| **Systemtest** | Das **ganze System** |
| **Abnahmetest** | Der **Kunde** prüft: Sind die Anforderungen erfüllt? |

> [!tip] Merkhilfe
> Klein → Zusammen → Ganz → Kunde

---

## 🟡 14. Fehlerarten

**Aufgabe:** Nenne die drei Fehlerarten.

| Fehlerart | Bedeutung |
|---|---|
| **Syntaxfehler** | Der Code passt nicht zur Sprache (z. B. Klammer fehlt). |
| **Laufzeitfehler** | Das Programm startet, aber bricht beim Laufen ab. |
| **Logikfehler** | Das Programm läuft, aber das Ergebnis ist falsch. |

---

## 🟡 15. Dokumentation

**Aufgabe:** Erkläre, warum man Software dokumentiert.

- Andere Personen verstehen die Software.
- Man findet Fehler schneller.
- Neue Mitarbeiter lernen schneller.
- Änderungen sind später nachvollziehbar.
- Die Wartung wird einfacher.

**Aufgabe:** Nenne Arten der Dokumentation.

| Art | Inhalt |
|---|---|
| **Funktionsbeschreibung** | Was kann die Software? |
| **Konfiguration** | Welche Einstellungen gibt es? |
| **Installation** | Wie installiere ich die Software? |
| **Benutzung** | Wie bedient der Nutzer die Software? |
| **Änderungen** | Was wurde wann geändert? |
| **Tests** | Was wurde getestet? Was war das Ergebnis? |

---

## 🟡 16. Versionsverwaltung

**Aufgabe:** Erkläre die Grundbegriffe.

| Begriff | Bedeutung |
|---|---|
| **Version** | Ein bestimmter Stand der Software. |
| **Änderung** | Eine Anpassung am Code oder an den Dateien. |
| **Release** | Eine fertige Version, die man veröffentlicht. |
| **Backup** | Eine Kopie zur Sicherheit. |
| **Git** | Ein Programm für Versionsverwaltung. |

**Aufgabe:** Erkläre, wozu man Versionsverwaltung nutzt.

- Ich sehe, wer was wann geändert hat.
- Ich kann zu einer alten Version zurückgehen.
- Mehrere Personen können zusammen arbeiten.

**Aufgabe:** Was ist der Unterschied zwischen Backup und Versionsverwaltung?

- **Backup** = Kopie für den Notfall.
- **Versionsverwaltung** = Verlauf aller Änderungen. Man kann zurückgehen.

> [!info] Wichtig
> Git musst du nicht wie ein Programmierer kennen. Die **Idee** reicht.

---

## 🟡 17. Datenschutz

> [!important] Verbindung zu LF4
> Datenschutz und Informationssicherheit gehören zusammen.

**Aufgabe:** Erkläre die Begriffe.

| Begriff | Bedeutung |
|---|---|
| **Personenbezogene Daten** | Daten, mit denen man eine Person erkennt (Name, Adresse, E-Mail). |
| **Zweckbindung** | Daten nur für den erlaubten Zweck nutzen. |
| **Datenminimierung** | Nur so viele Daten speichern wie nötig. |
| **Zugriff nur für Berechtigte** | Nur wer die Daten braucht, darf sie sehen. |
| **Löschung** | Daten löschen, wenn man sie nicht mehr braucht. |
| **Sichere Speicherung** | Daten schützen (z. B. Verschlüsselung, Backup). |

**Aufgabe:** Verbinde Datenschutz mit LF4.

| Datenschutz-Regel | Maßnahme aus LF4 |
|---|---|
| Zugriff nur für Berechtigte | Berechtigungskonzept, Zugriffskontrolle |
| Sichere Speicherung | Verschlüsselung, Backup |
| Schutz vor Diebstahl | Passwortregeln, MFA |
| Datenschutz im Alltag | Schulungen, Richtlinien |

---

## ✅ Kurz-Check

- [ ] Ich kenne Tabelle, Datensatz und Attribut.
- [ ] Ich kann Primär- und Fremdschlüssel erklären.
- [ ] Ich erkenne 1:n-Beziehungen.
- [ ] Ich verstehe SELECT, WHERE, ORDER BY, INSERT, UPDATE, DELETE.
- [ ] Ich verstehe INNER JOIN und LEFT JOIN.
- [ ] Ich kenne CSV, XML, JSON und XLSX.
- [ ] Ich kann die 6 Kriterien der Datenqualität nennen.
- [ ] Ich kann Validierungsregeln formulieren.
- [ ] Ich kenne den Ablauf der Datenverarbeitung.
- [ ] Ich kenne die Phasen der Softwareentwicklung.
- [ ] Ich unterscheide funktionale und nicht-funktionale Anforderungen.
- [ ] Ich kenne die 4 Testarten.
- [ ] Ich unterscheide Syntax-, Laufzeit- und Logikfehler.
- [ ] Ich kann Dokumentation, Versionsverwaltung und Datenschutz erklären.
