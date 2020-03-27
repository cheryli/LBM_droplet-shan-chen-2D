---
layout: default
---

# Brief introduction to LBM
## 1. Start with Boltzmann Equation
### 1.1 Distribution Function
&emsp;There are different views between LBM and other CFD methods. On the one hand, most of CFD methods directly solve the N-S equations by treating the fluid as a "control volume", which means that volume is small enough to be a differential volume of the whole flow and large enough to contain infinite molecules so that can be viewed as a continuous medium at the mean time. However, one the other hand, molecular dynamics trace every molecular using Newton's second law. However, lattice Boltzmann method study the probability density distribution function of the particle, which is the statistical characteristics of the flow. So, what is the PDF(probability density distribution) of particles?<br/>
&emsp;Firstly, we are all familia with the 3-dimensional space which has three position coordinates $x, y, z$. The small differential volume element is: $$ \mathrm{d} V = d^3\mathbf{r} = \mathrm{d}x \mathrm{d}y \mathrm{d}z $$  Then, let's image three more velocity coordinates $v_x, v_y, v_z $ which constitute to a 6-dimensional phase space with three position coordinates. A point in this phase space has the a differential volume element as: $$ \mathrm{d} V = \mathrm{d}^3\mathbf{r}\,\mathrm{d}^3\mathbf{r} = \mathrm{d}x \mathrm{d}y \mathrm{d}z \mathrm{d}v_x \mathrm{d}v_y \mathrm{d}v_z $$