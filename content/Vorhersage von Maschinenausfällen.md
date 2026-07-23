*23.07.2026 Donnerstag*
## Ausgangssituation

*Ein Produktionsunternehmen möchte ungeplante Maschinenstillstände reduzieren. Für jede Maschine liegen Sensor-, Betriebs- und Wartungsdaten vor. Das Ziel besteht darin, vorherzusagen, ob innerhalb der nächsten sieben Tage ein Ausfall auftritt.*

---
## Daten verstehen und Modelle fair vergleichen
#### Trainingsdaten

01_maschinen_training_5000.csv
![[Pasted image 20260723212150.png]]

Wir haben 5000 eingelesene Zeilen. Einzelne unvollständige Daten wurden mit dem Mittelwert mithilfe des Impute-Widgets aufgefüllt. Zusätzlich habe ich überprüft, ob das Entfernen der Zeilen mit fehlenden Werten bei Vibration und Ölqualität einen Unterschied macht - die Vorhersagen fielen jedoch identisch aus. **Die Klassenverteilung ist unausgeglichen: 891 Maschinen mit Ausfall = ja (17,82 %) und 4109 Maschinen mit Ausfall = nein (82,18 %).** Das muss bei der späteren Modellbewertung berücksichtigt werden - Kennzahlen wie CA (Accuracy) allein wären hier irreführend, aussagekräftiger sind MCC, Recall, F1 und AUC.

![[anzahl_ausfälle.jpg]]

---
#### Modellauswahl

Von allen getesteten Modellen hatten Gradient Boosting und **Logistic Regression die beste Kurve in der ROC-Analyse.** Zusätzlich fiel mir **Naive Bayes durch einen sehr guten Recall auf**, weshalb ich es ebenfalls beibehalten habe. Ich habe diese Modelle sowohl mit allen Daten als auch mit den auf die wichtigsten Parameter gefilterten Daten (ermittelt anhand des Box Plots) verglichen. Da alle Kennzahlen bei den gefilterten Daten besser ausfielen, **habe ich mich für die gefilterte Variante entschieden.**

![[Pasted image 20260723230242.png]]

grün - Logistic Regression | orange - Naive Bayes

---
#### *Stacking*

Zunächst habe ich diese drei Modelle gestackt, um zu sehen, ob ich dadurch bessere Vorhersagen erhalte. Allerdings haben Gradient Boosting und Logistic Regression den Recall von Naive Bayes gesenkt, während Naive Bayes wiederum den MCC von Logistic Regression verschlechtert hat. Deshalb habe ich mich entschieden, die Modelle getrennt zu betrachten: **Logistic Regression für AUC, F1 und MCC, und separat Naive Bayes für den Recall.** Gradient Boosting habe ich letztlich verworfen, da es sehr ähnliche, jedoch leicht schlechtere Vorhersagen als Logistic Regression lieferte.

![[Pasted image 20260723231548.png]]

---
## Orange

![[Pasted image 20260723231919.png]]
