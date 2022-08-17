---
layout: assignment
title: "Level Design"
index: 10
due: "Mar. 11, 2022 @ 11:59 PM"
material: ~
points: 50
rubric:
-
    name: Health System
    points: 5
    description: Display and track a player health metric
-
    name: New Mechanic
    points: 5
    description: Add a new mechanic to the player character
-
    name: Implement Enemies
    points: 10
    description: Implement all enemies as described in the MP spec
-
    name: Create New Enemy Type
    points: 5
    description: Design and implement another enemy type of your design
-
    name: Level Layout
    points: 5
    description: Create a level layout that can be traversed in 5 minutes and has a level complete screen
-
    name: Enemies
    points: 5
    description: Strategically place all enemy types throughout the level
-
    name: Collectibles
    points: 5
    description: Place collectible objects around the level and display them on the UI
-
    name: Design Document
    points: 10
    description: Submit a document that explains your level design and design decisions
---
![Matrix](https://github.com/illinois-cs498gd/illinois-cs498gd.github.io/raw/main/img/platform.PNG){:width="800px"}
# MP 2: Level Design
Your second MP is all about level design and all the important factors that go in to it. In this MP we will touch on player abilities, level layouts, and enemy AI.

To start you off we will need you to get familiar with the basics of how the level editor works in Unreal. We would recommend you complete the tutorial found here in order to do so:<br/><br/>
[Tutorial Link](https://docs.unrealengine.com/4.27/en-US/BuildingWorlds/LDQuickStart/)
<br/>
Once you have done that you can continue on to the main assignment.

Your objective with this assignment is to design and create your own 3D platformer level. You will be provided with a player character and you are going to place assets, add mechanics, and create enemies for that character to interact with.

The basic player controller along with a large number of assets you may want to use are found here: <br/><br/>
[Assets Link](https://www.unrealengine.com/marketplace/en-US/product/unreal-learning-kit-games)<br/>
It will say it only is updated for 4.26, just open it with 4.27 and it will work fine.

The character controller you will be using is under `BP_LearningKit_PlayerCharacter`.

## Part 1: Update Your Character
The first thing you need to do is update your character. You need to do this in two ways.

### **Add a Health System**
This should be very similar to the system used in the first MP. It should have a bar displayed somewhere on the screen, and a game over screen should be displayed if it reaches 0. You should also make an item that can be placed in the world and picked up to restore health. This item should be destroyed on collection. There are several given assets that could work well for this but you can use whatever you want.

### **Add a New Mechanic to the Player Character**
This can be basically anything you want. An ability to attack, a grapple hook, a roll. It should be similar in complexity to the flight mechanic the character controller already has.

## Part 2: Make Some Enemies
We need obstacles to fill our level. So lets make some enemies. You will be making 4 distinctly different enemy types.
<br/>
### **Enemy Behavior**

All enemies should do the following:
-	Be destroyed when the players collides with their “head” (the top of whatever model you decide to use)
-	Reduce the players health on collision with any part that is not the head
-	Knock the player back and remove player control for a short duration after a health reducing collision


### **Enemy Types**

You will create the following types of enemies

#### **The Pursuer** 
The Pursuer should:
-	Have a looping patrol path that it follows
-	Run at the player when they get within a moderate distance of each other, and they have line of sight with each other
-	Within reason, return to its patrol path if the player gets too far away (this should be done by the enemy moving, not teleportation)

#### **The Flyer**
The Flyer should:
-	Fly at a specific height above the player
-	Move to a new location ever few seconds, trying to keep some distance between itself and the player (the exact form of this is up to you)
-	Launch projectiles that lead the players movements (by lead we mean travel to where the player is going to, not where they are)
-	The projectiles should reduce the players health on collision

#### **The Mortar** 
The Mortar should:
-	Be an unmoving enemy placed on the ground
-	Randomly launch projectiles above and around it in an arc
-	The projectiles should cause a small explosion on collision with other objects
-	The explosions should knock back and reduce the players health on collision

#### **Your Own Enemy**
Create an enemy of your own design. It should have similar complexity to the other three and also be distinct and take on a different role.

You can use any assets you want for the enemies and their projectiles. Simple shapes will do as long as each enemy is visually distinct.

## Part 3: Putting It All Together 
The last step of the MP is to put it all together and make a platforming level.

Your level should:
- Be completable in around 5 minutes
- Present some degree of challenge
- Return the player to their start location when their health is reduced to zero or if they fall off the map
- Display a level complete screen upon reaching the end of the level
- Utilize all the created enemies in a way that contributes to the design
- Have health pick ups scattered around the level
- Have floating collectibles scattered around the level to guide the player and encourage them to explore
- You can use any asset you want for these, and there are several included in the given assets
- These objects should be destroyed on collection, and the number collected should be displayed some where on the UI
- The design of the level should specifically take into account the flight mechanic, the mechanic you created, and your enemy design

As far as environmental and visual assets, you can use any of the provided, built in, or any other assets in your level creation. Feel free to work in the provided project or in your own new project.

# Additional Submission Instructions
In addition to usual instructions below, you should also submit a short written document, either pdf or docx format, explaining your process for designing your level. It should be at most a page long. It should explain how you went about the design process and how your design had to accommodate the new mechanic and enemy you created.
