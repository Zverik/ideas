---
layout: default
title: GeoTIFF Processor
status: idea
---

A two-part system for processing GeoTIFF images and making tile layers out of them.

## Processor

A web page with an upload and URL fields. The latter one is for Landsat images. It automatically
downloads an image, for landsat it does pansharpening and color correction. After initial processing
it offers two or more options: with no color correction, basic constrast stretching etc.
When an option is selected, jpeg tiles are created, and all temporary files are removed.
The tile layer is accessible by a unique URL (maybe entered when selecting a color option).

## Tile merger

So we have a lot of separate tile layers, but need to create a single one. Firstly, there is a proxy
GCI script that returns all merged tiles.

### Simple solution

After creating tiles empty ones should be detected and deleted. In a manager script just enable
and disable layers. Proxy script returns the first existing tile for given numbers.

### Layer editor

An interactive map that shows layers in a current view, allowing to enable/disable them. Also
it can selectively remove or restore tiles of a top layer. This allows for removing cloudy parts
and more fine-grained control of layer edges. E.g. we could add a layer just for a single road.
