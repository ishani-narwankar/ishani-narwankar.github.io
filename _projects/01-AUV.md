---
name: Waypoint Navigation and Obstacle Avoidance with Autonomous Underwater Vehicle (AUV)
tools: [Python, ROS2, SLAM, CMake, Pixhawk, ArduSub, Path Planning, Controls]
image: https://ishani-narwankar.github.io/assets/AUV.jpg
description: ROS2 package that interfaces with ArduSub and PX4 to allow an AUV to autonomously navigate waypoints and avoid obstacles under water.
---
# Waypoint Navigation and Obstacle Avoidance with Autonomous Underwater Vehicle (AUV)
<br>

**THIS IS AN ONGOING INDEPENDENT PROJECT. THIS PAGE WILL CONTINUOUSLY BE UPDATED**
<br>
<br>

### **Project Brief**
The main goal of this project is to update a low-cost underwater vehicle and develop a ROS2 package that interfaces with ArduSub and PX4 to allow the AUV to autonomously navigate waypoints and avoid obstacles underwater.
<br>
<!-- project flow section here: map building -> digital waypoint -> waypoint navigation -> obstacle avoidance -->

### **Overall Project Flow**
![project_flow](../assets/AUV_flowchart.jpg)

## **Progress so far:**
Hardware:
- Determine configuration for neutral buoyancy
- Redesign, manufacture, and reconfigure hardware and electronics for AUV

Software:

- Tune PID control of AUV
- Create ROS2 package nemo_auv
- Convert QGroundControl livestream to OpenCV video frames for use with RVIZ
- Create control node for autonomous depth control

SLAM:

- Port ORBSLAM2 for use with ROS2 Iron
- Calibrate monocular camera in air and in pool
- Tune ORB params for better feature detection underwater
- Design underwater environment for sufficient initialization of ORBSLAM2 underwater
- Generate map of underwater environment with SLAM algorithm
<br>

### **Finding neutral buoyancy**
Determining the configuration to achieve physical neutral buoyancy is important for the robot so that the AUV does not sink to the bottom of the pool or immediately return to the surface of the water when it is stationary.

The buoyancy of the AUV was altered with the addition of weights and pool noodles pieces (as shown below). 

An ideal neutral buoyancy for the system is a slightly positive one.
<br>

<p float="center">
  <img src="../assets/new_float.jpg" width="49%" />
</p>

### **Demo Videos of Progress**
The following video showcases established manual drive and connection with QGroundControl.
<center><iframe width="560" height="315" src="https://www.youtube.com/embed/sCT3qU0JJ18?si=rvHk0taONFOJ48xA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe></center>

The following video showcases the ros2 package created manual/autonomous depth mode which allows users to move around the AUV without having to manually maintain depth. This mode is used to capture rosbag data to input into ORBSLAM for map generation.

<center><iframe
 width="720"
 height="576"
 src="{{'https://youtube.com/embed/nIQ-ettAFkg?si=26ZnPv025zFOqHaE' . $video}}"
 title="YouTube video player"
 frameborder="0"
 allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
 allowfullscreen>
</iframe></center>

