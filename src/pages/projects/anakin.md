---
layout: ../../layouts/Layout.astro
title: "Anakin"
summary: "A vision-guided robot arm that locates colored objects and plans smooth pick-and-place movements."
discipline: "Robot manipulation & vision"
context: "WPI · Unified Robotics III"
order: 0
image: /robotics-portfolio/anakin.png
tech: ["MATLAB", "Computer Vision", "Inverse Kinematics", "Trajectory Planning"]
---

<div class="video-wrapper">
  <iframe src="https://www.youtube.com/embed/7ueeSr73Q0U" title="Anakin robot arm demonstration" loading="lazy" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## From camera pixels to a robot grasp

Anakin is a three-degree-of-freedom robot arm built for autonomous object sorting. An overhead camera locates colored spheres, and the control software turns those detections into pick-and-place movements.

Developed in WPI's Unified Robotics III course, the project brings together camera calibration, object detection, kinematics, and trajectory planning in a single system.

## How it works

A MATLAB vision pipeline corrects fisheye distortion and uses a **25 mm checkerboard** to relate image coordinates to the robot's workspace. Color thresholds, masks, and blob detection identify the objects. The position estimate also accounts for the spheres' height above the work surface.

Forward and inverse kinematics translate between joint angles and end-effector positions. **Quintic trajectories** define the motion between positions, controlling how velocity and acceleration change throughout a move.

## The system

- **Robot arm:** Three degrees of freedom, actuated by Dynamixel smart servos with position feedback.
- **Camera:** An overhead 1080p USB fisheye camera covering the workspace.
- **Software:** MATLAB for image processing, coordinate transformations, kinematics, and motion planning.

The central challenge was connecting perception to motion: a detected object needed to become a reachable position in the arm's coordinate frame. Calibration and kinematics provided that connection, while trajectory planning shaped how the arm moved to it.

<a href="/robotics-portfolio/anakin-report.pdf?v=2" target="_blank" rel="noopener noreferrer" class="btn-report">Read the project report <span aria-hidden="true">↗</span></a>
