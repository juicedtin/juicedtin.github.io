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

## Initial Goals

In my research at the Kaplan Lab, I work on fabricating gel-spun catheters made of _Bombyx mori_ silk. The solution that I use is quite viscous, but I have to extrude it through a syringe onto a rotating mandrel - so any bubbles that get trapped in the solution presents issues with heterogeneity of the final fabrication. I usually remove these bubbles by spinning down the solution via centrifugation, but all the centrifuges I've used are constructed for 50 mL Falcon tubes rather than 3 mL syringes. Thus, I thought I would use this CAD assignment as a excuse to 3D print a scaffold that could hold my syringe in place during the centrifuging process.

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
![CAD Sketch of the syringe rest before extrusion](/assets/images/F1/Syringe%20TopPlate%20Sketch.png)
When it came to dimensions, I built relations between all the relevant shapes, but left the holder for the crossguard and both circles independent, without defined relations. Thus, if I need to add more tolerance into the outer ring, I can do so while leaving all of the other dimensions intact.  

I extruded the outer ring by **3mm** [CHECK THIS] and the crossguard rest by **1.5 mm** to create this 3D shape:
![CAD extrude of the syringe rest after sketching](/assets/images/F1/Syringe%20TopPlate%20Extrude.png)

One part down, 3 more to go!

OUTLINE: 
1. Measured syringe using calipers from NOLOP, recorded all dimensions in notebook for future CAD reference
2. Made top-plate using 3 different dimensions:
First, created circle with radius of 26.9 mm to match Falcon tube diameter
Created landing slot for syringe by creating a polygonal shape using alpha, beta, gamma dimensions
Created interior circle using offset tool by 8.175 mm to generate hole for the syringe body. All dimensions except for the outer Falcon tube dimension have a high tolerance of 0.05 mm, to ensure that stuff doens't get stuck. Final sketch is attached. 

Extrude Boss/Base to extrude the larger circular area of the sketch by 3 mm, then went back into the menu and extruded the lower area of the sketch by 1.5 mm to create an indented place to put my syringe "handles". See attached. 

Create 2 mm wide cylinder to hold guides in place that is 4 mm less than the total height of the Falcon tube as measured. Cut triangular holes in the tube to reduce material/weight while maintaining compressive strength for centrifuge. This was done using linpattern and circpattern, with a 4 mm offset at the bottom of the cylinder. See attached.  