---
layout: assignment
title: "Level Design"
index: 10
due: "Part 1: Feb 14, 2023 @  5PM<br/>
      Part 2: Feb 24, 2023 @  5PM"
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
MP2 is all about level design and all the important factors that go into it. In this MP we will touch on player abilities, level layouts, and enemy AIs. The objective of this assignment is to allow students to design and create their own 3D platformer level. You will be provided with a player character, and you will need to place assets, add mechanics, and create enemies for the player character to interact with.

**This MP is split into two parts**: Part 1 covers creating the map, health system, collectibles, and Pursuer enemy type.
**It is due Feb. 14 at 5pm. It is worth 10% of the total MP grade and is only graded for completion...there is no partial credit. If you do not submit on time and with all the required features working, you total MP will at most be 90% of the total points obtainable.** 
Part 2 covers creating the Mortar, Custom Enemy, and putting the level all together.
**It is due Feb. 24 at 5pm. It will be graded according to the MP rubric with partial credit.** 

**Please pay close attention to the guidelines about recording the video for submission:
[Video Guidelines Link](https://docs.google.com/document/d/1QY5t2wU9_6I7t4b-jneDRa7grhtQdSITzaOXVh-YKrA/edit?usp=sharing)<br/>
 If you do not follow the guidelines and your submission is hard to grade you may lose points.**

To start, you should get familiar with the basics of how the level editor works in Unreal. We recommend you complete the tutorial found here:
[Tutorial Link](https://docs.unrealengine.com/4.27/en-US/BuildingWorlds/LDQuickStart/). Once you have familiarized yourself with the level editor in Unreal, you may continue onto the main assignment. 

**Please read through the entire assignment spec before starting to get a better understanding of all the requirements.**

## Part 1: Player Character, Health System, Collectibles, and Pursuer Enemy (Due Feb. 14)
### Step 1: Setup the Map and Player Character
To start, import the [Unreal Learning Kit](https://www.unrealengine.com/marketplace/en-US/product/unreal-learning-kit) into your Unreal Engine. The kit contains a basic player character controller `BP_LearningKit_PlayerCharacter` along with a large number of assets you may want to use to construct your level. 

Next, setup the map for your platformer level. You may either create a new blank map and build from scratch or use the provided showcase map as a template and modify it to fit the complexity of your final game. The map should involve some platform(s) suspended in the air (game over if the player falls off).

Finally, add code to prompt a Game Over screen when the player falls off the map. For example, you can add a box collision component at some z position below the platform that will trigger the Game Over screen when the player collides with it.

### Step 2: Add a Health System
The Health System for this MP should be very similar to the one you created in the MP1. 

Your Health System should include:
* a Health Bar displayed somewhere on the screen
* a Game Over screen when the player's health reaches 0
* health packs scattered around the level that upon collection will be destroyed and increase the player's health

### Step 3: Add Collectible Items and a Score system
Next, place floating collectible items across the map to guide the player and encourage them to explore. The collectibles should be destroyed when the player collects (collides) them. The Unreal Learning Kit includes several assets that could work well as a collectible but feel free to upload or create your own asset.

In addition, add a Score system to your game so that the player's score increases when collectibles are collected.

### Step 4: Create a Pursuer enemy
The Pursuer should:
-	Follow a patrol path between multiple locations on the map
-	Run at the player when the player is at a moderate distance within the line of sight of the Purser
-	Return to its patrol path if the player gets too far away (this should be done by the enemy moving, not teleportation)

In addition, implement the following for collisions between the player and Pursuer:
* A player collision with the Pursuer's head should destroy the Pursuer
* A player collision with any other part of the Pursuer's body should:
    * Reduce the player's health
    * Knock the player back a small distance
    * Remove the player's control (key inputs disabled) for a short duration of time

<details><summary markdown="span">Click the arrow to see a tutorial to help get you started on the Pursuer enemy type:</summary>
    
***NOTE: This tutorial covers the basics for implementing the Pursuer with the Unreal Learning Kit. It DOES NOT cover all the requirements for the Pursuer! Use intuition, creativity, and other online tutorials to aid in completing all the requirements!***

### Step 1: Add a Nav Mesh
In the level map window, navigate to the + icon on the top left and select Volumes > NavMeshBoundsVolume.

<img src="../img/assignments/mp2/pursuer%20tutorial/step5a.png" alt="drawing" width="800"/>

The Nav Mesh indicates the area where AIs can be activated, so make sure the Nav Mesh is large enough to encapsulate the area you want the enemies to move around in. To visualize the navigable area inside of the NavMeshBoundsVolume, press "P" on your keyboard. This will highlight in green all surfaces that the AI character can be navigated to.

<img src="../img/assignments/mp2/pursuer%20tutorial/step5b.png" alt="drawing" width="600"/>

### Step 2: Create the AI Controller
*Unlike the player character which is controlled by an input device (i.e. keyboard and mouse, Xbox controller, etc.), the Pursuer will be controlled by an AI controller. This allows us to specify in code how we wish the Pursuer to behave. To do this, we will create an AI Controller object to control the actions of the Pursuer enemy.*

In the Content Drawer (Bottom left), create a new folder "AI", which will contain all the files related to the AI Enemies. Once within the folder, click Add > Blueprint Class > (type into "All Classes") > AIController and save the controller with the name `Pursuer_AIController`. 

<img src="../img/assignments/mp2/pursuer%20tutorial/step1.png" alt="drawing" width="800"/>

### Step 3: Create the Pursuer AI Character
*Both the player character and AI character use the Character blueprint, but the main difference is that the AI character is controlled by the AI Controller. The Character blueprint will connect the model geometry, animations, code for the behaviors, senses, and more.*

In the Content Drawer within the AI folder, go to Add > Blueprint Class > Character, save it with the name `BP_Pursuer`, and open the file in the blueprint editor. 

At the top left, find the "Components" panel and select the "Mesh" component. You should see the Details panel on the right containing parameters for the Mesh. If you do not see the Details panel, select Window > Details near the top of your screen to display the panel.

Scroll through the Details to find and set the following properties:
* Skeletal Mesh: SK_EpicCharacter
* Anim Class: EpicCharacter_AnimBP_C

<img src="../img/assignments/mp2/pursuer%20tutorial/step2.png" alt="drawing" width="400"/>

You may also use your own mesh and animations for the Pursuer.

Again, navigate to the Components panel and add a "CapsuleComponent". By default, the mesh will not be inside the capsule. Adjust the Z position and scale of the components so that the character mesh fits right within the borders of the capsule. This can be done using the arrow gizmos (the 3 red, blue, and green perpendicular arrows) or adjusting the transform values in the Details panel. In addition, adjust the rotation of the character mesh so that it faces the direction of the light blue arrow (specifies the movement direction) pointing out from the middle of the capsule.

<img src="../img/assignments/mp2/pursuer%20tutorial/step2b.png" alt="drawing" width="200"/>

Finally, select "AICharacter (self)" on the Components panel, then in the Details panel, set "AI Controller Class" to the AI controller `Pursuer_AIController` you created in step 1.

<img src="../img/assignments/mp2/pursuer%20tutorial/step2c.png" alt="drawing" width="400"/>

To add the Pursuer to your game, return to the main window, and from the Content Drawer, drag and drop `BP_Pursuer` into the viewport and adjust its position accordingly.

### Step 4: Add random movement to the Pursuer

**Note: The Roam event is only for showing you how to implement movement in AI Characters. You will need to modify this to make a Patrol event for the final product.**

First, we will need to create a new Roam event. In the Event Graph of `BP_Pursuer`, right-click and search for "Add Custom Event" in the pop-up tab. Name the new custom event "Roam". We will call "Roam" within the `BP_Pursuer` event graph whenever we want the Pursuer to roam.

<img src="../img/assignments/mp2/pursuer%20tutorial/step4a.png" alt="drawing" width="400"/>

Add an "AI MoveTo" block to the event and use the method "GetRandomReachablePointInRadius" to set the destination. This will move the Pursuer to the randomly selected location. Add a slight delay and call Roam again to create a continuous loop of roaming. The final Roam event graph should look: 

<img src="../img/assignments/mp2/pursuer%20tutorial/step4b.png" alt="drawing" width="800"/>

Call the custom Roam event from Event BeginPlay. Compile the file and play your game test that the Pursuer now roams.

<img src="../img/assignments/mp2/pursuer%20tutorial/step4c.png" alt="drawing" width="400"/>

### Step 5: Create a Chase Player Event
Create a new custom event titled "Chase Player". Like before, add an "AI MoveTo" block to the event, but this time instead of setting the destination to a random location, set the "Target Actor" to the Player Character. Again, add a delay from "On Success" and call "Chase Player" after the delay has completed to make the Pursuer continuously chase the player.

<img src="https://github.com/illinois-cs415/illinois-cs415.github.io/blob/mp2-sp24-update/img/assignments/mp2/pursuer%20tutorial/step6.png" alt="drawing" width="800"/>

To test, replace "Roam" in "Event Begin Play" with "Chase Player", compile the file, and run the game.

### Step 6: Apply Damage upon a Successful Chase Event
Break the link between "AI MoveTo" and "Delay". Insert an "Apply Damage" block after "On Success" of "AI MoveTo". 

Set "Damaged Actor" to the player character to apply damage on the player. You will also need to set up Event AnyDamage in `BP_Pursuer`. Check out [this tutorial](https://www.youtube.com/watch?v=vO1i9Wcx4Xc) on how to use the damage system/events.

<img src="https://github.com/illinois-cs415/illinois-cs415.github.io/blob/mp2-sp24-update/img/assignments/mp2/pursuer%20tutorial/step8.png" alt="drawing" width="600"/>

### (OPTIONAL) Step 7: Add Sound and Visual Effects Upon Successful Chase Event
First, download and add some particle effect and sound assets to your project. You can easily find and import asset kits in the Marketplace tab within the Epic Games Launcher. 

Insert "Spawn Emitter at Location" and "Play Sound at Location" blocks after "On Success" of "AI MoveTo". Connect "Get Actor Location" to the "Location" for both blocks.

Select your desired particle effect asset in the dropdown menu under "Emitter Template" on the "Spawn Emitter at Location" block. Select your desired sound asset under "Sound" on the "Play Sound at Location" block.

<img src="https://github.com/illinois-cs415/illinois-cs415.github.io/blob/mp2-sp24-update/img/assignments/mp2/pursuer%20tutorial/step7.png" alt="drawing" width="800"/>

### Step 8: Create an Enumerator Class
*We can create an enumerator class to help us keep track of the state of the Pursuer. Note that updating the value of AI State only changes the variable value. To update the character's behavior, you will still need to call the event.*

In the Content Drawer within the AI folder, create a Blueprint Enumeration class. This class will define what state our AI is in (ChasePlayer or Roam). Name this class "EAIState".

<img src="https://github.com/illinois-cs415/illinois-cs415.github.io/blob/mp2-sp24-update/img/assignments/mp2/pursuer%20tutorial/step9a.png" alt="drawing" width="400"/>

Add two enumerators: `Roam` and `Chase Player`. 

<img src="https://github.com/illinois-cs415/illinois-cs415.github.io/blob/mp2-sp24-update/img/assignments/mp2/pursuer%20tutorial/step9b.png" alt="drawing" width="600"/>

In `BP_Pursuer`, create a new variable called `AIState` of type "EAIState". Make the variable public by clicking on the eye icon on the right. 

<img src="https://github.com/illinois-cs415/illinois-cs415.github.io/blob/mp2-sp24-update/img/assignments/mp2/pursuer%20tutorial/step9c.png" alt="drawing" width="400"/>

Remove the connection between "Event BeginPlay" and "ChasePlayer". Drag from "Event BeginPlay" and type "Switch on EAIState". The AIState variable will be connected to the "Selection" node on "Switch on EAIState". 

Attach a 'Roam' event block to the 'Roam' node and a 'Chase Player' block to 'Chase Player'.

<img src="https://github.com/illinois-cs415/illinois-cs415.github.io/blob/mp2-sp24-update/img/assignments/mp2/pursuer%20tutorial/step9d.png" alt="drawing" width="600"/>

In the viewport, click on your Pursuer and specify the default "AIState" as 'Roam' in Details. Note that the default state is unique to each instance, so you can add multiple Pursuers to your map, some with the default set to Roam and some with the default set to Chase Player.

<img src="https://github.com/illinois-cs415/illinois-cs415.github.io/blob/mp2-sp24-update/img/assignments/mp2/pursuer%20tutorial/step9e.png" alt="drawing" width="800"/>

### Step 9: Add Pawn Sensing
In the Components panel of `BP_Pursuer`, add a "PawnSensing" element. See below for how the component hierarchy should look in `BP_Pursuer` after this step.

<img src="https://github.com/illinois-cs415/illinois-cs415.github.io/blob/mp2-sp24-update/img/assignments/mp2/pursuer%20tutorial/step3.png" alt="drawing" width="400"/>

Pawn sensing allows the character to see and hear within a specified radius and angle. Hint: Look at the events that come with Pawn Sensing and find the one that is triggered when the Pursuer sees the player. Think about how you might use this to call a Chase event.

### Note on Behavior Trees
Alternatively, students may implement AI Characters using Behavior Trees in Unreal. There are many resources available online for how to use Behavior Trees. And here are a few slides on [Using AI in Unreal](https://docs.google.com/presentation/d/1tsbdJHC0r5w-sF30vuK8PuOIJsRZvvv3xJhFrFzT600/edit?usp=sharing). However, this feature is more high-level and may be tougher to debug, so if you feel more comfortable working with blueprints, we recommend simply calling events from within the Pursuer blueprint.

### Additional Resources

In addition to the instructions above, the following set of tutorials may be helpful to you: 
* [Unreal Engine 4 - AI Roam](https://www.youtube.com/watch?v=eBjtKsgurLU) 
* [Unreal Engine 4 - AI Chase Player](https://www.youtube.com/watch?v=HK3FAbIkJ-g)
* [Create A Platformer Pt 4: Chasing Knockback Enemy! UE4 Tutorial](https://www.youtube.com/watch?v=4UsaiOEr6Bw)
* [Unreal Engine 5 Tutorial - AI Part 1: Character Setup](https://youtu.be/IDZh0epFTRY?si=iQheKNeQNEnvbBNG)
* [Using AI in Unreal](https://docs.google.com/presentation/d/1tsbdJHC0r5w-sF30vuK8PuOIJsRZvvv3xJhFrFzT600/edit?usp=sharing)

**End of Pursuer tutorial.**
    
</details>

## Part 2: Mortar Enemy, Custom Enemy, Completing the Level (Due Feb. 24)

### Step 1: Create a Mortar enemy
The Mortar should be a stationary enemy placed in the level. The Mortar will launch projectiles above and around it in random directions.

The projectiles launched by the Mortar should:
- be affected by gravity (have an arc shaped path)
- collide with other objects in the level, including the player and ground
- produce small explosions upon any collision
- knockback and reduce the player's health if the player is hit by the projectile or its explosion (hint: radial damage)

Implement the same player-enemy collision behaviors as described above in the Pursuer instructions. The Mortar should be destroyed if a player jumps on top of it, even if it does not have a "head".

### Step 2: Create your own enemy
Create an enemy of your own design. It should have a similar complexity to the other two enemies and also be distinct and take on a different role. Please discuss your design in your design document.

You can use any assets you want for the enemies and their projectiles. Simple shapes will do as long as each enemy is visually distinct.

Again, implement the same player-enemy collision behaviors as the other enemies for the custom enemy.

### Step 4: Level Restart
When the Game Over or Level Complete screen is displayed, the player should have the option to restart the game without exiting. Upon the restart, all the characters and assets should be returned to their initial locations and health/score should be reset to 0.

### Step 3: Putting It All Together
The last step of the MP is to put it all together and make a platforming level. Your level should present some degree of challenge for the player and **take around 5 to 10 minutes to complete**. 

Your final level should:
- Have health packs scattered around the level that increase the player's health when collected
- Have floating collectibles scattered around the level that are destroyed when collected and increase the player's score
- Integrate all three enemy types into the design of the level
- Display a Game Over screen when the player's health is reduced to 0 or the character falls off the map
- Display a Level Complete screen when the player reaches the end of the level
- Allow the player to restart the level after a win/loss, which returns the player to the starting location and resets all the level's components

As far as environmental and visual assets go, you may use any of the provided, built-in, or any other assets in your level creation. Feel free to work in the provided project or in your own new project. **The level layout, enemies, and collectibles portions of the rubric are all a part of the level design. Your level should be somewhat challenging, the player should have to interact with enemies, and there should be some exploring required to find the collectibles.** If any of these things aren't the case, you'll lose significant points from those portions of the rubric. Make sure that your level isn't just the tutorial level!

### **Hints for Common Issues**
<details><summary markdown="span">Click the arrow to see hints</summary>
    
* If the projectile is going through instead of colliding with the ground, make sure that both the projectile and map collisions are set to `BlockAllDynamic` in their Details panel
* If you are having trouble setting up collisions with static meshes, [check out this tutorial](https://docs.unrealengine.com/5.0/en-US/setting-up-collisions-with-static-meshes-in-unreal-engine/)
* If you are having trouble with character knockback, [check out this thread](https://forums.unrealengine.com/t/character-knockback/300225/3)
* If you are having trouble with importing your own character and animations into UE5, [check out this tutorial](https://youtu.be/PyXeB1QtC0A?si=9W59r_W1Gn40cJfo)
    
</details>

# Additional Submission Instructions
## For Part 1
Submit a demo video and link to repo/ drive folder containing your code. **

## For Part 2 
Submit a demo video and link to repo/ drive folder containing your code.
In addition, you should also submit a short written document, either pdf or docx format, explaining your process for designing your level. It should be at most a page long. It should explain how you went about the level design process and how your level design had to accommodate the new mechanic and enemy you created. For example, you could talk about why you placed your custom enemy or collectibles in certain parts of the level. Please also record your video according to [this guideline](https://docs.google.com/document/d/1QY5t2wU9_6I7t4b-jneDRa7grhtQdSITzaOXVh-YKrA/edit?usp=sharing).
