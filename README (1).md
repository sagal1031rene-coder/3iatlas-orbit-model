# 3iatlas-orbit-model: High-Precision Numerical Trajectory Validation for Interstellar Comet 3I/ATLAS

[![License: MIT](https.img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![AAS-AASTeX6.31](https://img.shields.io/badge/AAS-AASTeX_v6.31-orange.svg)](https://journals.aas.org/)

This repository contains the official numerical simulation engine, trajectory propagation scripts, LaTeX source files, and high-resolution figures for the manuscript titled:

**"High-Precision Numerical Validation of Hyperbolic Trajectories: Assessing Non-Gravitational Forces in Interstellar Comet 3I/ATLAS"**  
Submitted to *The Astronomical Journal* (AAS / IOP Publishing).

---

## Author & Contact Information

* **Lead Author & System Architect:** Rene Sagal Andrade  
* **Affiliation:** Independent Researcher, Mexico City, Mexico  
* **ORCID:** [0009-0003-5574-5348](https://orcid.org/0009-0003-5574-5348)  
* **Email:** `sagal233rene@outlook.com`  
* **Repository URL:** `https://github.com/sagal1031rene-coder/3iatlas-orbit-model`

---

## Abstract & Key Physical Findings

The `3iatlas` platform models the extreme kinematics of hyperbolic interstellar candidate **3I/ATLAS** during its inner Solar System transit. By coupling Newtonian heliocentric gravity with solar radiation pressure and asymmetric cometary outgassing (20% mass loss inside $2.5\text{ AU}$ and an $8^\circ$ jet offset), the adaptive **Runge-Kutta-Fehlberg 4th/5th-order (RK45)** integrator operates under a strict truncation tolerance of $\text{TOL} = 10^{-9}$.

Under spatial scale calibration ($R = 1.3\text{ km}$, $\rho = 550\text{ kg/m}^3$, $\text{AMR} = 1.05 \times 10^{-6}\text{ m}^2/\text{kg}$), the integration dynamically contracts its step-size to $h_{\min} \approx 1.2 \times 10^2\text{ s}$ near perihelion, resolving numerical stiffness and converging seamlessly to the official NASA observational perihelion distance of $q = 1.3565\text{ AU}$.

### Summary of Orbital & Non-Gravitational Results

| Physical / Numerical Parameter | Value | Unit | Description / Constraint |
| :--- | :---: | :---: | :--- |
| **Eccentricity ($e$)** | `6.1414` | -- | NASA Baseline Hyperbolic Trajectory |
| **Hyperbolic Excess Speed ($v_{\infty}$)** | `64.04` | km/s | Asymptotic Inbound/Outbound Speed |
| **Nucleus Radius ($R$)** | `1.3` | km | Kilometric Scale Calibration ($1300\text{ m}$) |
| **Bulk Density ($\rho$)** | `550.0` | kg/m$^3$ | Typical Cometary Porous Nucleus |
| **Initial Mass ($M_0$)** | $5.06 \times 10^{12}$ | kg | Derived Spherical Nucleus Mass |
| **Area-to-Mass Ratio ($\text{AMR}$)** | $1.05 \times 10^{-6}$ | m$^2$/kg | Normalized Cross-Sectional Area to Mass |
| **Jet Offset Angle ($\theta$)** | `8.0` | deg | Canonical Rotation Relative to Sun Vector |
| **Observational Perihelion ($q_{\text{obs}}$)** | **1.3565** | **AU** | **NASA Official Heliocentric Proximity** |
| **Simulated Perihelion ($q_{\text{sim}}$)** | **1.3565** | **AU** | **RK45 Converged Trajectory Result** |
| **Max Non-Grav. Accel. ($a_{\text{max}}$)** | $6.48 \times 10^{-12}$ | m/s$^2$ | Solar Radiation + Asymmetric Outgassing |
| **Cumulative Spatial Drift ($\Delta x$)** | **236.36** | **meters** | Integrated 138-day Active Outgassing Deflection |
| **Integrator Local Tolerance** | $10^{-9}$ | -- | RK45 Step-Size Control Threshold |
| **Asymptotic Exit Target** | **Lyra** | -- | Destination Constellation Coordinates |

---

## Repository Structure

```
3iatlas-orbit-model/
├── README.md                              # This documentation file
├── LICENSE                                # MIT Open Source License
├── 3iatlas_orbit_simulation.py            # Main Standalone Python Trajectory Propagator
├── AJ_3I_ATLAS_Trajectory_Validation.tex  # Complete Manuscript in AASTeX v6.31 LaTeX Format
├── AJ_3I_ATLAS_Trajectory_Validation.pdf  # Compiled Manuscript PDF for The Astronomical Journal
├── Cover_Letter_Astronomical_Journal.pdf  # AAS Cover Letter to Executive Editor
├── fig1_heliocentric_orbit.png            # High-Resolution Heliocentric Orbit Plot
└── figures/                               # Additional Trajectory and Energy Diagnostics
```

---

## Installation & Prerequisites

The numerical solver relies on standard scientific Python packages:

```bash
pip install numpy scipy matplotlib astropy
```

### Python Dependencies:
* `python >= 3.8`
* `numpy >= 1.21`
* `scipy >= 1.7` (for `scipy.integrate.solve_ivp`)
* `matplotlib >= 3.4`
* `astropy >= 5.0`

---

## Quick Start & Reproduction

To run the orbital simulation, propagate the trajectory through perihelion, verify convergence, and generate the heliocentric orbit plot, execute:

```bash
python 3iatlas_orbit_simulation.py
```

### Expected Output:
```text
=======================================================
 3I/ATLAS RK45 NUMERICAL TRAJECTORY INTEGRATION        
=======================================================
 Simulated Perihelion Distance (q_sim): 1.3565 AU
 Target Observational Perihelion:        1.3565 AU
 Status: CONVERGED WITH TOLERANCE 10^-9
=======================================================
Saved Figure 1 to fig1_heliocentric_orbit.png
```

---

## Software & Citation

If you use this codebase or numerical model in your research, please cite:

```bibtex
@article{Sagal2026_3I_ATLAS,
  author       = {Rene Sagal Andrade},
  title        = {High-Precision Numerical Validation of Hyperbolic Trajectories: Assessing Non-Gravitational Forces in Interstellar Comet 3I/ATLAS},
  journal      = {The Astronomical Journal},
  year         = {2026},
  note         = {Submitted},
  url          = {https://github.com/sagal1031rene-coder/3iatlas-orbit-model}
}
```

---

## License

This project is open-source software licensed under the **MIT License**. See [LICENSE](LICENSE) for details.
