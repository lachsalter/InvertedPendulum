# InvertedPendulum

Kombiniertes Hardware- und Software-Projekt: ein inverses Pendel mit BLDC-Gimbalmotoren und FOC-Regelung.

- [Hardware-Übersicht: Elektronik, Datenblätter, 3D-Druckteile](hardware/README.md)

## Vorbild: SimpleFOC Reaction Wheel Pendulum

Wir orientieren uns am [Reaction Wheel Inverted Pendulum von SimpleFOC](https://docs.simplefoc.com/simplefoc_pendulum). Repo mit 3D-Druckteilen und Code: [simplefoc/Arduino-FOC-reaction-wheel-inverted-pendulum](https://github.com/simplefoc/Arduino-FOC-reaction-wheel-inverted-pendulum).

Funktionsprinzip: Ein BLDC-Motor treibt ein Schwungrad an. Das Reaktionsmoment hält das Pendel aufrecht.

- **Aufschwingen:** Der Motor erzeugt eine Spannung, die gegen die aktuelle Pendelbewegung wirkt (etwa 40 % der Versorgungsspannung). So schaukelt sich das Pendel auf.
- **Stabilisieren:** Liegt das Pendel nahe der Senkrechten (|Winkel| < 0,5 rad), übernimmt eine lineare Zustandsrückführung aus Pendelwinkel, Pendelgeschwindigkeit und Motorgeschwindigkeit (LQR-artig).
- **Zeitschleifen:** Die FOC-Schleife läuft etwa jede 1 ms, die Regelung etwa alle 25 ms. Der Motor arbeitet im Spannungs-Drehmoment-Modus.

### Vergleich mit unserer Hardware

| | SimpleFOC-Projekt | Unser Projekt |
|---|---|---|
| Motor | iPower GM4108H-120T | gleich (2×) |
| Encoder | 2× AMT103-V (Motor 500 PPR, Pendel 1000 PPR) | gleich (2×) |
| Motortreiber | SimpleFOCShield | B-G431B-ESC1 (2×) |
| Controller | Arduino UNO | NUCLEO-F446RE (Pico W als Option) |
| Versorgung | 12 V | offen |

Weitere Links: [Arduino-FOC Library](https://github.com/simplefoc/Arduino-FOC) · [SimpleFOC-Doku](https://docs.simplefoc.com/) · [SimpleFOC Community](https://community.simplefoc.com)
