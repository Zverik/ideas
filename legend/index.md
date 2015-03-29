---
layout: default
title: Legend Generator
status: idea
---

Writing a route legend (that is, route turn-by-turn description) is hard and cumbersome. You have
to open google street view, a route, a map and a text editor, and using all four construct a
20 to 60 direction messages, that have to be short, unambigous and obvious. Veloroad members
are now using plotaroute.com for this task, but we can build simplier and more configurable
website.

## Planning a route

This should be a special Leaflet-based map, on which points are thrown, and it draws a route
using GraphHopper or other cycle-routing service. Each segment between points has a type:
hand-drawn, routed for bicycles, routed for cars (e.g. when we don't want to use cycleway along
the street). Segments are calculated when any of its end markers are moved (or deleted), but
calculated traces are stored as linestrings, so we don't bother routing servers much.
Hand-drawn segments are shown as straight lines from start to finish, which a user can
split using middle-segment markers (as usual). Segment type can, of course, be changed at any
time: e.g. one can get a route from A to B, then switch it to hand-drawn mode and fix some
turns.

## Turning points

A route description consists of many instructions at intersections and non-obvious turns of a route.
Locations of these instructions are placed on a route independently of route points.
They can be dragged along the route. When a new segment is created, at can automatically add
to instruction points array: e.g. when a route engine provides turn instructions, or when
hand-drawn route has turns of more than 80°. Each instruction can be freely edited.

For each instruction point the distance from previous one and the start of the route
is calculated. Also, the time of opening and closing (useful for checkpoints) is
calculated, based on a number of distance/speed coefficients, like in current
marathon tables.

## Database

All routes are stored in a server-side database. A route data consists of:

1. Route points.
2. Route segments between these points as linestrings.
3. Type of route segments.
4. Instruction points: location (lat/lon), text and type (CP, cafe).
5. Whole route data: title, length, description etc.

The system doesn't need an authorization system: as in MapBBCode Share, anyone who
has a special link can edit the route. Maybe there should be an administrator's account
with editing rights for all routes.

## Printing

Aside from obvious exporting of a route to gpx/kml/plt formats and a web view,
this tool should automatically generate a map (using nik4cgi service)
and a legend in html, or better, in an LibreOffice Calc table.
