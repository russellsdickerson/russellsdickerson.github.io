---
title: "Custom Additive Manufacturing for edible shear-thinning, viscoelastic, non-Newtonian fluids"
excerpt: "Short description of portfolio item number 1<br/><img src='/images/500x300.png'>"
collection: portfolio
---

# Syringe-Based CoreXY Icing 3D Printer  
**Mechanical Engineering Capstone Design Project**

We developed a functional prototype of a low-cost, syringe-based 3D printer for automated icing deposition on baked goods. The system was engineered for high geometric accuracy, modularity, and ease of DIY assembly under a strict cost constraint.

---

## 🛠 System Overview

- **Architecture**: Overhead **CoreXY gantry** with belt-driven motion in the X-Y plane; manual Z-axis via adjustable baseplate.
- **Extrusion Mechanism**: A **non-captive NEMA 17 stepper motor** drives a 100 mL syringe plunger using a lead screw interface.
- **Control & Firmware**:
  - **Arduino Mega** + **RAMPS 1.4**
  - **Marlin firmware**, interfaced via **Repetier-Host**
- **Mechanical Frame**:
  - Laser-cut wood frame with dovetail joints for simplified assembly
  - 3D-printed structural components (extruder mount, gliders, pulley housings)

---

## 🎯 Design Requirements

| Criterion                 | Target                     | Result                    |
|--------------------------|----------------------------|---------------------------|
| **Accuracy**             | ±2 mm in X, Y, Z axes      | Met (via steps/mm tuning) |
| **Volume Constraint**    | < 4 ft³                    | 3.58 ft³                  |
| **Budget**               | ≤ $250                     | $191.11 total             |
| **Assembly Time**        | < 48 hours (DIY)           | Met                       |
| **Cleanability**         | Tool-less syringe removal  | Met                       |

---

## 🔬 Experimental Validation

- **Motion Calibration**:
  - Factorial experiments tested effects of feed rate, print length, and movement direction
  - Diagonal motions showed higher print error due to compounded rod friction
- **Statistical Modeling**:
  - Regression + ANOVA models showed significant interactions between motion type and accuracy/time
- **Finite Element Analysis**:
  - FEA in SolidWorks identified high-stress regions at leg joints; reinforced using L-brackets

---

## ⚙️ Subsystem Breakdown

- **Extruder**:
  - Syringe-based plunger actuated by non-captive motor
  - Modular housing for easy cleaning and reloading

- **XY Motion**:
  - Belt-driven CoreXY
  - Glider-based design reduces friction and binding over traditional sliders

- **Frame**:
  - Laser-cut wood with interlocking joints
  - Acrylic baseplate for food-safe, non-absorbent surface

- **Electronics**:
  - Arduino Mega, RAMPS 1.4, stepper drivers
  - Power supply with integrated cooling ventilation

---

## 🔧 FMEA + Reliability Improvements

- **Key Fixes**:
  - Replaced slide bearings with top-mounted gliders → resolved XY binding
  - Added vent holes → mitigated overheating in electronics box
  - Upgraded belt mounting → reduced elastic deformation over time

- **Remaining Risks**:
  - Belt stretch over extended use → suggest future upgrade to Kevlar-reinforced belts

---

## 🌱 Sustainability Considerations

- **Reusability**:
  - Syringe-based extrusion avoids long, hard-to-clean tubing
- **Materials**:
  - Acrylic baseplate selected over wood/silicone to prevent mold and increase durability
- **Waste Reduction**:
  - Minimized custom parts; used standard components available at hardware stores

---

## 📉 Final BOM (Bill of Materials)

| Subsystem     | Cost     |
|---------------|----------|
| Electrical     | $92.35   |
| Extruder       | $40.00   |
| Frame          | $41.78   |
| XY System      | $16.97   |
| **Total**      | **$191.11** |

---

This project demonstrates a successful integration of low-cost components, mechanical precision, and user-centered design to realize a functional icing 3D printer suitable for DIY food customization.
