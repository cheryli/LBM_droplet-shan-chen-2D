---
layout: default
title: introduction
---

# Brief introduction to LBM
## 1. Start with Boltzmann Equation
### 1.1 Distribution Function


&emsp;There are different views between LBM and other CFD methods. On the one hand, most of CFD methods directly solve the N-S equations by treating the fluid as a *"control volume"*, which means that volume is small enough to be a differential volume of the whole flow and large enough to contain infinite molecules so that can be viewed as a continuous medium at the mean time. However, one the other hand, molecular dynamics trace *every molecular* using Newton's second law. However, lattice Boltzmann method study the probability density distribution function of the particle, which is the statistical characteristics of the flow. So, what is the *PDF(probability density distribution)* of particles?<br/>
<p>
&emsp;Firstly, we are all familia with the 3-dimensional space which has three position coordinates $x, y, z$. The small differential volume element is: 

$$ \mathrm{d} V = d^3x = \mathrm{d}x \mathrm{d}y \mathrm{d}z \nonumber .$$ 

&emsp;Then, let's image three more velocity coordinates $\xi _x, \xi _y, \xi _z $ which constitute to a 6-dimensional phase space with three position coordinates. A point in this phase space has the a differential volume element as: 

$$\mathrm{d} V = \mathrm{d}^3 x\,\mathrm{d}^3\mathbf{\xi} = \mathrm{d}x \mathrm{d}y \mathrm{d}z \mathrm{d}\xi _x \mathrm{d}\xi _y \mathrm{d}\xi _z \nonumber  .$$

&emsp;So that we can define a density distribution $ f(x, \xi, t) $ of the particles in that 6-dimensional phase space as:
$$ \mathrm{d} N = f(x, \mathbf{\xi}, t) \mathrm{d}^3x\,\mathrm{d}^3\mathbf{\xi}\nonumber .$$

Here $ d N $ is the number of molecular which all have positions lying within a volume element $ d^3 x $ about $x$ and velocities lying within a volume element $ d^3\xi $ about $\xi$ ,at time $t $.</p>

&emsp;Finally, the distribution function is also connected to the macroscopic variables using its **moments**.

&emsp;For instances, the **mass density** as the moment:
<p> $$ \rho(x, t) = \int f(x, \xi, t)\,  d^3 \xi .$$ </p><br/>

&emsp;The **momentum density** as:
<p> $$ \rho(x, t) u(x, t) = \int \xi f(x, \xi, t) \, d^3 \xi ,$$ </p>
note that $ u(x, t) $ is the local mean velocity of the fluid.
<br/>

&emsp;The **total energy density** as:
<p> $$ \rho (x, t) E(x, t) = \frac{1}{2} \int \left| \xi ^2 \right| f(x, \xi, t) \, d^3 \xi ,$$ </p>

which contains two types of energy: the **kinetic energy** $ \frac{1}{2} \rho u^2 $ due to the bulk motion of the fluid and the **internal energy** due to the random thermal motion of the particles.

&emsp;The **internal energy** as:
<p> $$ \rho(x, t) e(x, t) = \int \left|v^2 \right| f(x, \xi, t) \, d^3 \xi  .$$ </p>

Here we introduce the third velocity: **relative velocity $v$**, which represent the deviation of the particle velocity from the local mean velocity:
<p> $$ v(x, t) = \xi (x, t) - u(x, t) .$$ </p>

### 1.2 A brief Derivation of Boltzmann Equation

... to be continue ...
<p> 
$$ \frac{\partial f}{\partial t} + \xi \cdot \nabla f  + a \cdot \nabla_{\xi} f = \mathbf{\Omega}(f) .$$ </p>

&emsp;Then, collision term given by boltzmann based on "molecular chaos assumption" is too complicated and has so much challenges to solve. Therefore, Bhatnagar, Gross and Krook simplified collision term as so called **BGK-model**:
<p>
$$ \frac{\partial f}{\partial t} + \xi \cdot \nabla f  + a \cdot \nabla_{\xi} f = \frac{1}{\tau} \left( f^{eq} - f \right)  \label{ref_cbm_bgk} ,$$ </p>

where $\frac{1}{\tau} $ is the collision frequency, $f^{eq}$ is Maxwell-Boltzmann distribution function:
<p>
$$ f^{eq}(x, \xi, t) = \frac{\rho}{(2 \pi RT)^ {d/2}} exp\left[-  \frac{(\xi - u)^2}{2RT} \right]  \label{ref_ceq} ,$$

where $T,\rho, u$ are the macroscopic quantities of temperature, density and fluid velocity, respectively.   $d$ is the number of spatial dimensions and the gas constant $R = k_B / m$ is given by the Boltzmann constant $k_B$ and the particle mass $m$.
</p>

&emsp;Here we can see, the BGK model assumed the effect of collision term is to force the distribution function back to the Maxwell-Boltzmann distribution and the rate at which this occurs is proportional to the collision frequency. And the constant $ \tau $ is known as the **relaxation time** which directly determines the transport coefficients such as the viscosity and heat diffusivity. 

<br/>

### 1.3 Macroscopic Conservation Equation
<br/>

### 1.4 Chapman-Enskog Analysis
<br/>

## 2. Lattice Boltzmann Method
<br/>

### 2.1 Discretisation of Boltzmann Equation
&emsp;Recall the [section 1.2](#12-A-brief-Derivation-of-Boltzmann-Equation) , we have the continues Boltzmann equation with BGK collision term as:
<p>$$ \frac{\partial f}{\partial t} + \xi \cdot \nabla f  + a \cdot \nabla_{\xi} f = \frac{1}{\tau} \left( f^{eq} - f \right)  \tag{\ref{ref_cbm_bgk}} ,$$</p>

and the equilibrium distribution function $f^{eq}$ as:
<p> $$ f^{eq}(x, \xi, t) = \frac{\rho}{(2 \pi RT)^ {d/2}} exp\left[-  \frac{(\xi - u)^2}{2RT} \right]  \tag{\ref{ref_ceq}} .$$ </p>

<br/><br/><br/>... to be continue ...<br/><br/><br/>

&emsp;Here we get the **lattice Boltzmann Equation with BGK collision operator**, also sometimes called the **_lattice BGK(LBGK) equation_**:
<p> $$ f_i(x + \mathbf{e}_i \delta_t, t + \delta_t ) - f_i(x, t) = - \frac{\delta_t}{\tau} [ f(x, t) - f^{eq}(x, t) ] .$$ </p>

Usually in our simulations, we use *lattice units* and set time step $\delta_t = 1$ and lattice space $\delta_x = 1$, which represent the time and space resolutions, respectively. 

&emsp;So that we can define a **lattice constant** $c = \delta_x / \delta_t = 1$. And the **LBGK equation** becomes:
<p> $$ f_i(x + \mathbf{e}_i, t + 1 ) - f_i(x, t) = - \frac{1}{\tau} [ f(x, t) - f^{eq}(x, t) ] $$ </p>

where $f_i(x, t)$ is the **discrete-velocity distribution function**, often called the particle **populations**. $ e_i = (e_{ix}, e_{iy}, e_{iz})$ is a set of **discrete velocity**.

&emsp;And the **discrete equilibrium distribution function** $f^{eq}$ as:

<p> $$ f^{eq} = \rho w_i \left[1 + \frac{e_i u}{c_s^2} + \frac{(e_i u)^2}{c_s^4} - \frac{u^2}{2c_s^2} \right] $$</p>

with the **wight** $w_i$ specific to the chosen velocity set. The constant $c_s$ determines the relation $ p = c_s^2 \rho $ between pressure $p$ and density $\rho$ in basic isothermal LBE. So it represents the isothermal model's **speed of sound**. The value is given by $ c_s^2 = \frac{1}{3}c = \frac{1}{3} \delta_x^2 / \delta_t^2.$
<br/>

### 2.2 MRT Collision Operators
<br/>

### 2.3 Discrete Velocity Models
<br/>

## 3. Forces in LBM
<br/>

## 4. Initial and Boundary Conditions
<br/>

## 5. Multiphase Flow


<p>


</p>




<p>
<!-- reference example -->
\begin{equation}
E = mc^2 \label{ref1}
\end{equation}

here is the famous equation: \ref{ref1}
<!-- ------------------------------------ -->
</p>
