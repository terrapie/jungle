Von historischen Verkaufszahlen zur Produktionsentscheidung

## Ausgangssituation

*Die Bäckerei **Morgenstern** produziert jeden Morgen Brötchen für ihre Filialen. Die bisherige Produktionsplanung erfolgt hauptsächlich nach Erfahrung.*

*Dabei entstehen zwei Probleme:*

*- Werden zu viele Brötchen produziert, bleiben Waren übrig.*

*- Werden zu wenige Brötchen produziert, können Kunden nicht bedient werden.*

*Die Produktionsleitung möchte deshalb untersuchen, ob die tägliche Verkaufsmenge mit einem Zeitreihenmodell prognostiziert werden kann.*

*Für die vergangenen 500 Tage stehen tägliche Verkaufs- und Umfelddaten zur Verfügung. Auf dieser Grundlage soll **eine Planung für 14 Tage entwickelt werden.***

## Datensatz

![[Pasted image 20260729194252.png]]

## Meine Rolle

*Sie arbeiten in der Daten- und Prozessanalyse der Bäckerei. Die Produktionsleitung erwartet von Ihnen nicht nur eine Prognose, sondern eine begründete Entscheidung:*

**Kann ein ARIMA-Modell als Grundlage für die tägliche Produktionsplanung verwendet werden?**

## ARIMA-Test

**Trainingszeitraum:** 01.01.2025 – 01.01.2026  
**Validierungszeitraum:** 27.04.2026 – 10.05.2026 (2 Wochen)

### Interpolate

Es gab 3 fehlende Werte in Verkaufte_Broetchen. Interpolationsmethode: **Linear**
Die Daten sind eine tägliche Zeitreihe mit klarem Trend zwischen benachbarten Tagen. Linear interpolation schließt Lücken entlang der geraden Verbindung zwischen Vor- und Nachwert und erhält so den zeitlichen Verlauf. Mean/Mode würde stattdessen einen festen Durchschnittswert einsetzen und den natürlichen Verlauf an dieser Stelle verfälschen.

### Time Slice

☆**Time Slice 1 - Trainingsdaten für ARIMA:** Zeitraum 01.01.2025–01.01.2026 (ein volles Jahr). Diese Daten dienen dem Modell zum Lernen von Muster und Struktur.

☆**Time Slice 2 - Vergleichsdaten:** Zeitraum 27.04.2026–10.05.2026 (2 Wochen). Dies sind die tatsächlichen, bekannten Verkaufszahlen, gegen die die Prognose später geprüft wird.

### Merge Data

Die ARIMA-Prognose (aus Time Slice 1 → ARIMA Model) wird per Merge Data mit den tatsächlichen Werten aus Time Slice 2 zusammengeführt. Im Line Chart werden beide Reihen übereinandergelegt: Verkaufte_Broetchen (forecast) vs. Verkaufte_Broetchen (tatsächlich).

![[Pasted image 20260729202039.png]]
*blau - die Prognose | rot - echte Verkaufszahlen*

### Warum nicht ARIMA?

**Die Prognose ist zu flach.**

![[Pasted image 20260729204058.png]]


☆ **Samstag:** Echte Verkäufe steigen stark. Die Prognose bleibt niedrig.

☆ **Sonntag:** Echte Verkäufe fallen stark. Die Prognose zeigt das nicht so deutlich.

☆ **Feiertag (01. Mai, Freitag):** Echte Verkäufe fallen stark. Die Prognose weiß nichts von Feiertagen und zeigt keinen Einbruch.

**Das Modell sieht die großen Sprünge nicht. Die Linie bleibt fast gerade, während die echten Zahlen stark auf und ab gehen.**


# Saisonalität untersuchen

## Correlogram

![[Pasted image 20260729213625.png]]

Der Correlogram zeigt: alle 7 Tage gibt es eine Spitze - das beweist das Wochenmuster im Verkauf.

# ARIMA-Modelle vergleichen

![[Pasted image 20260729223617.png]]

**Ich wähle ARMA(14,0,0) wegen des niedrigsten RMSE und des höchsten R².**


# Eine frühere Zukunft simulieren

*Die letzten 14 Tage werden als simulierte Zukunft verwendet. Das Modell darf diese Tage beim Lernen nicht erhalten.*

## Ausgabe

![[Pasted image 20260729225327.png]]

Der Forecast beginnt am 03.05., also genau am ersten Tag des Testdatensatzes nach dem Time Slice. Die Prognose umfasst 14 Werte, was aufgrund einer fehlenden Folgewertbeobachtung im Datensatz 13 Kalendertagen entspricht. Insgesamt folgt die Prognose dem tatsächlichen Verlauf relativ gut, insbesondere nach der Seasonal Adjustment, wodurch die Vorhersage deutlich genauer geworden ist. Die größten Abweichungen treten vor allem an Feiertagen und Sonntagen auf, da sich das übliche Muster an diesen Tagen verändert. Die tatsächlichen Werte liegen größtenteils innerhalb des Prognoseintervalls, auch wenn es vereinzelt kleinere Abweichungen gibt. Mit zunehmendem Prognosehorizont nimmt die Unsicherheit der Vorhersage zu, was sich an breiter werdenden Prognoseintervallen erkennen lässt und für Zeitreihenprognosen typisch ist.

...
