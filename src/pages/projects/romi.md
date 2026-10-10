---
layout: ../../layouts/Layout.astro
title: "Romi"
summary: "A mobile pick-and-place robot with a custom five-bar arm designed to move small boxes between shelf levels."
discipline: "Mechanisms & embedded control"
context: "WPI · Unified Robotics I"
order: 2
image: /robotics-portfolio/rbe2001.png
tech: ["C++", "Mechanical Design", "Inverse Kinematics", "FEA"]
---

<figure>
  <img src="/robotics-portfolio/rbe2001-2.png" alt="Romi mobile robot and its custom five-bar linkage arm." />
  <figcaption>A mobile base paired with a custom linkage and gripper for shelf-level pick-and-place tasks.</figcaption>
</figure>

## A small robot with a practical handling task

Romi combines a differential-drive base with a two-degree-of-freedom, five-bar linkage arm. Its task is to pick up small boxes and place them on shelves at different heights.

Built in WPI's Unified Robotics I course, the project connects mechanism design, fabrication, structural analysis, and embedded C++ control.

## Designing the arm

A geared DC motor and a servo drive the linkage, while a separate servo operates the gripper. The arm uses laser-cut acrylic links and 3D-printed parts, including gears and structural supports. The gripper is designed around **3-gram boxes**.

The design had to balance reach with stability. Free-body diagrams and tipping analysis in MATLAB were used to evaluate loads and extension limits. SolidWorks finite element analysis helped assess stresses in the acrylic links and printed gears.

## Turning a target position into motion

The C++ controller uses **inverse kinematics** to calculate the actuator positions needed to move the end effector to a target point. PID control supports wheel motion and trajectory execution on the Pololu Romi 32U4 base.

This made the mechanical design and control software closely linked: the geometry determined which positions were reachable, while the controller translated those positions into motor commands.

<a href="/robotics-portfolio/rbe2001-report.pdf?v=2" target="_blank" rel="noopener noreferrer" class="btn-report">Read the project report <span aria-hidden="true">↗</span></a>
