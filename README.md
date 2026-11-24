# anyPLC

Compact (53 × 53 mm), 4-layer, ESP32-C3-based ESPHome-compatible industrial controller PCB featuring dual high-current PWM outputs, optocoupled tachometer inputs, hardware power telemetry, and an external watchdog.

## Key Features

* **MCU:** ESP32-C3-MINI-1 (Wi-Fi / BLE)
* **Power Input:** 12–24 V DC (`J1`), 8 A fuse (`F1`), MOSFET reverse-polarity protection (`Q1`), and TVS surge suppression (`D1`)
* **Internal Power Rails:** Dual independent buck converters (`+5V` and `+3.3V`)
* **Power Telemetry:** INA226 voltage/current monitor (`U1`) across a 10 mΩ 2512 shunt (`R1`) with Kelvin sensing
* **Outputs (CH1 / CH2):** 2× low-side PWM MOSFET channels (`Q2`, `Q3`) driven by a dedicated dual gate driver (`U_DRV1`) with B560C freewheeling diodes (`D3`, `D5`)
* **Tachometer Inputs:** 2× optocoupled inputs (`U7`, `U8`) routed directly to the channel terminal blocks
* **Expansion Ports:** ESD-protected (`U6`) I2C (`J2`) and UART (`J3`) connectors
* **Reliability:** External hardware watchdog (`U5`) with disable/enable jumper (`JP1`)
* **Status Indicators:** Addressable RGB LED (`D_RGB1`) and per-channel output LEDs (`D4`, `D6`)
* **PCB Design:** 4-layer stackup (`F.Cu` / `GND` / `Power` / `B.Cu`), 53 × 53 mm, teardrops and dual-sided fiducials for automated assembly

## Pinout

### `J1` — Power Input (12–24 V DC)
| Pin | Function |
| :--- | :--- |
| 1 | `VIN+` (12–24 V DC via `F1` 8 A) |
| 2 | `GND` |

### `J4` (CH1) & `J5` (CH2) — Power Outputs
| Pin | Function |
| :--- | :--- |
| 1 | `+V_IN_MAIN` |
| 2 | `PWM OUT` (Low-side Drain) |
| 3 | `GND` |
| 4 | `+5V` |
| 5 | `TACHO` (Optocoupled input) |

### `J2` (I2C) & `J3` (UART) — Expansion Ports
| Pin | `J2` (I2C) | `J3` (UART) |
| :--- | :--- | :--- |
| 1 | `GND` | `GND` |
| 2 | `+3.3V` | `+3.3V` |
| 3 | `I2C_SDA` | `UART / ESD3` |
| 4 | `I2C_SCL` | `UART / ESD4` |

### `J6` — Programming / Debug Pogo-Pad (2×4)
| Pin | Function | Pin | Function |
| :--- | :--- | :--- | :--- |
| 1 | `+3.3V` | 5 | `EN` |
| 2 | `GND` | 6 | `BOOT` |
| 3 | `UART_TX` | 7 | `USB_D+` |
| 4 | `UART_RX` | 8 | `USB_D-` |

## Hardware Revisions

* **Rev 1.1** — Initial 4-layer PCB release (`DRC: 0 errors, 0 unconnected`), teardrops, dual-sided fiducials, and full silkscreen documentation.
