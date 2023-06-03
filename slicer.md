---
layout: page
title: Slicer
permalink: /slicer/
---

## Slicer

Slice your geometries!

kiri.newEngine()
    .setListener(display_message)
    .load("/obj/cube.stl")
    .then(eng => eng.setProcess({
        sliceShells: 1,
        sliceFillSparse: 0.25,
        sliceTopLayers: 2,
        sliceBottomLayers: 2
    }))
    .then(eng => eng.setDevice({
        gcodePre: [ "M82", "M104 S220" ],
        gcodePost: [ "M107" ]
    }))
    .then(eng => eng.slice())
    .then(eng => eng.prepare())
    .then(eng => eng.export())
    .then(display_gcode);

<!-- <iframe src="https://github.com/sameer/svg2gcode" width="100%" height="600" style="border:none;"> -->
<!-- </iframe> -->
