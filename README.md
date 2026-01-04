# 🛰️ Phoenix-1: CubeSat GNC Framework
**3-Axis Attitude Control System (ACS) for a 3U Nanosatellite**


## 📖 Executive Summary
The **Phoenix-1** project is a high-fidelity Guidance, Navigation, and Control (GNC) simulation developed in MATLAB/Simulink. The objective is to design a control system capable of **detumbling** a 3U CubeSat after deployment and achieving high-precision **nadir-pointing** (Earth-facing orientation). 

This framework models non-linear rigid body dynamics, handles actuator saturation for reaction wheels, and utilizes quaternion-based feedback to avoid mathematical singularities (gimbal lock).

---

## 🛠 Project Specifications

| Parameter | Value | Details |
| :--- | :--- | :--- |
| **Form Factor** | 3U CubeSat | $10 \times 10 \times 30\text{ cm}$ |
| **Mass** | $4.0\text{ kg}$ | Uniform distribution assumed |
| **Actuators** | 3-Axis Reaction Wheels | Max Torque: $0.004\text{ N}\cdot\text{m}$ |
| **Control Law** | Nonlinear PID | Quaternion feedback |
| **Primary States** | 13-DOF | Pos (3), Vel (3), Quat (4), Omega (3) |

---

## 📐 Mathematical Foundations

### 1. Moments of Inertia
For a rectangular prism of mass $m$, width $w$, height $h$, and depth $d$, the principal moments are calculated as:
* $I_{xx} = \frac{1}{12} m (h^2 + d^2)$
* $I_{yy} = \frac{1}{12} m (w^2 + d^2)$
* $I_{zz} = \frac{1}{12} m (w^2 + h^2)$

### 2. Equations of Motion
The plant model is driven by **Euler’s Equations for Rigid Body Rotation**:

$$M = I \dot{\omega} + \omega \times (I \omega)$$

Where $M$ represents the sum of external and control moments, $I$ is the inertia matrix, and $\omega$ is the angular velocity in the body frame.



---

## 🚀 Project Roadmap

- [ ] **Phase 1: Plant Modeling** - Deriving Inertia Matrices and setting up the Nonlinear 6-DOF physics engine.
- [ ] **Phase 2: Guidance & Navigation** - Implementation of Coordinate Frames (Body, ECI) and Quaternion kinematics.
- [ ] **Phase 3: Controller Design** - PID tuning, actuator saturation logic, and anti-windup implementation.
- [ ] **Phase 4: Visualization & Verification** - 3D animation and Monte Carlo robustness testing.

---

## 📂 Repository Structure
* `/src`: Contains all functional code.
    * `/models`: Simulink (.slx) files for the Plant and Controller.
    * `/scripts`: MATLAB (.m) scripts for initialization and plotting.
    * `/functions`: Custom helper functions (e.g., cross-product matrices).
* `/docs`: Technical derivations, LaTeX notes, and hardware spec sheets.
* `/results`: Simulation outputs, `.mat` data files, and performance plots.

---

## 💻 Getting Started
1. **Initialize Workspace:** Run `/src/scripts/init_params.m` to load mass properties and initial conditions into the MATLAB workspace.
2. **Run Simulation:** Open `/src/models/Phoenix_ACS.slx` and click 'Run'.
3. **Analyze:** Use the scoped outputs in Simulink or run `post_process.m` to generate performance metrics.

---

**Author:** [Your Name]  
**Lead Documentation Engineer** | Aerospace Engineering Junior  
**Affiliation:** UCSD Design, Build, Fly (DBF)
