---
layout: default
title: Watchcat JOSM Plugin
status: idea
---

This is a simple watcher plugin for JOSM. It regularly downloads diff files (minutely/hourly/daily, depending
on how long ago JOSM was last used) and monitors changes for given objects. It would be highly useful for
posessive mappers who don't like their objects touched, but also for mappers concerned with validity of
public transport or bicycle routes, or for watching a state of disputable features.

## Presentation

_(picture todo)_

## How it works

Watchcat is a plugin which has it own panel, but that is not required to be open to operate. It maintains
a list of watched objects, just id and type for each. For displaying purposes it can also store textual
description generated by JOSM. To watch an object, select it (or group of objects) and click a button.
You are obviously not notified of edits made by yourself. The plugin can also be configured to add all
modified objects or just those with chosen tags (e.g. all relations, or just routes).

To edit a list of watched objects it would download all of them in a new data layer,
so instead of searching for it in a list you can select it and press a button.

When JOSM starts, the plugin download all daily/hourly/minutely diffs and looks for objects in the list.
After that it downloads minutely or hourly diffs (it should be configurable). Notifications are unobtrusive:
changes are just shown in the panel, sorted by time, with an option to clear that list or download objects
or open a relevant changeset in a browser. If the panel is not visible, it can employ an unobtrusive
notification mechanism that was introduced lately.
