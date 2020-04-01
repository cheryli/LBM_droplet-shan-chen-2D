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
$$ \mathrm{d} V = d^3\mathbf{x} = \mathrm{d}x \mathrm{d}y \mathrm{d}z \nonumber$$ 
Then, let's image three more velocity coordinates $\xi _x, \xi _y, \xi _z $ which constitute to a 6-dimensional phase space with three position coordinates. A point in this phase space has the a differential volume element as: 
$$\mathrm{d} V = \mathrm{d}^3\mathbf{x}\,\mathrm{d}^3\mathbf{\xi} = \mathrm{d}x \mathrm{d}y \mathrm{d}z \mathrm{d}\xi _x \mathrm{d}\xi _y \mathrm{d}\xi _z \nonumber$$
So that we can define a density distribution $ f(\mathbf{x}, \xi, t) $ of the particles in that 6-dimensional phase space as:
$$ \mathrm{d} N = f(\mathbf{x}, \mathbf{\xi}, t) \mathrm{d}^3\mathbf{r}\,\mathrm{d}^3\mathbf{\xi}\nonumber $$
Here $ d N $ is the number of molecular which all have positions lying within a volume element $ d^3\mathbf{r} $ about $\mathbf{r}$ and velocities lying within a volume element $ d^3\xi $ about $\xi$ ,at time $t $.</p>
<br/>

Finally, the distribution function is also connected to the macroscopic variables using its **moments**.

For instances, the **mass density** as the moment:
<p> $$ \rho(\mathbf{x}, t) = \int f(\mathbf{x}, \xi, t)\,  d^3 \xi  $$ </p><br/>

The **momentum density** as:
<p> $$ \rho(\mathbf{x}, t) u(\mathbf{x}, t) = \int \xi f(\mathbf{x}, \xi, t) \, d^3 \xi $$ </p>
&emsp; note that $ u(\mathbf{x}, t) $ is the local mean velocity of the fluid.
<br/>

The **total energy density** as:
<p> $$ \rho (\mathbf{x}, t) E(\mathbf{x}, t) = \frac{1}{2} \int \left| \xi ^2 \right| f(\mathbf{x}, \xi, t) \, d^3 \xi $$ </p>

&emsp; This contains two types of energy: the **kinetic energy** $ \frac{1}{2} \rho u^2 $ due to the bulk motion of the fluid and the **internal energy** due to the random thermal motion of the particles.

The **internal energy** as:
<p> $$ \rho(\mathbf{x}, t) e(\mathbf{x}, t) = \int \left|v^2 \right| f(\mathbf{x}, \xi, t) \, d^3 \xi  $$ </p>

&emsp; here we introduce the third velocity: **relative velocity $v$**, which represent the deviation of the particle velocity from the local mean velocity:
<p> $$ v(\mathbf{x}, t) = \xi (\mathbf{x}, t) - u(\mathbf{x}, t) $$ </p>

### 1.2 A brief Derivation of Boltzmann Equation

... to be continue ...
<p> 
$$ \frac{\partial f}{\partial t} + \xi \cdot \nabla f  + a \cdot \nabla_{\xi} f = \mathbf{\Omega}(f) $$ </p>

Then, collision term given by boltzmann based on "molecular chaos assumption" is too complicated and has so much challenges to solve. Therefore, Bhatnagar, Gross and Krook simplified collision term as so called **BGK-model**:
<p>
$$ \frac{\partial f}{\partial t} + \xi \cdot \nabla f  + a \cdot \nabla_{\xi} f = \frac{1}{\tau} \left( f^{eq} - f \right)  \label{ref_cbm_bgk}$$ </p>

where $\frac{1}{\tau} $ is the collision frequency, $f^{eq}$ is Maxwell-Boltzmann distribution function.
<p>
$$ f^{eq}(\mathbf{x}, \xi, t) = \frac{\rho}{(2 \pi RT)^ {d/2}} exp\left[-  \frac{(\xi - u)^2}{2RT} \right]  \label{ref_ceq} $$
</p>

&emsp;here we can see, the BGK model assumed the effect of collision term is to force the distribution function back to the Maxwell-Boltzmann distribution and the rate at which this occurs is proportional to the collision frequency. And the constant $ \tau $ is known as the **relaxation time** which directly determines the transport coefficients such as the viscosity and heat diffusivity. 

[paragraph](### "1.2 A brief Derivation of Boltzmann Equation")

<br/>

### 1.3 Macroscopic Conservation Equation
<br/>

### 1.4 Chapman-Enskog Analysis
<br/>

## 2. Lattice Boltzmann Method
<br/>

### 2.1 Discretisation of Boltzmann Equation
Recall the [section 1.2](# "1.2 A brief Derivation of Boltzmann Equation") , we have the continues Boltzmann equation with BGK collision term as:
<p>$$ \frac{\partial f}{\partial t} + \xi \cdot \nabla f  + a \cdot \nabla_{\xi} f = \frac{1}{\tau} \left( f^{eq} - f \right)  \tag{\ref{ref_cbm_bgk}} $$</p>

&emsp; and the equilibrium distribution function $f^{eq}$ as:
<p> $$ f^{eq}(\mathbf{x}, \xi, t) = \frac{\rho}{(2 \pi RT)^ {d/2}} exp\left[-  \frac{(\xi - u)^2}{2RT} \right]  \tag{\ref{ref_ceq}} $$ </p>


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
