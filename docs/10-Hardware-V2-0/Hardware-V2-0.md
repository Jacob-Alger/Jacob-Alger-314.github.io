---
title: Hardware V2.0
---

## Version 2.0

When making anything, hindsight is always 20/20. On this page, I will discuss every part of my PCB and Schematic for my HMI that I would change if I were to make a Version 2.0 of my subsystem. 

The first thing I would do is make sure the ribbon cable connectors aren't too close together, as they currently are. I had to use male headers to solder, and female-to-female jumper wires to mimic the ribbon cable, as I couldn't put both ribbon cables on at the same time. This was frustrating as the entire point of the ribbon cables is to make daisy-chaining the boards simple, but I had to plug each line in carefully, one by one, into the communication subsystem.

The second thing I would do is utilize the silkscreen far more. I sort of used it with the OLED screen, because all I was adding was female header pins to plug the OLED in, but I added a silkscreen of the screen size, so I didn't crowd the screen and make my board unable to hold it. However, I did not use the silkscreen to label the buttons, my jumpers, or the conditional logic on my board. This was ultimately fine since I built the board and had the schematic to reference from, but it would have been nice to be able to just read the PCB and understand what the jumpers are for and what the buttons are labeled.

The third thing I would change is some of the footprints and components I picked, which proved difficult to solder. The prime example is the inductor, which I ended up ripping off a pad and had to add a wire to circumvent the trace. This could have been fixed if I had made the pads wider than the part or if I had picked an inductor that was easier to solder. I also could have used a reflow oven, but I wanted to solder everything myself to build my soldering skills. I should also have picked larger debug/reset buttons, as they ended up being tiny and hard to use, or easy to break. For my first PCB with surface-mount components, it worked, and I was able to populate it, but I could have made my life easier with better component selection and footprint design.

The last thing I would change is small, but a place to store unused jumpers would be nice. I ended up using my spare headers to hold the USB jumper, or the power sharing jumpers, but I should have done what I did with the power supply header and added a dead line that could be the off position. This would also include the silkscreen change, which would help me, at a glance, ensure that everything is connected properly.

Overall, I am largely happy with my design, as it ended up functioning fully, but there are many changes I could have made to make my life far easier.
