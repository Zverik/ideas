---
layout: default
title: JOSM Route Editing Plugin
status: idea
---

The current relation editing is too generic, and there should be a plugin specifically for editing public transport relations.
The complexness of the schema is the main reason why there are so few of those relations, and they are easy to break.
It should be easy to edit and easy to verify connectivity and stops, including their order.

## Panel

The main UI is the route editing panel. When an object is selected, a list of routes going through it is displayed there.
Click on a route to start editing it. On that moment it is higlighted in its entirety, some stats and validation results
are displayed in the panel. There are buttons to add and remove member object (like in *Relation Toolbox* plugin). But
also there are route-specific buttons like "extend to this way" (find a path and include it) and "find stops" (adds all
stops and platforms along the route).

## Master Routes

Most PT routes are bidirectional: there are two separate relations for each direction. It should be easy, as in clicking
a button, to switch between directions, add missing direction (with respect to one-directional highways; this should also
be checked by a validator), create route_master relations and manage tags in general.

