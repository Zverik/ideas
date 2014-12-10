---
layout: default
title: Video Map Overlay
status: idea
---

So let's assume we have a dashcam video [like this](https://www.youtube.com/watch?v=HgiZ72tsyoE).
It would be nice to have a moving mini-map in a corner, that would show
map (or a satellite view) of a current location, maybe along with a speed.

Possible overlay configuration options:

* tile source (regular osm, transparent, satellite).
* width, height, margin.
* round or square.
* opacity.
* rotating or north-top.
* icon for the camera.
* style for the optional speed: font, size, corner of the mini-map.

The result would possibly be a series of frames, which can be then overlaid onto
the original video with ffmpeg.

This all could be done in a script, no point in creating a GUI. Or maybe a simple GUI
for configuring an overlay, but without a video.

Georeferencing frame is a harder task. A single GPX trace should be prepared.
But timestamps mean nothing. Maybe use a player that shows frame numbers,
and correlate some of these with points in a trace. If the trace has no timestamps,
this also would be used to reference it. The result might be just a plain text file.

Said correlation file can be then used for [dashcamref](../dashcamref/).
