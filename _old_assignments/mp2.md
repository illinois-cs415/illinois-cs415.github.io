---
layout: assignment
title: "Level Design"
index: 10
due: "Oct 6, 2023 @ 11:59 PM"
material: ~
points: 100
rubric:
-
    name: Health System
    points: 10
    description: Display and track a player health metric
-
    name: Implement the Pursuer Enemy
    points: 10
    description: Implement the Pursuer enemy described in the MP spec
-
    name: Implement the Mortar Enemy
    points: 15
    description: Implement the Mortar enemy described in the MP spec
-
    name: Create New Enemy Type
    points: 15
    description: Design and implement another enemy type of your design
-
    name: Level Layout
    points: 10
    description: Create a level layout that can be traversed in 5 minutes and has a level complete screen
-
    name: Enemies
    points: 10
    description: Strategically place all enemy types throughout the level
-
    name: Collectibles
    points: 10
    description: Place collectible objects around the level
-
    name: Design Document
    points: 15
    description: Submit a document that explains your level design and design decisions
-
    name: Video
    points: 5
    description: Submit a link to a video demo of your game
---
![Matrix](https://github.com/illinois-cs498gd/illinois-cs498gd.github.io/raw/main/img/platform.PNG){:width="800px"}
# MP 2: Level Design
Your second MP is all about level design and all the important factors that go in to it. In this MP we will touch on player abilities, level layouts, and enemy AI.

**Please pay close attention to the guidelines about recording the video for submission:<br/>
 [Video Guidelines Link](https://docs.google.com/document/d/1QY5t2wU9_6I7t4b-jneDRa7grhtQdSITzaOXVh-YKrA/edit?usp=sharing)<br/>
 If you do not follow the guidelines and your submission is hard to grade you may lose points.**

To start you off we will need you to get familiar with the basics of how the level editor works in Unreal. We would recommend you complete the tutorial found here in order to do so:
[Tutorial Link](https://docs.unrealengine.com/4.27/en-US/BuildingWorlds/LDQuickStart/)
<br/>
Once you have done that you can continue on to the main assignment. Please read through the entire assignment spec before starting so that you can get a better understanding of the requirements.

Your objective with this assignment is to design and create your own 3D platformer level. You will be provided with a player character and you are going to place assets, add mechanics, and create enemies for that character to interact with.

The basic player controller along with a large number of assets you may want to use are found here:
[Assets Link](https://www.unrealengine.com/marketplace/en-US/product/unreal-learning-kit)<br/>

The character controller you will be using is under `BP_LearningKit_PlayerCharacter`.

## Part 1: Update Your Character
The first thing you need to do is update your character as follows.

### **Add a Health System**
This should be very similar to the system used in the first MP. It should have a bar displayed somewhere on the screen, and a game over screen should be displayed if it reaches 0. You should also make an item that can be placed in the world and picked up to restore health. This item should be destroyed on collection. There are several given assets that could work well for this but you can use whatever you want.

## Part 2: Make Some Enemies
We need obstacles to fill our level. So lets make some enemies. You will be making 3 distinctly different enemy types.
<br/>
### **Enemy Behavior**

All enemies should do the following:
-	Be destroyed when the players collides with their “head” (the top of whatever model you decide to use)
-	Reduce the players health on collision with any part that is not the head
-	Knock the player back and remove player control for a short duration after a health reducing collision

### **Enemy Types**

You will implement all three types of enemies

#### **The Pursuer**
The Pursuer should:
-	Have a looping patrol path that it follows
-	Run at the player when they get within a moderate distance of each other, and they have line of sight with each other
-	Within reason, return to its patrol path if the player gets too far away (this should be done by the enemy moving, not teleportation)

Here is a tutorial to help get you started on the Pursuer enemy type:
[Tutorial Link](https://drive.google.com/file/d/1zoJnzQR6WuSpxx6g3fdB4aDGg7fbOIke/view?usp=sharing)
<br/>

#### **The Mortar**
The Mortar should:
-	Be an unmoving enemy placed on the ground
-	Randomly launch projectiles above and around it in an arc **affected by gravity**
-	The projectiles should cause a small explosion on collision with other objects
-	The explosions should knock back and reduce the players health on collision **the explosion does not need to have any other effect...e.g. it does not effect the terrain.**

#### **Your Own Enemy**
Create an enemy of your own design. It should have similar complexity to the other two and also be distinct and take on a different role. If you'd like your enemy to have different , please talk about why in your design document.

You can use any assets you want for the enemies and their projectiles. Simple shapes will do as long as each enemy is visually distinct.

## Part 3: Putting It All Together
The last step of the MP is to put it all together and make a platforming level.

Your level should:
- **Take around 5 minutes to play completely**
- Present some degree of challenge
- Return the player to their start location when their health is reduced to zero or if they fall off the map and reset score to 0
- Display a level complete screen upon reaching the end of the level
- Utilize both the created enemies in a way that contributes to the design
    - The design of the level should specifically take into account your enemy design.
- Have health pick ups scattered around the level
- Have floating collectables scattered around the level to guide the player and encourage them to explore
    - You can use any asset you want for these, and there are several included in the given assets
    - These objects should be destroyed on collection and should effect player score

As far as environmental and visual assets, you can use any of the provided, built in, or any other assets in your level creation. Feel free to work in the provided project or in your own new project. **The level layout, enemies, and collectables portions of the rubric are all a part of the level design. Your level should be somewhat challenging, the player should have to interact with enemies, and there should be some exploring required to find the collectables."** If any of these things aren't the case, you'll lose significant points from those portions of the rubric. Make sure that your level isn't just the tutorial level!

# Additional Submission Instructions
In addition to usual instructions below, you should also submit a short written document, either pdf or docx format, explaining your process for designing your level. It should be at most a page long. It should explain how you went about the level design process and how your level design had to accommodate the new mechanic and enemy you created. For example, you could talk about why you placed your custom enemy or collectables in certain parts of the level. Please also record your video according to [this guideline](https://docs.google.com/document/d/1QY5t2wU9_6I7t4b-jneDRa7grhtQdSITzaOXVh-YKrA/edit?usp=sharing).
