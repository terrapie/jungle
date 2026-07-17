## „Im Jahr 2139 wird es auf der Welt nur noch Verrückte geben"

*Ein Engländer hat berechnet, dass die ganze Welt im Jahr 2139 nur noch aus Verrückten bestehen wird. Dies sind keine Prophezeiungen und auch keine bloßen Mutmaßungen, sondern rein mathematische Berechnungen. Im Jahr 1859 kam ein Verrückter auf 535 Gesunde, im Jahr 1897 bereits nur noch auf 312 Gesunde; das Verhältnis entwickelte sich weiter wie folgt: im Jahr 1926 — 1:150, im Jahr 1977 wird es 1:100 betragen. Setzt man diese Rechenweise fort, gelangt man zu dem Schluss, dass im Jahr 2139 die ganze Welt nur noch aus Verrückten bestehen wird. Diese Berechnungen sind streng mathematisch durchgeführt. Wie könnte man ihnen also nicht glauben!*

![[A4A8AF19-2C13-41D7-8C84-D85FF936D552.jpeg]]

Quelle: Zeitung „Orędownik", 1936, Posen (Poznań)

---
## Streng mathematische Prognose

Dieser Artikel stammt aus einer polnischen Zeitung von 1936. Ein Engländer hatte wahrscheinlich nur Daten aus den Jahren 1859 und 1897. Auf dieser sehr kleinen Datenbasis berechnete er dann die weiteren Werte für 1926 und 1977 - und schließlich die "Prognose" für 2139.

Mit Orange möchte ich mit linearer Regression testen, wie sich sein Trend nach 1977 tatsächlich weiterentwickelt, und ob seine Prediction mit einer echten linearen Regression übereinstimmt.

---
## Import von CSV und Data Table

![[Pasted image 20260716174414.png]]

*Jahr - Feature | Verhaeltnis - Target*

---
## Darstellung der Quelldaten

![[Pasted image 20260716184025.png]]

**Der Scatter Plot zeigt deutlich: Je später das Jahr, desto weniger Gesunde kommen auf einen Verrückten.**

---
## Test - Daten

In den Testdaten habe ich Jahre in 20-Jahres-Abständen sowie die Jahre aus der Zeitung berücksichtigt.

___
## Ausgabe

![[ausgabe_update.jpg]]

---
## Fazit

Die Methode des Engländers war nicht nur ungenau - seine eigenen Daten widersprechen sich sogar selbst. **Laut der linearen Regression wäre das Verhältnis schon um 1988/1989 bei 0 gewesen.** Das würde bedeuten, dass **schon damals alle Menschen verrückt gewesen wären - und nicht erst 2139.**

Obwohl die lineare Regression innerhalb der bekannten Daten eine starke Korrelation zeigt (r = -0,94), führt die Extrapolation weit über den Datenbereich hinaus zu unsinnigen Ergebnissen.

Außerdem gibt es keine sinnvolle biologische Grundlage dafür, dass die Anzahl psychisch kranker Menschen linear und unendlich ansteigt.


![[Pasted image 20260716190657.png]]

---
## Sind die Daten überhaupt linear?

![[Pasted image 20260716231000.png]]

In einer kleinen Excel-Tabelle habe ich die Differenz zwischen den aufeinanderfolgenden Jahren sowie die Differenz zwischen der jeweiligen Anzahl der Gesunden pro einem Verrückten berechnet und geschaut, wie sich das Tempo des Rückgangs entwickelt hat


### Wie schnell sinkt das Verhältnis pro Jahr?

![[Screenshot 2026-07-17 090528.jpg]]

Der Graph zeigt deutlich, dass sich die Daten nicht linear verändern. Zwischen 1859 und 1926 sinkt das Verhältnis von Gesunden pro einer verrückten Person um etwa 5 pro Jahr. Bis 1977 sinkt es dann nur noch um knapp 1 pro Jahr, um schließlich bis 2139 auf ein Tempo von 0,617 zu fallen.