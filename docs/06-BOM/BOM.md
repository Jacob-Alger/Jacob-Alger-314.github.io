---
title: HMI Bill of Materials
tags:
- tag1
- tag2
---

## Overview

The bill of materials for my entire subsystem is shown in* Table 1*. It includes all components and any additional parts needed to build my PCB. Every part is either sourced from DigiKey or Peralta 109. The DigiKey parts will be ordered, with additional instances in case of errors or losses, and kept within my allotted budget of **$60**. The Peralta parts are free for my use, and are mostly general parts like headers or jumpers. You can view this BOM in PDF or XLSX format in the **Resources** section below.

* The sum total of my subsystem is **$25.04**
* The minimum total of parts that need to be ordered is **$18.50**
* However, to account for issues, the order subtotal with extras is **$29.35**

## Bill of Materials

*Table 1: Human-Machine Interface Bill of Materials*

| Part Name / Description | Qty | Unit Cost | Total Cost | Manufacturer | Manufacturer # | Supplier | Vendor Link | Datasheet Link | Schematic Reference Designators |
|---|---|---|---|---|---|---|---|---|---|
| Barrel Jack Connector | 1 | $0.71 | $0.71 | Same Sky | PJ-102AH | DigiKey | [Link](https://www.digikey.com/en/products/detail/same-sky-formerly-cui-devices/PJ-102AH/408448?s=N4IgTCBcDaIAoCkC0BGADGAggCRAXQF8g) | [PDF](https://www.cuidevices.com/product/resource/pj-102ah.pdf) | J1 |
| 3.3V Switching Voltage Regulator | 1 | $2.16 | $2.16 | onsemi | LM2575D2T-3.3R4G | DigiKey | [Link](https://www.digikey.com/en/products/detail/onsemi/LM2575D2T-3-3R4G/1476688) | [PDF](https://www.onsemi.com/pdf/datasheet/lm2575-d.pdf) | U1 |
| ESP32 Microcontroller | 1 | $5.06 | $5.06 | Espressif Systems | ESP32-S3-WROOM-1-N4 | DigiKey, Peralta | [Link](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639) | [PDF](https://www.espressif.com/sites/default/files/documentation/esp32-s3-wroom-1_wroom-1u_datasheet_en.pdf) | U2 |
| OLED Screen | 1 | $- | $- | GoldenMorning Electronic | GME12864-17 | Peralta | n/a | [PDF](https://goldenmorninglcd.com/oled-display-module/0.96-inch-128x64-ssd1306-gme12864-11/) | U12 |
| 12mm Pushbutton | 7 | $0.60 | $4.20 | E-Switch | TL3300CF160Q | DigiKey | [Link](https://www.digikey.com/en/products/detail/e-switch/TL3300CF160Q/2498433) | [PDF](https://configured-product-images.s3.amazonaws.com/Datasheets/TL3300.pdf) | U5, U6, U7, U8, U9, U10, U11 |
| 3mm Pushbutton | 3 | $0.90 | $2.70 | Omron Electronics Inc-EMC Div | B3U-1000P | DigiKey | [Link](https://www.digikey.com/en/products/detail/omron-electronics-inc-emc-div/B3U-1000P/1534338) | [PDF](https://omronfs.omron.com/en_US/ecb/products/pdf/en-b3u.pdf) | U3, U4, U13 |
| USB Micro B Receptacle | 1 | $0.77 | $0.77 | GCT | USB3131-30-0230-A | DigiKey, Peralta | [Link](https://www.digikey.com/en/products/detail/gct/USB3131-30-0230-A/9859642) | [PDF](https://gct.co/files/specs/usb3131-spec.pdf) | J5 |
| Red LED | 1 | $0.71 | $0.71 | Visual Communications Company - VCC | CMD17-21VRD/TR8 | DigiKey | [Link](https://www.digikey.com/en/products/detail/visual-communications-company-vcc/CMD17-21VRD-TR8/254853) | [PDF](https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/4320/CMD17-21_Rev10.pdf) | D4 |
| Green LED | 1 | $0.67 | $0.67 | Visual Communications Company - VCC | CMD17-21VGD/TR8 | DigiKey | [Link](https://www.digikey.com/en/products/detail/visual-communications-company-vcc/CMD17-21VGD-TR8/254855) | [PDF](https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/4320/CMD17-21_Rev10.pdf) | D2 |
| Blue LED | 1 | $0.45 | $0.45 | QT Brightek (QTB) | QBLP653-IB5-2897 | DigiKey | [Link](https://www.digikey.com/en/products/detail/qt-brightek-qtb/QBLP653-IB5-2897/22106657) | [PDF](https://www.qt-brightek.com/datasheet/QBLP653-IB5-2897.pdf) | D3 |
| 100uF, 50V Electrolytic Capacitor | 1 | $0.93 | $0.93 | Panasonic Electronic Components | EEE-FTH101XAP | DigiKey | [Link](https://www.digikey.com/en/products/detail/panasonic-electronic-components/EEE-FTH101XAP/2652055) | [PDF](https://industrial.panasonic.com/cdbs/www-data/pdf/RDE0000/ABA0000C1240.pdf) | C1 |
| 330uF, 25V Electrolytic Capacitor | 1 | $0.85 | $0.85 | Panasonic Electronic Components | EEE-FK1E331P | DigiKey | [Link](https://www.digikey.com/en/products/detail/panasonic-electronic-components/EEE-FK1E331P/765972) | [PDF](https://industrial.panasonic.com/cdbs/www-data/pdf/RDE0000/ABA0000C1181.pdf) | C2 |
| 22uF, 25V Ceramic Capacitor | 1 | $0.33 | $0.33 | Murata Electronics | GRM21BR61E226ME44K | DigiKey | [Link](https://www.digikey.com/en/products/detail/murata-electronics/GRM21BR61E226ME44K/6606267) | [PDF](https://search.murata.co.jp/Ceramy/image/img/A01X/G101/ENG/GRM21BR61E226ME44-01.pdf) | C4 |
| 1uF, 25V Ceramic Capacitor | 1 | $0.12 | $0.12 | KEMET | C0805C105K3RACTU | DigiKey | [Link](https://www.digikey.com/en/products/detail/kemet/C0805C105K3RACTU/2211765) | [PDF](https://yageogroup.com/content/datasheet/asset/file/KEM_C1002_X7R_SMD) | C6 |
| 0.1uF, 50V Ceramic Capacitor | 13 | $0.08 | $1.04 | KEMET | C0805C104K5RACTU | DigiKey | [Link](https://www.digikey.com/en/products/detail/kemet/C0805C104K5RACTU/411169?s=N4IgTCBcDaIMIAYAcCCscCMCAsBpVASgIJwAqAqiALoC%2BQA) | [PDF](https://yageogroup.com/content/datasheet/asset/file/KEM_C1002_X7R_SMD) | C3, C5, C7, C8, C9, C10, C11, C12, C13, C14, C15, C16, C17 |
| 100, 1/4W Resistor | 1 | $0.10 | $0.10 | YAGEO | RC1206JR-10100RL | DigiKey | [Link](https://www.digikey.com/en/products/detail/yageo/RC1206JR-10100RL/13694487) | [PDF](https://yageogroup.com/content/datasheet/asset/file/PYU-RC_GROUP_51_ROHS_L) | R11 |
| 330, 1/4W Resistor | 2 | $0.11 | $0.22 | YAGEO | RC1206FR-07330RL | DigiKey | [Link](https://www.digikey.com/en/products/detail/yageo/RC1206FR-07330RL/728822) | [PDF](https://yageogroup.com/content/datasheet/asset/file/PYU-RC_GROUP_51_ROHS_L) | R1, R13 |
| 10k, 1/4W Resistor | 10 | $0.10 | $1.00 | Stackpole Electronics Inc | RMCF1206JG10K0 | DigiKey | [Link](https://www.digikey.com/en/products/detail/stackpole-electronics-inc/RMCF1206JG10K0/21720266) | [PDF](https://www.seielect.com/catalog/SEI-RMCF_RMCP.pdf) | R2, R3, R4, R5, R6, R7, R8, R9, R10, R12 |
| 220uH, 1.38A, 380mOhm Inductor | 1 | $1.01 | $1.01 | Bourns Inc. | SRR1260-221K | DigiKey | [Link](https://www.digikey.com/en/products/detail/bourns-inc/SRR1260-221K/1969970) | [PDF](https://www.bourns.com/docs/Product-Datasheets/SRR1260.pdf) | L1 |
| 40V, 3A Schottky Diode | 1 | $0.69 | $0.69 | onsemi | SS34 | DigiKey | [Link](https://www.digikey.com/en/products/detail/onsemi/ss34/1052384) | [PDF](https://www.onsemi.com/download/data-sheet/pdf/ss39-d.pdf) | D1 |
| 800mA Fuse 5x20mm | 1 | $0.57 | $0.57 | SCHURTER Inc. | 34.1515 | DigiKey, Peralta | [Link](https://www.digikey.com/en/products/detail/schurter-inc/0034-1515/639670) | [PDF](https://www.schurter.com/en/datasheet/typ_FSF_5x20.pdf) | F1 |
| Cartridge Fuse Holder 5x20mm | 1 | $0.75 | $0.75 | Keystone Electronics | 4628 | Digikey, Peralta | [Link](https://www.digikey.com/en/products/detail/keystone-electronics/4628/2137316) | [PDF](https://www.keyelco.com/userAssets/file/K75p50.pdf) | F1 |
| 40 Pin Male Header Connector | 1 | $- | $- | Lystaii | n/a | Peralta | [Link](https://www.amazon.com/Header-Lystaii-Pin-Connector-Electronic/dp/B06ZZN8L9S/ref=sr_1_15?dchild=1&keywords=40+pin+header+male+to+male&qid=1608606507&sr=8-15) | n/a | J2, J3, J4, J6, J7, J8, J9, J10, J11, J12 |
| 40 Pin Female Header Connector | 1 | $- | $- | Qunqi | n/a | Peralta | [Link](https://www.amazon.com/Qunqi-2-54mm-Straight-Connector-Arduino/dp/B07CGGSDWF/ref=sr_1_17?dchild=1&keywords=female+header+strips&qid=1595380282&sr=8-17) | n/a | U12 |
| 2-pin Female Jumper Connector | 6 | $- | $- | n/a | n/a | Peralta | n/a | n/a | J3, J4, J6, J7, J9, J11 |

> Note: This table scrolls side to side. Please scroll to see all of the information.

## Resouces

The Bill of Materials is available as a PDF [*here*](../06-BOM/EGR314-HMI_BOM.pdf) and as an XLSX download [*here*](../06-BOM/EGR314-HMI_BOM.xlsx).


