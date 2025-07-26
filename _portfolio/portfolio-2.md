---
title: "R/C Electric Racecar: Design, Simulation, and Testing"
excerpt: "Short description of portfolio item number 1<br/><img src='/images/RC_Car.jpg' alt='racecar_design' style='max-width:100%; height:auto; width:450px;'>"
collection: portfolio
---

<img src='/images/RC_Car.jpg' alt='racecar_design' style='max-width:100%; height:auto; width:450px;'>

## Introduction

In this project, my team and I designed, modeled, manufactured, and tested a remote-controlled car. The design prioritized achieving the following goals: maximizing speed and acceleration, reducing drag, ensuring sturdy construction, enabling modularity, and protecting internal components. These design priorities guided every stage of the engineering process. By leveraging additive manufacturing, we developed a compact chassis and modular bumper design, enabling us to tailor mechanical performance while accommodating space and weight constraints inherent to small-scale mobile platforms[^1].

 The team’s design focused on achieving several key goals: maximizing speed and acceleration, reducing drag, ensuring sturdy construction, enabling modularity, and protecting critical components. To accomplish this, the strategy emphasized leveraging 3D printing to shape both the form factor and protective features. FEA simulations were conducted to analyze deflections and estimate impact forces, which guided iterative design improvements. The drivetrain was designed using MATLAB simulations to evaluate velocity and acceleration across different gear ratios and wheel radii, leading to the selection of an optimal transmission ratio based on Jake’s 3D code visualizations. Bearings were chosen from McMaster-Carr, with custom machining to match a compact 3mm bore and 8mm outer diameter. The steering mechanism was built around a parallelogram configuration for consistent turning behavior, modeled in SolidWorks and supported by analytical turn radius calculations. Assembly involved multiple iterations of 3D-printed chassis components, which initially caused interference issues between gears and motors. These were resolved by adding an intermediate gear and mirroring the assembly to ensure proper forward motion. Shaft dimensions were refined through custom machining, allowing for a better fit and additional protection for the wheels. The steering assembly posed 3D printing challenges, which were addressed through motion studies and renders demonstrating gear operation, component placement, and overall movement of the vehicle.

## Design

### Chassis

The main chassis was 3D printed in ABS plastic, selected for its combination of geometric flexibility and moderate strength-to-weight ratio. The design geometry emulated traditional R/C cars to allow the use of known aerodynamic coefficients while optimizing internal component fit. Finite Element Analysis (FEA) conducted in SolidWorks indicated that peak deflections in the steering linkage holders—the most fragile structural elements—were minimal, affirming the structural feasibility of additive manufacturing for low-load mobile platforms[^1].

### Drivetrain

The drivetrain was rear-wheel drive, implemented using a custom gear train with a 6” long, ⅛” diameter steel shaft (Brinell hardness: 167; yield strength: 70,000 psi). The shaft was selected based on endurance calculations under a conservative impact load estimate of 5.4 lbs. We verified shaft durability via the modified Goodman fatigue criterion using surface condition and reliability factors (ka = 0.876, ke = 0.9), confirming a high cycle life under anticipated operating conditions[^2].

### Steering

A custom rack-and-pinion mechanism was developed to enable active front-wheel steering. The servo-driven rack actuated two pinned steering linkages affixed to the chassis. Due to the complexity of the geometry, all steering components were 3D printed, and metal pins were machined for durability. Multiple reprints were required to ensure proper meshing of gear teeth and mechanical tolerances[^3].

## Modeling

To ensure structural and dynamic performance, we performed a series of simulations and analytical calculations. FEA in SolidWorks was used to determine the car’s stiffness by measuring force-displacement relationships, which then informed our calculation of impact forces during collision scenarios using \( F = v \sqrt{mk} \). These modeling efforts verified that the structure could withstand expected loading scenarios during operation and crash events[^2].

<img src='/images/wheel_spin.gif' alt='wheel_spin' style='max-width:100%; height:auto; width:450px;'>"
<!--<img src='/images/competition_video.gif' alt='racecar GIF' style='max-width:100%; height:auto; width:450px;'>"-->
<img src='/images/ME_1.jpg' alt='' style='max-width:100%; height:auto; width:450px;'>
<img src='/images/ME_2.jpg' alt='' style='max-width:100%; height:auto; width:450px;'>
<img src='/images/ME_3.jpg' alt='' style='max-width:100%; height:auto; width:450px;'>

## Optimization

A MATLAB-based simulation was developed to evaluate how varying transmission ratios would impact velocity and torque across a range of values. The simulation incorporated aerodynamic drag, weight, frictional losses, and motor torque-speed curves. Our final transmission ratio of 0.39 was within the acceptable operational range (≥ 0.2), resulting in an estimated maximum velocity near 12 m/s. Additionally, a 3D surface plot was generated to visualize tradeoffs between torque, speed, and gear ratio, guiding system-level design decisions[^3].

We also analytically derived the minimum turning radius by geometrically modeling the chassis and applying a maximum steering angle of 45°. This confirmed that the custom steering design met maneuverability targets for the constrained track layout[^4].

## Manufacturing

While our design originally incorporated off-the-shelf oil-embedded sleeve bearings, we transitioned to custom-machined bearings to match 3D printed wheel tolerances. These bearings enabled free rotation in the front wheels and secure mounting on the rear driveshaft. Key challenges included low-resolution 3D printers, infill calibration, and strength degradation due to print orientation. Components like the steering rack and linkages required multiple iterations to achieve functional mechanical tolerances[^3].

The chassis itself was manufactured using overnight ABS prints, and metal shafts and pins were manually machined. Assembly included adhesive bonding and mechanical fasteners, with particular attention to the interface between printed and metallic components.

<img src='/images/ME_4.jpg' alt='' style='max-width:100%; height:auto; width:450px;'>
<img src='/images/ME_5.jpg' alt='' style='max-width:100%; height:auto; width:450px;'>

## Performance

Our car successfully completed one race lap before mechanical failure occurred due to an impact with the track wall. Post-race analysis revealed that the failure was initiated at a weak shear interface resulting from print orientation. The affected steering linkage had been printed with layers perpendicular to the primary impact force, compromising its structural integrity. The optional front bumper, which could have absorbed the impact, was omitted from the race due to clearance issues.

Despite the failure, the system demonstrated strong alignment between modeling predictions and observed performance. All mechanical subsystems operated as designed under nominal conditions[^5].

## Conclusion

This project showcased the integration of mechanical design, simulation, and prototyping in the development of a small-scale mobile system. Through iterative modeling, precision fabrication, and simulation-informed decision making, we achieved a modular, functional R/C car platform. Our design leveraged the strengths of additive manufacturing while highlighting its limitations, particularly in strength anisotropy. Future iterations will involve material optimization, simplified steering kinematics, and more robust impact protection strategies.

This work serves as a representative example of interdisciplinary mechanical engineering, combining CAD, FEA, system dynamics, MATLAB-based modeling, and experimental validation.
