---
title: "F2 &#124;&#124; Printing the Syringe Scaffold"
excerpt: "Printing my previously-CADed syringe scaffold via Prusa printers!"
permalink: /bme66/F2
classes: wide
sidebar:
- title: Relevant Topics
  text:  PRUSASlicer, 3D Printing
---
- [Introductions](#introductions)
- [Slicing](#slicing)

## Introductions
Now that I've made a SolidWorks assembly for the syringe scaffold from [F1](juicedtin.github.io/bme66/F1), I can try to 3D print it from an STL file! This is a relatively short assignment documentation-wise, since there's not a whole lot of design required.

## Slicing
All 3D printers operate off of GCode, which tells it what to deposit, where to deposit it, at what time to deposit it, what supports are required, etc. Because I'll be using PRUSA printers for this type of thing, I decided to use the open-source [PrusaSlicer](https://github.com/prusa3d/PrusaSlicer/releases) for this. After exporting my assembly in STL form, I imported it into the PrusaSlicer program.

Note that SolidWorks can export either the entire assembly or each file separately. Distinguishing from this is a weird file setting in options (thanks Tracy for pointing out this issue) at the Save As screen. 
{: .notice}

I used the default values for my first slicing attempt, checking "generate supports" and "brim" so I can see what's needed, and increase the stability of the model as much as possible:
![First slicing attempt via PrusaSlicer](/assets/images/F2/FirstSlice.png)

Quite a lot of supports. I diagnosed that this is probably due to how thin and tall the model is - so I tried to fiddle with the settings and used a "Snug" support structure, along with only building supports on the build plate instead. Although this is theoretically less stable for tall and thin structures, it decreased the printing time significantly to approx. 4:24 (which is still a while, but not the 7 hours of the previous iteration)
![Second slicing attempt via PrusaSlicer](/assets/images/F2/SecondSlice.png)
