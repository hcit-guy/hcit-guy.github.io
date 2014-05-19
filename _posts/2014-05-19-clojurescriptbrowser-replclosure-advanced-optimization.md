---
layout: post
title: clojurescript+browser repl+closure advanced optimization
summary:
status: draft
hn-discussion:
comments: true
---

As with many bugs and errors, this is quite obvious in hindsight but was more
difficult to track down than it should have been...

Basically, I had enabled a browser repl by adding the following:

```clojure
(repl/connect "http://localhost:9000")
```

I forgot to remove this line when deploying the app to my staging server with
the production profile.  My production profile enables advanced optimization and
when loading the offending script, the ensuing error is:

```javascript
Uncaught TypeError: Cannot read property 'Mg' of undefined 
```

I had added a bunch of code in the last commit so it wasn't immediately obvious
to me what the problem was.  Of course, disabling optimization resulted in code
that functioned as expected (including enabling the wonderful browser repl).

I'm going to add this to my [list of things to check anytime something doesn't
work when optimizations are enabled]({% post_url 2014-05-19-List-of-things-to-check-when-compiling-cljs-with-advanced-optimization %})
