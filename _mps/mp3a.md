---
title: MP3 Part 1
permalink: "/mp3-1/"
layout: page
---

### <span style="color:blue">Environment Mapping</span>
**Due: April 14, 11:55pm**

![teapot](/assets/img/teapot.png)  
Your goal is to write an app that loads the Utah teapot from a file and renders it. 

Your app should have the following features:

+ Perspective
+ Phong or Blinn-Phong Reflectance Model
+ Skyboxing
+ Allow the user view to orbit around the teapot

Your app should look something like the image above, but your teapot won't be reflective.

#### Skyboxing ####
Create and draw an environment using skyboxing...render a large cube surrrounding the viewer...this is the skybox. Use the cube map images to texture map the inside of the skybox. You should use the same set of six images that you will use for the teapot environment map later in Part 2 of this MP. 

Pro-tip: Instead of texture mapping each side of the skybox independently, you can create an environment map and use that...you just have to figure out what direction vector to use when accessing the environment map to color a fragment on the box.

##### Background Reading and Resources #####
 A set of 6 image files forming a cubemap are available in this [zip file](https://github.com/illinois-cs418/illinois-cs418.github.io/raw/master/assets/sample.zip). You can use these for the MP if you wish.
 
You can make your own cubemaps as well. There is a somewhat dated tutorial on generating cube maps [here](https://aerotwist.com/tutorials/create-your-own-environment-maps/).Please note that they use 3.js to render... so don't steal their code. You need to use WebGL. Alterrnatively you can try to use one of the cubemaps from [this collection](http://www.humus.name/index.php?page=Textures).

#### Teapot Mesh ####
You can grab an OBJ file containing the famous Utah Teapot Mesh [here](https://github.com/illinois-cs418/illinois-cs418.github.io/raw/master/assets/teapot_0.obj).

##### Background Reading and Resources #####

The OBJ file format is documented in this [wikipedia article](https://en.wikipedia.org/wiki/Wavefront_.obj_file).
You will need to get the OBJ file from the server, and then parse it to generate the vertex and face arrays. If you know how to use AJAX or jquery you can use those to get the file.

If you don't know how to use those, you can use the function given in [readText.js](https://github.com/illinois-cs418/illinois-cs418.github.io/raw/master/assets/readText.js) to get a file and send it to the function you will write to parse the file.

Use the above linked teapot model, which consists only of vertices and triangular faces. Load the vertices into a vertex position array, and the triangle faces into a face array whose elements are triples of vertex indices. **Note that the indices of the vertices in the OBJ start at 1**. This means you will need to adjust them assuming your arrays start indexing at 0. You will need to create per-vertex normals for the mesh as well, which you should compute as the average normal of the the trangles incident on the vertex.

##### Running a Local Server #####
To get around the issue of reading files from the local filesystem, it is best to test by running a local webserver. There are two relatively easy ways to do this:

+ If you use the Brackets editor, the live preview function will start up a server (and browser) to test your code.
Just have Chrome open, and the open your html file in Brackets. Click the lightning bolt icon in the top right of the Brackets window.

+ Alternatively, you can install [node.js](https://nodejs.org/en/) Then install and run [httpserver](https://www.npmjs.com/package/httpserver) to serve the directory that it is run from.

#### User Interface ####
Your initial user interface should alllow to the user view to orbit the tepot (just letting the view circle the teapot by rotating around the y-axis is fine, it needn't employ quaternions). This effect can be achieved by rotating the world (teapot and enclosing environment box) assuming the teapot is at the origin.

#### Lighting ####
Use a point light source to light the model from the direction (1,1,1). You can adjust the ambient light as you wish, but it must be possible to see the effects of diffuse shading and a specular highlight on the teapot. Use the Blinn-Phong reflectance model and Phong shading.

## Submission ##

You will need to submit the following files in a zip archive via Compass:

- **mp3.html**  

- Any **.js files** you create to implement the app. You can use as many as you wish to implement the app using good software engineering practices. Use any naming scheme you wish.

- **webgl-utils.js** if you use it  

- **gl-matrix-min.js** where this is whichever version of the glMatrix library you used.

- All the image and OBJ files required for the app to run

Name your submission as NETID_MP3.zip and submit it to Compass, where NETID is your netid.

### Grading Rubric ###
The assignment will be graded based on the following:

|:----------------+----------------------|
| **Feature**     | **Points**           |
|:--------------------|-----------------:|
|Load teapot geometry correctly| 2|
|User can change view in an orbit around the teapot, light behaves correctly| 2|
|Teapot surface is shaded correctly| 2|
|Environment is rendered on a box enclosing the viewer| 2|
|Your code should be commented and user interface on the webpage should be clear| 1|
| **TOTAL**	                                                | 9   |
|===
