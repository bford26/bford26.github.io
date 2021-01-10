---
layout: single
title: "A* Maze Solver"
permalink: /projects/a-star/
classes: wide-nosb-toc
author_profile: false
toc: true

gallery:
  - image_path: /assets/my_images/code/AStarPath.png
    alt: "Found Path"
    title: "Found Path"
  - image_path: /assets/my_images/code/nopath.png
    alt: "No Path"
    title: "No Path"
---

I started this project as a fun and simple experiment to learn more about computer science algorithms.

## Methods

For a basic path finding algorithm the main idea is to weigh the different possibilities and create a cost function based on weights. A* uses this same concept, but uses a heuristic function which adds to the cost for each path.

$$f(n) = g(n) + h(n)$$

This project uses a basic euclidean distance for the heuristic function.

$$ h(n) = \sqrt{\Delta x^2 + \Delta y^2} $$

This heuristic function the algorithm can easily prioritize the more valuable path moving towards the goal, and increases the search speed.

## Generating Obstacles

For creating more complex paths for the algorithm to choose between I added two main options:

* Random Blockades (problematic)
* Prim's Maze

The random option gives a quick and easy method of making a unique path, but depending on what type of obstacle density is give a solution may not always be available.

A more interesting option is the Prim's Maze algorithm. This method ensures a path will always be available, but does create a much easier solution for the A* method.

## Results

Here are the results from the project. For a display method I used the python package PyGame. The left image shows the A\* path with a found solution. Red cells represent the closed set, while the green show the openset at the time of finding a solution. The right image is an example of the randomized obstacle generation creating a grid with no solution. This example shows one of the main drawbacks to the A\* algorithm, memory use. All red cells represent a closed set spot object. For the situation here this problem is not significant, but for situations that required massive searches A* can become problematic because of the memory requirements.

{% include gallery caption="" %}

## Resources

* [A* Pseudocode](https://en.wikipedia.org/wiki/A*_search_algorithm)
* [Maze Generator](https://en.wikipedia.org/wiki/Maze_generation_algorithm) 
* [Prim's Algorithm](https://en.wikipedia.org/wiki/Prim%27s_algorithm)

