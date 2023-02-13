---
title: "F1 &#124;&#124; Soldiworks Syringe-Spin Project"
excerpt: "Using Soldiworks to CAD a scaffold to hold a 3-mL syringe in a 50 mL Falcon tube!"
permalink: /bme66/F1
classes: wide
sidebar:
- title: Relevant Topics
  text:  Solidworks, 3D Printing, CAD
---
- [Initial Goals](#initial-goals)
- [CAD-ing the Parts](#cad-ing-the-parts)
  - [Syringe Rest](#syringe-rest)
  - [Syringe Guide](#syringe-guide)
  - [Tube Shell](#tube-shell)
  - [Conic Endcap](#conic-endcap)
- [Assembly!](#assembly)
- [Summary (Assignment Requirements)](#summary-assignment-requirements)

## Initial Goals
In my research at the Kaplan Lab, I work on fabricating gel-spun catheters made of _Bombyx mori_ silk. The solution that I use is quite viscous, but I have to extrude it through a syringe onto a rotating mandrel - so any bubbles that get trapped in the solution presents issues with heterogeneity of the final fabrication. I usually remove these bubbles by spinning down the solution via centrifugation, but all the centrifuges I've used are constructed for 50 mL Falcon tubes rather than 3 mL syringes. Thus, I thought I would use this CAD assignment as a excuse to 3D print a scaffold that could hold my syringe in place during the centrifuging process.
All of this CAD work was done in SolidWorks, with no additional packages or add-ons involved. 
Firstly, I have to make some measurements. Using calipers, I was able to take an example Falcon tube and 3 mL syringe and record the most relevant dimensions (to 0.01 mm precision in most cases). Note that I had some issues measuring irregular segments of the tube (like the length of the conical end) using the calipers, so I estimated as best I could - I might need to refine these further before I 3D print my prototype.

![Recorded measurements of the Falcon tube and the syringe](/assets/images/F1/MeasurementNotes.png)

## CAD-ing the Parts
To make the "holder", I decided to CAD 4 different parts in SolidWorks and combine them into an assembly: 
1. The syringe rest at the top of the tube
2. A syringe guide to ensure the syringe remains perfectly upright
3. A shell that mimics the cylindrical section of the Falcon tube
4. A shell that mimics the conical section of the Falcon tube and supports the assembly (to make sure it doesn't collapse during centrifugation)

### Syringe Rest
To create the syringe rest, I first sketched a circle with a 0.1 mm tolerance with respect to the original tube, offset an inner circle to hold the syringe barrel, and traced a mirrored trapezoidal shape that fits the measurements I took of the syringe "crossguard":

![Sketch of the syringe rest before extrusion](/assets/images/F1/Syringe%20TopPlate%20Sketch.png)

When it came to dimensions, I built relations between all the relevant shapes, but left the holder for the crossguard and both circles independent, without defined relations.
 This was quite difficult to learn - I actually increased the tolerance once while going back through everything, and realized that my relations didn't actually adjust the dimensions that I wanted to adjust. I had to re-dimension and re-do all my relations to make sure that everything matched together after my changes. 
 {: .notice}
Thus, if I need to add more tolerance into the outer ring, I can do so while leaving all of the other dimensions intact.  I extruded the outer ring by 3mm and the crossguard rest by 1.5 mm to create this 3D shape:

![Extrude of the syringe rest after sketching](/assets/images/F1/Syringe%20TopPlate%20Extrude.png)

One part down, 3 more to go!

### Syringe Guide
To ensure that the syringe rests perfectly upright, I decided to make another rest similar to my first one, with slightly different dimensions. As shown in my measurements, the syringe barrel is actually slightly thinner than the top - so I adjusted the dimensioning of my sketches accordingly:

| CAD Sketch |  3mm Extrude |
|:-------------------------:|:-------------------------:|
![Sketch for syringe guide](/assets/images/F1/Syringe%20Guide%20Sketch.png) | ![Extrude for syringe guide](/assets/images/F1/Syringe%20Guide%20Extrude.png)

There's a simple syringe guide that I'll place a bit lower than the top plate in the final assembly. Annnd...that was the easy part.

### Tube Shell
I wanted to make a shell that was just a _bit_ smaller than the normal Falcon tube to support the two guides I had made. However, I didn't want to just make it a big cylinder - since this scaffold is probably going to get centrifuged at 9000x G, I thought that reducing as much weight as possible while retaining compressive strength would be ideal. After making a 85 mm tall extruded cylinder that was 2 mm thick (which I later edited to be 3.5 mm thick and 80 mm tall) from my tube measurements, I decided to try and make a pattern of some sort to cut from the cylinder.

My first idea was to cut out a helical shape, to create a "spring" that would absorb force, since PLA plastic is reasonably flexible. I tried this initially using a helix shape:

![Failed helix shape to cut into the original cylinder](/assets/images/F1/FailedHelix.png) 

I soon realized that this was not as easy as I thought it would be, since sweeping a pattern across a helix required moving sketch planes in 3D space (which I still cannot do easily, I need more practice/figure out a better way to move these sketch planes around). So, I abandoned this idea and decided to go for a different approach: patterned triangular cuts.
{: .notice}

In the Front plane, I sketched out this parallelogram-ish triangular shape:
![Sketch of the cutting shape as a pattern](/assets/images//F1/Mesh%20Pattern%20Sketch.png) that I then extruded into an extrude cut on the cylindrical surface of my shell. To make sure that I could get even spacing, I did a bit of math to dimension my pattern such that 7 repetitions of the pattern would perfectly space the patterns across the cylinder. Using the circpattern tool, I pattnered the parallleogram across the face of the cylinder, and then I used the linear pattern with a 4 mm offset (to preserve the 2 mm margins at the top and bottom of the cylinder) to extend this pattern down the shell. At the end, I had something like this:

| Initial Extrude Cut | Final Shell Pattern |
| :---: | :---: |
|![Extrude cut of the parallelogram into the cylinder](/assets/images/F1/CircPattern%20(After%20ExtrudeCut).png) | ![Final patterned tubular shell with triangular cutouts](/assets/images/F1/LinCirc%20Pattern.png) |

To put a place for the endcap I'm about to make, I also closed off the bottom of the cylinder with a 2mm cap:
![Cylindrical cap for conic end for mating](/assets/images/F1/CapCylinder.png)

### Conic Endcap
To make sure that this entire assembly doesn't just sink into the bottom of the tube when it's being centrifuged, I decided to make a conic endcap using the dimensions I measured. It's notable that these dimensions were significantly more difficult to measure with the calipers (the height of a cone doesn't have easy line-up points for caliper teeth), so I'm anticipating that I'll have to edit this section later on. 

First off, I created a "frustum-shell" that was designed to mesh with the original cylindrical shell, making it 3D via revolution:
![frustum shell sketch and revolution preview](/assets/images/F1/RevolveConeSupSketch.png)

To do the similar "weight-cutting" mechanism as previous, I decided to cut a pattern similar to the cylindrical shell, using the same mechanism:
|Initial Cutting Pattern Sketch| Extrude Cut & 3X Circular Patterning |
| :---: | :---: |
| ![Sketch of the cutting pattern for frustum shell](/assets/images/F1/RevolveConeExtrudeCutSketch.PNG)| ![Cut frustum shell after circular patterning](/assets/images/F1/CutCone.PNG)

I still had concerns about the assembly collapsing under strain, so I decided to make one more support in the middle of the cone using the "loft" feature to build a mini-frustum. The dimensions of this part are also a little arbitrary, since I didn't have a good rationale for a calculation. The loft operation itself is made of two circles on different sketch planes, along with a line connecting them as a guide curve:
|Support Frustum (Loft Operation) | Full Final Product |
|:---: | :---:| 
| ![Isometric view of the support after the loft operation](/assets/images/F1/ConeLoftSupport.PNG)| ![Final Conic Endcap](/assets/images/F1/FinalEndSupport.PNG)

## Assembly!
Now that all of my parts have been made, it's quite simple to assemble them together. After importing all of my parts into a new SolidWorks "assembly", I "mated" them together primarily by using 3D coincident relations, which lined up two edges perfectly together as so:
![Example of coincident relation mating](/assets/images/F1/ConeCylinderMate.png)
After doing this with all the parts (including the syringe guide, which I mated to one of my extrude cut patterns), the final product:
![Final Product](/assets/images/F1/Final.png)

## Summary (Assignment Requirements)

To summarize, I designed a scaffold to hold a 3-mL syringe in place within a 50 mL Falcon tube for centrifugation purposes. I used 4 separate part assemblies in SolidWorks, without any other necessary packages. It was most difficult to learn how to pattern extrude-cuts on the cylindrical surfaces as the way SolidWorks structured many of its patterning tools were not intuitive (much trial and error was required). As previously stated, I think much of my problems could be solved by learning how to move sketch plates without extruding. For example, the loft used as a central support in the conic endcap was made by extruding a cylinder to be able to sketch a larger circle on the top plane. I'm sure there is a method in SolidWorks to get around this extra extrusion step, but at the moment I wasn't able to find it.

I've attached the SolidWorks assembly [here](https://drive.google.com/file/d/1_dsctThYayf49K04GnpHgq6YShHBpgCG/view?usp=share_link) for grading and/or access purposes.

Thanks for reading!
