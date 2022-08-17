---
title: MP2 Part 1
permalink: "/mp2-1/"
layout: page
---

### <span style="color:blue">Terrain Generation</span>
**Due: March 4, 11:55pm**

![terrain](/assets/img/terrain.PNG)  

For your second Machine Problem, you will procedurally model a piece of terrain. For now, this can be a static scene. We will add interaction in the second part of the MP.

You will need to implement the following:

### 1. Implement the diamond-square algorithm ###

To procedurally generate the terrain, you should implement the diamond-square algorithm. This fractal-based terrain generation algorithm is quite old, first published in 1982, but does a acceptable job generating a rocky terrain consideirng how short the code is. Realistic terrain generation in modern games requires considerably more complicated algorithms and tools...see [this talk by Ubisoft developer Etienne Carrier](https://www.youtube.com/watch?v=NfizT369g60) if you are interested in seeing the tools technical artists use these days. 

This [wikipedia entry on diamond-sqaure](https://en.wikipedia.org/wiki/Diamond-square_algorithm) is a good introduction. We will discuss details of how to implement it WebGL in lecture on Thursday February 21 by working on Lab 3. 

In brief, your implementation should generate an indexed mesh and render it using the WebGL function **`void gl.drawElements(mode, count, type, offset)`{: style="background-color: GainsBoro"}**. You should pay attention to the `type` parameter as the type **`gl.UNSIGNED_SHORT`{: style="background-color: GainsBoro"}** is the largest supported natively in WebGL 1.0. This will limit your mesh to having only 65536 vertices. If you want more, you will need to use the extension **[`OES_element_index_uint`{: style="background-color: GainsBoro"}](https://developer.mozilla.org/en-US/docs/Web/API/OES_element_index_uint)**.

In [Lab 3](https://github.com/illinois-cs418/cs418CourseMaterial/raw/master/Labs/Lab3.zip), we will work on one possible approach to generating an indexed mesh structure. We will create a grid of vertices in the X-Y plane and triangulate them. You can use a Model transformation to rotate this flat terrain to position it however you want to make viewing easier. If you use this as the basis for your code, you will then need to set the z coordinates of the triangles according diamond-square algorithm to complete the terrain model.

In order for the mesh to be shaded correctly **you will also need to generate per-vertex normals** for the mesh. Each normal is a vector perpendicular to the mesh at the vertex, and is computed as an average of the normals of the triangles that surround the vertex. These normals will be another attribute that you will need to send down to the vertex shader.


**Debugging Tips** 
- Start by generating a small flat terrain (for example 3 vertices by 3 vertices).  
 Use this to set up the view you want.
- Then, add in the ability to set the z coordinates of the vertices.   
Do something simple like random heights.
- Then, work on implementing the diamond-square algorithm.
- Be aware that Lab 2 and Lab 3 both use an older version of the glMatrix library.  
You may need to update the code if you use a newer version of the glMatrix library.

### 2. Implement a perspective view of the scene ###

Your code should generate a view matrix and a perspective projection matrix in the javascript portion of the app and send them to the vertex shader...and use them to transform the vertices. You should use the [glMatrix library](http://glmatrix.net/) functions **`lookAt(out, eye, center, up)`{: style="background-color: GainsBoro"}** and **`perspective(out, fovy, aspect, near, far)`{: style="background-color: GainsBoro"}** to generate the matrices. It is up to you to understand how to specify the parameters to generate a good view. 

### 3. Implement the Blinn-Phong reflection model ###
Implement the Blinn-Phong illumination model with Gouraud shading. This means your shading calculations should be done per-vertex...meaning in the vertex shader. You can position your light source(s) anywhere in the scene as long as the rendered images are well-lit. You can use the [Lab 2 shader code](https://github.com/illinois-cs418/cs418CourseMaterial/raw/master/Labs/Lab2-Mesh.zip) as a starting point...it implements the Phong illumination model and Gouraud shading. You will need to understand the difference between the two reflection models and make the relatively minor change to the code to switch it to Blinn-Phong. In addition, you will need to change how the shader handles material colors...you will need to generate a color for the terrain based on elevation as described below.

### 4. Implement an elevation-based colormap for the terrain ###

In your shading calculation, you should assign colors to vertices based on the elevation of the vertex. If you use the z-coordinate as elevation, that means you should base your color assignment on the value of the z-coordinate. For example, you could define four different intervals of z values and assign blue to the vertices in the lowest interval, green to the second lowest, brown to the second highest, and white to the highest. You should create your own scheme; do something that looks good. In terms of implementation, you can compute the color to be used in the vertex shader by making the necessary information available to the shader program. Or, you could compute the color on the CPU (i.e. in the javascript portion of the app) and pass it as an attribute. Computing the color in the shader program will be more perfomant. 


### 5. Comment appropriately ###

You should comment each file with an author comment and comment each function you write with a header. Use JSDoc comments with the appropriate tags and types.
Details can be found in the Google JavaScript Style Guide. 
 

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
|Code is well documented, with comments for each function   | 1     |
|                        |       |
|||
|Code renders a terrain generated using the diamond-square algorithm   | 3      |
||| 
|Scene uses an elevation-based colormap to shade the terrain           | 2     | 
|||
|Shading is done using the Blinn-Phong reflectance model and Gouraud shading  | 2     |
|||
|The scene exhibits reasonable aesthetic quality (i.e it looks good)      | 1     |
|||
| **TOTAL**	                                                | 9    |
|===
