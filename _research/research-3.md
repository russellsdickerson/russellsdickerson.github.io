---
title: "Bio-Inspired Passive Thermal Regulation in Soft Actuators"
excerpt: "Jan 2024 – May 2024<br/><img src='/images/Bio_6.jpg' alt='actuator' style='max-width:100%; height:auto; width:25%;'>"
collection: research
---

<div style="display: flex; flex-wrap: wrap; gap: 1rem; justify-content: center;">
  <img src="/images/Ant_Image_A.jpeg" alt="antA" style="width: 30%; height: auto;">
  <img src="/images/Ant_Image_B.jpg" alt="antB" style="width: 30%; height: auto;">
  <img src="/images/Bio_13.jpg" alt="hair" style="width: 30%; height: auto;">
</div>
<p style="text-align: center; font-size: 0.9em; color: #888; margin-top: 0.5rem;">
  Figure 1: Saharan Silver Ant (left) and Hair Structure (right)
</p>

## Overview
The Saharan silver ant survives extreme desert temperatures through a unique thermoregulatory adaptation: dense arrays of triangular hairs on its dorsal and lateral surfaces. These hairs are characterized by corrugated triangular cross-sections, which enhance broadband reflectivity in the visible and near-infrared (NIR) via Mie scattering and total internal reflection. The result is reduced solar heat absorption. In the mid-infrared (MIR), where thermal emission dominates, the hairs act as a refractive index layer to boost emissivity and radiative heat loss. Furthermore, the absence of hairs on the ventral side limits heat gain from the ground. Together, these mechanisms enable thermal resilience in harsh environments and inspire scalable, passive cooling strategies. This study explores how such geometric principles can be translated into soft robotic systems by modulating actuator surface shape to reduce thermal load.

## Design
Inspired by the structure of the surface hairs, a soft robotic system was designed to mimic the thermoregulatory properties of the Saharan silver ant. The goal was to identify if the passive scattering of infrared radiation was translatable to soft robotic systems at scale. The idea behind the design is that these soft actuators could be arranged in a side-by-side pattern to create a thermal shield that maintains a cooler surface temperature than other structures and can actively change its shape depending on environmental conditions. This kind of shield would have implications for wearables or external surfaces of buildings or tents.

<div style="text-align: center;">
  <img src="/images/Bio_6.jpg" alt="actuator" style="max-width:100%; height:auto; width:75%;">
</div>
<p style="text-align: center; font-size: 0.9em; color: #888; margin-top: 0;">Figure 2: Triangular Soft Robotic Actuator</p>

## Fabrication
To replicate the ant-inspired surface geometry, six EcoFlex silicone models were fabricated using 3D-printed molds. These molds were designed using SolidWorks and were defined by a housing with an inner triangular cavity and a plunger to create the air chamber. Prior to casting, a mold release agent was applied to the sides in order to prevent unwanted adhesion to the inner surfaces. EcoFlex was mixed at a 1:1 ratio by weight, degassed under vacuum to remove air bubbles, and poured into the molds. After curing at room temperature, the actuators were demolded and visually inspected for uniformity and potential defects.

<div style="display: flex; flex-wrap: wrap; gap: 1rem; justify-content: center;">
    <img src="/images/Bio_11.jpg" alt="mold1" style="max-width: 100%; width: 45%; height:auto;">
    <img src="/images/Bio_12.jpg" alt="mold2" style="max-width: 100%; width: 45%; height:auto;">
</div>
<p style="text-align: center; font-size: 0.9em; color: #888; margin-top: 0;">Figure 3: Exploded View of Mold Design with Plunger (left) and Plunger Inserted into Mold Design(right)</p>

## Experimental Setup
The thermal performance of each sample was evaluated under simulated solar loading using three identical IR heat lamps. These lamps were positioned at the same distance above each test fixture. Each fixture consisted of a tissue box housing with thin parachute fabric over it. On top of two of the fixtures were three inflated soft actuators and three deflated soft actuators, respectively. These were to act as a thermal shield. The third fixture was left bare as a control. The internal air temperature within each box was monitored using digital thermometers placed inside. Once the lamps were turned on, temperature measurements were taken for all three setups at intervals of one minute over a twenty minute time period. This setup allowed direct comparison between circular actuators, triangular actuators, and no actuators under identical conditions. Testing was conducted in a controlled indoor environment to eliminate ambient variability.

<div style="display: flex; flex-wrap: wrap; gap: 1rem; justify-content: center;">
    <img src="/images/Test_setup.png" alt="setup" style="max-width: 100%; width: 45%; height:auto;">
    <img src="/images/Bio_7.jpg" alt="test" style="max-width: 100%; width: 45%; height:auto;">
</div>
<p style="text-align: center; font-size: 0.9em; color: #888; margin-top: 0;">Figure : Diagram of Experimental Test Setup (left) and Actual Experimental Test Setup (right)</p>

## Results
Temperature measurements showed that both inflated and deflated soft actuator configurations reduced internal temperatures by around 15°F compared to the control. The deflated triangular geometry also had a slower temperature rise. This suggests improved radiative scattering or enhanced emissivity. However, comparisons between inflated and deflated states should be interpreted cautiously, as the increased internal air volume in the inflated state may introduce insulative effects unrelated to surface geometry. Additionally, future experiments will need to determine the effect caused by the presence vs. lack of material. Despite this, the results support the hypothesis that geometric structuring alone could passively reduce thermal loading via broadband reflection and angle-dependent scattering.

## Conclusion
This study demonstrates that ant-inspired triangular surface geometries can passively reduce thermal load in soft materials by enhancing infrared scattering and directional reflectivity. Triangular EcoFlex structures showed measurable temperature reductions compared to circular and control conditions, supporting the scalability of biological thermoregulatory strategies. However, the experimental setup operates at macroscopic scales and under simplified conditions that may not fully capture wavelength-scale interactions such as true Mie scattering. Material optical properties and environmental factors like wind and humidity were also not varied. Future work should include outdoor testing to further validate and extend these findings for more practical thermal management applications.