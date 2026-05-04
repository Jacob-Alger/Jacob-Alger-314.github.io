---
title: HMI Microcontroller Selection
---
## Selected Microcontroller

* Peripherals Needed: I2C, UART, GPIO (~10), USB, Bluetooth, Wi-Fi
* **ESP32-S3-WROOM-1-N4**: 36 GPIOs, *“ESP32-S3 integrates a rich set of peripherals including SPI, LCD, Camera interface, UART, I2C, I2S, remote control, pulse counter, LED PWM, USB Serial/JTAG, MCPWM, SD/MMC host controller, TWAI® controller (compatible with ISO 11898-1, i.e., CAN Specification 2.0), ADC, touch sensor, and temperature sensor. It also includes a full-speed USB 2.0 On-The-Go (OTG) interface to enable USB communication.”*

I have selected the ESP32-S3-WROOM-1-N4 because I know it will cover everything I need for my subsystem. I have reached this conclusion using the reasoning and selection process outlined below. The ESP32-S3-WROOM-1-N4 supports I2C, UART, and GPIO, which is everything I need to build my subsystem. If later I realize there's an issue with this process I didn't see, I will redo it and select a new microcontroller type, but it will most likely be an ESP32, as that is what most OLED screens prefer.

In *Table 1* below, I have left a few sections blank because I need to become more familiar with my project before I can fill them in. However, as I find useful things, I will save them in the table for later use.

*Table 1: ESP32 Info*

| ESP Info                                      | Answer | Notes  |
| --------------------------------------------- | ------ | ------------------------------------------------------------------------------------------------------- |
| Model                                         | ESP32-S3-WROOM-1-N4      | Surface Mount module |
| Product Page URL                              | [Espressif.com](https://www.espressif.com/en/module/esp32-s3-wroom-1-en)      |          |
| ESP32-S3-WROOM-1-N4 Datasheet URL             | [Datasheet PDf](https://documentation.espressif.com/esp32-s3-wroom-1_wroom-1u_datasheet_en.pdf)      |   |
| ESP32 S3 Datasheet URL                        | [Datasheet PDF](https://documentation.espressif.com/esp32-s3_datasheet_en.pdf)      |  |
| ESP32 S3 Technical Reference Manual URL       | [Manual PDF](https://documentation.espressif.com/esp32-s3_technical_reference_manual_en.pdf)      |     |
| Vendor link                                   | [Digikey](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639)      |    |
| Code Examples                                 | ?      | url(s) for libraries on github or other sites related to the microcontroller and your planned peripherals |
| External Resources URL(s)                     | ?      | Search on Google and YouTube for other resources for each specific microcontroller.   |
| Unit cost                                     | $5.06     |    |
| Absolute Maximum current <br> (for entire IC)        | 1.5 A or 1500 mA      |  |
| Supply Voltage Range                          | 0.3V / 3.3V / 3.6 V      | Min / Ideal / Max |
| Maximum GPIO current <br> (per pin)           | 40 mA      |  |
| Supports External Interrupts?                 | Yes      | |
| Required Programming Hardware, Cost, URL      | USB Micro B Receptacle, $0.78, [Digikey](https://www.digikey.com/en/products/detail/jae-electronics/DX4R005JJ2R1800/3903229?s=N4IgTCBcDaIGwHYAMBaMiCsKCMKByAIiALoC%2BQA)  | Also requires Boot and Enable Buttons, see Component Selection and Schematic for more information |

## Subsystem Explanation

My subsystem, the Human-Machine Interface, will need to facilitate device control and sensor data reading for my team. My subsystem will need a screen, specifically an OLED, that can display data in both numerical and graphical formats, so the user can read and understand the exploration device's sensing data. The OLED screen will also let the user know which part of the rover they are currently controlling: the wheels or the arm subsystems. Control will be via pushbuttons for movement, selection, and menu navigation. The buttons should also allow the user to change parameters to some extent. Then the system will need to communicate with the communication subsystem, which will send button inputs and receive sensor data. All of these features will need to be facilitated by the microcontroller for reading signals, displaying, and interpreting user input.

## Chip Compatibility

* OLED - ESP32 can handle since we are using it in class. Should be able to use any OLED with I2C and appropriate libraries. The ESP32-S3-WROOM-1-N4 can manage the OLED display, interpret button inputs, and communicate via UART.
* Buttons - ESP32, like any microcontroller, has plenty of GPIOs that can be used with pushbuttons to interpret input signals. The ESP32-S3-WROOM-1-N4 has internal pullups on certain pins, but I plan to use external pullups on every button for safety.

## Pinout Diagram and Table

![Pinout Diagram](../04-Microcontroller-Selection/ESP32-S3-WROOM-1-N4_PinoutFigure.png)

**Figure 1: Pinout Diagram sourced from ESP32-S3-WROOM-1-N4 Datasheet.**

*Table 2: Peripherals and Pins*

| Peripheral               | Pins Used                                                                 | Notes |
|---------------------------|--------------------------------------------------------------------------|-------|
| UART0                     | RXD0 (36), TXD0 (37)                                                     | Default hardware UART0 RX/TX on module; used for serial console/programming by default. UART0 hardware flow control can map to IO15/IO16 via IO MUX but is generally routed via the GPIO matrix if needed. |
| UART1                     | IO17 (10), IO18 (11), IO19 (13), IO20 (14)                               | UART1 signals are available on these pins via IO MUX by default (TX/RX/RTS/CTS). All UARTs can also be reassigned via GPIO Matrix to almost any GPIO. |
| UART2                     | No fixed pins                                                             | UART2 does not have default mapped pins in the module; must be assigned via GPIO Matrix. |
| I2C (I2C0/I2C1)           | Any GPIO pins via GPIO Matrix                                             | Two I2C interfaces; no fixed SDA/SCL — choose via GPIO Matrix. |
| SPI0 / SPI1 (Flash/PSRAM) | Module internal (not exposed as general GPIO)                             | SPI0 and SPI1 are connected to flash/PSRAM in package; these signals (e.g., SPICLK, SPIQ, etc.) are on pins such as IO8–IO15 and IO46–IO48 but are not recommended for general peripherals. |
| SPI2 (Host SPI)           | Any GPIO pins via GPIO Matrix                                             | Available as general SPI; assign MOSI/MISO/SCLK/CS via GPIO Matrix. |
| SPI3                      | Any GPIO pins via GPIO Matrix                                             | General SPI available for use; assign via GPIO Matrix. |
| ADC (SAR ADC1 / ADC2)     | IO0, IO1, IO2, IO3, IO4, IO5, IO6, IO7, IO8, IO9, IO10, IO11, IO12, IO13, IO14, IO15, IO16, IO17, IO18, IO19, IO20 (multiplexed) | Two 12‑bit SAR ADCs; analog functions are multiplexed with GPIOs 0–20. For ADC2 when Wi‑Fi is active, ADC2 channels may not be usable. |
| USB OTG (integrated)      | GPIO19 (13) USB_D‑, GPIO20 (14) USB_D+                                    | USB OTG data signals are multiplexed with GPIO19/20; see datasheet for USB Serial/JTAG options. |
| LED PWM (LEDC)            | Any GPIO pins via GPIO Matrix                                             | PWM channels can be output on virtually any GPIO. |
| Motor PWM (MCPWM)         | Any GPIO pins via GPIO Matrix                                             | MCPWM channels are assignable via GPIO Matrix. |

### Final Pins and Peripherals

*Table 3: Pins and Peripherals Used*

| Peripheral | GPIO | Module Pin # | Direction | Connected To | Notes |
|------------|------|-------------|-----------|--------------|-------|
| UART2 TX | IO17 | 10 | Output | Daisy-chain UART bus | Assigned via GPIO Matrix; 9600 baud, 8N1 |
| UART2 RX | IO18 | 11 | Input | Daisy-chain UART bus | Assigned via GPIO Matrix; internal pull-up enabled |
| SoftI2C SCL | IO13 | 21 | Output | SSD1306 OLED display | Software I2C via GPIO Matrix; clock line |
| SoftI2C SDA | IO14 | 22 | Bidirectional | SSD1306 OLED display | Software I2C via GPIO Matrix; data line |
| LED PWM (LEDC) | IO10 | 18 | Output | Blue LED | GPIO Matrix; 1000 Hz PWM; duty_u16 controls brightness |
| GPIO Output | IO12 | 20 | Output | Red LED | Heartbeat; toggled by Hardware Timer 0 at 1 Hz |
| GPIO Input | IO9 | 17 | Input | Comm subsystem wifi_ready signal | Internal pull-down; HIGH = MQTT handshake complete |
| GPIO Input | IO4 | 4 | Input | Button UP | Active LOW; external pull-up; IRQ falling edge |
| GPIO Input | IO5 | 5 | Input | Button RIGHT | Active LOW; external pull-up; IRQ falling edge |
| GPIO Input | IO6 | 6 | Input | Button DOWN | Active LOW; external pull-up; IRQ falling edge |
| GPIO Input | IO7 | 7 | Input | Button LEFT | Active LOW; external pull-up; IRQ falling edge |
| GPIO Input | IO8 | 8 | Input | Button MENU | Active LOW; external pull-up; IRQ falling edge; mode cycle / shift key |
| GPIO Input | IO11 | 19 | Input | Button DEBUG | Active LOW; external pull-up; IRQ falling edge |
| GPIO Input | IO15 | 8 | Input | Button SELECT | Active LOW; external pull-up; IRQ falling edge |
| GPIO Input | IO16 | 9 | Input | Button BACK | Active LOW; external pull-up; IRQ falling edge |
| Hardware Timer 0 | — | — | Internal | Red LED heartbeat callback | PERIODIC mode; 1000 ms period; no dedicated GPIO |
