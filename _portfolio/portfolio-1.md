---
title: "Remote-Controlled Electric Racecar"
excerpt: "January 2019 - May 2019<br/><img src='/images/RC_Car.jpg' alt='racecar_design' style='max-width:100%; height:auto; width:450px;'><img src='/images/wheel_spin.gif' alt='wheel_spin' style='max-width: 100%; width: 450px; height:auto;'>"
collection: portfolio
---

<br/>
<div style="text-align: center;">
    <img src="/images/RC_Car.jpg" alt="racecar_design" style="max-width:100%; height:auto; width:90%; justify-content: center;">
</div>
<p style="text-align: center; font-size: 0.9em; color: #888; margin-top: 0;">Figure 1: Completed Model of Racecar Design</p>

## Overview

The following sections detail the thought processes underlying the design, modeling, and fabrication of a remote-controlled racecar for a competition I participated in. Overall, the design prioritized achieving the following goals: maximizing speed and acceleration, reducing drag, maintaining durability, capitalizing on modular parts, and protecting internal components. In turn, these goals informed design decisions throughout the engineering process.

## Design

### Chassis

The main chassis was printed using ABS thermoplastic on an FDM printer. This method was selected due to its combination of high customizablity, and moderate strength-to-weight ratio. The structure emulated traditional R/C cars to allow the use of known aerodynamic coefficients while optimizing internal component fit. Finite Element Analysis conducted in SolidWorks demonstrated that the structure was durable, with the only semi-fragile features being the steering linkage holders located at the front wheels. In order to be certain of the integrity of the design and manufacturing method, the car’s stiffness was determined by measuring force-displacement relationships, which then informed our calculation of impact forces during collision scenarios. These modeling efforts verified that the structure could withstand expected loading scenarios during operation and crash events.

<div style="text-align: center;">
  <img src="/images/ME_1.jpg" alt="" style="max-width:100%; height:auto; width:75%;">
</div>
<p style="text-align: center; font-size: 0.9em; color: #888; margin-top: 0;">Figure 2: Chassis Impact Deflection Analysis</p>

### Drivetrain

The drivetrain was rear-wheel drive, implemented using a custom gear train with a 6” long, ⅛” diameter steel shaft. The shaft was selected based on endurance calculations under a conservative impact load estimate of 5.4 lbs. The shaft durability verified via the modified Goodman fatigue criterion using surface condition and reliability factors (ka = 0.876, ke = 0.9). This confirmed a high cycle life under anticipated operating conditions.

### Steering

A rack-and-pinion mechanism was developed to enable active front-wheel steering. The servo-driven rack actuates two pinned steering linkages affixed to the chassis. Due to the complexity of the geometry, all steering components were 3D printed, and metal pins were machined for durability. Multiple iterations were required to ensure proper meshing of gear teeth and mechanical tolerances. Additionally, the minimum turning radius was analytically derived by geometrically modeling the chassis and applying a maximum steering angle of 45°. This confirmed that the custom steering design met maneuverability targets for the constrained racetrack layout.

<div style="display: flex; flex-wrap: wrap; gap: 1rem; justify-content: center;">
    <img src="/images/wheel_spin.gif" alt="wheel_spin" style="max-width: 100%; width: 45%; height:auto;">
    <img src="/images/wheel_turn.gif" alt="ME_3" style="max-width: 100%; width: 45%; height:auto;">
</div>
<p style="text-align: center; font-size: 0.9em; color: #888; margin-top: 0;">Figure 3: Demonstration of Rear-Wheel Spin (left) and Steering Angle (right)</p>

## Optimization

A MATLAB simulation was developed to evaluate how varying transmission ratios would impact car velocity and torque across a range of values. The simulation incorporated aerodynamic drag, weight, frictional losses, and motor torque-speed curves. The final transmission ratio of 0.39 was within the acceptable operational range (≥ 0.2), resulting in an estimated maximum velocity near 12 m/s. Additionally, a 3D surface plot was generated to visualize tradeoffs between torque, speed, and gear ratio, guiding system-level design decisions.

<div style="text-align: center;">
    <img src="/images/ME_2.jpg" alt="" style="max-width:100%; height:auto; width:75%;">
</div>
<p style="text-align: center; font-size: 0.9em; color: #888; margin-top: 0;">Figure 4: Torque vs. Speed vs. Transmission Ratio Optimization Plot</p>

## Manufacturing

The chassis, wheels, steering apparatus, and roll cage were additively manufactured, while the metal shafts, pins, and bearings were manually machined. The design originally incorporated oil-embedded sleeve bearings. However due to time constraints, custom bearings were machined to match the 3D printed wheel tolerances. These bearings enabled free rotation in the front wheels and secure mounting on the rear driveshaft. Key challenges included low-resolution 3D printers, infill calibration, and strength degradation due to print orientation.

<div style="text-align: center;">
    <img src="/images/ME_4.jpg" alt="" style="max-width:100%; height:auto; width:75%;">
</div>
<p style="text-align: center; font-size: 0.9em; color: #888; margin-top: 0;">Figure 5: Racecar Design Assembly</p>

## Performance

The car successfully completed the race and was overall the fastest, most agile design. Watch as it speeds around an obstacle and safely crosses the finish line below.

<div style="text-align: center;">
    <img src="/images/competition.gif" alt="racecar GIF" style="max-width:100%; height:auto; width:75%; justify-content: center;">
</div>
