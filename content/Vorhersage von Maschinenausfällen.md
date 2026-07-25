*23.07.2026 Donnerstag*
## Ausgangssituation

*Ein Produktionsunternehmen möchte ungeplante Maschinenstillstände reduzieren. Für jede Maschine liegen Sensor-, Betriebs- und Wartungsdaten vor. Das Ziel besteht darin, vorherzusagen, ob innerhalb der nächsten sieben Tage ein Ausfall auftritt.*

---
## Daten verstehen und Modelle fair vergleichen
### Trainingsdaten

01_maschinen_training_5000.csv
![[Pasted image 20260723212150.png]]

Wir haben 5000 eingelesene Zeilen. Einzelne unvollständige Daten wurden mit dem Mittelwert mithilfe des Impute-Widgets aufgefüllt. Zusätzlich habe ich überprüft, ob das Entfernen der Zeilen mit fehlenden Werten bei Vibration und Ölqualität einen Unterschied macht - die Vorhersagen fielen jedoch identisch aus. **Die Klassenverteilung ist unausgeglichen: 891 Maschinen mit Ausfall = ja (17,82 %) und 4109 Maschinen mit Ausfall = nein (82,18 %).** Das muss bei der späteren Modellbewertung berücksichtigt werden - Kennzahlen wie CA (Accuracy) allein wären hier irreführend, aussagekräftiger sind MCC, Recall, F1 und AUC.

![[anzahl_ausfälle.jpg]]

---
### Kurzanalyse Box Plot und Correlations

Die Box-Plot-Analyse hat gezeigt, dass folgende Variablen den größten Einfluss auf Ausfall haben: Alter_Jahre, Betriebsstunden, **Oelqualitaet_pct**, Temperatur_C, Vibration_mm_s, **Wartung_seit_Tagen**, Fehlercodes_30T und Last_pct.

Außerdem sieht man bei den Box Plots nach Maschinentyp aufgeteilt, dass **Maschinentyp D am häufigsten Ausfälle hat** - das hängt mit Betriebsstunden, Vibration, Alter_Jahre und der höchsten Anzahl an Tagen seit der letzten Wartung zusammen.

![[Pasted image 20260724000511.png]]

---
### Modellauswahl

Von allen getesteten Modellen hatten Gradient Boosting und **Logistic Regression die beste Kurve in der ROC-Analyse.** Zusätzlich fiel mir **Naive Bayes durch einen sehr guten Recall auf**, weshalb ich es ebenfalls beibehalten habe. Ich habe diese Modelle sowohl mit allen Daten als auch mit den auf die wichtigsten Parameter gefilterten Daten (ermittelt anhand des Box Plots) verglichen. Da alle Kennzahlen bei den gefilterten Daten besser ausfielen, **habe ich mich für die gefilterte Variante entschieden.**

![[Pasted image 20260723230242.png]]
*grün - Logistic Regression | orange - Naive Bayes*

---
### Stacking

Zunächst habe ich diese drei Modelle gestackt, um zu sehen, ob ich dadurch bessere Vorhersagen erhalte. Allerdings haben Gradient Boosting und Logistic Regression den Recall von Naive Bayes gesenkt, während Naive Bayes wiederum den MCC von Logistic Regression verschlechtert hat. Deshalb habe ich mich entschieden, die Modelle getrennt zu betrachten: **Logistic Regression für AUC, F1 und MCC, und separat Naive Bayes für den Recall.** Gradient Boosting habe ich letztlich verworfen, da es sehr ähnliche, jedoch leicht schlechtere Vorhersagen als Logistic Regression lieferte.

![[Pasted image 20260723231548.png]]
*zuerst ausgewählte Modelle*

---

*24.07.2026 Freitag*
## Unabhängige Validierung

Beim Vergleich der drei Modelle auf den Trainingsdaten und auf den Testdaten (den 1200 neuen Daten) hat sich gezeigt, dass Logistic Regression auf den Testdaten gar nicht mehr gut funktioniert - die meisten Kennzahlen sind auf null gefallen. Auch Gradient Boosting hat auf den Testdaten schlecht abgeschnitten. Deshalb arbeite ich für die weiteren Berechnungen mit **Naive Bayes** weiter.

In der Tabelle mit den Testdaten fehlten Werte in den Spalten Vibration und Ölqualität, und wenn man diese nicht berücksichtigt, wird die Vorhersage besser.

![[Pasted image 20260724114123.png]]
*Trainingsdaten vs. Testdaten*

---
## Praxistest

*Übersehener Ausfall: 8.000 Euro | Unnötige Kontrolle: 250 Euro*

![[Pasted image 20260725121500.png]]
*Naive Bayes - Confusion Matrix*


**Kostenvergleich:**

☆ Alle Maschinen als Ausfall markieren: 933 × 250 € = 233.250 €

☆ Aktuelle Einstellung: 167 × 8.000 € + 31 × 250 € = 1.343.750 €

Daraus ergibt sich, dass **es sich eher lohnt, fälschlicherweise einen Ausfall zu melden, obwohl die Maschine funktioniert, als einen echten Ausfall zu übersehen.**

---
### Schwellenwert fachlich auswählen

Bei der Verwendung des Naive Bayes Modells für die Vorhersage lohnt es sich am meisten, den Schwellenwert im Calibration Plot auf 0,02 (für "ja") einzustellen.

![[Pasted image 20260725183811.png]]
*Naive Bayes, tresh. = 0.98*


**Berechnung:**

☆ Übersehene Ausfälle: 1 × 8.000 € = 8.000 €

☆ Unnötige Kontrollen: 687 × 250€ = 171.750€

**Gesamtkosten: 179.750€**


Im Vergleich zur Markierung aller Maschinen als Ausfall **spart der kalibrierte Schwellenwert:**

![[Pasted image 20260725184125.png]]

---
## Orange

![[Pasted image 20260726011610.png]]