---
title: MP4
permalink: "/mp4/"
layout: page
---

### <span style="color:blue"> A Simple Particle System</span>
**Due: May 1, 11:55pm**

![spheres](/assets/img/mp4.png){:height="300px" width="300px"}   

Write a simple particle system using WebGL to handle the display. 
Particle systems are typically used to model fine-grained physical effects like fire, smoke, and water.
We will do something simpler and just render a system of bouncing spheres in 3D.
The specifics of how you implement the following features are up to you...write an app that you think is fun...

Your program will render a set of spheres bouncing around an invisible (or visible if you wish...) 3D box.
You could use a box with corners (-1,-1,-1) to (1,1,1) for example.
When a sphere hits one of the walls in the box, it should reflect in physically realistic manner.  

#### Particles ####
You should keep an array or list of particles.

Each particle will be have a postion P and velocity V...both of these quantities will be three-dimensional quantities. Each particle will be represented by a sphere.

It is acceptable to render all the spheres with a uniform radius and color, however...you can include other attributes if you like. For example, you could have each sphere have an individual color or radius or alpha value....
 
You only need to generate one sphere mesh...you simply draw that mesh in multiple different spots each frame...once for each particle.
You can use some of the code on the course website that can generate and render a sphere.

#### User Interface ####

Your user interface should allow you to create spheres using a mouse click or key press. Each creation event should create X spheres, where X is some number of your choosing.

The spheres should be genereated with a random position and velocity.

You will need to bound those values to be reasonable (e.g. position inside the box).
You will also need a reset button that will remove all existing spheres from the scene.
 
#### Physics #### 

After rendering a frame showing the current position of the spheres, you will need to update the position and velocity of each sphere.
Update the position using the current velocity and Euler Integration
Update the velocity using the set of forces you are implementing (e.g. gravity and friction) 
 
Implement 2 forces that affect the spheres: gravity and friction. If you want to violate physics for fun and have the spheres gain velocity after hitting walls, you can do that as well.

### Submission ###

You will need to submit the following files in a zip archive via Compass:

- **mp4.html**

- Any **.js files** you create to implement the app. You can use as many as you wish to implement the app using good software engineering practices. Use any naming scheme you wish.

- **webgl-utils.js** if you use it  

- **gl-matrix-min.js** where this is whichever version of the glMatrix library you used.

- All the files required for your app to run

Name your submission as NETID_MP4.zip and submit it to Compass, where NETID is your netid.

### Grading Rubric ###
The assignment will be graded based on the following:

|:----------------+----------------------|
| **Feature**     | **Points**           |
|:--------------------|-----------------:|
| Interactive UI	 | 1 |
| Forces           | 2 |
| Euler Integration|	2| 
| Sphere-Wall Collision Detection| 	2 |
| Document interface on webpage | 1| 
| Nicely shaded spheres | 2|
| **TOTAL**	                                                | 10   |
|===
