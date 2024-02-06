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
![Demo](../assets/Best_run_cropped.gif)

<!-- <center>
    <div style="position: relative; padding-bottom: 28.125%; height:0; overflow: hidden;">
        <video src="https://ishani-narwankar.github.io/assets/Best_run_cropped.mp4" controls style="position: absolute; top:0; left:0; width: 60%; height: 100%;"></video>
    </div>
</center> -->

<br>
<br>

### **Trajectory Algorithm**
There are four functions that contribute to the working trajectory algorithm: NextState, TrajectoryGenerator, ScrewTrajectory, and FeedbackControl.
<br>

Using the first-order Euler equation, the **NextState** function determines the robot's configuration at the next time step.
<br>

The **TrajectoryGenerator** function takes in the transformation matrix of the necessary cube initial and ending waypoints and outputs a list of transformation matrices of end-effector positions in the space frame.
<br>

Each stage of the algorithm utilizes the **ScrewTrajectory** function which is from the modern robotics library. This function takes the starting and ending transformations of the end-effector and generates a discrete trajectory as a list of end-effector transformation matrices with the fifth-order polynomial time-scaling method.
<br>

Lastly, the **FeedbackControl** function is used to calculate the kinematic task-space feedforward plus feedback control law, which is written as:
<br>
<br>
![FeedbackControl](../assets/feedforwardlaw.png)

<br>
<br>

### **Results**
The following cases were tested to prove the usability and reliability of the trajectory algorithm:

1. **Best**
![Alt text](../assets/X_err_best_plot.png)

2. **Overshoot**
![Alt text](../assets/X_err_newtask_plot.png)

3. **New Task**
![Alt text](../assets/X_err_overshoot_plot.png)

<br>
<br>
