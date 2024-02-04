---
name: Kuka youBot Mobile Manipulator 
tools: [Python, CoppeliaSim, Kinematics, Motion Planning, Path Planning, Trajectory Generation]
image: https://ishani-narwankar.github.io/assets/portfolio_kuka.gif
description: Control algorithm to pick and place a cube with a Kuka youBot simulated in Coppeliasim.
---
# Kuka youBot Mobile Manipulator
<br>

### **Project Brief**
The main goal of this project was to write software that plans a trajectory for the end-effector of the youBot mobile manipulator (a mobile base with four mecanum wheels and a 5R robot arm), performs odometry as the chassis moves, and performs feedback control to drive the youBot to pick up a block at a specified location, carry it to a desired location, and put it down. This was visualized in CoppeliaSim.
<br>
<br>

### **Best PID Control Demo**
![youBot_pick_n_place](https://ishani-narwankar.github.io/assets/Best_run_cropped.mp4)

<br>
<br>

### **Trajectory Algorithm**
There are four functions that contribute to the working trajectory algorithm: NextState, TrajectoryGenerator, ScrewTrajectory, and FeedbackControl.
<br>

The **NextState** ________________

<br>

The **TrajectoryGenerator** _____________

<br>

The **ScrewTrajectory** _______________

<br>

The **FeedbackControl**__________

<br>
<br>

### **Initial States**
[enter here]
<br>
<br>

### **Results**
The following cases were tested to prove the usability and reliability of the trajectory algorithm:

1. **Best**

2. **Overshoot**

3. **New Task**
<br>
<br>
