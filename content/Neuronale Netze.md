## Ausgangssituation

*Die Serviceabteilung eines IT-Unternehmens möchte verspätete Ticketanalysen früh erkennen. Beim Statuswechsel `ANALYSE_BEREIT` soll ein Modell ein Risikosignal erzeugen. Ein Ticket gilt als verspätet, wenn zwischen Übergabe und Analysebeginn mehr als 60 Minuten liegen.*

*Die Warnung soll keine automatische Schuldzuweisung oder Ablehnung auslösen. Sie dient dazu, gefährdete Tickets gezielt zu prüfen und gegebenenfalls neu zu priorisieren.*

---
## Daten verstehen und Datenleck erkennen

Eine Beobachtungseinheit ist ein Supportticket. Es handelt sich um eine binäre Klassifikation, bei der vorhergesagt wird, ob die Analyse mehr als 60 Minuten nach der Übergabe beginnt. Die Vorhersage wird beim Statuswechsel `ANALYSE_BEREIT` benötigt. Die positive Klasse ist `ja`. Die Vorhersage soll dabei helfen, gefährdete Tickets frühzeitig zu erkennen und gegebenenfalls neu zu priorisieren.

![[Pasted image 20260824101707.png]]

**Meta** ist meine Primary Key bzw. ID, die den Datensatz identifiziert, aber nicht zum Trainieren verwendet wird. **Features** sind die Merkmale, anhand derer das Modell das **Target** vorhersagt. Das **Target** ist also der Wert, den ich vorhersagen möchte. **Skip** sind Daten, die zwar in der Tabelle vorhanden sind, aber nicht als Eingabe für das Modell verwendet werden dürfen, z. B. weil sie erst später bekannt sind.

Impute: missing Data ausgefüllt
Data Domain: categorical Data gecheckt

---
### Correlations

![[Pasted image 20260824111714.png]]

Die höchste Korrelation besteht zwischen **`auslastung_prozent` und `offene_tickets`** und beträgt **0,718**.

### Klassenverteilung

![[Pasted image 20260824112016.png]]

---
## Ein einzelnes Neuron von Hand berechnen

Ein vereinfachtes Neuron verwendet drei bereits skalierte Eingaben:
- `x₁ = 1,0`: hohe Auslastung,
- `x₂ = 0,6`: Anteil fehlender Informationen,
- `x₃ = 1,0`: Übergabe außerhalb der Kernzeit.

Gewichte und Bias:
- `w₁ = 0,8`
- `w₂ = 1,2`
- `w₃ = 0,7`
- `b = −1,0`

Berechnung:
`z = w₁×x₁ + w₂×x₂ + w₃×x₃ + b`

z = 0,8 * 1 + 1,2 * 0,6 + 0,7 * 1 - 1 = **1,22**

### ReLU

Berechnen Sie:
`ReLU(z) = max(0, z)`

max(0, 1,22) -> **1,22 > 0**


### Sigmoid

Berechnen Sie näherungsweise:
`σ(z) = 1 / (1 + e^(−z))`

σ(1,22) = 1 / (1 + e⁻¹·²²)
σ(1,22) ≈ 0,772

**Features (`x`) → Gewichte (`w`) + Bias → `z` → Sigmoid → Wahrscheinlichkeit**

Bei einem Schwellenwert von **0,5** wird `0,772` als **„ja“ (verspätet)** eingestuft, bei einem Schwellenwert von **0,8** dagegen als **„nein“ (nicht verspätet)**. Der Schwellenwert ist eine fachliche Entscheidung, weil man entweder mehr gefährdete Tickets erkennen oder weniger Fehlalarme haben möchte. Ein positives Gewicht bedeutet nur, dass ein Merkmal das Ergebnis des Modells beeinflusst, nicht dass es die Verzögerung verursacht.

## Netzarchitektur


![[Pasted image 20260824195925.png]]

Ein sehr tiefes neuronales Netz wäre für diesen **kleinen, tabellarischen Datensatz** nicht automatisch sinnvoll, weil es unnötig komplex wäre und sich leicht an die Trainingsdaten **überanpassen (Overfitting)** könnte. Ein einfacheres Modell kann hier möglicherweise genauso gut oder sogar besser funktionieren und ist leichter zu verstehen.


-> Aufgabe 5...