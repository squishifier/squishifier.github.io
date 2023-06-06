---
layout: page
title: Library
permalink: /library/
---

This section helps you determine the right machine setting for your application depending on the material you choose for prototyping. Additionally, it provides snippets of code for you to enhance your .GCODE file with, so that your 3D printer can perform various functions required for inflatable prototyping.

## Pick your material

Adjust your settings according to what material you would like to seal. You can determine the right settings based on the chart below developed as part of the <strong><a href="https://www.media.mit.edu/projects/therms-up/overview/" target="_blank">Therms-Up!</a></strong> project. Some materials can be sealed more easily by placing a cardboard underneath them or an aluminium foil on top. The following snippets of code were developed for sealing metalised film from crisps packets placed on top of a 2mm thick piece of cardboard.<br>
<img src="/images/material-chart.png" alt="Material properties">

## Seal top two layers

These settings allow you to seal only the top two layers of your design and not any layers underneath those. The seal achieved using these settings is slightly less strong than the ones that can be achieved using the settings described in the chart. This is due to the relatively lower sealing temperature to avoid sealing more than two layers. As a result, in order to strengthen the seal overall, it is helpful to introduce multiple seams into the design by offsetting the seam.

```
M104 S190
M105
M109 S190

G00 Z5
G01 X50 Y50
G01 Z1.8 F400
G01 X60 Y50 Z1.8 F400
G00 Z5
```

## Pierce hole into top two layers

This code snippet allows you to pierce a hole through the top two layers of plastic sheets into your prototype. This can be useul for creating perforations and also for connecting multiple air bladders together.

```
M104 S200
M105
M109 S200

G0 Z5
G0 X50 Y70
G1 Z1.8 F100
G0 Z5
```

## Seal and cut

You can use these settings not only to seal multiple layers of plastic sheets together, but also to cut through the layers of material by melting them.

```
M104 S220
M105
M109 S220

G00 Z5
G01 X50 Y60
G01 Z1.5 F100
G01 X60 Y60 Z1.8 F100
G00 Z5
```

## Add new layer

You can insert this section of code into your .GCODE file where you require the 3D printer to load a new layer of plastic sheet on top of the already sealed ones. This code is only functional if the 3D printed add-ons available from the <strong><a href="./tools">Tools</a></strong> section are attached to the 3D printer.

```
G0 Z10
G0 X0 Y30
G0 Z1

G1 X85 Y30 F400
G1 X85 Y220 F600
G1 X0 Y220 F600

G0 Z10
```
