---
layout: ../../layouts/Layout.astro
title: Romi
summary: 2-DOF translational parallel manipulator for autonomous box pick-and-place on multi-level warehouse shelves, integrated with one brushed DC motor and two servo motors.
image: /robotics-portfolio/rbe2001.png
tech: [C++, FBD Analysis, 3D Printing, CAD, FEM Analysis]
---


<img 
  src="/robotics-portfolio/rbe2001-2.png" 
  alt="Romi Robot" 
  style="width: 100%; height: auto; border-radius: 8px; border: 1px solid #333; margin: 1.5rem 0;" 
/>

### Project Overview
Built as part of Worcester Polytechnic Institute's Unified Robotics I (RBE 2001) course, "Romi" is a differential-drive mobile robot equipped with a 2-DOF translational parallel manipulator (a 5-bar linkage). The primary objective of the system is to navigate autonomously and perform precise pick-and-place operations on multi-level warehouse shelves.

To achieve this, the robot utilizes a custom-built C++ kinematics engine. Rather than relying on hardcoded joint positions, the software calculates real-time Inverse Kinematics (IK) to determine the exact motor and servo angles required to position the end-effector at specific *(X, Y)* coordinates in 2D space. The system also integrates PID control for smooth wheel odometry and trajectory execution.


### Hardware Setup
The mechanical architecture of the Romi integrates an off-the-shelf drive base with a completely custom-manufactured manipulator, specifically optimized for a balance of weight and structural integrity.

* **Base Chassis:** A Pololu Romi 32U4 differential-drive platform, utilizing an onboard ATmega32U4 microcontroller to manage drive motors and high-level logic.

* **5-Bar Linkage Arm:** Actuated by a hybrid motor setup consisting of one brushed DC "Blue Motor" (with a 20:1 gear reduction and magnetic encoder for precise positional feedback) and a high-torque servo.

* **Custom End-Effector:** A lightweight, servo-actuated pincer claw designed to securely grip and manipulate 3-gram payload boxes without exceeding the system's center of mass (CoM) limitations.

* **Materials & Manufacturing:** The structural links were primarily laser-cut from medium-high impact acrylic to minimize joint friction and allow for rapid prototyping. Complex mechanical components, such as the 20-tooth drive gears and structural standoffs, were 3D printed using PLA.

* **Engineering Validation:** The physical design was rigorously validated mathematically prior to fabrication. SolidWorks Finite Element Method (FEM) analysis was conducted to identify stress concentrations on the acrylic links and PLA gears to ensure forces remained well below yield strength limits. Additionally, full-system static Free Body Diagrams (FBD) and tipping point analysis were calculated via MATLAB to establish the maximum safe extension distances and payload capacities.


<a href="/robotics-portfolio/rbe2001-report.pdf?v=2" target="_blank" class="btn-report">
  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path><polyline points="14 2 14 8 20 8"></polyline><line x1="16" y1="13" x2="8" y2="13"></line><line x1="16" y1="17" x2="8" y2="17"></line><polyline points="10 9 9 9 8 9"></polyline></svg>
  Read the Full PDF Report
</a>