### Ziel

Dashboard für monatliche Abteilungsmeetings. Gibt dem Geschäftsleiter einen Überblick über die Ticketbearbeitung aller Abteilungen - ohne Einzeldaten von Mitarbeitern, Fokus auf Teamleistung.
Tickets über 60 Tage offen haben besondere Priorität.

### User-Story

*„Als Geschäftsleiter möchte ich einen monatlichen Überblick über die Ticketbearbeitung aller Abteilungen, um die Leistung im Abteilungsmeeting besprechen zu können."*

### Ergebnis

**Dashboard mit drei Bereichen:**

KPI-Übersicht — Ø Bearbeitungszeit gesamt + nach Abteilung (Bar Chart)  

Kritische Tickets — offen über 60 Tage, mit Priorität  

Ticket Volume — wöchentlicher Verlauf pro Abteilung (abgeschlossen vs. offen)


![[abteilungen_vergleichen.jpg]]


### *Entwicklung*

*1. Ø Bearbeitungszeit nach Abteilung*
*In Python: neue Spalte Woche hinzugefügt, dann Gruppierung nach Kategorie und Woche:*
```python
brbzeit_woche = df[df["Status"] == "Abgeschlossen"].groupby(
    ["Kategorie", "Woche"]
)[["Bearbeitungszeit_h"]].mean().reset_index()

```

*In Grafana: SQL-Abfrage auf Wochen 22-27 eingegrenzt:*
```sql
SELECT Kategorie, AVG(Bearbeitungszeit_h)
FROM analyse.brbzeit_woche
WHERE Woche BETWEEN 22 AND 27
GROUP BY Kategorie
```

*Visualisierung: Bar Chart zeigt Unterschiede zwischen Abteilungen besser als Gauge. Farben angepasst - Werte über 133 Std. werden gelb dargestellt.*

*2. Tickets über 60 Tage offen - Priorität hinzufügen*
*In Python: Spalte Priorität in den Datensatz aufgenommen und in die Datenbank exportiert.*

*3. Ticket Volume pro Woche*


*In Grafana:*
```sql
WHERE Woche BETWEEN 22 AND 27
```
*hinzugefügt. Farbe für offene Tickets auf Gelb geändert.*


*Problem - fehlende Woche 22 bei Verwaltung:
In Woche 22 gab es keine offenen Tickets der Verwaltung. Da pd.DataFrame() ohne definierten Index den Index der ersten Spalte übernimmt, fehlte Woche 22 komplett im DataFrame.*

```python
# Vorher - fehlerhaft:
volume_ver["Offen"] = df_ver[df_ver["Status"] == "Offen"].groupby("Woche")["Status"].count()
# → Woche 22 nicht im Index, weil keine offenen Tickets vorhanden
```

*Woche 22 nicht im Index, weil keine offenen Tickets vorhanden*
```python
# Lösung - Index von Anfang an definieren:
volume_ver = pd.DataFrame(index=pd.RangeIndex(start=22, stop=29, name="Woche")) volume_ver["Offen"] = df_ver[df_ver["Status"] == "Offen"].groupby("Woche")["Status"].count()
volume_ver["Abgeschlossen"] = df_ver[df_ver["Status"] == "Abgeschlossen"].groupby("Woche")["Status"].count()
volume_ver = volume_ver.fillna(0)
```