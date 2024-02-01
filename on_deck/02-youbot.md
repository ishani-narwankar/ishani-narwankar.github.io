---
name: Kuka youBot Mobile Manipulator 
tools: [Python, CoppeliaSim, Kinematics, Motion Planning, Path Planning, Trajectory Generation]
image: https://ishani-narwankar.github.io/assets/portfolio_kuka.gif
description: insert info here
---
# Kuka youBot Mobile Manipulator
<br>

### **Project Brief**
The main goal of this project was to write software that plans a trajectory for the end-effector of the youBot mobile manipulator (a mobile base with four mecanum wheels and a 5R robot arm), performs odometry as the chassis moves, and performs feedback control to drive the youBot to pick up a block at a specified location, carry it to a desired location, and put it down. This was visualized in CoppeliaSim.
<br>
<br>
<center><iframe width="560" height="315" src="https://www.youtube.com/embed/tPG9MygONDw?si=8R5erDGjVC5_ZGkQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe></center>

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