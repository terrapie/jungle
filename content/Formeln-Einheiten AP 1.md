
## 1. Elektrotechnik-Grundformeln

### Ohmsches Gesetz
```
U = R × I
```
- U = Spannung (Volt, V)
- R = Widerstand (Ohm, Ω)
- I = Stromstärke (Ampere, A)

Umgestellt:
```
R = U ÷ I
I = U ÷ R
```

### Leistung (elektrisch)
```
P = U × I
```
- P = Leistung (Watt, W)
- U = Spannung (V)
- I = Stromstärke (A)

Andere Formen (wenn andere Werte gegeben sind):
```
P = I² × R
P = U² ÷ R
```

![[Pasted image 20260906174132.png]]
### Stromkosten
```
Stromkosten = Leistung (kW) × Zeit (h) × Preis (€/kWh)
```

**Wichtig:** Leistung muss in **kW** sein, nicht in W!

---

## 2. Einheiten-Umrechnung – Leistung

| Einheit | Kürzel | Umrechnung |
|---|---|---|
| Watt | W | 1 W |
| Kilowatt | kW | 1 kW = 1.000 W |
| Megawatt | MW | 1 MW = 1.000 kW = 1.000.000 W |

**Formel:**
```
kW = W ÷ 1.000
W = kW × 1.000
```

---

## 3. Einheiten-Umrechnung – Datenmenge (Speicher)

⚠️ **Achtung: Bit ≠ Byte!** Das ist die häufigste Fehlerquelle.

| Einheit  | Kürzel | Umrechnung                                              |
| -------- | ------ | ------------------------------------------------------- |
| Bit      | b      | kleinste Einheit                                        |
| Byte     | B      | 1 Byte = 8 Bit                                          |
| Kilobyte | KB     | 1 KB = 1.000 Byte (oder 1 KiB = 1.024 Byte *bei binär*) |
| Megabyte | MB     | 1 MB = 1.000 KB = 1.000.000 Byte                        |
| Gigabyte | GB     | 1 GB = 1.000 MB                                         |
| Terabyte | TB     | 1 TB = 1.000 GB                                         |

**Groß-/Kleinschreibung ist wichtig:**
- **kleines b** = Bit
- **großes B** = Byte

---

## 4. Einheiten-Umrechnung – Datenübertragung (Netzwerk)

Netzwerkgeschwindigkeit wird fast immer in **Bit pro Sekunde** angegeben, nicht Byte!

| Einheit | Kürzel | Umrechnung |
|---|---|---|
| Bit pro Sekunde | bit/s, bps | Grundeinheit |
| Kilobit pro Sekunde | kbit/s, kbps | 1 kbit/s = 1.000 bit/s |
| Megabit pro Sekunde | Mbit/s, Mbps | 1 Mbit/s = 1.000 kbit/s |
| Gigabit pro Sekunde | Gbit/s, Gbps | 1 Gbit/s = 1.000 Mbit/s |

### Bit/s in Byte/s umrechnen 🔥

```
Byte/s = Bit/s ÷ 8
```

**Beispiel:** Internetleitung mit 100 Mbit/s
```
100 Mbit/s ÷ 8 = 12,5 MByte/s
```

Das erklärt, warum ein Download bei "100 Mbit/s Internet" nur mit ca. 12,5 MB/s läuft, nicht 100 MB/s!

---

## 5. Übertragungszeit berechnen

```
Zeit (s) = Dateigröße (Bit) ÷ Übertragungsrate (Bit/s)
```

**Wichtig:** Dateigröße wird meist in Byte angegeben → zuerst in Bit umrechnen (× 8)!

**Beispiel:** Datei mit 500 MB, Leitung mit 50 Mbit/s
1. 500 MB in Mbit umrechnen: 500 × 8 = 4.000 Mbit
2. Zeit berechnen: 4.000 Mbit ÷ 50 Mbit/s = 80 Sekunden

![[Pasted image 20260906174508.png]]

---

## 6. Dezimal- vs. Binärpräfixe

| Dezimal (SI, üblich bei Herstellerangaben) | Binär (IEC, üblich im Betriebssystem) |
|---|---|
| 1 KB = 1.000 Byte | 1 KiB = 1.024 Byte |
| 1 MB = 1.000.000 Byte | 1 MiB = 1.048.576 Byte |
| 1 GB = 1.000.000.000 Byte | 1 GiB = 1.073.741.824 Byte |

**Warum eine 500-GB-Festplatte im Windows-Explorer weniger anzeigt:**
Hersteller rechnen dezimal (1 GB = 1.000 MB), Windows rechnet binär (1 GB ≈ 1.024 MB) → dadurch zeigt Windows eine kleinere Zahl an.

---

## 7. Typische Rechenschritte in der Prüfung

1. **Einheiten immer zuerst angleichen** (alles in W, alles in Bit, alles in Sekunden)
2. **Bit und Byte nicht verwechseln** (Faktor 8!)
3. **Zeit in Stunden umrechnen**, wenn nach Kosten pro Jahr/Monat gefragt wird
   - 1 Tag = 24 h
   - 1 Jahr = 365 Tage = 8.760 h
4. **Ergebnis auf Plausibilität prüfen** – wirkt die Zahl realistisch?

---

## 8. Bildgröße berechnen (Rastergrafik)

### Grundformel für die Dateigröße eines unkomprimierten Bildes

```
Dateigröße (Bit) = Breite (Pixel) × Höhe (Pixel) × Farbtiefe (Bit pro Pixel)
```

Danach ggf. in Byte umrechnen (÷ 8) und in KB/MB (÷ 1.000 bzw. ÷ 1.000.000).

**Beispiel:** Bild mit 1.920 × 1.080 Pixel, Farbtiefe 24 Bit (RGB, "True Color")
1. Pixel gesamt: 1.920 × 1.080 = 2.073.600 Pixel
2. In Bit: 2.073.600 × 24 = 49.766.400 Bit
3. In Byte: 49.766.400 ÷ 8 = 6.220.800 Byte
4. In MB: 6.220.800 ÷ 1.000.000 ≈ **6,22 MB**

### Farbtiefe (Bit pro Pixel) – wie viele Farben sind möglich?

```
Anzahl Farben = 2^Farbtiefe
```

| Farbtiefe | Bezeichnung | Anzahl Farben |
|---|---|---|
| 1 Bit | Schwarz/Weiß | 2 (2¹) |
| 8 Bit | Graustufen / Palette | 256 (2⁸) |
| 16 Bit | High Color | 65.536 (2¹⁶) |
| 24 Bit | True Color (RGB, je 8 Bit pro Kanal) | ca. 16,7 Mio. (2²⁴) |
| 32 Bit | True Color + Alphakanal (Transparenz) | ca. 16,7 Mio. + Transparenzstufen |

### Anzahl der Pixel aus Auflösung (DPI) berechnen

**DPI = Dots per Inch** (Punkte/Pixel pro Zoll) – gibt an, wie fein aufgelöst gedruckt/gescannt wird.

```
Pixel (Breite oder Höhe) = Zoll (Größe des Ausdrucks) × DPI
```

**Beispiel:** Foto soll 6 × 4 Zoll groß gedruckt werden, mit 300 DPI
```
Breite: 6 × 300 = 1.800 Pixel
Höhe: 4 × 300 = 1.200 Pixel
```
→ Danach kann mit diesen Pixelwerten wieder die Dateigröße wie oben berechnet werden.

**Umrechnung Zoll ↔ cm** (falls in cm gegeben):
```
1 Zoll (inch) = 2,54 cm
Zoll = cm ÷ 2,54
```

### Typischer kompletter Rechenweg in der Prüfung

1. Gegeben: Druckgröße in cm/Zoll + DPI → **Pixelanzahl berechnen**
2. Gegeben: Pixelanzahl + Farbtiefe → **Dateigröße in Bit berechnen**
3. Bit → Byte (÷ 8) → KB/MB (÷ 1.000 bzw. ÷ 1.000.000)

⚠️ Diese Berechnung gilt nur für **unkomprimierte** Bilder (z. B. BMP). Formate wie JPEG oder PNG sind komprimiert und daher in der Realität kleiner – das wird aber nur erwähnt, wenn explizit danach gefragt ist.

---

## 9. Schnellübersicht Zehnerpotenzen

| Vorsilbe | Kürzel | Faktor |
|---|---|---|
| Kilo | k | × 1.000 |
| Mega | M | × 1.000.000 |
| Giga | G | × 1.000.000.000 |
| Tera | T | × 1.000.000.000.000 |
