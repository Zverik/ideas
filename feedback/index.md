---
layout: default
title: Changeset Feedback
status: idea
---

<p>Right now there is little feedback in OpenStreetMap. Basically, if you edit something, your changes almost surely would go
unnoticed, and if not, the first feedback you will get may come from DWG. We can fix that by making a small improvement to osm.org.</p>

<p>Let's assume someone has tagged all McDonald's amenities as restaurants. What do you do then? First thing would be asking a user
why did he do it. Right now the only option you have is to use private messages: "Hello, good day to you sir, I'm sorry for bothering you..."
etc etc. It is too hard, especially for introverts who I think are the majority in OSM. But there are no other options.</p>

<p>There was an attempt to add <i>ratings</i> to OpenStreetMap: [+] and [-] buttons which affect both changeset and user ratings. With
this feedback tool user can easily know whether their edits are good, but actually it doesn't show any sense. If someone uploaded
a changeset, they surely consider it good, so positive votes bear no meaning: they already know that it's good. And in an opposite
case, negative votes are often taken personally: "your edits are bad and you should feed bad". Total ratings value cannot be
taken seriously, because every vote means something, so adding those numbers is like adding apples and shades of blue.</p>

<h2>Feedback Interface</h2>

<div class="changeset"><a href="#">37794875</a> | 09 September 2013 | <a href="#">Beginner96</a></div>
<div class="chcomment">Fixing amenity tags <a href="#">diff »</a></div>
<div class="buttons">
<input type="button" value="Thank you!" style="color: green;">
<input type="button" value="It's problematic, see comments" style="color: red;">
</div>
<div class="commentfield">Comment: <input type="text" value="" id="comment" size="40"> <input type="button" value="Add"></div>
<div class="comments"></div>

<h2>How it works</h2>

<i>todo</i>
