---
layout: single
title: "Particle-in-Cell Codebase"
permalink: /projects/pic-code/
class: wide-nosb-toc
author_profile: false
toc: true
---

I started this project after being inspired by my summer experience at ORNL working with beam physics simulations. The major concept is to use a PIC framework to solve the governing equations (i.e. maxwell's, Vlasov-Poisson).     

## Important Classes

### Particle

A particle object is a 4D object, that also contains a charge and mass to allow for various species to be simulated. It should be noted this particle object is defined as a macro-particle to represent some collection of actual particles. A small distribution class is used to create the basic template for populating the grid with particles. Used only for basic testing, a random distribution is currently the only option.

### YeeSpot

A YeeSpot object hold its position, and a charge. The charge on a YeeSpot will be made by the projection of all near by macro-particles.

### Grid

A grid object is what will be used to hold all the YeeSpot objects. A grid will take a resolution for the coordinates and the minimum and maximum values to create a uniformly spaced posistioning of grid points.


## Process

For this project, using [1] and [3] as a guideline. I broke down the process into the following steps:

### Setup

* Create a YeeSpot GRID from simulation parameters
* Populate the GRID with a particle distribution
  
### Simulation Loop

* For each particle project the charge onto the surrounding YeeSpots, then find the density
* Using the matrix form of the Poisson Equation, solve it for the electric potential.
* With the potential, the E-field can be approximated using our Yee Grid
* Solve for the magnetic field created by particle motion
* Update particles using the "Leap Frog Method"

## Project's Current State

Recently, I updated the PIC code to handle magnetic fields using the Boris method. The boris method seems to be the most common particle push method for plasma PIC codes. Other codes using this method normally use a pure rotation test case and measure the Larmor radius. Because of its simplicity I did the same. I put a particle in a uniform magnetic field of 0.1T and evaluated its radius.

$$r_g = \frac{m v}{q B}$$

From the equation our expected value for the Larmor radius is $r_g = 5.69$ $\mu m$. From the recorded data the average radius for our particle was $r_{sim} = 7.27$ $\mu m$. I have not yet determined the main cause for this error, however, I did confirm that the Yee Mesh is not the source of the error. Running the simulation neglecting the calculations of the mesh and I got very similar answers. 

Here is a gif of the pure rotation simulation:

<div style="text-align:center"><img src="/assets/my_images/PICrotattion.gif" alt="Rotation Simulation" class="center" width="500"></div>

The actual code is *simulation.py* in the pPIC repo on my github. 

Also I will be soon updating this page with a more updated version of this simulation. I am currently working on the method to determine the generated magnetic field. Also I plan to better manage the bound conditions (i.e periodic), and possibly add a new class of nodes. The node objects would help create an environment to study different situations. The first environment I hope to implement would be a particle trap or something very interesting like a two-stream instability simulation.

## Future Plans

Eventually my plan for this project is to take advantage of a more efficient programming language. The PIC project is currently written in python because of its high accessibility, given that my major task is learning the new concepts rather than efficiency. I have significant experience using C/C++, and intend to make the foundation of the project using C++.  

## Resources

  1. A detailed explaination and methodology, which helped with details of the simulation process. [link](https://www.particleincell.com/2010/es-pic-method/)
  2. A documentation of the Yee Lattice, which I hope to implement into my code to improve the FDM. [link](https://meep.readthedocs.io/en/latest/Yee_Lattice/)
  3. An example of a Vlasov Solver. [link](https://www.particleincell.com/2018/intro-to-vlasov-solvers/)
  4. This paper provided the proper information to solve the Poisson equation and information on the FDM. [link](https://my.ece.utah.edu/~ece6340/LECTURES/Feb1/Nagel%202012%20-%20Solving%20the%20Generalized%20Poisson%20Equation%20using%20FDM.pdf)
  5. Here is a lecture about the PIC method I found extremely helpful. [link](https://youtu.be/I09QeVDoEZY)
  6. This video talks about Maxwell's Equations on a Yee Grid. [link](https://youtu.be/hv5lIx4u8mY)
  7. A quick video on the Collisionless Boltzmann equation. [link](https://youtu.be/u9OgtXxsBNU)
  8. A similar project from Princeton using the Boris method. [link](https://www.astro.princeton.edu/~anatoly/PICHW2016.html) 
  