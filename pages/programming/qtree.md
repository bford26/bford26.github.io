---
layout: single
title: "QuadTree Implementation"
permalink: /projects/qtree/
classes: wide-nosb-toc
author_profile: false
toc: true
---

## Important Classes

* The Particle class creates an object which stores its location and radius for interactions. For classical particle simulations this is just a radius that pertains to the size of the object. For more modern or complex interactions it would be different ranges or lengths.

* The bound class creates a boundary with the position and dimensions as member variables. An important function in the bound class returns a bool based on if the particle is in the boundary.

* A Quadtree object holds 4 major member variables, the particle capacity, a boundary object, the contained particles, and if the quadtree has any children quadtrees. The functions in the Quadtree class are insert, branch, and getChildren. The insert function handles the main logic of the Quadtree's functionality by checking capacity and boundaries, and branching the Quadtree if needed.

* Octree is the 3D implementation of a Quadtree, which uses the same base classes bound and particle but using a 3D equivalent.
  
## Process

The basic process for this project is to create single quadtree object, populate the boundary with a set number of particles, and apply basic collision and equations of motion.

## Results

I do not have any created particle simulations, but I have uploaded the python files for my QuadTree implementation to my GitHub. In the PIC project, the Quadtree package will be used to help reduce the amount of calculations required for calculating the collisions operator and effect of self generated magnetic fields.

## Resources

* [Quadtree wiki](https://en.wikipedia.org/wiki/Quadtree)
* [Coding Train Video](https://www.youtube.com/watch?v=OJxEcs0w_kE&vl=en)