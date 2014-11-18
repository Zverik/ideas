---
layout: default
title: Imagery Central
status: idea
---

For some services (like validators) we often need to know if it is possible to quickly map at a certain point.
That is, if there is detailed imagery available: Bing, MapBox or other. Usually this results in another Bing
pinger, but the smarter solution would be to centralize this.

"Imagery Central" is a proxy between imagery providers and validators. It answers a simple, single question:
"Is there a detailed imagery at these coordinates?" It handles caching internally, and check for imagery
updates. It could provide its own web interface to handle bigger updates and to browse statistics.

    http://imcentral.osmz.ru/query?lat=...&lon=...&provider=...&force=0&format=...

Here `lat` and `lon` are coordinates, `provider` is a comma-separates list of imagery providers (if missing,
imcentral checks all providers), and `force` flag requests cache update. Formats can be `xml`, `json`, `csv`.
Return codes might be as follows:

* 0 — no detailed imagery at given point
* 1 — there is detailed imagery
* 2 — no data, ask later
* 9 — system error

## Imagery Providers

Providers are identified by a simple alphanumeric string, like `bing` or `orbview3`. `-` is allowed
for word separation (e.g. `ov3-rus`). The list of providers should be accessible via API call and/or
with a web interface.

Sources can be of two types, probably extensible with plugins: simple tiled and geometric. Simple
tiled sources, like Bing and MapBox, provide just images. By analyzing them, e.g. by checking file size,
we can determine if there is detailed imagery at given zoom, or a tile is blank. Resutls of such testing
should be cached, not to overload tile providers' servers.

Geometric sources provide exact bounds to their imagery, so it is possible to test the imagery with a
simple geometric query. For example, OrbView3 sources usually provide Shape files with bounds, which
can be loaded in Imagery Central to test against.

## Caching

Since tile requests happen at zooms 14+, and there are hundreds of millions of tiles there, test results
should be cached. Along with tile coordinates and test results, a hash of a tile image should be stored.
Once a minute a random tile should be tested on each of tile providers, to see if there was an update.
Updates should be treated as major events: a notification should go off, a bunch of tiles neighbouring
the updated tile should be removed from cache, signal tiles at bounds of that cleared area should be
added to non-prioritized update queue, and so on.

There are two queues: non-prioritized, which searches for updates, and prioritized, populated with
`force=1` parameter. Actually, there would be another one, immediate, for tiles requested synchronously
(when they are not yet cached, and bandwidth limits allow). A great care must be put in limiting
requests to tile providers, to not be banned and to not burden servers much.

## Web Interface

Besides the usuall stuff like API reference and statistics, the web interface can also provide
an interactive map with available coverage for each of the providers. It can be enhanced in a way
of "Bing Analyzer" tools, letting users pan the map and "fill" areas, though again, not in a way
that would overload imagery servers.
