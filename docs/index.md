---
layout: default
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

---

&emsp;Here we get the Boltzmann Equation:
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

---

<br/><br/><br/>... to be continue ...<br/><br/><br/>

---

&emsp; The **lattice Boltzmann equation(LBE)** is:
<p> $$ f_i(x + \mathbf{e}_i \delta_t, t + \delta_t ) - f_i(x, t) = \delta_t \Omega_i(x,t)\ $$ </p>

where $f_i(x, t)$ is the **discrete-velocity distribution function**, often called the particle **populations** and $ e_i = (e_{ix}, e_{iy}, e_{iz})$ is a set of **discrete velocity**.
<br/>

---

&emsp;Here we get the **lattice Boltzmann equation with BGK collision operator**, also sometimes called the **_lattice BGK(LBGK) equation_**:
<p> $$ f_i(x + \mathbf{e}_i \delta_t, t + \delta_t ) - f_i(x, t) = - \frac{\delta_t}{\tau} [ f_i(x, t) - f_i^{eq}(x, t) ] .$$ </p>

Usually in our simulations, we use *lattice units* to set time step $\delta_t = 1$ and lattice space $\delta_x = 1$, which represent the time and space resolutions, respectively. 

&emsp;So that we can define a **lattice constant** $c = \delta_x / \delta_t = 1$. And the **LBGK equation** becomes:
<p> $$ f_i(x + \mathbf{e}_i, t + 1 ) - f_i(x, t) = - \frac{1}{\tau} [ f_i(x, t) - f_i^{eq}(x, t) ] .$$ </p>

&emsp;The **discrete equilibrium distribution function** $f^{eq}$ as:

<p> $$ f_i^{eq} = \rho w_i \left[1 + \frac{e_i u}{c_s^2} + \frac{(e_i u)^2}{2c_s^4} - \frac{u^2}{2c_s^2} \right]  , $$</p>

with the **wight** $w_i$ specific to the chosen velocity set. The constant $c_s$ determines the relation $ p = c_s^2 \rho $ between pressure $p$ and density $\rho$ in basic isothermal LBE. So it represents the isothermal model's **speed of sound**. The value is given by $ c_s^2 = \frac{1}{3}c = \frac{1}{3} \delta_x^2 / \delta_t^2.$ And the **kinematic viscosity** of the fluid $\nu$ is determined by the relaxation time $\tau$ as $ \nu = c_s^2 (\tau - 0.5)$.
<br/>

### 2.2 MRT Collision Operators
&emsp;The BGK model is an elegant and simple collision operator of LBE, however, it suffers from the accuracy(especially for large viscosities) and stability(in particular for small viscosities or large Reynolds numbers). So we have **multiple-relaxation-time(MRT)** collision operators to offer more free parameters that can be tuned to overcome these problems.

The main idea of MRT collision operators is to perform the collision in **moment space** instead of the velocity space. We use a carefully chosen *transformation matrix* $M$ to linearly map the *population space* $f$ to the *moment space* $m$, using $ m = Mf $. So that the $m_k$ directly correspond to the hydrodynamic moments(density, momentum, momentum flux tensor, etc). Thus, it's possible to affect those terms by choosing different relaxation rates $w_i$. In contrast, the BGK model relaxes all the moments with the same relaxation rate $w = 1 / \tau$. 

&emsp; LBE with MRT collision operator:

<p>$$ f_i(x + \mathbf{e}_i, t + 1 ) - f_i(x, t) = -M^{-1} S M \left[f_i(x,t) - f_i^{eq}(x,t) \right]  ,$$</p>

where S is the relaxation matrix and it's a diagonal matrix $ S = diag(w_1, w_2, w_3, \dots, w_q) $

&emsp; Left multiply M to the both side of the above equation, we get:

<p>$$ m^* - m = -S(m -m^{eq}) .$$</p>


<br/>

### 2.3 Discrete Velocity Models
&emsp;D2Q9 model for two-dimensional simulations:

<!-- ![D2Q9.png](https://i.loli.net/2020/04/02/OxP75GjokFCvWac.png) -->

<div style="align: center">
    <img src="https://i.loli.net/2020/04/02/OxP75GjokFCvWac.png">
</div> 

<br/>
the weights are $ w_0 = 4/9, w_{1-4} = 1/9, w_{5-8} = 1/36 $,  and the discrete velocity is given as:
<p>$$ 
[e_0, e_1, e_2, e_3, e_4, e_5, e_6, e_7, e_8] = c \left[
\begin{matrix}
    0 & 1 & 0 & -1 & 0  & 1 & -1 & -1 & 1  \\
    0 & 0 & 1 & 0  & -1 & 1 &  1 & -1 & -1
\end{matrix}    
\right].
$$ </p>
Remember that $ c = \delta_x / \delta_t $ is the lattice constant.
<br/><br/><br/>

&emsp;For MRT model, we choose the transformation matrix $M$ as:
<p>$$
M_{D2Q9} = \left[
\begin{matrix}
    M_\rho      \\
    M_e         \\
    M_\epsilon  \\
    M_{j_x}     \\
    M_{q_x}     \\
    M_{j_y}     \\
    M_{q_y}     \\
    M_{p_{xx}}  \\
    M_{p_{xy}}
\end{matrix}
\right] = \left[
\begin{matrix}
    1   \\
    -4 + 3(e_x^2 + e_y^2)   \\
    4 - \frac{21}{2} (e_x^2 + e_y^2) + \frac{9}{2} (c_x^2 + c_y^2)^2  \\
    e_x \\
    \left[-5 + 3(e_x^2 + e_y^2) \right] e_x \\
    e_y \\
    \left[-5 + 3(e_x^2 + e_y^2) \right] e_y \\
    e_x^2 - e_y^2   \\
    e_x e_y
\end{matrix}
\right] = \left[
\begin{matrix}
    1  & 1  & 1  & 1  & 1  & 1  & 1  & 1  & 1   \\
    -4 & -1 & -1 & -1 & -1 & 2  & 2  & 2  & 2   \\
    4  & -2 & -2 & -2 & -2 & 1  & 1  & 1  & 1   \\
    0  & 1  & 0  & -1 & 0  & 1  & -1 & -1 & 1   \\
    0  & -2 & 0  & 2  & 0  & 1  & -1 & -1 & 1   \\
    0  & 0  & 1  & 0  & -1 & 1  & 1  & -1 & -1  \\
    0  & 0  & -2 & 0  & 2  & 1  & 1  & -1 & -1  \\
    0  & 1  & -1 & 1  & -1 & 0  & 0  & 0  & 0   \\
    0  & 0  & 0  & 0  & 0  & 1  & -1 & 1  & -1
\end{matrix}
\right],
$$</p>

where the moments $ m = Mf $ correspond to the physical quantities; i.e., $\rho$ is the density, $j_x$ and $j_y$ are components of momentum flux, $q_x$ and $q_z$ correspond to the energy flux components, $e$ and $\epsilon$ correspond to the energy and energy square, $p_{xx}$ and $p_{xy}$ correspond to the diagonal and off-diagonal components of the stress tensor.

&emsp;The equilibrium moments as:
<p> $$ m_{D2Q9}^{eq} = M f^{eq} = M  \rho \left[
\begin{matrix}
    1   \\
    \left( -2 + 3 u^2\right)    \\
    \left(1 - 3 u^2\right)  \\
    u_x \\
    - u_x  \\
    u_y \\
    - u_y \\
    \left(u_x^2 - u_y^2\right)   \\
    u_x u_y  \\
\end{matrix}
\right].
$$ </p>

you can find the detailed derivation at [here](https://cheryli.github.io/LBM_droplet-shan-chen-2D/derivation).

&emsp;The relaxation matrix is:
<p>$$ S_{D2Q9} = diag(s_\rho, s_e, s_\epsilon, s_j, s_q, s_j, s_q, s_\nu, s_\nu) .$$ </p>

We usually set $ s_\rho  = 0 $ and $ s_j = 0 $, the $s_\epsilon$ and $s_q$ are free parameters to tune. And the pressure $p$, shear viscosity $\eta$ and bulk viscosity $\eta_B$ are given by:
<p>$$ p = \rho c_s^2,   \qquad  \eta = \rho c_s^2 \left( \frac{1}{s_\nu} - \frac{1}{2} \right),    \qquad   \eta_B = \rho c_s^2 \left( \frac{1}{s_\nu} - \frac{1}{2} \right) - \frac{\eta}{3}.     $$</p>

<!-- 可折叠式内容 -->
<details>
  <summary> Click here for more information of these different viscosity coefficients: </summary>

  &emsp;Let's have a look of four different kinds of viscosity coefficients which we used very often. Note that all kind of viscosity coefficients are positive due to the [second law of thermodynamics](https://en.wikipedia.org/wiki/Second_law_of_thermodynamics). Moreover, if viscosity doesn't play an important role, we can neglect it to treat the fluid as *ideal or inviscid fluid*.

  1. coefficient of *Shear viscosity* or *dynamic viscosity* or *absolute viscosity*  $\eta$ :
  2. coefficient of *longitudinal viscosity* or *second coefficient of viscosity* $\zeta$ :
  3. coefficient of *bulk viscosity* $\eta_B$ :
  4. coefficient of *kinematic viscosity* or *momentum diffusivity* $\nu$ :

  <p> $$ \nu = \frac{\eta}{\rho},  \qquad  \eta_B = 2\eta / 3 + \zeta $$</p>

  &emsp;Now, let's consider a general viscous stress tensor $\sigma$ as:
  <p> $$
    \sigma = \eta \left( \frac{\partial u_\alpha}{\partial x_\beta} + \frac{\partial u_\beta}{\partial x_\alpha}   \right) + \zeta \, \delta_{\alpha \beta} \frac{\partial u_\gamma}{\partial x_\gamma},
  $$ </p>

  separate to the *shear stress* and *normal stress* as:
  
  <p> $$
    \sigma = \eta \left( \frac{\partial u_\alpha}{\partial x_\beta} + \frac{\partial u_\beta}{\partial x_\alpha} - \frac{3}{2} \delta_{\alpha \beta} \frac{\partial u_\gamma}{\partial x_\gamma}  \right) + \eta_B \, \delta_{\alpha \beta} \frac{\partial u_\gamma}{\partial x_\gamma},
  $$ </p>

  where $ \delta_{\alpha \beta} $ is an 2 by 2 identity matrix, and the [Einstein’s summation convention](https://en.wikipedia.org/wiki/Einstein_notation) is used.


</details>

<br/>

## 3. Forces in LBM

<br/>

## 4. Initial and Boundary Conditions

&emsp;The initial and boundary conditions can be very complicated. However, we will keep it simple for now.

### 4.1 Initial conditions：

&emsp;For most cases, we set the initial distribution function as the equilibrium state:
<p>$$
    f_i(x, \, t=0) = f_i^{eq} (x, \, t=0)
$$</p>

### 4.2 Boundary conditions:

&emsp;We will introduce two kinds of boundary conditions: Periodic and Wall.

#### 4.2.1 Periodic boundary conditions:

&emsp;Periodic boundary conditions state that *the fluid leaving the domain on one side will, instantaneously, re-enter at the opposite side*. Consequently, the momentum and mass are conserved in periodic boundary conditions. We usually this when simulating the periodic flow or just to provide a free boundary.

&emsp;Assume our lattice node is from 1 to N. When doing the propagation(streaming), we need to apply a extra rule:  
$$ x_N + 1 = x_1 $$
The periodic boundary conditions, like a bridge, connected two separate boundaries together.
<br/>

#### 4.2.2 The Wall conditions - Bounce Back:

&emsp;Note that we will only consider the **no-slip wall condition** for this moment.

&emsp;Firstly, for the cases that the wall is *stationary*. Then we can assume that *the populations hit the solid wall during the propagation will reflect back to where they originally came from*. However, based on the how much time they take for the reflection, we have the **full-way bounce back** and the **half-way bounce back**.

&emsp;Let's assume that the $x_N$ is a lattice node near the *bottom* wall. For the propagation of $D2Q9$ model:
1. full-way bounce back: $ f_{2, 5, 6}(x_N, t + 1) = f_{4, 7, 8}(x_N, t) $
2. half-way bounce back: $ f_{2, 5, 6}(x_N, t + 2) = f_{4, 7, 8}(x_N, t) $

It's straightforward that those two scheme differ at the distance they need(time they need) for the bounce back. Keep in mind that the full-way bounce back has *first-order accurate*, however the half-way bounce back has a *second-order error*.

---

&emsp;Moreover, if the wall is moving with the velocity $u_w$, the half-way bounce back reads:
<p>$$ f_i(x_N, t + 1) = f_i(x_N, t) - 2 w_i \rho \frac{e_i \cdot u_w}{c_s^2} $$</p>

<br/>

## 5. Multiphase Flow


<p>


</p>

<br/>
<br/>
<br/>

---

<p>
<!-- reference example -->
\begin{equation}
E = mc^2 \label{ref1}
\end{equation}

here is the famous equation: \ref{ref1}
<!-- ------------------------------------ -->
</p>
