---
name: Underwater SLAM and Waypoint Navigation with Autonomous Underwater Vehicle (AUV)
tools: [Python, ROS2, SLAM, CMake, Pixhawk, ArduSub, Path Planning, Controls]
image: https://ishani-narwankar.github.io/assets/AUV.jpg
description: ROS2 package that interfaces with ArduSub to allow an AUV to autonomously navigate waypoints and avoid obstacles under water.
---
# Underwater SLAM and Waypoint Navigation with Autonomous Underwater Vehicle (AUV)
<br>

![header_photo](../assets/nemo_header_photo.png)

### **Project Brief**
In 10 weeks, I updated a low-cost underwater vehicle, ported an existing feature-based visual SLAM package into ROS2 Iron and tuning it for use in an underwater environment, and developed a ROS2 package that interfaces with ArduSub to autonomously navigate waypoints underwater.

The system was updated, tuned, and coded for use in a university pool. The ultimate purpose for this project was to develop a system that may be used for underwater mapping and directed search and inspection uses.

The following post outlines the different aspects of this project:
- Hardware and Electronics
- Manual Control
- Environment Design
- ROS Architecture
  - ORB SLAM 2 into ROS2
  - Testing and data collection
  - Control
- Simulation
- Future Work

<br>
<!-- project flow section here: map building -> digital waypoint -> waypoint navigation -> obstacle avoidance -->

### **Overall Project Flow**
![project_flow](../assets/AUV_project_flow.png)

### **Hardware and Electronics**
For this project I inherited the underwater vehicle that James Oubre (MSR '23) built for his independent project. This vehicle was originally built for testing done in a lab water tank, so some hardware and electronics upgrades were necessary for reliable and effective use in a university pool.

The following are the upgrades I made to the physical system:
- Redesigned motor and weight mounts
- Replaced 3D-printed water-tight enclosures mounts to aluminum mounts
- Redesigned and lasercut new top and bottom AUV plates (added new standoff mounting holes and dive reel mount)
- Replaced and tuned motors for better manual control
- Added servo-mounted monocular camera

![hardware_upgrades](../assets/nemo_hardware_upgrades.png)

#### **Finding neutral buoyancy:**
Determining the configuration to achieve physical neutral buoyancy is important for the robot so that the AUV does not sink to the bottom of the pool or immediately return to the surface of the water when it is stationary.

The buoyancy of the AUV was altered with the addition of weights and pool noodles pieces (as shown below). 

An ideal neutral buoyancy for the system is a slightly positive one.
<br>

<p float="center">
  <img src="../assets/new_float.jpg" width="49%" />
</p>
<br>

### **Manual Control**
The first step was establishing manual control which was done by setting up the low-level control settings of the AUV through QGroundControl. Manual control was important for map generation and tuning ORB SLAM 2 as it was used as a way to test Visual SLAM live. QGroundControl was also used to tune the PID gains used by the pixhawk controller. The following picture shows the livestream feed through QGroundControl:

</center>
<p float="center">
  <img src="../assets/QGC.png" width="55%" />
</p>
<br>
### **Environment Design**
Visual SLAM relies on edge and feature detection in an environment. As a result, when tuning the ORB SLAM 2 package to work in an underwater environment I faced the issue of noise being created by the tiles at the bottom of the pool and the lack of distinct features in the environment. The lack of features was discovered when testing the visual SLAM algorithm on the AUV in a feature-heavy environment outside of the water.
<center>
**Pool with underwater obstacles added**
</center>
<p float="center">
  <img src="../assets/underwaterenvironment.jpg" width="55%" />
</p>
<br>

<center>**Feature detection with vs. without added obstacles**

![featurevfeatureless](../assets/feature_featureless.gif)
</center>

### **Implementing ORBSLAM 2 (Orb Feature SLAM) Underwater**
In order to localize the AUV while conducting autonomous waypoint navigation, I am generating a map using visual odometry. The available ROS package ORBSLAM 2 calculates the camera trajectory and creates a sparse 3D reconstruction for monocular cameras.

ORBSLAM 2 was developed for ROS1, so I ported it into ROS2 in order to use it on my system which uses ROS2 Iron. This required

After porting ORBSLAM 2 into ROS2, my main task was tuning the ORB parameters and adjusting the package to work in an underwater environment.

***Feature Detection in Pool Pre-camera Calibration***
[will be added soon]

***Good Camera Good Calibration Test***
The purpose of this test was to isolate the issue with ORBSLAM initialization onboard the AUV
[will be added soon]

***Feature Detection in Pool Post-camera Calibration***
[will be added soon]

***Feature Detection in Pool with Underwater Environment and tuned ORB Parameters***
[will be added soon]

### **Acknowledgments**
The AUV project was my own individual project, but the following people helped me with taking behind-the-scenes photos/videos and setting up the underwater environment in Northwestern's Pool:
Kyle Wang, Max Palay, Courtney Smith, Megan Black, Fiona Neylon, Kassidy Shedd, and Stella Yu. Thank you for your contributions.

### **Additional Videos**
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

