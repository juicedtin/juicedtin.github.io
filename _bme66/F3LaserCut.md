---
title: "F3 &#124;&#124; Laser Cutting an Acrylic Box"
excerpt: "Laser-cutting a open-topped box out of frosted acrylic as a pencil holder!"
permalink: /bme66/F3
classes: wide
sidebar:
- title: Relevant Topics
  text:  Laser Cutting, Acrylic Bonding, Illustrator, SolidWorks
---
- [Introductions](#introductions)
- [Pattern and Kerf](#pattern-and-kerf-nolop)
- [SolidWorks Sketch](#solidworks-sketch)
- [Wood TestRun](#wood-testrun)

## Introductions
Laser cutting is great for making gifts, so I figured I'd make a gift for one of my friends in the form of a pencil holder/cup/whatchamacallit. I also thought that making something like this would be a good way to get into 3D rapid prototyping via laser cutting, since 2D machining is a little easier on harder materials like acrylic and metal if I wanted to use the waterjet, etc. It's also nice that it's much easier to print patterns, and Illustrator has an easy "image trace" function (more on that below). 

## Pattern and Kerf (Nolop)
When I first started working on this project, I wasn't sure if I would be able to do my fabrication on the Bray machines - so I decided to do a Nolop test run to take a look at how different patterns come out on frosted acrylic and to note the relevant kerf for that laser cutter. 

| Illustrator 2D Vector Drawing |  Cut Product |
|:-------------------------:|:-------------------------:|
<img src="../assets/images/F3/Testrun.png" alt ="Illustrator vector image of the laser cut test run" width = 350> | ![Full laser cut output on frosted acrylic](/assets/images/F3/TestrunCut.png)

Although this wasn't that useful in the end, I did measure out a kerf of approximately `0.195mm` that might be useful for me or others who wish to cut on the Nolop machine later on. 

## SolidWorks Sketch

<img src = "../assets/images/F3/PaperPlans.png" alt="Paper schematics of the box before SolidWorks design" align="right" width="500">
After doing some drawings on paper to make sure I was getting my design straight (right)
To make sure I'm not going insane when it comes to matching tabs and slots, I decided to make the box entirely in SolidWorks, then add kerf compensation, etc. after exporting to DXF to make my life easier. I won't bore you with all of the sketch documentation - it was essentially the same process as in [F1](juicedtin.github.io/bme66/f1), and the final product looks something like this: 

![Full SolidWorks tab-box sketch without compensation for kerf](/assets/images/F3/SW%20Box3D.PNG)

I exported these to DXFs using SolidWorks (making sure to specify the plane I was exporting to): 
| Base DXF |  North/South Face DXFs | East/West Face DXFs |
|:-------------------------:|:-------------------------:|:-------------------------:|
<img src="../assets/images/F3/BoxBaseNKDXF.png" alt ="Vector DXF of the box base" width = 300> | <img src="../assets/images/F3/BoxFaceNSNKDXF.png" alt ="Vector DXF of the north and south box faces" width = 300> |<img src="../assets/images/F3/BoxFaceEWNKDXF.png" alt ="Vector DXF of the box base" width = 300> |

And now I have my Illustrator files, ready for some cool designs to be plastered on them via image trace!

## Wood TestRun

First things first, I don't want to use the _precious_ frosted acrylic considering how expensive it is - so I decided to do a wood testrun in Nolop over the weekend before my Bray "actual" run. Which means I need to figure out how to deal with kerf. How fun.

Since one of my high-school friends has a really cute cat, I decided to play around with the test print and figure out what it would look like if you plastered Lilac's face via bitmap and raster onto my kerf test: 

| Illustrator 2D Vector Drawing |  Cut Product |
|:-------------------------:|:-------------------------:|
<img src="../assets/images/F3/WoodTestCut.svg" alt ="Illustrator vector image of the laser cut test run" width = 350> | <img alt="Full laser cut output on frosted acrylic" src="../assets/images/F3/TestrunCutWood.jpg" width=350>

Looks like Lilac got a little mangled in the engraving - bitmap doesn't translate brightness super well into wood. Good thing my target symbols up above came out relatively well, though! Calculated kerf came out to `0.195 mm`, which checks out to be almost exactly the same as acrylic (interesting, I thought it would be slightly wider).

Putting everything into Illustrator (all 5 faces and the patterns, along with some cool etched frames), I use the Offset Path tool to push out all of my current lines by 0.195 mm to get this as my final cut that I sent into Nolop:
![Final Illustrator Cut File](/assets/images/F3/BoxFaces%20WoodK.png)
After cutting, I got something like this:

### Bonding the Box
To bond the testrun, I used wood glue and some clamps

