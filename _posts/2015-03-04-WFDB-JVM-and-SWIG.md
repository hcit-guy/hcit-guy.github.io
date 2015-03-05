---
layout: post
title: WFDB, JVM (and SWIG)
summary:
status: draft
hn-discussion:
comments: true
date: 2015-03-04 22:42:15
---

It's been a while since I tried combining
[WFDB](http://www.physionet.org/physiotools/wfdb.shtml) with the JVM via SWIG.
So, after some difficulties getting it up and running, here are some notes to
help myself and anyone else:

1. The current version of swig is 3.0.5 but 2.0.4 is the latest version that
   appears to work.  (I tried 2.0.5 and it also bombed.)

2. It's best to compile swig from source ([tag on
   github](https://github.com/swig/swig/tree/rel-2.0.4))

3. "make install" (within wfdb-java within [wfdb-swig](http://www.physionet.org/physiotools/wfdb-swig.shtml)) doesn't seem to do anything so I manually
   copied ```build/.libs/libwfdbjava.dylib``` to ```/usr/lib/``` and
   ```build/wfdb.jar``` to ```/usr/share/java/```.  These seem to be the default
   paths that ```make check``` uses for basic tests
