---
layout: default
title: Public Transport Editor
status: idea
---

If we need a plugin, the tagging schema is too complex. For routes, we can make a simple web editor.

## Viewer

An interactive map. Download all stops and platform from the Overpass API and display them.
On click, a list of routes via this stop are displayed. When no stop is selected,
a user can choose a route to view. For a route, all tags are displayed, its stops
are highlighted, and a route is drawn either with ways in the relation, or directly
connecting stop to stop from beginning to end. The latter allows for displaying
routes with no or obsolete route data.

When a route has `route_master` relation, an additional panel is displayed above
tags and stops, with a list of route variants. By clicking on each, a user can quickly
browse through all of these. Route variants do not appear in a full list of routes,
masters are shown instead. But when clicking on a route master, the first variant
is displayed.

So, we have three panels: list of routes in a viewport, stop/platform data with
all routes passing through it, and a route variant data.

## Editor

A user can enter edit mode by logging in to OSM via OAuth. Then he has some options:

* Add a stop on the map: select type (stop position on platform) and route type (bus, tram etc.),
then drag a marker: for a stop position, it will be moved to a nearest highway or tram line.
After all that, a user should fill out a form, though if they don't know even a name
for the stop, they can submit just the addition of a stop.

* Edit a stop: add a name, for example. This is a sample tag editor with the ability
to move a node. For a stop position, care should be taken to not detach a node from
its way, and not to mess node order. Also, a route can be added to the stop: first,
user should select a route master, and then -- its variant. And he gets pulled to...

* Editing a route variant. There are tags, and a list of stops and platforms (which
are linked together). User can swap stops, duplicate any stop, and add or remove stops
from the route with a simple click on the map. When adding, stops are added according
to their geometric position in relation to other stops.

* Create and delete a route variant. When creating, the mode is changed to editing,
so a user can immediately click on stops along the way. No reversal function should
be available, since all stops are different. Although stops from other route variants
can be somehow highlighted. Deletion of a route variant with more than three stops
should be forbidden.

* Create or delete a route master. Should be done from a route variant editor somehow.
Like, when the last route variant is deleted, its master should be also deleted.

So, there are a lot of editing options, some of which are quite complex. Maybe it
should be done in stages, e.g. first with only editing existing routes and stops.

### Stops And Platforms

Since all platforms should have their related stop positions, and vice versa,
it should be reflected in the user interface. For example, viewers and editors
for both should be combined, with options to add corresponding stop or platform.
There should be additional tests for broken relations or differently-named
nodes, e.g. with a distance limit.

I guess it's safe to assume stop positions at all times should be named the same
as their platforms.

## Ways

Editing ways in a web interface is hard, and we are stepping on a territory of
a complex OSM editor. Editing a route can be done in either of two ways:

* By clicking on road segments. All highways are visually split into segments,
regardless of their ways, and a user clicks on each they want to add to a route.
Oneway-ness and connectiviy are, of course, validated.

* By building a route with a third-party routing engine. A user clicks on a start
point, end point, and places some intermediary points along the route. After
that, we get a list of way segments for a route.

These interfaces could be combined: for example, first we use a routing engine
to build a draft version of a route (maybe automatically from stop positions!),
and then for editing we allow user to click on road segments.

There should be an additional check that all stops are near the route. Though
it is not completely clear what to do if they are not.
