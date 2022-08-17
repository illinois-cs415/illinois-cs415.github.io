---
title: MP2 4 Credit
permalink: "/mp2-4cr/"
layout: page
---

### <span style="color:blue">Terrain From Texture</span>
**Due: April 1, 11:55pm**

![terrain color](/assets/img/colorHMBIG.png){:height="300px" width="300px"} 
![terrain color](/assets/img/heightHMBIG.png){:height="300px" width="300px"} 

### 4-Credit Students: ###

Your assignment is to implement terrain generation using a height map. A height map is an image in which height is encoded as color, usually grayscale. Your code will use the two images shown here to render the terrain. You will use the the grayscale image to generate the height for a vertex and the color image to generate a material color for the vertex.

#### Handling a Large Terrain ####

The height image is 512x512 and the color image is 1024x1024 (you shoudl get the full-sized image when you donwload them). If you generate a grid with 1024 vertices by 1024 vertices you wll exceed the capacity of an UNSIGNED_SHORT to index the set vertices. One solution is to use the exetnsion [OES_element_index_uint](https://developer.mozilla.org/en-US/docs/Web/API/OES_element_index_uint). If you read the linked material, you will note that gl.UNSIGNED_INT is available natively  in WebGL  2.0...but it's probably easier to stick to WebGL 1.0 and use the extension with your existing code base. Note that in addition to changing the type in the gl.drawElements call you will also want to use Uint32Array when creating the buffer.

#### Reading Data from Files ####

Modern broswers typically prevent JavaScript from accessing local files. The images you download for height and color will be colocated with your code, which is to say they will be local files. So, in order for access to happen you will likely need to actually run a webserver and serve your html file. Two simple ways to do this are:

+ If you use the Brackets editor, the live preview function will start up a server (and browser) to test your code.
Just have Chrome open, and the open your html file in Brackets. Click the lightning bolt icon in the top right of the Brackets window.

+ Alternatively, you can install node.js and then install and run httpserver to serve the directory that it is run from.
 
#### Computing Normals ####

You can approximate the normals using information from the height map in the vertex shader - you just need to figure out how to access the heights of neighboring texels. There are different ways to do this, but one relatively straightforward one is to sample the height map at some offsets around the vertex and use those to generate a normal. You will know the (u,v) offset to each neighboring vertex...you can send that to the shader as a uniform...given that and your knowledge of the structure of the mesh you can compute an average normal. Alternatively, you could approximate a normal doing something like what is described in [this stackoverflow post](https://stackoverflow.com/questions/13983189/opengl-how-to-calculate-normals-in-a-terrain-height-grid). 

#### Shading ####

Your code should have two shading modes:

+ Blinn-Phong shading - you generate a color for a fragment using the Blinn-Phong refectance model and Phong shading...use any material color you wish along with a light positioned in the scene so that it illuminates the terrain.

+ Pre-baked - set the color for a fragment by sampling the pre-baked color image provided using texture mapping...no shading is needed. 
The user should be able to switch modes using an html control of some kind.

#### Using Multiple Textures ####

You will create two texture objects and make both available to your vertex shader. Note that this is different than typical texturing in which the fragment shader samples the texture. You will sample the heightmap to transform the vertex, giving it a height. Typically this means in the z direction, but that depends on your code. You will also sample the colored image to assign a material color to the vertex. This color should be sent as a varying to the fragment shader. 

#### Submission ####

You will upload your files to compass in a zipped folder with name NetID_MP2-4CR.zip. Include all of the files necessary for your application to run locally.

#### Grading ####
Your score on this MP will be added to your scores for the other parts of MP 2. So your MP2 will be out of 25 points total rather than 15, and whatever percentage you receive will be used to compute how much of the 15% credit for the MP you will recieve.  

|:----------------+----------------------|
| **Feature**     | **Points**           |
|:--------------------|-----------------:|
|Setting height at vertex correctly |	3pts |
|Setting color at the vertex correctly	| 3pts |
|Rendering 1024x1024 grid of vertices	| 2pts |
|Computing approximate normals and shading correctly |	2pts|
|||
| **TOTAL**	                                                | 10    |
|===
 
