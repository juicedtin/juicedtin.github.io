---
title: "F5 &#124;&#124; Molding and Casting - Hands, Keycaps"
excerpt: "Trying to mold and cast a keycap (and a hand)!"
permalink: /bme66/F2
classes: wide
sidebar:
- title: Relevant Topics
  text:  Molding, Casting, CAD, Materials
---
- [Introductions](#introductions)
- [CAD-ing a Two-Piece Mold](#cad-ing-a-two-piece-mold)
- [Molding/Casting](#moldingcasting)

## Introductions
Molding and casting, although a pretty old and unpopular technique in the age of 3D printers and laser cutters, is still quite good for mass-producing a certain part or mimicking a complex shape. So, after a bunch of Reddit searching, we decided to mold two different objects - a one-piece mold of a human hand, and a two-piece mold to create a keycap for a mechanical keyboard! I took point on the two-piece mold, so I'll cover that first.

## CAD-ing a Two-Piece Mold
To start off, I needed to figure out how to make a good two-piece mold. I used the following "keycap" model from [Thingiverse](https://www.thingiverse.com/thing:2783650) as a baseline. I incorporated a few 0.2 cm radius cylinders and expanded the boundaries of the keycap to create an upper (right) and lower (left) molds in SolidWorks:
![SolidWorks upper and lower models before adding pattern](/assets/images/F5/2PieceCAD.png)

Note the "blocks" on the top model that are designed to be air holes. After this, I searched online for some vectors to slap on top of the keycap, and found the Aperture Science Logo from Portal (*"How are you holding up? Because I'm a potato" - GLaDOS*) as a pretty good structure that interfaced well into Solidworks as a DXF. I added this to the keycap and extruded it by 0.25cm, which made the final bottom mold look like this: 
![Solidworks import and extrude of the Aperture Science logo](/assets/images/F5/ApertureExtrude.png)

I 3D printed these using PLA filament
![3D printed keycap molds](/assets/images/F5/3DPrintMolds.jpg) - now onto molding! 

## Molding/Casting

To create silicone molds that I would later cast polyurethane into, I utilized [Ecoflex 00-30 Pt-cured silicone](https://www.smooth-on.com/products/ecoflex-00-30/), as it usually plays well with polyurethane, along with mold-releasing agent. After combining approx. 10 mL (5 mL A and B) per "side" of the mold with two syringes and curing overnight, I found that most of the features translated well:
![Silicone molds after casting](/assets/images/F5/SiliconeCastMolds.jpg)

