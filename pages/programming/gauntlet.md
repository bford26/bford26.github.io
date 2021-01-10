---
layout: single
title: "*Gauntlet* OOP Codesample"
permalink: /projects/gauntlet/
classes: wide-nosb-toc
author_profile: false
toc: true
---

## Game Structure

The game structure revolves around the three main functions in the Gauntlet class.

### OnUserCreate

<!-- This function allows for the resources and data required in the game to be loaded prior to the actual loop being entered. -->

OnUserCreate main purpose is allocating memory and loading in game information, like player and level data, while also initializing any important variables.

### OnUserUpdate

This is by far the most import function since it is responsible for all the function calls and general game logic. The main structure of the Update function is a switch statement, handling the differing logic for the various gamestates.

#### Gamestates

##### START

START is just a loading screen, and can be exited at the press of any button.

##### GAME

GAME is the actual game loop, which is triggered the most in the switch statement. GAME breaks down into the 4 stages:

* Physics - timing, fixed game updates, resolving collisions
* Rendering Game Data - in order: level, display info, mobs, player
* Game Logic - Updates for tiles, player, projectiles, mobs
* Gather Input Events - movement, create projectiles, use abilities

##### PAUSED

PAUSED halts all game logic and simply overlaps a resume and quit menu.

##### OVER

OVER does not exit the game immediately. This gamestate renders the exit animation for the player, then ends the OnUserUpdate game loop.

![Exitgif](/assets/my_images/code/player_exit.gif){: .align-center width="50%"}

### OnUserDestroy

This function has the sole purpose of memory management. Any allocations made during OnUserCreate will be freed, at which point the program will terminate.

## Project Classes

### Gauntlet
Public inheritance from olc::PixelGameEngine. Gains access to rendering functions. Game logic is defined through the member functions.

### Resources
A singleton created so that level data and sprites would only have one instance. Also adds functionality for referencing sprites to be rendered.
  
### Tile Objects

Seen from the class hierarchy shown below, the tile class is the highest level of abstraction for interacting game objects.

![Tile Class Hierarchy](https://bford26.github.io/OOPcodeSample/html/class_tile.png){: .align-center}

The differences between each of the child classes is typically due to the need for more member variables. But classes inheriting from InterActionBlock only really differ in constructors and an override for the interaction public inherited member function.

## Interactions

Because static objects never move no collision or interaction logic is required. So game interactions fall into one of the two categories:

* Dynamic vs Static
  * Projectiles, Mobs, or Players, interacting with a static object
* Mob vs Dynamic
  * Mobs interacting with projectiles or players

Which are handled with the Unit Collision member functions in the Gauntlet class.





Check all rendered objects for overlapping
Resolve the collision through defined game logic


## File Structure

```bash
OOPcodeSample
|
├── data                    # holds all resources needed for the game
|  ├── files            
|  |  ├── ...               # misc. game data like object ids and configurations
|  ├── levels
|  |  ├── ...               # level files
|  ├── sprites
|  |  ├── ...               # sprite sheets for players, level, mobs, projectiles
|
├── doc                     # Doxygen output folder
|  ├── html
|  ├── latex
|
├── include                 # External libraries
|  ├── olc                  # Pixel Game Engine Library 
|  |  ├── olcPGE.cpp   
|  |  ├── olcPGE.h
|  |  ├── Makefile          # olc specific makefile
|  ├── Makefile             # general makefile
|
├── src                     # contains all source code 
|  ├── gauntlet             # gauntlet class
|  |  ├── gauntlet.cpp
|  |  ├── gauntlet.h
|  |  ├── Makefile          # gauntlet specific makefile
|  ├── main                 # main function / program entrance
|  |  ├── main.cpp
|  |  ├── main.h
|  |  ├── Makefile          # main specific makefile, final compiler operations
|  ├── resources            # singleton class
|  |  ├── resources.cpp
|  |  ├── resources.h
|  |  ├── Makefile          # singleton specific makefile
|  ├── tile                 # contains tile object class hierarchy
|  |  ├── dynamic
|  |  |  ├── ...
|  |  ├── static
|  |  |  ├── ...
|  |  ├── Makefile          # specific makefile for subdirs compiling
|  ├── Makefile             # general makefile
|
├── Doxyfile                # Doxygen customization file
├── Makefile                # root general makefile
```


## Build Structure

This project is built using GCC Make.

To build this project *Makefile* was the preferred choice, given its wide accessibility. In the project root folder we have the main Makefile, which is used recursively in the root subfolders. This makes creation of new objects or functionalities easy just by creating a new subdirectory and specific makefile.

The first compiles are for all external libraries, located in the */root/include/* directory. Currently, the only external library used is the OneLone

## Documentation

Documentation for this coding project was created using *Doxygen* 1.8.20. The documentation has the project broken down into namespaces, classes, and files. Also in the documentation is the information about the Pixel Game Engine functionality and the olc namespace.

* [Documentation Link](/OOPcodeSample/html/index.html){:target="_blank"}

## Sources & Resources

* [Full Level Demo Video](https://youtu.be/D4eO0zghXyo) 
* [OneLoneCoder PGE](https://github.com/OneLoneCoder/olcPixelGameEngine)
* [Gauntlet Walkthrough](https://strategywiki.org/wiki/Gauntlet_(NES)/How_to_play)