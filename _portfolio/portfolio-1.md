---
title: "Embedded Pressure Sensing for Dog Bite Force Measurement"
excerpt: "Short description of portfolio item number 1<br/><img src='/images/DogBiteXSection.png' alt='mage of Dog Bite Cross-section' style='max-width:100%; height:auto; width:450px;'>"
collection: portfolio
---

<div style="text-align: center;">
    <img src="/images/DogBiteXSection.png" alt="design" style="max-width:100%; height:auto; width:90%; justify-content: center;">
</div>
<p style="text-align: center; font-size: 0.9em; color: #888; margin-top: 0;">Figure 1: Completed Model of the Design</p>

### Overview  
In collaboration with the Travis County Medical Examiner’s Office, I worked with a team of four people to develop a device to measure and record dog bite force. The device was designed for capturing data from small to medium-sized breeds. Existing solutions lacked realism, requiring human involvement and offering only instantaneous measurements. Our goal was to create a passive, standalone device that could continuously capture bite force data in a natural setting for forensic and behavioral analysis.

---

### Design  
The device was engineered to satisfy the following baseline requirements: resemble a familiar dog toy to encourage interaction, record bite data over a multi-minute window, support export of recorded data in a standard format, remain compact and low-cost for small-scale testing, provide a pathway for future empirical validation with physical prototypes. The proposed form factor was a bone-shaped device with a central rod as the primary bite target and two outer endcaps to house electronics. The rod enclosed a pressurized polyethylene bladder designed to deform slightly under bite force. A commercial rubber toy was used as a protective sleeve, and the endcaps were 3D printed using ABS plastic for mechanical protection.

<div style="text-align: center;">
    <img src="/images/DogBiteExploded.jpg" alt="exploded_view" style="max-width:100%; height:auto; width:90%; justify-content: center;">
</div>
<p style="text-align: center; font-size: 0.9em; color: #888; margin-top: 0;">Figure 2: Exploded View of the Design</p>

Finite element analysis was used to simulate mechanical durability under a conservative applied load of 200 lbs, since small dog breed bite forces usually are in the range of 50-100lbs. While simulation results showed that components remained under material yield limits, these simulations were based on idealized conditions and were not validated with physical testing due to current world events.

---

### Sensing and Software 
The sensing method relied on a pressure transducer (MPX5700) connected to the internal bladder. As dogs bit the center rod, the internal pressure would increase, and the sensor output was captured using an Arduino Nano microcontroller. The Arduino firmware sampled analog pressure data and logged values to a CSV text file. The code was functional on a breadboarded prototype but was not integrated into a final, tested enclosure due to current world events.

---

### Deliverables  
The project produced a CAD model, engineering drawings, simulation results, embedded code, and a manufacturing guide. These materials provide a starting point for future prototyping and validation work.