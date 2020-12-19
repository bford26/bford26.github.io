---
layout: single
title: "*Gauntlet* OOP Codesample"
permalink: /projects/gauntlet/
class: wide-nosb-toc
author_profile: false
toc: true
---

## Game Object Structure

* Include inheritance diagram

### Classes
 


## File Structure

* include file structure graphic

## Build Structure

To build this project *Makefile* was the prefered choice, given its wide asscessibility. In the project root folder we have the main Makefile, which is used recursively in the root subfolders. This makes creation of new objects or functionalities easy just by creating a new subdirectory and specific makefile.

The first compiles are for all external libraries, located in the */root/include/* directory. Currently, the only external library used is the OneLone





## Level Info, Sprites, and Data Conventions

In the data subdirectory are the files containing all the information for level design, sprites, and conventions used for indexing various in game items.


## Documentation

Documentation for this coding project was created using *Doxygen* 1.8.20. The documentation has the project broken down into namespaces, classes, and files. Also in the documentation is the information about the Pixel Game Engine functionality and the olc namespace.

* [Documentation Link](/OOPcodeSample/html/index.html){:target="_blank"}

## Sources \& Resources

* [Full Level Demo Video]() 
* [OneLoneCoder PGE]()
* [Gauntlet Walkthrough]()