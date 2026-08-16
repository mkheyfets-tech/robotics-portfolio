---
layout: ../../layouts/Layout.astro
title: Anakin
summary: Autonomous Pick-and-Place robotic sorting system that uses computer vision, forward and inverse kinematics, and quintic trajectory planning.
image: /robotics-portfolio/anakin.png
tech: [MATLAB, Computer Vision, FK/IK, Image Processing]
---


<div class="video-wrapper">
  <iframe 
    src="https://www.youtube.com/embed/7ueeSr73Q0U" 
    title="Robotics Project Video" 
    frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
    allowfullscreen>
  </iframe>
</div>

### Project Overview
Built as part of Worcester Polytechnic Institute's Unified Robotics III: Manipulation (RBE 3001) course, "Anakin" is a 3-DOF robotic manipulator designed for autonomous object retrieval and sorting. The system bridges the gap between computer vision and physical manipulation by dynamically detecting colored spheres and executing precise pick-and-place operations based on real-time sensor data.

To achieve this, the software architecture utilizes a custom MATLAB-based kinematics engine. It performs complex Forward and Inverse Kinematics (FK/IK) to translate the robot's Cartesian task space into precise joint angles. To ensure smooth, hardware-safe movement between locations, the system employs quintic trajectory generation, calculating optimized position, velocity, and acceleration profiles for the arm during operation.


### Hardware Setup
The physical and perceptual architecture of Anakin pairs a stationary manipulator with a calibrated overhead vision system to create a fully autonomous, closed-loop sorting environment.

* **Manipulator:** A 3-Degrees-of-Freedom (3-DOF) robotic arm actuated by Dynamixel smart servos, allowing for high-precision joint space control, continuous position feedback, and reliable gripping.

* **Vision Sensor:** A 1080p USB fisheye camera mounted directly above the workspace, capturing high-resolution (1920x1080) RGB images to actively monitor the state of the board.

* **Workspace Calibration:** The system is grounded by a 25mm checkerboard calibration grid. Using MATLAB's computer vision toolboxes, the camera's intrinsic fisheye distortion is linearized, and an extrinsic transformation matrix is calculated to seamlessly map 2D image pixels directly into 3D physical robot coordinates.

* **Detection Pipeline:** The perception system uses advanced color thresholding, binary masking, and blob detection to isolate target objects. It then utilizes custom trigonometric projection algorithms to account for the physical volume of the spheres, accurately calculating where the center of the ball touches the checkerboard plane so the arm can perfectly align its grasp.

<a href="/robotics-portfolio/anakin-report.pdf?v=2" target="_blank" class="btn-report">
  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path><polyline points="14 2 14 8 20 8"></polyline><line x1="16" y1="13" x2="8" y2="13"></line><line x1="16" y1="17" x2="8" y2="17"></line><polyline points="10 9 9 9 8 9"></polyline></svg>
  Read the Full PDF Report
</a>