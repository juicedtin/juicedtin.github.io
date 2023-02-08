---
title: "F1 &#124;&#124; Soldiworks Syringe-Spin Project"
excerpt: "Using Soldiworks to CAD a scaffold to hold a 3-mL syringe in a 50 mL Falcon tube!"
permalink: /bme66/F1
classes: wide
sidebar:
- title: Relevant Topics
  text:  Solidworks, 3D Printing, CAD
---
OUTLINE: 
1. Measured syringe using calipers from NOLOP, recorded all dimensions in notebook for future CAD reference
2. Made top-plate using 3 different dimensions:
First, created circle with radius of 26.9 mm to match Falcon tube diameter
Created landing slot for syringe by creating a polygonal shape using alpha, beta, gamma dimensions
Created interior circle using offset tool by 8.175 mm to generate hole for the syringe body. All dimensions except for the outer Falcon tube dimension have a high tolerance of 0.05 mm, to ensure that stuff doens't get stuck. Final sketch is attached. 

Extrude Boss/Base to extrude the larger circular area of the sketch by 3 mm, then went back into the menu and extruded the lower area of the sketch by 1.5 mm to create an indented place to put my syringe "handles". See attached. 

Create 2 mm wide cylinder to hold guides in place that is 4 mm less than the total height of the Falcon tube as measured. Cut triangular holes in the tube to reduce material/weight while maintaining compressive strength for centrifuge. This was done using linpattern and circpattern, with a 4 mm offset at the bottom of the cylinder. See attached.  