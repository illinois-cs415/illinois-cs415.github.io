---
layout: assignment
title: "4 Credit Assignment"
index: 10
due: "May 6, 2024 @ 11:59 PM"
material: ~
points: 100
rubric:
- name: Proposal
  points: 10
  description: Submit a description of your project
- name: Create an Environment
  points: 40
  description: A 3D environment that the user can navigate in 
- name: Teleportable and Walkable and Blocked Areas
  points: 10
  description: Implement a teleportation mechanic in addition to a walking mechanic and blocked areas
- name: Grabbable Object
  points: 10
  description: Have at least 3 grabbable objects the user can interact with
- name: Button
  points: 10
  description: Implemenment a touchable button with feedback
- name: Creativity
  points: 20
  description: Have something unique or quirky in the environment or gameplay that shows you made the game yourself
--- 

![Matrix](https://duet-cdn.vox-cdn.com/thumbor/0x0:950x534/640x427/filters:focal(475x267:476x268):format(webp)/cdn.vox-cdn.com/uploads/chorus_asset/file/16193538/CI_News_TheLegendOfZeldaBreathOfTheWild_LaboCVR_Zelda_01_image950w.jpg){:width="800px"}

## What is the 4 Credit Project About?

Taking the course for an extra credit hour requires the completion of a extra project in addition to the course project done by the entire class. 
The main focus of the 4 Credit Project will be to implement something using the VR capabilities of Unreal Engine. But there are other options as well.

## Frequently Asked Questions

1. **Do we have to work in groups?** No! You can work on your own if you wish.
2. **How big of a group can work in?** There's no limit as long as we decide the proposal is sufficient work for the group size.
3. **Do we have to do a VR project?** No! But you should strongly consider it. It's a chance to work with equipment not everyone has.
4. **What equipment?** We have 9 Oculus Rift S HMDs, 7 Quest 2 HMDs and a HoloLens 2. These can be loaned out or hosted in the 1104 NCSA lab.
5. **What are the non-VR options?** Yes! You can implement a mobile or web game using the Godot Engine. Details below.

## VR Projects

Ideally, a VR project will be done as a team (the number of HMDs we have is limited). You can implement one of our ideads below, or propose your own VR project or consider one of the sponsored projects listed below. 

Your Virtual Reality Project is designed for you to develop the fundamental skills in creating virtual environments using the basic mechanics employed in Virtual Reality. When designing a virtual environment, it's essential to keep in mind that the level of immersion is significantly higher than when playing on a flat screen, so attention to usability details is crucial. 

There are various tools and methods available for Virtual Reality development, but using a game engine is a prerequisite for this task. You cannot employ a high-level tool or system to construct your environment. The recommended tool for developing your VR application is Unreal, though you are also free to choose Unity.

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



### Alternative Project

Instead of using VR, you can complete a separate game **on your own (meaning not a team project).** Choosing this project is probably the easier choice of the two in terms of access to hardaware and software.

1. You should use the [Godot Engine](https://godotengine.org/)

2. You should build a mobile or web-based game

3. It should be very simple...something with the complexity of MP1 would be perfect

4. Consider making a 2D game instead of 3D

You will need to learn how to use Godot on your own through their tutorials. Course staff experience with Godot is limited but we will do our best to help if you have questions

## Project Proposal

The project proposal should be submitted as a link to a Google Doc. That doc link should have edit capability enabled so we can easily comment on the proposal. The proposal should meet the following expectations:

+ One page or less
+ List all group members by name and netid
+ One paragraph that gives an overview of the project (e.g. "We will implement a VR game in which the player searches for their phone which has fallen next to their car seat while driving.").
+ **For a Godot proposal you must include your own rubric. Make a list of 5 features the game will have with each feature worth 18 points in grading** 

**You DO NOT need to wait until you proposal is graded before starting the project!**

## Deadlines

**April 10 11:59 PM submit proposal on canvas.**

**May 4 11:59 PM submit project on canvas**


