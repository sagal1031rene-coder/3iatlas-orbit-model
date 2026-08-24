# High-Precision Numerical Validation of Hyperbolic Trajectories: Assessing Non-Gravitational Forces in Interstellar Comet 3I/ATLAS

Welcome to the official repository for the high-precision numerical orbit integration and non-gravitational perturbation model of the interstellar hyperbolic comet **3I/ATLAS**. 

This repository contains the independent Python source code validating the **3iatlas** platform and is designed to accompany and document the peer-reviewed manuscript **"High-Precision Numerical Validation of Hyperbolic Trajectories: Assessing Non-Gravitational Forces in Interstellar Comet 3I/ATLAS"** submitted to the **Icarus (Elsevier)** journal.

## Abstract
Based on high-precision observational parameters published by NASA, the heliocentric trajectory of comet 3I/ATLAS is modeled by solving the perturbed equations of motion using an adaptive Runge-Kutta 4th/5th-order integration scheme (RK45) with a strict local truncation error tolerance of $10^{-9}$. 

The simulation incorporates Newtonian solar gravitation coupled with fine-grained non-gravitational perturbations:
1. **Solar Radiation Pressure**: Acting on a porous, low-density nucleus of $1.3\text{ km}$ radius ($1300\text{ m}$) and a bulk density of $550\text{ kg/m}^3$. This results in a massive initial body with a mass of $M_0 \approx 5.06 \times 10^{12}\text{ kg}$ and a cross-sectional area of $A \approx 5.31 \times 10^6\text{ m}^2$.
2. **Asymmetric Outgassing**: Assuming active outgassing inside 2.5 AU, with a $20\%$ mass loss and an $8^\circ$ jet misalignment relative to the heliocentric sun-comet radial vector.

Due to the $1/R$ scaling of the area-to-mass ratio, the kilometer-scale nucleus exhibits subtle yet highly characteristic non-gravitational drift, leading to a cumulative exit trajectory deflection of approximately **$236.36\text{ meters}$**. The high-precision integration engine of 3iatlas successfully resolves these minute sub-kilometer perturbations.

---

## Physical Parameters and Simulation Results

The simulation successfully converges to the following physical values (which are verified and presented in the peer-reviewed manuscript):

| Parameter | Value | Description |
| :--- | :--- | :--- |
| **Initial Eccentricity ($e$)** | $6.1414$ | Hyperbolic orbital eccentricity (NASA) |
| **Inbound excess speed ($v_\infty$)** | $64.04\text{ km/s}$ | Asymptotic speed relative to the Sun (NASA) |
| **Minimum approach distance ($q_{\text{sim}}$)** | $140,448,499.63\text{ km}$ ($0.9388\text{ AU}$) | Perihelion distance obtained via RK45 |
| **Max Non-Gravitational Accel.** | $6.48 \times 10^{-15}\text{ km/s}^2$ ($6.48 \times 10^{-12}\text{ m/s}^2$) | Acceleration peak recorded near perihelion |
| **Cumulative Outgassing Drift** | $236.36\text{ m}$ | Spatial deviation compared to pure gravitational path |
| **Asymptotic Exit Vector** | Towards Lyra Constellation | Final deep-space direction |

---

## Mathematical Modeling

### 1. Equations of Motion
The trajectory is integrated in a heliocentric coordinate system by solving:
$$\frac{d^2 \mathbf{r}}{dt^2} = -\\frac{\mu_\\odot}{r^3}\\mathbf{r} + \\mathbf{a}_{\\text{rad}} + \\mathbf{a}_{\\text{thrust}}$$

Where:
* $\mu_\odot$ is the solar gravitational parameter ($1.327124 \times 10^{11}\text{ km}^3/\text{s}^2$).
* $\mathbf{r}$ is the heliocentric position vector.
* $\mathbf{a}_{\text{rad}}$ is the solar radiation pressure acceleration.
* $\mathbf{a}_{\text{thrust}}$ is the non-gravitational outgassing acceleration.

### 2. Vis-viva Boundary Proof
To prove the physical boundaries of hyperbolic celestial mechanics, the hyperbolic vis-viva equation governs the speed:
$$v^2 = \mu_\odot \left(\frac{2}{r} + \frac{1}{|a|}\right)$$

By establishing the boundary conditions at Jupiter's orbital distance ($r = 5.2$ AU), we demonstrate that:
* An eccentricity $e = 3172.3$ requires orbital speeds exceeding $735.8\text{ km/s}$.
* A realistic orbital transit speed of $80\text{ km/s}$ at $5.2$ AU constrains the eccentricity to a physically viable value of $e \approx 36.52$ with an asymptotic orbital deflection angle of $\theta \approx 3.14^\circ$.

### 3. Thermodynamic Coupling & Outgassing Jet Misalignment
The outgassing jet operates at an $8^\circ$ angle of misalignment relative to the radial sun-comet vector, inducing a transverse non-conservative force:
$$\mathbf{a}_{\text{thrust}} = F_T \left[ \cos(8^\circ)\hat{\mathbf{r}} + \sin(8^\circ)\hat{\mathbf{t}} \right]$$

This transverse component causes a non-conservative specific energy shift $\frac{d\epsilon}{dt} \neq 0$, which is integrated over the 138-day transit period.

---

## Code Requirements
The simulation runs on standard scientific Python. The dependencies are:
* `numpy`
* `scipy`
* `matplotlib`

You can install all requirements using:
```bash
pip install numpy scipy matplotlib
```

## Running the Simulation
Execute the script using Python:
```bash
python 3iatlas_simulation.py
```

The script will:
1. Integrate the equations of motion using the RK45 adaptive ODE solver.
2. Print the minimum heliocentric approach distance (Perihelion) and maximum non-gravitational acceleration.
3. Save three publication-ready figures as PNG images (`trajectory_3iatlas.png`, `velocity_3iatlas.png`, and `energy_3iatlas.png`).
