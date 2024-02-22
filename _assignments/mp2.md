---
layout: assignment
title: "Level Design"
index: 10
due: "<br/>
      Part 1: Feb 15, 2023 @  5PM<br/>
      Part 2: Feb 27, 2023 @  5PM"
material: ~
points: 100
rubric:
-
    name: Health System
    points: 10
    description: Display and track a player's health metric
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
MP2 is all about level design and all the important factors that go into it. In this MP we will touch on player abilities, level layouts, and enemy AI. The objective of this assignment is to allow students to design and create their own 3D platformer level. You will be provided with a player character, and you will need to place assets, add mechanics, and create enemies for the player character to interact with.

**This MP is split into two parts**:<br/><br/>

**Part 1** covers creating the map, health system, collectibles, and Pursuer enemy type.
**It is due Feb. 15 at 5pm. It is worth 10% of the total MP grade and is only graded for completion...there is no partial credit. If you do not submit on time and with all the required features working, you total MP will at most be 90% of the total points obtainable.** 
<br/><br/>
**Part 2** covers creating the Mortar and custom enemies, as well as handling player-enemy collisions and putting the level all together.
**It is due Feb. 27 at 5pm. It will be graded according to the MP rubric with partial credit.** 
<br/><br/>
**Please pay close attention to the guidelines about recording the video for submission:
[Video Guidelines Link](https://docs.google.com/document/d/1QY5t2wU9_6I7t4b-jneDRa7grhtQdSITzaOXVh-YKrA/edit?usp=sharing)<br/>
 If you do not follow the guidelines and your submission is hard to grade you may lose points.**

To start, you should get familiar with the basics of how the level editor works in Unreal. We recommend you complete the tutorial found here:
[Tutorial Link](https://docs.unrealengine.com/4.27/en-US/BuildingWorlds/LDQuickStart/). Once you have familiarized yourself with the level editor in Unreal, you may continue onto the main assignment. 

**Please read through the entire assignment spec before starting to get a better understanding of all the requirements.**

## Part 1: Player Character, Health System, Collectibles, and Pursuer Enemy (Due Feb. 14)
### Step 1: Setup the Map and Player Character
To start, import the [Unreal Learning Kit](https://www.unrealengine.com/marketplace/en-US/product/unreal-learning-kit) into your Unreal Engine. You will find that the basic player controller along with a large number of assets you may want to use are already included and preset in the kit. Construct a new platform level. Leave the map relatively blank for now, as you will gradually add components later on.

The character controller you will be using is under `BP_LearningKit_PlayerCharacter`.

### Step 2: Add a Health System
The Health System for this MP should be very similar to the one you created in the MP1. 

Your Health System should include:
* a Health Bar displayed somewhere on the screen
* a Game Over screen when the player's health reaches 0
* health packs scattered around the level that upon collection will be destroyed and increase the player's health

### Step 3: Create Collectible Items
Next, you will need to place floating collectible items across the map to guide the player and encourage them to explore. To represent being collected, the collectibles should be destroyed when the player collides with them. You should add a Score system to your game, so that upon collection of a collectible, the player's score increases. The Unreal Learning Kit includes several assets that could work well as a collectible but feel free to also upload or create your own asset.

### Step 4: Create a Pursuer enemy
The Pursuer should:
-	Follow a patrol path between random locations around the starting point
-	Run at the player when the player is at a moderate distance within the line of sight of the Purser
-	Return to its patrol path if the player gets too far away (this should be done by the enemy moving, not teleportation)

## Tutorial to help get you started on the Pursuer enemy type:
    
*NOTE: This tutorial covers the basics for implementing the Pursuer starting from the UnrealLearningKit starter project. It does not cover all the requirements for the chaser. Use intuition, creativity, and other online tutorials to aid in completing all the requirements!*

### **Step 1: Create the AI Controller**
*Unlike the player character that is controlled by an input device (i.e. keyboard and mouse, Xbox controller, etc.), the Pursuer will be controlled by an 'AI controller'. This allows us to specify in code how we wish the Pursuer to behave. To do this, we will create an 'AI Controller' object to control the actions of the Pursuer enemy.*

In the Content Drawer (Bottom left), click Add > Blueprint Class > (type into "All Classes") > AIController and save the controller with the name 'Pursuer_AIController'. 

<img src="../img/assignments/mp2/pursuer tutorial/step1.png" alt="drawing" width="400"/>

### **Step 2: Create the AI Character**
*Both the player characters and the AI character use the 'Character' blueprint. As explained above, the main difference is that it will be controlled by the 'AI Controller'. This 'Character' blueprint will connect the model geometry, animations, code for the behaviors, senses, and more.*

In the Content Drawer, go to Add > Blueprint Class > Character and save the AI character with the name 'BP_Pursuer'. Open its blueprint editor. Inside the "Components" panel (top left), select the "Mesh" component. For starters, set the following properties in the Details panel (right):
* Skeletal Mesh: SK_EpicCharacter
* Anim Class: EpicCharacter_AnimBP_C

<img src="../img/assignments/mp2/pursuer tutorial/step2.png" alt="drawing" width="400"/>

This can be changed later to whatever mesh/animations you like later!

Add a "CapsuleComponent" in the Components panel (top left). By default, the mesh will not be inside of the capsule. Adjust the Z position and scale of the character mesh so that it fits right within the borders of the capsule. This can be done using the arrow gizmos (the 3 red, blue, and green perpendicular arrows) or adjusting the transform values in the details panel (right)  to roughly -80 for Z position and 0.85 for scale.

<img src="../img/assignments/mp2/pursuer tutorial/step2b.png" alt="drawing" width="200"/>

Finally, select "AICharacter (self)" on the Components panel (left), then in the Details panel (right) set its "AI Controller Class" to the AI controller ('Pursuer_AIController') you created in step 1.

<img src="../img/assignments/mp2/pursuer tutorial/step2c.png" alt="drawing" width="400"/>

### **Step 3: Add Pawn Sensing**
*For the Pursuer to start chasing the player when it is nearby, we will add Pawn Sensing to the enemy so that it can sense the location of the player.*

Remaining in the 'BP_Pursuer' blueprint, select Add > PawnSensing in the Components tab on the top left. See below for how the component hierarchy should look in 'BP_Pursuer' after this step.

<img src="../img/assignments/mp2/pursuer tutorial/step3.png" alt="drawing" width="400"/>

### **Step 4: Add random movement to the AI Character**
*Now we will add the code into our Pursuers blueprint to move. This will create the behavior of continuously roaming the map.*

In the Event Graph of 'BP_Pursuer', add a custom event titled 'Roam' and use the "AI MoveTo" method to move the character to a random location. 

To create a custom event, right-click on the event graph, search and select "Add Custom Event" in the pop-up tab and name the event "Roam". This custom event will be called within the BP_Pursuer event graph whenever we want the Pursuer to roam.

<img src="../img/assignments/mp2/pursuer tutorial/step4a.png" alt="drawing" width="400"/>

Add an "AI MoveTo" block to the event and use the method "GetRandomReachablePointInRadius" to set the destination. 

Since we want the AI Character to keep roaming, add a slight delay after the custom method and call Roam again to create a loop. Here is how the event graph should look: 

<img src="../img/assignments/mp2/pursuer tutorial/step4b.png" alt="drawing" width="800"/>

Call the custom Roam event from Event BeginPlay. 

<img src="../img/assignments/mp2/pursuer tutorial/step4c.png" alt="drawing" width="400"/>

### **Step 5: Add the Nav Mesh**
*The pursuer needs to know what places in the level it can and cannot walk on. To do this, we define the area our AI Character can roam in by adding a navigation mesh bounds volume to the level.*

Return to the level map window. From the Content Drawer, drag and drop 'BP_Pursuer' into the level map. Then, navigate to the + icon on the top left and select Volumes > NavMeshBoundsVolume.

<img src="../img/assignments/mp2/pursuer tutorial/step5a.png" alt="drawing" width="800"/>

A Nav Mesh indicates the area where AIs can be activated, so make sure the Nav Mesh is large enough to encapsulate the area you want the enemies to move around in. To visualize the navigable area inside of the NavMeshBoundsVolume, press "P" on your keyboard. This will highlight all surfaces that the AI character can be navigated to in green.

<img src="../img/assignments/mp2/pursuer tutorial/step5b.png" alt="drawing" width="600"/>

### **Step 6: Create a Chase Player Event**
*We will use the same logic from “Roam” to initiate a "Chase Player" event.*

Create a new custom event titled "Chase Player".

From the Chase Player event, add an "AI MoveTo" block and set the Target Actor to the Player Character. Like in the Roam event, add a "Delay" block from "On Success" and call "Chase Player" again after the delay has completed. 

<img src="../img/assignments/mp2/pursuer tutorial/step6.png" alt="drawing" width="800"/>

To test, replace "Roam" in "Event Begin Play" with "Chase Player", compile the file, and run the game.

### **(OPTIONAL) Step 7: Add Enemy Functionality Upon Chase Event**
*We will show you how to cause the enemy to blow up with a sound and particle effect upon collision with the player character.*

Break the link between "AI MoveTo" and "Delay". Insert a "Spawn Emitter at Location" block on success of the "AI MoveTo". Next, connect a "Play Sound at Location" block and a "Destroy Actor" block. 

Connect "Get Actor Location" to the "Location" node for both "Spawn Emitter at Location" and "Play Sound at Location".

You will need to add particle effects and sounds to your project. Select your desired particle effect asset in the dropdown menu under "Emitter Template" on the "Spawn Emitter at Location" block. Select your desired sound asset under "Sound" on the "Play Sound at Location" block.

<img src="../img/assignments/mp2/pursuer tutorial/step7.png" alt="drawing" width="800"/>

### **(OPTIONAL) Step 8: Apply Damage**
Insert an "Apply Damage" block between the "AI MoveTo" and "Spawn Emitter at Location" blocks.

Set the "Damaged Actor" node to "Get Player Character". Play around with the different damage parameters to get your desired effect.

<img src="../img/assignments/mp2/pursuer tutorial/step8.png" alt="drawing" width="600"/>

[Check out this tutorial on how to use the damage system/events](https://www.youtube.com/watch?v=vO1i9Wcx4Xc)

### **Step 9: Create an Enumerator Class**
*We can create an enumerator class to help us control the behaviors of our AI Character.*

In the Content Drawer, within the AI folder, create a Blueprint Enumeration class. This class will define what state our AI is in (ChasePlayer or Roam). Name this class "EAIState".

<img src="../img/assignments/mp2/pursuer tutorial/step9a.png" alt="drawing" width="400"/>

Add three enumerators: 'Default', 'Roam', and 'Chase Player'. 

<img src="../img/assignments/mp2/pursuer tutorial/step9b.png" alt="drawing" width="600"/>

In the AICharacter class, create a variable called "AIState" of type "EAIState". Make the variable public by clicking on the eye icon on the right. 

<img src="../img/assignments/mp2/pursuer tutorial/step9c.png" alt="drawing" width="400"/>

Remove the connection between "Event BeginPlay" and "ChasePlayer". Drag from "Event BeginPlay" and type "Switch on EAIState". The AIState variable will be connected to the "Selection" node on "Switch on EAIState". 

Attach a 'Roam' event block to the 'Roam' node and a 'Chase Player' block to 'Chase Player'.

<img src="../img/assignments/mp2/pursuer tutorial/step9d.png" alt="drawing" width="600"/>

In the viewport, click on your AI Character and specify the default "AIState" as 'Roam'. Default states are unique to each character, so you can create multiple AI characters, some with the default set to Roam and some with the default set to Chase Player.

<img src="../img/assignments/mp2/pursuer tutorial/step9e.png" alt="drawing" width="800"/>

#### Note on Behavior Trees
Alternatively, students may implement the AI Character using Behavior Trees in Unreal. There are many resources available online for how to use Behavior Trees. And here are a few slides on [Using AI in Unreal](https://docs.google.com/presentation/d/1tsbdJHC0r5w-sF30vuK8PuOIJsRZvvv3xJhFrFzT600/edit?usp=sharing). However, this feature is more high-level and may be tougher to debug, so if you feel more comfortable working with blueprints, we recommend simply calling the Roam and Chase events from within the Pursuer blueprint.

### **Additional Resources**

In addition to the instructions above, the following set of tutorials may be helpful to you: 
* [Unreal Engine 4 - AI Roam](https://www.youtube.com/watch?v=eBjtKsgurLU) 
* [Unreal Engine 4 - AI Chase Player](https://www.youtube.com/watch?v=HK3FAbIkJ-g)
* [Create A Platformer Pt 4: Chasing Knockback Enemy! UE4 Tutorial](https://www.youtube.com/watch?v=4UsaiOEr6Bw)
* [Unreal Engine 5 Tutorial - AI Part 1: Character Setup](https://youtu.be/IDZh0epFTRY?si=iQheKNeQNEnvbBNG)
* [Using AI in Unreal](https://docs.google.com/presentation/d/1tsbdJHC0r5w-sF30vuK8PuOIJsRZvvv3xJhFrFzT600/edit?usp=sharing)

**End of Pursuer tutorial.**

## Part 2: Mortar Enemy, Custom Enemy, Player-Enemy Collisions, Completing the Level (Due Feb. 24)

### Step 1: Create a Mortar enemy
The Mortar should:
-	Be an unmoving enemy placed on the ground
-	Randomly launch projectiles above and around it in an arc **affected by gravity**
-	The projectiles should cause a small explosion on collision with other objects
-	The explosions should knock back and reduce the player's health on collision (**the explosion does not need to have any other effect...e.g. it does not affect the terrain**)

### Step 2: Create your own enemy
Create an enemy of your own design. It should have a similar complexity to the other two enemies and also be distinct and take on a different role. Please discuss your design in your design document.

You can use any assets you want for the enemies and their projectiles. Simple shapes will do as long as each enemy is visually distinct.

### Step 3: Add Player-Enemy collision behaviors
All three enemy types should display the same behaviors upon colliding with the player character. 

There will be two different types of collision behaviors:
* Collision with the enemy's "head" (or the top of whichever model you decide to use)
    * Destroy the enemy
* Collision with any other part of the enemy
    * Reduce the player's health
    * Knock the player back a small but noticeable distance
    * Remove player control for a short duration of time

### Step 4: Putting It All Together
The last step of the MP is to put it all together and make a platforming level. Your level should present some degree of challenge for the player and **take around 5 to 10 minutes to complete**. 

Your final level should:
- Have health packs scattered around the level that increase the player's health when collected
- Have floating collectibles scattered around the level that are destroyed when collected and increase the player's score
- Integrate all three enemy types into the design of the level
- Display a Game Over screen when the player's health is reduced to 0 or the character falls off the map
- Display a Level Complete screen when the player reaches the end of the level
- Allow the player to restart the level after a win/loss, which returns the player to the starting location and resets all the level's components

As far as environmental and visual assets go, you may use any of the provided, built-in, or any other assets in your level creation. Feel free to work in the provided project or in your own new project. **The level layout, enemies, and collectibles portions of the rubric are all a part of the level design. Your level should be somewhat challenging, the player should have to interact with enemies, and there should be some exploring required to find the collectibles.** If any of these things aren't the case, you'll lose significant points from those portions of the rubric. Make sure that your level isn't just the tutorial level!

### **Hints for Common Bugs**

* If the projectile is going through instead of colliding with the ground, make sure that both the projectile and map collisions are set to `BlockAllDynamic` in their Details panel
* If you are having trouble setting up collisions with static meshes, [check out this tutorial](https://docs.unrealengine.com/5.0/en-US/setting-up-collisions-with-static-meshes-in-unreal-engine/)
* If you are having trouble with character knockback, [check out this thread](https://forums.unrealengine.com/t/character-knockback/300225/3)
* If you are having trouble with importing your own character and animations into UE5, [check out this tutorial](https://youtu.be/PyXeB1QtC0A?si=9W59r_W1Gn40cJfo)
    

# Additional Submission Instructions
## For Part 1
**Just submit a demo video and link to repo/ drive folder containing your code.**

## For Part 2 
Submit a demo video and link to repo/ drive folder containing your code.<br/><br/>
In addition, you should also submit a short written document, either pdf or docx format, explaining your process for designing your level. It should be at most a page long. It should explain how you went about the level design process and how your level design had to accommodate the new mechanic and enemy you created. For example, you could talk about why you placed your custom enemy or collectibles in certain parts of the level. Please also record your video according to [this guideline](https://docs.google.com/document/d/1QY5t2wU9_6I7t4b-jneDRa7grhtQdSITzaOXVh-YKrA/edit?usp=sharing).
