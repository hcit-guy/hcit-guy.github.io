---
layout: post
title: Zotero connector doesn't play nice with clojurescript browser repl
summary: 
status: draft
tags: [zotero,clojure,clojurescript,om,repl]
hn-discussion:
comments: true
---

Context: Mac OS 10.8.5, Chrome 34.0.1847.116, clojurescript 0.0-2173,
lein-cljsbuild 1.0.2

I finally decided to bite the bullet and try and get a browser repl working.
I'm using [om](https://github.com/swannodette/om) so
[austin](https://github.com/cemerick/austin) wasn't an option for me because om
requires clojurescript >= 0.0-2173 and austin doesn't work with clojurescript >=
0.0-2173.

This
[readme](https://github.com/emezeske/lein-cljsbuild/blob/master/doc/REPL.md)
made it sound pretty straightforward so I started to bang my head against the
wall as my repl just sat there, refusing to output anything for something as
simple as (+ 1 1).

Something made me decide to try it with Firefox and then all of a sudden
everything started to work, as expected.  After some additional digging, I found
this [issue (lein-cljsbuild #262)](https://github.com/emezeske/lein-cljsbuild/issues/262).  I dug a
little deeper and found that the offending extension was the Zotero connector.
I haven't looked into why this is a problem but I imagine it has something to do
with how the connector parses a page to see if there if it's something that it
can translate.

Given that much of my work starts as an academic project, Zotero is something
that I use often.  I now have to enable/disable the extension depending on the
immediate task at hand.
