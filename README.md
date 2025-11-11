# nRF9151 MicroMod Processor Board

The nRF9151 MicroMod Processor Board is based on the [nRF9151](https://www.nordicsemi.com/Products/nRF9151) SiP by Nordic Semiconductor. It comes with an M.2 E-Key connector and is compatible with [SparkFun's MicroMod](https://www.sparkfun.com/micromod) ecosystem.

## Getting Started

Install the [nRF Connect SDK](https://docs.nordicsemi.com/bundle/ncs-latest/page/nrf/index.html) (ncs; > v2.8) and connect the MicoMod DK Board with USB to your PC.

## Building and running

To build the Zephyr blinky sample, run the following command:

```
cd micromod9151-getting-started
west build -b micromod9151/nrf9151/ns $ZEPHYR_BASE/samples/basic/blinky -- -DBOARD_ROOT=$PWD
```

Once you have built the application, run the following command to flash it:

```
west flash
```

## Testing

The MicroMod DK comes with an Serial to USB convert, open it to see the serial communication of the nRF9151 MicroMod board:

```
screen /dev/ttyACM0 115200
```

## Hardware

The nRF9151 MicroMod Processor board has a SIM card connector on the bottom of the board, it has an external flash ([MX25R3235F](https://www.macronix.com/Lists/Datasheet/Attachments/8755/MX25R3235F,%20Wide%20Range,%2032Mb,%20v1.8.pdf)) to support over the air updates and GPIO expander to access all the MicroMod pins.

### GPIO expander

The GPIO expander is a [MCP23S18](https://ww1.microchip.com/downloads/aemDocuments/documents/APID/ProductDocuments/DataSheets/MCP23018-Data-Sheet-DS20002103.pdf) with open-drain outputs.

### Pinout

| micromod9151 Pin       | Primary Function        | Bottom Pin | Top Pin | Primary Function                 | micromod9151 Pin       |
| :--------------:       | :--------------:        | :--------: | :-----: | :--------------:                 | :--------------:       |
| -                      | (Not Connected)         |            | 75      | GND                              | -                      |
| -                      | 3.3V                    | 74         | 73      | G5 / BUS5                        | GPIO A3 (MCP23S18)     |
| -                      | -                       | 72         | 71      | G6 / BUS6                        | GPIO A4 (MCP23S18)     |
| -                      | -                       | 70         | 69      | G7 / BUS7                        | GPIO A5 (MCP23S18)     |
| -                      | -                       | 68         | 67      | G8                               | GPIO A6 (MCP23S18)     |
| -                      | -                       | 66         | 65      | G9                               | GPIO A7 (MCP23S18)     |
| -                      | -                       | 64         | 63      | G10                              | GPIO B0 (MCP23S18)     |
| P0.30 (nRF9151)        | SPI_SDO1 (O)            | 62         | 61      | SPI_SDI (I)                      | P0.00 (nRF9151)        |
| P0.31 (nRF9151)        | SPI_SCK1 (O)            | 60         | 59      | SPI_SDO (O)                      | P0.01 (nRF9151)        |
| -                      | -                       | 58         | 57      | SPI_SCK (O)                      | P0.03 (nRF9151)        |
| -                      | -                       | 56         | 55      | SPI_CS#                          | P0.02 (nRF9151)        |
| -                      | -                       | 54         | 53      | I2C_SCL1 (I/O)                   | P0.04 (nRF9151)        |
| -                      | -                       | 52         | 51      | I2C_SDA1 (I/O)                   | P0.05 (nRF9151)        |
| -                      | -                       | 50         | 49      | BATT_VIN/3 (I - ADC) (0 to 3.3V) | AIN7 / P0.20 (nRF9151) |
| GPIO A2 (MCP23S18)     | G4 / BUS4               | 48         | 47      | PWM1                             | P0.16 (nRF9151)        |
| GPIO A1 (MCP23S18)     | G3 / BUS3               | 46         | 45      | GND                              | -                      |
| GPIO A0 (MCP23S18)     | G2 / BUS2               | 44         | 43      | -                                | -                      |
| P0.18 (nRF9151)        | G1 / BUS1               | 42         | 41      | -                                | -                      |
| P0.17 (nRF9151)        | G0 / BUS0               | 40         | 39      | GND                              | -                      |
| AIN1 / P0.14 (nRF9151) | A1                      | 38         | 37      | -                                | -                      |
| -                      | GND                     | 36         | 35      | -                                | -                      |
| AIN0 / P0.13 (nRF9151) | A0                      | 34         | 33      | GND                              | -                      |
| P0.16 (nRF9151)        | PWM0                    | 32         | 31      | Module Key                       | -                      |
| -                      | Module Key              | 30         | 29      | Module Key                       | -                      |
| -                      | Module Key              | 28         | 27      | Module Key                       | -                      |
| -                      | Module Key              | 26         | 25      | Module Key                       | -                      |
| -                      | Module Key              | 24         | 23      | SWDIO                            | SWDIO (nRF9151)        |
| P0.11 (nRF9151)        | UART_TX2 (O)            | 22         | 21      | SWCLK                            | SWDCLK (nRF9151)       |
| P0.12 (nRF9151)        | UART_RX2 (I)            | 20         | 19      | UART_RX1 (O)                     | P0.06 (nRF9151)        |
| GPIO B3 (MCP23S18)     | D1                      | 18         | 17      | UART_TX1 (I)                     | P0.07 (nRF9151)        |
| P0.10 (nRF9151)        | I2C_INT#                | 16         | 15      | UART_CTS1                        | P0.08 (nRF9151)        |
| P0.21 (nRF9151)        | I2C_SCL (I/O)           | 14         | 13      | UART_RTS1                        | P0.09 (nRF9151)        |
| P0.22 (nRF9151)        | I2C_SDA (I/O)           | 12         | 11      | BOOT# (I - Open Drain)           | P0.19 (nRF9151)        |
| GPIO B2 (MCP23S18)     | D0                      | 10         | 9       | -                                | -                      |
| GPIO B1 (MCP23S18)     | G11                     | 8          | 7       | GND                              | -                      |
| -                      | RESET# (I - Open Drain) | 6          | 5       | -                                | -                      |
| GPIO B4 (MCP23S18)     | 3.3V EN                 | 4          | 3       | -                                | -                      |
| -                      | 3.3V                    | 2          | 1       | GND                              | -                      |
