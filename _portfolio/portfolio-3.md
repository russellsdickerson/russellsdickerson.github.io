---
title: "Additive Manufacturing Device for Deposition of Icing"
excerpt: "Short description of portfolio item number 1<br/><img src='/images/3D_Printer.png' alt='Image of Printer_Design' style='max-width:100%; height:auto; width:450px;'>"
collection: portfolio
---

<div style="text-align: center;">
    <img src="/images/3D_Printer.png" alt="printer_design" style="max-width:100%; height:auto; width:45%; justify-content: center;">
</div>
<p style="text-align: center; font-size: 0.9em; color: #888; margin-top: 0;">Figure 1: Completed Model of Printer Design</p>

## Design

The goal of this project was to create a functional prototype of a low-cost, 3D printer for automated deposition of edible materials, such as icing. The design process began with stakeholder interviews to identify key user requirements. From the results of the interviews, it was determined that print customizability, food safety, print accuracy, affordability, and ease of use were the most important requirements to consider. They were then translated into quantitative specifications such as ±2 mm positional tolerance, < 4 ft³ build volume, and a sub-$250 total cost. Several design concepts were explored using tools such as functional decomposition, morph matrices, and Pugh chart analyses. In the end, a CoreXY motion system was selected and paired with a syringe-based extrusion mechanism as the optimal configuration for meeting performance, manufacturability, and cost criteria.

At a high level, the mechanical design consists of four integrated subsystems: the XY gantry, the extruder, the support enclosure, and the control system. These subsystems will be explained in the following sections.

<div style="display: flex; flex-wrap: wrap; gap: 1rem; justify-content: center;">
  <img src="/images/CoreXY.jpg" alt="XY_system" style="width: 30%; height: auto;">
  <img src="/images/Extruder.jpg" alt="extruder" style="width: 30%; height: auto;">
  <img src="/images/Support.png" alt="support" style="width: 30%; height: auto;">
</div>
<p style="text-align: center; font-size: 0.9em; color: #888; margin-top: 0.5rem;">
  Figure 2: Printer Subsystems (left to right): CoreXY, Extruder, Support
</p>

### CoreXY Gantry

The printer employs a CoreXY system for planar motion, selected for its mechanical efficiency, low inertia, and precision at scale. It consists of two orthogonally mounted rods, each actuated by independent stepper motors via a belt loop mechanism. The print head is suspended at the intersection of the rods and moves through a carriage glider system. To minimize friction and backlash, the team replaced traditional sliding bearings with top-mounted gliders that ride on the guide rods, reducing assembly complexity and mechanical binding. This configuration also allowed for consistent belt tensioning and simplified calibration. The gantry system was optimized through iterative prototyping and validated using factorial experiments assessing motion accuracy, confirming the system's ability to maintain sub-2 mm error across travel paths, including diagonals.

### Extruder

The extrusion mechanism uses a syringe-actuated design. A non-captive NEMA 17 stepper motor drives a threaded lead screw, converting rotary motion into linear displacement of the syringe plunger. This direct-drive approach eliminates the need for pneumatic or pump-based systems, which are more complex and harder to clean. The syringe is held within a custom 3D-printed clamp that allows for quick insertion and removal without tools. The use of a standard 100 mL syringe enables users to preload icing and easily switch between batches. The plunger interface was designed with modularity in mind, allowing for accurate, repeatable extrusion strokes while maintaining food safety standards. Experimentally, this design provided sufficient extrusion force even under varying icing viscosities, without requiring heating or pressure feedback.

### Support Enclosure

The support frame and enclosure were constructed using laser-cut wood panels and joined via interlocking dovetail features to eliminate the need for screws or adhesives at the major joints. This design choice simplified alignment during assembly and improved the reproducibility of builds for DIY users. The total printer volume was 3.58 ft³ which meets the 4 ft³ requirement to fit within standard kitchen workspaces. An acrylic baseplate was used in place of a wood-silicone sandwich design to improve food safety and cleanability, avoiding moisture retention and mold formation. Structural integrity o the frame was analyzed via finite element simulation of the frame legs, revealing stress concentrations located at the connection points. In order to mitigate this, L-brackets were introduced to reinforce the joints and reduce deflection under load. Vibration damping and motor torque accommodation were also considered, ensuring that the enclosure would remain stable during operation.

### Control System

The control system is built around an Arduino Mega microcontroller paired with a RAMPS 1.4 shield and A4988 stepper drivers. The firmware used is Marlin, a widely adopted open-source platform configured to support Cartesian motion and manual Z-axis adjustments. Users interact with the printer via Repetier-Host, which serves as the G-code sender and real-time interface. This combination of software allows for fine-grained tuning of parameters such as feed rate, steps/mm, and acceleration curves. During calibration, custom motion commands were issued through Repetier to analyze positional accuracy and response timing. Adjustments to firmware parameters were made iteratively based on experimental data, ultimately converging on a setting of 5 steps/mm for both X and Y axes. The electrical components are housed in a ventilated top-mounted enclosure to prevent overheating during long print sessions, and wiring was routed internally for safety and organization.

## Experimentation & Validation

To evaluate the accuracy of our XY motion system and verify firmware calibration, we conducted a factorial experiment examining how feed rate, travel distance, and motion type (straight vs. diagonal) affected positional error and print time. Our primary goal was to determine whether the configured steps-per-millimeter parameter in the Marlin firmware produced accurate physical displacement.

A Sharpie marker was mounted to the extruder carriage to draw test lines on paper. For each of eight trials, we varied feed rate, travel distance, and line type using Repetier-Host, then measured actual line lengths and print durations. These data were used to compute error and assess system behavior under different motion conditions. Diagonal paths were of particular interest, as they involve simultaneous activation of both motors and introduce greater mechanical complexity.

Results showed that higher feed rates and diagonal movements reduced print time but increased positional error. Longer travel distances improved accuracy at the cost of speed. Interaction and main effect plots, supported by regression and ANOVA analyses, confirmed that diagonal motion significantly impacted both error and timing. Some interaction terms were insignificant for error prediction, but all factors meaningfully influenced duration.

This experiment confirmed that our XY system met the target accuracy of ±2 mm under calibrated conditions and provided guidance for future improvements—particularly in reducing diagonal motion error through mechanical reinforcement and firmware tuning.

## Manufacturing and Assembly

Throughout the design process, manufacturing efficiency and ease of assembly were prioritized. The use of dovetail joints reduced the need for fasteners and simplified frame alignment, while 3D-printed gliders replaced commercial linear bearings, reducing part count and reliance on tight tolerances. The extruder design avoided the use of long tubing, which is difficult to clean and prone to contamination. In contrast, a syringe can be easily removed, cleaned, and reused. The frame and baseplate materials were selected for durability, food safety, and ease of assembly. In fact, since the system was designed for reproducibility by DIY users, no custom tooling or excessive calibration were required. The entire printer can be assembled in under 48 hours using standard tools, and all parts were sourced from common suppliers. The final cost of the system was $191.11, which is well within the project’s $250 budget.

## Conclusion

The final prototype met all core performance and design criteria. It delivered consistent icing deposition within ±2 mm of design paths, demonstrated modularity and user-friendliness, and remained within the prescribed budget and size constraints. Overall, the project demonstrates the viability of a low-cost, precision food printer built from accessible components and guided by structured engineering design principles. See below for an example of the printer in action.

<video controls autoplay loop muted playsinline style="display: block; margin: 0 auto; width: 60%;">
  <source src="/videos/Printing_heart_x1.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
<p style="text-align: center; font-size: 0.9em; color: #888; margin-top: 0.5rem;">
  Figure 3: Demonstration of Print: Heart
</p>