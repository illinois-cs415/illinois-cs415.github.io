---
layout: assignment
title: "4 Credit Assignment"
index: 10
due: "Nov. 17, 2023 @ 11:59 PM"
material: ~
points: 100
rubric:
  -
    name: Proposal
    points: 10
    description: Submit a description of your project complete with a grading rubric
  - 
    name: Project Implementation
    points: 70
    description: Submit the code or similar work product through a link to a repo or compressed folder 
  -
    name: Video
    points: 20
    description: Submit a short video demonstrating your project
--- 
![Breath of the Wild](https://www.theverge.com/_next/image?url=https%3A%2F%2Fcdn.vox-cdn.com%2Fthumbor%2FirIOIA243mp1aEMOHqPkxc4rsKQ%3D%2F0x0%3A950x534%2F2000x1333%2Ffilters%3Afocal(475x267%3A476x268)%2Fcdn.vox-cdn.com%2Fuploads%2Fchorus_asset%2Ffile%2F16193538%2FCI_News_TheLegendOfZeldaBreathOfTheWild_LaboCVR_Zelda_01_image950w.jpg&w=2400&q=75)
## What is the 4 Credit Project About?
Taking the course for an extra credit hour requires the completion of a extra project in addition to the course project done by the entire class. 
The main focus of the 4 Credit Project will be to implement something using the VR capabilities of Unreal Engine. But there are other options as well.
This is an opportunity to learn a new thing or implement something you always wanted to...so long as it is related to the course in some way. 

## Frequently Asked Questions
1. **Do we have to work in groups?** No! You can work on your own if you wish.
2. **How big of a group can work in?** There's no limit as long as we decide the proposal is sufficient work for the group size.
3. **Do we have to do a VR project?** No! But you should strongly consider it. It's a chance to work with equipment not everyone has.
4. **What equipment?** We have 9 Oculus Rift S HMDs, 7 Quest 2 HMDs and a HoloLens 2. These can be loaned out or hosted in the 1104 NCSA lab.
5. **What are the non-VR options?** Yes! You can propse your own project. Details below.

## VR Projects

Ideally, a VR project will be done as a team (the number of HMDs we have is limited). You can implement one of our ideads below, or propose your own VR project or consider one of the sponsored projects listed below. 

Your Virtual Reality Project is designed for you to develop the fundamental skills in creating virtual environments using the basic mechanics employed in Virtual Reality. When designing a virtual environment, it's essential to keep in mind that the level of immersion is significantly higher than when playing on a flat screen, so attention to usability details is crucial. 

There are various tools and methods available for Virtual Reality development, but using a game engine is a prerequisite for this task. You cannot employ a high-level tool or system to construct your environment. The recommended tool for developing your VR application is Unreal, though you are also free to choose Unity or Godot. If you intend to use a different tool, please consult with your professor first. 

 

Project Goals 

This project is open-ended, giving you the creative freedom to design any type of environment, game, or other virtual activity. However, it is essential that your software incorporates some mechanics that will be presented later in this document. 

Your project should have a clear objective; merely creating a visually appealing environment for exploration is not sufficient. There must be some form of interaction. This interaction can be straightforward, such as clicking objects to access additional information, like in an educational application to get information about something. Alternatively, you have the option to create an intense and highly interactive game with multiple points of engagement. Fell free, just take care with your expectation related to the time available. 

 

Project Ideas 

You have the freedom to choose the theme of your project, but here are some suggestions for you and your group: 

Escape Game: This is a highly popular concept in VR gaming. In this idea, the user becomes locked in one or more virtual rooms and must solve puzzles to escape from the virtual confinement. 

 

Superhero Game: Game development offers the exciting opportunity to create experiences that would otherwise be impossible. You can empower your players with extraordinary abilities like flying, shooting laser beams, wall-crawling, and more. 

 

Additionally, you can draw inspiration from well-known games such as Beat Saber or Super Hot. However, it's essential to inject something original or unique into your implementation to make it stand out. 

 

Please pay close attention to the guidelines about recording the video for submission: 
Video Guidelines Link 
If you do not follow the guidelines and your submission is hard to grade you may lose points. 

 

Unreal VR Development: 

Unreal is the recommended platform for your VR project. To get started and learn about VR development in Unreal, we are going to present some online resources. Please note that Unreal has seen several improvements in recent years for Virtual Reality support, so some instructions you find online may not match your Unreal version. 

One significant improvement is that Unreal is now fully compatible with OpenXR, allowing you to use the OpenXR API directly in Unreal. This simplifies porting your application to popular head-mounted displays. You can also consider using the Meta XR plugin if it fits your project's needs. 

To begin your project, you can utilize the basic VR template available in modern versions of Unreal. You'll find this template under Games > Virtual Reality. For comprehensive documentation on Virtual Reality development in Unreal Engine, visit the official Unreal Engine website:  

https://docs.unrealengine.com/5.3/en-US/developing-for-xr-experiences-in-unreal-engine/  

For video tutorials, consider the following: 

 

Unreal Engine YouTube Channel: Introduction to Virtual Reality in Unreal Engine 5 - This video covers the core concepts of Virtual Reality in Unreal Engine 5, providing background information and best practice recommendations. 

https://www.youtube.com/watch?v=JD95BklloHk  

 

 

Setting Up Unreal Engine for Virtual Reality - This shorter video guides you through configuring Unreal Engine for Virtual Reality, ensuring your Head Mounted Display functions correctly. 

https://www.youtube.com/watch?v=DiGh6MxDFds  

 

Creating a Floating User Interface in VR - Another video from the same author explains how to design a floating user interface in VR. 

https://www.youtube.com/watch?v=kM27HYbpvc0 

 

These resources should help you kickstart your VR development journey with Unreal.  

 

VR Test and Simulations: 

While it's crucial to test your project with a Head Mounted Display (HMD), you can accomplish a significant portion of the development without one. This includes tasks such as setting up levels, positioning objects, programming behaviors, and lighting. 

You can perform these initial development tasks without the need for a headset. Subsequently, you can employ solutions like XR Device Simulator and HMD Mock to simulate how VR interaction devices interact with your project, including head positioning and controller behavior. 

However, it's vital to emphasize that testing your solution with a headset is essential. Without this, you might miss important details that are only observable in the full immersive experience. 

 

Part 1: Scene Creation 

Begin by crafting a foundational scene. You have the option to either reuse a template map or scene, but we strongly recommend creating a new level. Populate this virtual environment with various objects, such as buildings, trees, or any other elements of your choice. Ensure that there is some space for user navigation, allowing them to teleport or walk. Pay attention to scene details, including the sky, lighting, and background environment, as these elements can significantly enhance the overall appeal of your scene. 

Part 2: Teleportable or Walkable Areas 

To allow user movement within the scene, establish navigation volumes or areas. This will define where users can navigate, whether it's teleporting to different locations or walking. Design adequate areas within your scene for these navigation purposes. Include some areas with ramps or stairs. Avoid creating only a big walking plane for your simulation, unless it serves a specific purpose within your game logic. 

Part 3: Blocked Areas 

Create areas that you wish to block users from teleporting or walking into. At a minimum, create one area to limit user movement. 

Part 4: Integrating Grabbable Objects 

Place some objects into your scene that users can interact with by virtually holding them. The choice of grabbable objects is flexible, but it's essential not to rely solely on template mesh examples (like cubes or pistols). Provide a rationale for users to hold these objects, perhaps as a means of discovering something or as a key to unlock another aspect of the experience. These grabbable objects can be held in different ways, depending on the interaction you intend to create. 

Part 5: Including Interactive Buttons 

Incorporate a touchable element within your scene, which can be referred to as a button. It's not necessary to use a specific geometric shape like a light switch, but it is crucial to have an interactive element in the scene that users can virtually touch. When this virtual button is pressed, it should provide feedback, such as movement or a change in color (if active). Additionally, the button's activation should trigger an event or action, such as playing music, opening a door, or turning on a lamp. 

 

Shape 

Submission Instructions 

Hand-in will be done on Canvas. You will be expected to upload the following: 

A link to a git repo or drive/box folder containing your project code. It should be possible to build your game in Unreal using the submitted code. 

A short video up to 10 minutes long (can be much shorter) showing your game and demonstrating all the required features. Your video ideally should be a screen capture with brief narration by you pointing out the features as they appear in the game. 

Some good options for video capture software are: 

OBS 

Game Bar on Windows 

QuickTime on Mac 

If recording narration is problematic (e.g. you lack a microphone) you can skip that part. Please only resort to capturing video using your phone if you have tried one of the above methods and just could not get it to work. 

On Canvas you should put the link to your code in the Comment box and then upload a video file using the Upload Media tab. 

Canvas Upload 

Shape 

Name 

Points 

Description 

Create an environment 

15 

A 3D environment that the user can navigate on it 

Teleportable areas 

15 

Create some teleportable areas in your environment, these areas must have a ramp or stairs. 

Non-teleportable areas 

15 

Specify an area that your user can’t access 

Create Grabbable Object 

20 

Create at least 3 objects that you can hold with your VR controllers 

Button 

20 

Create a button on your scene that has some kind of feedback 

Design Document 

15 

Submit a document that explains your level design and design decisions 

Video 

5 

Submit a link to a video demo of your game 

Total 

100 

 

 







### VR Project Proposal

The project proposal should be submitted as a link to a Google Doc. That doc link should have edit capability enabled so we can easily comment on the proposal. The proposal should meet the following expectations:
+ One page or less
+ List all group members by name and netid
+ One paragraph that gives an overview of the project (e.g. "We will implement a VR game in which the player searches for their phone which has fallen next to their car seat while driving.").
+ One paragraph stating what hardware platform you wish to target.
+ A rubric containing specific elements with points assigned that add up to 70 points. This should tell us what the key features are that we will grade. 
+ The rubric should include at least 3 features.
+ One of the features on the rubric should be Using Unreal Engine VR Best Practices and be worth 20 points. You can find the Best Practices guide [at this link](https://docs.unrealengine.com/4.26/en-US/SharingAndReleasing/XRDevelopment/VR/DevelopVR/ContentSetup). Just to be clear, we will not be super strict about grading this element. You just need to show an a good faith effort to conform to the guidelines.

**Wait until you proposal is graded before starting the project!**

## Sponsored Projects

We have two opportunities for individuals or teams of people to work with existing groups that have a VR project going. **These projects will be 
available on a first-request basis.** This means that not everyone that requests a sponsored project will for sure get the opportunity to work on it. 

### Sponsored Project Request Process
To request to work on a sponsored project, post to [CampusWire](https://campuswire.com/c/GA821B381/feed) visible only to course staff and using the `Sponsor Request` category. Include the following information:
1. Name and netid of everyone asking to work on the project
2. Which sponsored project you are requesting

We will contact you within a few days of the request to let you know the result of the request.

### List of Sponsored Projects

1. ![UE5](/img/pointvr.png){:class="img-responsive" style="display:block; margin:auto" width="400px"}Work with PointVR. See their project document here: [PDF](https://github.com/illinois-cs415/illinois-cs415.github.io/raw/main/img/pdf/CS_415_Features_List.pdf). More info about the group can be found here: [PointVR](https://icasu.illinois.edu/outreach/point-vr)
2. ![UE5](/img/corona1.jpg){:class="img-responsive" style="display:block; margin:auto" width="400px"}Work with NCSA visualizing data from a simulation of a coronal mass ejection (CME) on the sun, optionally combined with a separate, but also cool-looking, animation of convection on the sun's surface.
3. ![UE5](/img/trees.jpg){:class="img-responsive" style="display:block; margin:auto" width="400px"}Work with NCSA visualizing 760 million trees in West Africa.
4. ![UE5](/img/crystal.png){:class="img-responsive" style="display:block; margin:auto" width="400px"}Work with a Civil Engineering research group on their educational game Crystal Vision...which teaches people about crystallography.

## Proposing a Non-VR Project ##

If you wish to propose a non-VR project you can do so in same way as a VR project...just without the VR specific elements of the proposal format. 

### Proposal Guidelines
The project proposal should be submitted as a link to a Google Doc. That doc link should have edit capability enabled so we can easily comment on the proposal. The proposal should meet the following expectations:
+ One page or less
+ List all group members by name and netid
+ One paragraph that gives an overview of the project (e.g. "We will implement a non-VR game in which the player searches for their phone which has fallen next to their car seat while driving.").
+ One paragraph stating what hardware platform you wish to target.
+ A rubric containing specific elements with points assigned that add up to 70 points. This should tell us what the key features are that we will grade 
+ The rubric should include at least 3 features.

**Wait until you proposal is graded before starting the project!**

## Deadlines
 
**Oct 15 11:59 PM submit proposal on canvas.**

**Dec 7 11:59 PMP submit project on canvas**

