
## ReLU und XOR

### ReLU berechnen

| Eingabe vor ReLU | Ausgabe nach ReLU |
| ---------------: | ----------------: |
|             −2,5 |                 0 |
|             −0,2 |                 0 |
|                0 |                 0 |
|              0,3 |               0,3 |
|              1,8 |               1,8 |

ReLU blockiert negative Werte (und die Null) und gibt positive Werte unverändert weiter.


### XOR-Netz untersuchen

| $x_1$ | $x_2$ | H1 aktiv? | H2 aktiv? | Ausgabe | XOR korrekt? |
| ----: | ----: | --------- | --------- | ------: | ------------ |
|     0 |     0 | inaktiv   | inaktiv   |       0 | ja           |
|     0 |     1 | inaktiv   | aktiv     |       1 | ja           |
|     1 |     0 | aktiv     | inaktiv   |       1 | ja           |
|     1 |     1 | inaktiv   | inaktiv   |       0 | ja           |

