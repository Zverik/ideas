---
layout: default
title: Automated extracts with GUI
status: idea
---

A set of scripts to deploy on a cloud servlet, for generation of regular OpenStreetMap extracts,
with a modern web interface for downloading and administration.

## Why

I know, there are a lot of similar tools, and some companies provide daily extracts, and there
are even services for generating extracts on request. Sadly, these are unreliable, shape files
often lack required layers, and bounding polygons sometimes cut out just the part you need.
And nobody publishes their sources! So this is an attempt to create a simple extraction server,
easy installable on a droplet (from 5$ a month), and/or connected to Amazon S3 (3 cent per GB).

Note: maybe employ Amazon EC2 service, see Michal's Extractotron.

## How it works

## Configuration

## See Also

* https://github.com/migurski/Extractotron
* https://github.com/mapzen/metroextractor-cities
* https://github.com/mapzen/chef-metroextractor
* http://gis-lab.info/qa/osmshp.html
* http://beryllium.gis-lab.info/project/osmshp/
* http://gis-lab.info/projects/osm_dump/
* http://download.geofabrik.de/
* http://extract.bbbike.org/
