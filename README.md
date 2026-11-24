# anyPLC

Kompakt (53 × 53 mm), 4 rétegű, ESP32-C3 alapú, ESPHome-kompatibilis vezérlőpanel két nagyáramú PWM kimenettel, optocsatolt fordulatszám-méréssel (Tacho), hardveres telemetriával és külső watchdoggal.

## Fő jellemzők

* **MCU:** ESP32-C3-MINI-1-H4X (Wi-Fi / BLE)
* **Tápellátás:** 12–24 V DC bemenet (`J1`), 8 A biztosíték (`F1`), fordított polaritás elleni MOSFET-védelem (`Q1`) és TVS (`D1`)
* **Belső tápsínek:** Két független Buck konverter (`+5V` és `+3.3V`)
* **Telemetria:** INA226 feszültség- és árammérés 10 mΩ (2512) söntellenálláson (`R1`), Kelvin-bekötéssel
* **Kimenetek (CH1 / CH2):** 2× alacsony oldali (low-side) PWM MOSFET fokozat dedikált gate driverrel (`U_DRV1`) és B560C szabadonfutó diódákkal (`D3`, `D5`)
* **Tacho bemenetek:** 2× optocsatolt (`U7`, `U8`) bemenet a kimeneti sorkapcsokon
* **Bővítőportok:** ESD-védett (`U6`) I2C (`J2`) és UART (`J3`) csatlakozók
* **Megbízhatóság:** Külső hardveres watchdog (`U5`) engedélyező jumperrel (`JP1`)
* **Státuszjelzés:** Címzezhető RGB LED (`D_RGB1`) és csatornánkénti kimeneti LED (`D4`, `D6`)
* **PCB:** 4 rétegű (`F.Cu` / `GND` / `Power` / `B.Cu`), 53 × 53 mm

## Csatlakozók lábkiosztása

### `J1` – Tápbemenet (12–24 V DC)
| Pin | Funkció |
| :--- | :--- |
| 1 | `VIN+` (12–24 V DC, `F1` 8 A) |
| 2 | `GND` |

### `J4` (CH1) és `J5` (CH2) – Teljesítménykimenetek
| Pin | Funkció |
| :--- | :--- |
| 1 | `+V_IN_MAIN` |
| 2 | `PWM OUT` (Low-side Drain) |
| 3 | `GND` |
| 4 | `+5V` |
| 5 | `TACHO` (optocsatolt bemenet) |

### `J2` (I2C) és `J3` (UART) – Bővítőportok
| Pin | `J2` (I2C) | `J3` (UART) |
| :--- | :--- | :--- |
| 1 | `GND` | `GND` |
| 2 | `+3.3V` | `+3.3V` |
| 3 | `I2C_SDA` | `UART / ESD3` |
| 4 | `I2C_SCL` | `UART / ESD4` |

### `J6` – Programozó / Debug pogo-pad (2×4)
| Pin | Funkció | Pin | Funkció |
| :--- | :--- | :--- | :--- |
| 1 | `+3.3V` | 5 | `EN` |
| 2 | `GND` | 6 | `BOOT` |
| 3 | `UART_TX` | 7 | `USB_D+` |
| 4 | `UART_RX` | 8 | `USB_D-` |

## Revíziótörténet

* **Rev 1.1** – Kezdeti 4 rétegű PCB layout, teljes DRC-ellenőrzés (`Errors: 0`, `Unconnected: 0`).
