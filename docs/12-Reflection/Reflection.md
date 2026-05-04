---
title: Reflection
---

## Review of Module's Success

Below is a list of all the requirements I set at the start of this project. I will review whether I succeeded or failed in meeting the requirement. Please review the Requirements page to refresh your memory of the success thresholds.

- **Surface-mounted, 3.3V switching power regulator**
    - **Yes**, I included the LM2575D2T-3.3R4G in my PCB, and it successfully gave a steady, regulated output of 3.3 Volts.
- **Barrel Jack Adapter Power supply**
    - **Yes**, I included the PJ-102AH that I used last semester, and found it to still be a reliable source of unregulated power from the wall adapter.
- **Jumper that switches from Barrel Jack to Upstream Power**
    - **Yes**, and I even included a jumper to allow for the USB 5 Volt output. All three of these are capable of supplying the voltage regulator and being regulated down to 3.3 Volts.
- **Surface-mounted microcontroller**
    - **Yes**, I included the ESP32-S3-WROOM-1-N4 microcontroller from Espressif. I used several peripherals, which can be reviewed on the Microcontroller Selection Page.
- **Wireless Communication**
    - **Technically**, the full controller is capable of wireless communication with minimal delay (more delay on the ASU Guest Wi-Fi) because my HMI subsystem is daisy-chained to the Communication subsystem, which allows for wireless communication. My subsystem does not allow wireless individually, but it could, since my selected microcontroller is the same as my teammate's.
- **Movement Controls**
    - **Yes**, my PCB features a Directional-Pad, which allows the user to steer the wheels and move the arm. It also includes Select, Back, and Menu buttons for navigating the modes and menus of my subsystem.
- **Movement Controls (Analog Stick Stretch Goal)**
    - **No**, I did not do a ton of research into what it would take to make this work, but I probably could rebuild this subsystem with an analog stick if I wanted to, as there are some simple modules you can buy.
- **OLED Screen**
    - **Yes**, I included an OLED screen that allows for the sensors to be read and displays the arm and wheel drive information. I didn't include any graphical support, but that would most likely just be a small code change to store previous sensor readings and then add a new OLED function.
- **Data Management**
    - **No**, I did not include the ability to set thresholds, as the modules that would best benefit this would be the metal detector and pressure sensor sensitivities, and both of those subsystems failed to become operational, so I forgot about this requirement.
- **Data Management (File Export Stretch Goal)**
  - **No**, I did not add this functionality. I would think in order to export data, I would have to build an array from the sensors, and then learn how to convert that to a CSV file, and then allow the user to connect via USB to download the files. This is beyond my capabilities, hence why it was a stretch goal.
- **Controller Body (Size Stretch Goal)**
    - **Yes**, the 3D printed controller body is 5.5 inches wide, 2.8 inches deep, and 4.785 inches tall. I found it to be fairly comfortable to hold, with rounded corners and a compact design.

## Microcontroller/Module Startup Tip

1. ...

## Lessons Learned

1. ...
2. ...
3. ...
4. ...
5. ...
6. ...
7. ...
8. ...
9. ...
10. ...

## Recommendations for Future Students

1. ...
2. ...
3. ...
4. ...
5. ...
