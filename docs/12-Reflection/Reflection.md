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
    - **Yes**, I included the ESP32-S3-WROOM-1-N4 microcontroller from Espressif. I used several peripherals, which are listed on the Microcontroller Selection Page.
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

## Microcontroller/Module Startup Tips

1. USB Connection: If using an ESP32, you may notice that when you connect to your computer, it keeps connecting and disconnecting. A fix I used is to hold your boot button (very useful to include), then plug in the USB cable. While still holding the boot, tap enable/reset (again, useful button) then release the boot button. You should hopefully notice that the USB connection has stabilized and that the COM port may have switched.
2. Thonny: Learning how to configure your board using Thonny is very useful, as Thonny will recognize what ESP32 you are using and download the firmware automatically. Thonny also helps with uploading your first test program.
3. MPRemote: MPRemote is a Python tool that helps to upload your MicroPython code to your ESP32 using VSCode. All you need to do is install it, and then you can use 4 useful commands. **mpremote connect auto** lets you connect to the ESP32 REPL. **mpremote connect auto fs cp -r . :** uploads your current project to the ESP32. **mpremote fs ls -r** lets you see the files currently on your ESP32 (useful to check that the program function worked). **mpremote connect auto fs rm -r :** deletes the files on your ESP32, which is useful to clean up clutter from other testing/programs.
4. Pin Numbers: When programming your ESP32, remember that the physical pin location numbers are not the same as the GPIO pin numbers that micropython wants. Very important to remember when trying to blink an LED for the first time.

## Lessons Learned

1. Datasheets, datasheets, datasheets. Make sure that you read the datasheets, as many issues or questions you may have are probably answered there. This is very important for your voltage regulator, as each switching regulator will most likely use different components based on what you want, and the datasheet will not only provide a schematic but also information on sizing Schottky diodes, inductors, and capacitors. They are also useful for your microcontroller. For example, the ESP32-S3 datasheet states that the ground pads on the back do not need to be soldered. They only act as a potential heatsink for high-load ESP32 designs.
2. Make sure you are communicating constantly with your teammates while making your schematic and PCB. One misunderstanding or unclarified specification can lead to a month of headaches and testing, or even a nonfunctional subsystem.
3. Go to the Professor or TAs for clarifications or schematic reviews. Many of my teammates chose the wrong ribbon connector symbol, so we had to use jumper cables to connect. This caused one of our ESP32s to fry when the unregulated voltage line accidentally fed into the UART RX pin. The teaching team can help you spot these oversights or misunderstandings before they ruin your board.
4. When soldering, don't just go from smallest to largest, but also from most important to least important. On my first board, I waited until last to solder the ESP32, which caused me to misalign it, and when I tried to remove it, I melted my plastic headers and ripped up my D+ trace. This completely killed my first board, and I had to resolder. Start with the ESP or PIC, because if you mess that up, then the whole board is ruined. It's better to fail fast and all that.
5. Think about the way you are going to solder when selecting components. For example, my inductor was very frustrating to solder because the pads were under the enclosure, and my PCB had pads that were exactly the same size. This caused me pain when soldering, and my final board even ripped up a trace because I overheated it. Think about how you might solder a part and whether you should look for a different package or redesign the footprint.
6. Larger parts are easier to solder and find in your workspace. 0805 or 1206 parts may appear large in ECAD software, but they are tiny in real life. If this is also your first time using surface-mount components, use larger parts to avoid losing them.
7. There are many tools that are very useful when soldering. I bought a pair of tweezers, pliers, solder braid, a flux pen, and solder paste, and ended up using all of them. The Peralta Lab does have some of these things you can borrow, but having your own is convenient, and most of these are inexpensive.
8. Ask about using the reflow oven or gun in the Peralta Lab. They have a ton of useful, expensive tools you can use to make your soldering easier. I didn't use the reflow oven, but I definitely used the gun a ton when resoldering or soldering the ESP32.
9. Don't be afraid to ask a ton of questions when designing your schematic and PCB. It is crucial to align with your teammates and ensure your module meets class specifications. If you don't clarify something that seems small, you may find it was actually crucial to helping your board integrate into your team's system.
10. Learning the fundamentals of code is very crucial to succeeding in this class. It may be tempting to use generative AI to write all your code, and I've used Claude and ChatGPT to program, too, but if you don't understand what it is writing, it will be impossible to debug your software when something inevitably goes wrong. Make sure you prompt with a lot of detail, ask it to explain itself or ask clarifying questions, and tell it to comment the code or write it for readability, so when you ask for help, you don't find yourself unable to articulate the issue because you have no idea what's happening in your code.

## Recommendations for Future Students

1. Make sure you seriously review your work from EGR 304. If you didn't understand something back in 304, now's the time to learn and try again.
2. Read and research things when they don't make sense. There are many videos on I2C and SPI, and learning how many bits are in a byte, why an ASCII character is a byte, and why that matters in this class is very useful.
3. Make a weekly meeting schedule with your teammates. Not only will you get to know them better, but meeting weekly will help you stay on pace and not fall behind. It's always nice to have peers who can help you.
4. Make sure you work ahead in the labs. You probably learned this quickly in EGR 304, but you cannot get the labs done in class. You need to walk in either ready for a checkoff or ready to ask a list of questions.
5. Treat this class like it is a job, because it essentially is. If you have some spare time in the afternoon, try to work ahead or go to office hours to get ahead or catch up in this class. Keeping active is the best way to avoid falling behind.
