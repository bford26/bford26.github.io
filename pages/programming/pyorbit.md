---
layout: single
title: "PyOrbit Contributions"
permalink: /projects/pyorbit/
author_profile: false
toc: true
---

Mentioned previously, PyOrbit is a simulation framework used to better study particle accellerators. The framework uses two major simulation tools; a bunch and nodes. A bunch is a collection of marco-particles, which can have a varity of attributes and flags. Nodes are used at the segmentation tool, in which a collection of nodes can be used to create a complete lattice. A defined lattice keeps the order of all nodes, and simulates an accellerator.

## Uniform Focusing

My project was to implement a Uniform Focusing Lattice to help study self-consistent beams. Self-consistent beams are defined as a particle distribution that has a consistent form and density through all linear transformations and linear forces due to spacecharge.

<div style="text-align:center"><img src="/assets/images/SelfConDist.png" alt="SelfConDist" class="center" width="500"></div>

A major concept in the field of beam physics is linear transformations (i.e. FODO matrices), specificaly in 6D phase space. The linear transformations of the 6 coordinates can be represented by the transport matrix $R(s,s_0)$, where the it is a function of the points $s$ and $s_0$.

$$\Phi(s) = R(s,s_0) \cdot \Phi(s_0)$$

For the concept of uniform focusing our transport matrix simplifies because we make simple assumptions about the symmitries and it is defined in terms of the Twiss parameters.  

<div style="text-align:center"><img src="/assets/images/TransportMatrix.PNG" alt="TransMatrix" class="center" width="500"></div>

Using this transport matrix and parameters defined in by the particle distribution. We created a new node class that can be given certain parameters like element length, curvature, and XY tunes to determine the values to fill the matrix. We determined the validity of the model using a test case of the following specifications:

* 200 Nodes - 10 loops (2000 eff. passes)
* 50 meter length lattice - LINAC
* XY Tunes = $2 \pi$
* Including Spacecharge
  
From the test case we were looking for two major concepts to be upheld from the model, matching initial and final distributions and a decrease in the oscillation frequency from the statistical beta function.

<img src="/assets/images/DistPic.png" alt="Distributions Comparison" width="450"/> <img src="/assets/images/StatBetaFunc.PNG" alt="Statistical Beta Functions" width="450"/>

As seen from the results, both criteria for our model were met. Fortunately, we had about 7 weeks left for the internship and were able to continue the project to create 2 envelope solvers.

## Envelope Solver

The major assumptions for the solver are a periodic lattice and self-consistent beam. Including spacecharge forces, we have a modified Hill equation given by,

$$ x'' + k_x(s) x  - \frac{2\Lambda}{a(s)(a(s)+b(s))} x  = 0$$

$$ y'' + k_y(s) y  - \frac{2\Lambda}{b(s)(a(s)+b(s))} y  = 0$$

Therefore our envelope solver was based on *Eqs. (2-3)* where $u$ and $\nu$ represent the envelope in the X and Y cross section of the beam, respectively.

$$u'' + k(s) u = \frac{E_u^2}{u^3} + \frac{2 \Lambda}{\sqrt{u^2 + 4 D^2\sigma_E^2} + \nu}$$

We made a new child node class to implement the envelope solver, which could be inserted into each node in a lattice. The solver will only use a single particle bunch, which will hold the envelope inital parameters defined by the Twiss parameters. Testing the envelope solver, we used the same test case defined above (50m, 200 Nodes), and created two different bunches. The first bunch was a collection of 10,000 macro particles, and the second contained only an envelope particle. Comparing the simulation results from the two bunches we determined the solver works as intended.

<div style="text-align:center"><img src="/assets/images/Envelopecomp.png" alt="EnvelopeCompared" class="center" width="500"></div>

## Tilting Envelope Solver

Moving foward in the project, we aimed to make a different solver that could add a wider range of distrobutions/beams that can use the envelope solver. This final envelope solver was made to handle tilting beams in contrast to basic rotating beams seen in the figures above. Unfortunately, the tilting envelope solver was tested using a particle bunch. However, we did do basic exmaples to verify it worked.

<div style="text-align:center"><img src="/assets/images/tiltinggif.gif" alt="Tilting Envelope" class="center" width="500"></div>

These solvers and Uniform Focusing model will help study the behavior of self-consistent beams. Such beams may be able to provide low-loss environments. For high intensity accelerators this may lead to increased longevity, reduced costs, and higher power. If the project was continuned, the major simulations and experimential runs would have involved self-consistent beams with extranious particles.

<div style="text-align:center"><img src="/assets/images/external.png" alt="Envelope and Particles" class="center" width="500"></div>

This would allow for a significant decrease in computational power and processing time. Using the envelope solver would give details about the beam and spacecharge forces that would effect the external particles.

### References and Sources

The contributions made for [PyOrbit](https://github.com/PyORBIT-Collaboration/py-orbit) can be found at the PyOrbit forked repository on my [GitHub](https://github.com/bford26/py-orbit).

* Rosenzweig, James B. *Fundamentals of Beam Physics*.Los Angeles, University of California, 2012.
* Edwards, D.A. and M.J.Syphers. *An Introduction to the Physics of High Energy Accelerators.* Wiley-VCH, 1993.
