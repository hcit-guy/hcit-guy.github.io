---
layout: post
title: List of things to check when compiling cljs with advanced optimization
summary:
modified: 2014-05-19
status: draft
hn-discussion:
---

I haven't found a good way to debug my clojurescript production code when
optimization is set to advanced.

Here's a running list of items (in no particular order) to check if you encounter some [cryptic
exception]({% post_url 2014-05-19-clojurescriptbrowser-replclosure-advanced-optimization %}):

* Did you forgot to remove `(repl/connect ...)`?
