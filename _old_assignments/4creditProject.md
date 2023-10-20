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
    description: Submit a description of your project
  - 
    name: Create an Environment
    points: 40
    description: A 3D environment that the user can navigate in 
  - 
    name: Teleportable and Walkable and Blocked Areas
    points: 10
    description: Implement a teleportation mechanic in addition to a walking mechanic and blocked areas
  - 
    name: Grabbable Object
    points: 10
    description: Have at least 3 grabbable objects the user can interact with
  - 
    name: Button
    points: 10
    description: Implemenment a touchable button with feedback
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

### Suggested Project Goals 

This project is open-ended, giving you the creative freedom to design any type of environment, game, or other virtual activity. However, it is essential that your software incorporates some mechanics that will be presented later in this document. 

Your project should have a clear objective; merely creating a visually appealing environment for exploration is not sufficient. There must be some form of interaction. This interaction can be straightforward, such as clicking objects to access additional information, like in an educational application to get information about something. Alternatively, you have the option to create an intense and highly interactive game with multiple points of engagement. Feel free, just take care with your expectation related to the time available. 

### Project Ideas 

You have the freedom to choose the theme of your project, but here are some suggestions for you and your group: 

+ Escape Game: This is a highly popular concept in VR gaming. In this idea, the user becomes locked in one or more virtual rooms and must solve puzzles to escape from the virtual confinement. 

 

+ Superhero Game: Game development offers the exciting opportunity to create experiences that would otherwise be impossible. You can empower your players with extraordinary abilities like flying, shooting laser beams, wall-crawling, and more. 

 

Additionally, you can draw inspiration from well-known games such as Beat Saber or Super Hot. However, it's essential to inject something original or unique into your implementation to make it stand out. 



 

#### Unreal VR Development: 

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

 

#### VR Test and Simulations: 

While it's crucial to test your project with a Head Mounted Display (HMD), you can accomplish a significant portion of the development without one. This includes tasks such as setting up levels, positioning objects, programming behaviors, and lighting. 

You can perform these initial development tasks without the need for a headset. Subsequently, you can employ solutions like XR Device Simulator and HMD Mock to simulate how VR interaction devices interact with your project, including head positioning and controller behavior. 

However, it's vital to emphasize that testing your solution with a headset is essential. Without this, you might miss important details that are only observable in the full immersive experience. 

 

#### Part 1: Scene Creation 

Begin by crafting a foundational scene. You have the option to either reuse a template map or scene, but we strongly recommend creating a new level. Populate this virtual environment with various objects, such as buildings, trees, or any other elements of your choice. Ensure that there is some space for user navigation, allowing them to teleport or walk. Pay attention to scene details, including the sky, lighting, and background environment, as these elements can significantly enhance the overall appeal of your scene. 

#### Part 2: Teleportable or Walkable Areas 

To allow user movement within the scene, establish navigation volumes or areas. This will define where users can navigate, whether it's teleporting to different locations or walking. Design adequate areas within your scene for these navigation purposes. Include some areas with ramps or stairs. Avoid creating only a big walking plane for your simulation, unless it serves a specific purpose within your game logic. 

#### Part 3: Blocked Areas 

Create areas that you wish to block users from teleporting or walking into. At a minimum, create one area to limit user movement. 

#### Part 4: Integrating Grabbable Objects 

Place some objects into your scene that users can interact with by virtually holding them. The choice of grabbable objects is flexible, but it's essential not to rely solely on template mesh examples (like cubes or pistols). Provide a rationale for users to hold these objects, perhaps as a means of discovering something or as a key to unlock another aspect of the experience. These grabbable objects can be held in different ways, depending on the interaction you intend to create. 

#### Part 5: Including Interactive Buttons 

Incorporate a touchable element within your scene, which can be referred to as a button. It's not necessary to use a specific geometric shape like a light switch, but it is crucial to have an interactive element in the scene that users can virtually touch. When this virtual button is pressed, it should provide feedback, such as movement or a change in color (if active). Additionally, the button's activation should trigger an event or action, such as playing music, opening a door, or turning on a lamp. 

 

### Sponsored Projects

We have two opportunities for individuals or teams of people to work with existing groups that have a VR project going. **These projects will be 
available on a first-request basis.** This means that not everyone that requests a sponsored project will for sure get the opportunity to work on it. 

### List of Sponsored Projects

1. ![UE5](/img/crystal.png){:class="img-responsive" style="display:block; margin:auto" width="400px"}Work with a Civil Engineering research group on their educational game Crystal Vision...which teaches people about crystallography. The research project will focus on developing an educational game for undergraduate engineering students. The game is supposed to teach some basic topics of crystallography (crystallographic points, directions, planes or miller indices) in an immersive learning environment. The topics require complex 3D visualizations. Hence, the gameplay will require significant number of features for 3D object interactions. It will be a single player, third person actor game which will mostly follow adventure game genre. The game will be developed using Unreal Engine using Blueprints scripting. The game will be played using VR (Meta Quest 2 and/or the latest Quest 3) headsets.

2. The Cyprus Institute and NCSA are developing a VR experience of the history of the Nicosia airport, an example of modernisation of the post-colonial society of Cyprus, built by German companies, to expand the new touristic development of the island after the establishment of the Republic. This is an important infrastructure of the city that lies in the buffer zone under the control of the UN. They have been processing 3D reality capture data and collecting historical information about the airport for the last couple of years, and want to developing a VR exeprience.
 


## VR Project Proposal

The project proposal should be submitted as a link to a Google Doc. That doc link should have edit capability enabled so we can easily comment on the proposal. The proposal should meet the following expectations:
+ One page or less
+ List all group members by name and netid
+ One paragraph that gives an overview of the project (e.g. "We will implement a VR game in which the player searches for their phone which has fallen next to their car seat while driving.").

**You DO NOT need to wait until you proposal is graded before starting the project!**

## Deadlines
 
**Oct 27 11:59 PM submit proposal on canvas.**

**Nov 31 11:59 PM submit project on canvas**

