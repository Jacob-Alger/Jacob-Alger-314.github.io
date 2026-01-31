---
title: Human Machine Interface Module Requirements
---

## Module Requirements
The following table, *Table 1*, documents the requirements the Human Machine Interface (HMI) module must meet to be considered a success for my team and the class. My subsystem needs to, at minimum, allow the user to control the device in direct-drive mode, read the sensor data in text and graphical form, and toggle GPIO pins across the entire system. The HMI will take the form of a controller separate from the rover and will also interact with the communication module to control the rover and receive sensor data. Whether this takes the form of two communication modules, with the HMI having a slave module, or the controller serving as the master system and the rover having a slave module, is still unknown as our team learns more about wireless communication.

*Table 1: HMI Subsystem Requirements*

| **Requirement Description** | **Measure of<br> Threshold** | **Target<br>Measure** |**Stretch<br>Requirement<br>(Y-N)**|
|-----------------------------| ----------------- | ----------------- | :-----: |
| Surface mounted, 3.3V switching power regulator | 3.2 Volts | 3.3 Volts | No |
| Surface mounted microcontroller | 1 PIC or ESP | ESP | No |
| Wireless Communication | Able to send or receive data | Send movement instructions with less than half-second delay and receive sensor data in less than 15 seconds | No |
| Movement Controls | Enough Buttons to move rover and control screen | D-Pad and 4 selecting buttons | No |
| Movement Controls | Analog Stick that can move the rover in 4 directions | Full analog movement for precise control | Yes |
| OLED Screen | Able to display 1 sensor's data at a time | Can show a summary of all sensors, in both Numerical and Graphical Form | No |
| Data Management | Able to modify sensor threshold when measuring | Menu that allows every sensor setpoint to be edited | No |
| Data Management | Can remember previous measurement for comparison | Can export all data in file format | Yes |
| Controller Body | Able to be held comfortably in two hands | Between 6-8 inches wide | Yes |
