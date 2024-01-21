---
name: Hangman Game with Robot Arm
tools: [Python, ROS2, OpenCV, Embedded Systems, CAD]
image: https://ishani-narwankar.github.io/assets/hangman_franka.gif
description: ROS2 package and services allowing Franka Emika arm to facilitate a game of hangman with a human player.
---

# Hangman Game with Franka Emika Robot Arm
<br>

### **Project Brief**
The main goal of this project was to use the Franka Emika robot arm as a facilitator for a game of hangman. My team and I developed a ROS2 package to implement force control for writing, utilize april tags for a more dynamic gameplay, and apply object character recognition to interact with the human player. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/tPG9MygONDw?si=8R5erDGjVC5_ZGkQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

<br>
<br>

### **Subsystems**
- Franka Emika Robot Arm: The arm was controlled using the ROS2 MoveIt API. Realistic writing technique were implemented using force control methods. 
- Gameplay: The backend ROS2 organization and implementation of all of the subsystems allowed the Franka robot to keep track of and change states during the hangman game.
- Computer Vision: An Intel RealSense D435 Camera was used for all computer vision. April Tags were used for calibrating the arm's position with respect to the whiteboard. This allows for a more dynamic gameplay (ie the whiteboard could be moved between player turns and the game could still continue). An object character recognition algorithm was trained to allow players to write letter or full-word guesses.
<br>
<br>

### **System Flow**
- **Calibration:** Franka moved to detect April Tags on whiteboard and create transforms to determine whiteboard position and orientation with respect to the robot.
- **Game Setup:** ROS2 service set up to call MoveIt actions in order to draw dashes for the 6-letter randomly generated word, additional dashes for the 6 letter guesses, and the hangman tree stand.
- **Player Interaction:** Franka moved towards player in order to use Intel RealSense Camera to detect player's guess written on a personal whiteboard.
- **Franka Response:** Arm utilizes force control to determine end-effector distance from board and write or draw necessary component for gameplay.
- **Endgame:** The game continues until the player guesses the right word or until they use up their 6 wrong guesses.
<br>
<br>

### **Personal Work**
Personal work on this project includes:
- Creating and implementing ROS2 service for Game Setup
- Designing and manufacturing mounts needed for Franka Emika arm interaction with pen (a spring-loaded pen holder was designed and 3D printed as a fallback goal for the force control)
- Organizing team dashboard to integrate team member work and keep track of completed tasks
<br>
<br>

### **Background Information**
This work was developed as a group project from Northwestern University's **ME 495: Embedded Systems in Robotics class**. The goal of the class was to learn and implement ROS2 (Robotic Operating System).

**Group Members: Ishani Narwankar, Ananya Agarwal, Graham Clifford, Abhishek Sankar, Srikanth Schelbert**

<br>
<br>

### **Additional Videos**
The following two videos closely demonstrate the OCR system and how player guesses are seen by the robot.
<br>
<br>


<video src="../assets/hm_single_letter.mp4" controls title="Single Letter Guess:"></video>



Full word guess:


<video src="../assets/hm_full_word.mp4" controls title="Full Word Guess:"></video>



<br>
<a href="https://github.com/ishani-narwankar/hangman-with-franka">Hangmanbot GitHub Repository</a>
