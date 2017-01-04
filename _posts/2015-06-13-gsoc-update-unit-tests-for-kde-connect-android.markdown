---
layout: post
title: 'GSOC update: Unit tests for KDE Connect Android'
categories: [ GSOC, KDE ]
comments: true
tags: [GSOC, KDE, KDEConnect]
---
Test driven development is considered as one of the best approach to develop good quality, efficient and maintainable software. While refactoring Android version and adding support for SSL, I realized that it is becoming more and more difficult to test it on emulator. So while my new phone arrives :D, I tried my hands on Android Testing Framework.

While there are some tests for desktop version of KDE Connect, Android version had no tests at all. Also, I had never realized how UI applications can be tested or how unit tests are going to work if all classes are linked with each other. I had no idea how to isolate a class for unit test.

Android Testing Framework which is built on top of JUnit provides excellent functionality to write unit tests for an Android application. It provides context for the application needed to access shared preferences etc., annotations for categorizing tests like small test, medium test, large test, annotation to specify the test to run on UI thread for UI testing, controlling the UI programmatically like programmatically pressing a button etc. and a lot of other functionalities.

Unit tests are meant to run in isolated mode, that is minimal dependency on any other class or module and I still had no idea how it can be done. While using real classes for unit tests, my mentor recommended to mock some objects using Mockito. Then I came to know about Mockito, an excellent framework to mock any Java class where we can control the behavior of methods when called, based on types or values of the arguments, and also perform other task on some conditions. Mockito makes writing stubs for object very easy.

I just studied about Software Testing this semester, but all I learned was theoretical which is good for analyzing what test to write and what test cases to use, but implementing unit tests was completely different.

After discovering this wonderful and exciting stuff, looking forward to a full summer like this :)
