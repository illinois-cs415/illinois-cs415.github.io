---
title: MP3 Part 2
permalink: "/mp3-2/"
layout: page
---

### <span style="color:blue">Environment Mapping</span>
**Due: April 21, 11:55pm**

![teapot](/assets/img/teapot.png)  
Your goal is to add the following features to your work from MP3 Part 1:

+ A radio button (or similar control) in the HTML that allows the user to switch between simply shading the teapot and making the teapot reflective.

+ If the user selects reflective, youe code should render the teapot using a cubemap. The reflection should be consistent with the scene rendered on the skybox.

+ Add the capaibility to rotate the teapot. Make sure the image on the teapot changes correctly.

** Note: When using the environment map to shade the teapot, you do not have to implement Blinn-Phong or Phong illumination. **

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
|The teapot surface reflects the environment | 3|
|Teapot rotation works correctly and the image on the teapot changes correctly | 2|
|Your code should be commented and user interface on the webpage should be clear| 1|
| **TOTAL**	                                                | 6  |
|===
