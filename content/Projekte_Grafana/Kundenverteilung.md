Python ☆ pandas ☆ MySQL ☆ Grafana

In diesem Projekt wurde eine Übersicht der Kundenverteilung eines Unternehmens nach Bundesland erstellt.

Mit Python und pandas wurde der Datensatz bereinigt und als Tabelle df_final in eine MySQL-Datenbank (phpMyAdmin) geladen. Die Tabelle enthält folgende Spalten: Bundesland, Hauptstadt, Latitude, Longitude und die Anzahl der Kunden (count).

![[tabelle.jpg]]

In Grafana wurde die Tabelle per SQL-Abfrage eingebunden und auf zwei Panels visualisiert: einer interaktiven Karte (Geomap) sowie einer Datentabelle. Die Karte zeigt die geografische Verteilung der Kunden – farblich nach Anzahl kategorisiert;
(rot: unter 60, gelb: 60+, grün: 200+).

![[landkarte.jpg]]

SQL-Abfrage:

```sql
SELECT Bundesland, Latitude, Longitude, count
FROM df_final

