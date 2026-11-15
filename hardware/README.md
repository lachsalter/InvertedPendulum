# Hardware-Übersicht

Vorhandene Teile für das Inverted-Pendulum-Projekt (Stand: 2026-11-15).

## Elektronik und Antrieb

| # | Teil | Anzahl | Was es ist | Datenblatt / Doku |
|---|------|:-----:|------------|-------------------|
| 1 | iPower **GM4108H-120T** Gimbal Motor (RobotShop RB-Ifl-16) | 2 | BLDC-Gimbalmotor, 24N22P (11 Polpaare), 120 Windungen, ca. 11,1 Ω, Hohlwelle 8 mm ID, ca. 125 g | [RobotShop](https://eu.robotshop.com/products/ipower-gbm4108h-120t-gimbal-motor) · [iFlight](https://iflight-rc.eu/products/gm4108h-120t-gimbal-motor) |
| 2 | ST **B-G431B-ESC1** | 2 | ESC-Discovery-Kit: STM32G431CB, Gate-Treiber L6387, MOSFETs STL180N6F7; FOC-fähig (ST Motor Control SDK, SimpleFOC) | [User Manual UM2516 (lokal)](datasheets/UM2516_B-G431B-ESC1_user_manual.pdf) · [MCU-Datenblatt STM32G431CB (lokal)](datasheets/STM32G431CB_datasheet.pdf) · [Produktseite](https://www.st.com/en/evaluation-tools/b-g431b-esc1.html) |
| 3 | Same Sky (ex CUI) **AMT103-V** | 2 | Kapazitiver Inkremental-Encoder, A/B + Index, Auflösung per DIP-Schalter einstellbar, mit Hülsen für verschiedene Wellendurchmesser | [Datenblatt AMT10 (lokal)](datasheets/AMT10_datasheet.pdf) · [Original](https://www.sameskydevices.com/product/resource/amt10.pdf) · [Serienseite](https://www.sameskydevices.com/product/motion-and-control/rotary-encoders/incremental/modular/amt10-series) |
| 4 | Raspberry Pi **Pico W** (SC0918) | 1 | RP2040-Board (2× Cortex-M0+) mit 2,4-GHz-WLAN/Bluetooth | [Pico W Datenblatt (lokal)](datasheets/Pico-W_datasheet.pdf) · [RP2040 Datenblatt (lokal)](datasheets/RP2040_datasheet.pdf) · [Originale](https://datasheets.raspberrypi.com/) |
| 5 | ST **NUCLEO-F446RE** | 1 | Nucleo-64-Board mit STM32F446RE (Cortex-M4F, 180 MHz), ST-LINK on board, Arduino- und Morpho-Header | [User Manual UM1724 (lokal)](datasheets/UM1724_NUCLEO-64_user_manual.pdf) · [MCU-Datenblatt STM32F446RE (lokal)](datasheets/STM32F446RE_datasheet.pdf) · [Produktseite](https://www.st.com/en/evaluation-tools/nucleo-f446re.html) |
| 6 | DFRobot **SEN0373** BMX160 9-Achsen-Modul | 1 | IMU: Beschleunigung (±2…16 g), Gyro (±125…2000 °/s), Magnetometer; I²C (Default 0x68), 3,3–5,5 V | [DFRobot Wiki](https://wiki.dfrobot.com/BMX160_9_Axis_Sensor_Module_SKU_SEN0373) · [BMX160 Datenblatt (lokal)](datasheets/BMX160_datasheet.pdf) · [Quelle: SparkFun-Kopie](https://cdn.sparkfun.com/assets/2/2/8/7/d/BMX160_datasheet.pdf) · [Library](https://github.com/DFRobot/DFRobot_BMX160) |
| 7 | DFRobot **FIT0588** XT90-Steckerpaar | 1 | XT90 Stecker + Buchse, vergoldet, 40 A dauer / 90 A Spitze, für 10 AWG | [DFRobot Produktseite](https://www.dfrobot.com/product-1764.html) |
| 8 | Mechatronics Bearing Group **R4-2RS** | 5 | Rillenkugellager, beidseitig gedichtet, 1/4" (6,35 mm) ID × 5/8" (15,88 mm) AD × 4,98 mm breit | [DigiKey (Datenblatt dort verlinkt)](https://www.digikey.de/en/products/detail/mechatronics-bearing-group/R4-2RS/9608359) |

## Mechanik (3D-Druck)

Gedruckte Teile aus dem [SimpleFOC Reaction Wheel Pendulum](https://github.com/simplefoc/Arduino-FOC-reaction-wheel-inverted-pendulum/tree/master/CAD%20files) (MIT-Lizenz, © 2020 Antun Skuric, siehe [Lizenz](mechanics/stl/LICENSE-simplefoc-pendulum)). Im Original-Repo liegen dazu auch STEP- und SolidWorks-Dateien.

| # | Teil | Datei | Status | Hinweis |
|---|------|-------|--------|---------|
| 1 | Basis mit Lagersitzen | [bottom_swingup.STL](mechanics/stl/bottom_swingup.STL) | gedruckt | Wegen der Lager möglichst präzise drucken |
| 2 | Pendelarm | [pendulum_arm.STL](mechanics/stl/pendulum_arm.STL) | gedruckt | Löcher passen auf Motor und Encoder des Originals |
| 3 | Schwungrad (Reaction Wheel) | [reaction_wheel.STL](mechanics/stl/reaction_wheel.STL) | gedruckt | Möglichst präzise drucken, sonst vibriert es |
| 4 | Kabelhalter (optional) | [cable_holder.STL](mechanics/stl/cable_holder.STL) | gedruckt | – |

### Zubehör laut SimpleFOC-Design

| Teil | Anzahl | Bei uns vorhanden? |
|------|:-----:|--------------------|
| Kugellager 8 × 16 × 5 mm (688) | 3 | Nein. Die R4-2RS (6,35 × 15,88 × 4,98 mm) haben eine kleinere Bohrung, siehe Hinweise |
| Aluminiumrohr Ø 8 mm, 30 mm lang (Pendelachse) | 1 | offen |
| Schrauben M3 × 10 mm | 7 | offen |
| Schrauben M4 × 50 mm + Muttern | 2 | offen |

## Hinweise

- **GM4108H:** Die Händlerseiten widersprechen sich bei der Leerlaufdrehzahl (RobotShop 1025–1089 rpm, iFlight 513–567 rpm). Ein offizielles Datenblatt von iFlight gibt es nicht; den Wert besser selbst messen.
- **BMX160:** Ein offizielles Bosch-Datenblatt ist nicht mehr direkt verfügbar. Die verlinkte Kopie ist Rev. 1.1 (Mai 2018), Dokument BST-BMX160-DS000-11.
- **R4-2RS:** Die gedruckte Basis ist für 8 × 16 × 5-mm-Lager und eine 8-mm-Achse ausgelegt. Die R4-2RS sind 0,12 mm kleiner im Außendurchmesser und haben 6,35 mm statt 8 mm Bohrung. Entweder 688-Lager kaufen oder Basis und Achse auf 1/4" anpassen.
- **Motor-Lochbild:** Das Original nutzt eine ältere Version des GM4108. Vor dem Montieren prüfen, ob die Löcher in Pendelarm und Schwungrad auf unseren GM4108H-120T passen.
- **Datenblätter lokal:** Alle verfügbaren PDFs liegen unter `datasheets/`. Der STM32G431CB ist der Mikrocontroller auf den B-G431B-ESC1-Boards. Für die Gimbalmotoren, den XT90-Stecker und das Lager gibt es keine herunterladbaren Datenblätter.
