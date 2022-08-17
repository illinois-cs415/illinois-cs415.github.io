---
title: MP2 Part 2
permalink: "/mp2-2/"
layout: page
---

### <span style="color:blue">Terrain Generation</span>
**Due: March 15, 11:55pm**

![terrain](/assets/img/terrain.PNG)  

To complete the second Machine Problem, you will implement a simple flight simulator. Your "plane" will fly over the terrain you generate.  You will also add the capability of applying fog to your terrain.

The airplane should automatically move forward at a fixed speed. The user will control the bank and tilt of the airplane through the arrow keys.

+ Pressing the left (right) arrow key will make the plane roll to its left (right).
+ Pressing the up (down) arrow key will cause the airplane to pitch up (down).
+ Pressing the + (-) key will increase (decrease) the airplane's speed

You will need to implement the following: 

#### A quaternion based viewing system ####
The glMatrix library provides support for using [quaternions](http://glmatrix.net/docs/module-quat.html). We would suggest using that library instead of creating your own quaternion class. **Note** if you are using the example code from this course, that code uses an older version of the glMatrix library. The library downloaded from the course website may not include all of the functions documented in the current API. It is suggested that you donwload the current glMatrix library from the web and work with that version.

#### A working and documented user interface #### 
You should implement a user interface that minimally implements the arrow-key and +/- key controls described above. You can add additional controls to affect yaw if you wish.
Your webpage should include text instructions describing how the user interface works...you can simply include text in the HTML file that explains how to control the view and speed. 

#### Phong shading ####

You should perform per-pixel shading and compute colors using either the Phong or Blinn-Phong reflection model in the **fragment shader**.

#### A cloud of fog, placed over and around your terrain ####
The fog computation should be done per-pixel, which means implemented in the fragment shader. Implement a control on the webpage (e.g. a checkbox) which allows the user to turn the fog on and off in the scene. More details about how to simulate fog will be provided in lecture.

## Submission ##

You will need to submit the following files in a zip archive via Compass:

- **mp2.html**  

- Any **.js files** you create to implement the app. You can use as many as you wish to implement the app using good software engineering practices. Use any naming scheme you wish.

- **webgl-utils.js** if you use it  

- **gl-matrix-min.js** where this is whichever version of the glMatrix library you used.

Name your submission as NETID_MP2.zip and submit it to Compass, where NETID is your netid.

### Grading Rubric ###
The assignment will be graded based on the following:

|:----------------+----------------------|
| **Feature**     | **Points**           |
|:--------------------|-----------------:|
|Working and documented user interface  | 1     |
|                        |       |
|||
|Forward motion   | 1      |
||| 
|Ability to roll           | 1     | 
|||
|Ability to pitch  | 1     |
|||
|Ability to change speed |1|
|||
|Fog      | 1     |
|||
| **TOTAL**	                                                | 6    |
|===
