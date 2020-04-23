---
layout: default
title: HCZ Model for Multiphase Flow
---

[**Back to the introduction.**](https://cheryli.github.io/LBM_droplet-shan-chen-2D)

 
You can also refer to the original thesis: [He et al.(1999)](https://doi.org/10.1006/jcph.1999.6257) and [Zhang et al.(2000)](https://doi.org/10.1016/S0010-4655(00)00099-0), and this model has been developed for many years so a review of recent researches using this model is necessary for its best performance. 

---

## Basic of Model

&emsp;This model introduced two distribution functions: a pressure distribution function $ \overline{g}_i $ which is able to recover the [N-S equation](https://en.wikipedia.org/wiki/Navier%E2%80%93Stokes_equations), and a index distribution function $ \overline{f}_i $ which is able to recover the [Cahn-Hilliard equation](https://en.wikipedia.org/wiki/Cahn%E2%80%93Hilliard_equation) to track the interface. And they satisfy the following evolution equations:

<p>$$
    \overline{f}_i(x + \mathbf{e}_i \delta_x, t + \delta_t) - \overline{f}_i(x, t)    
    =   - \frac{\overline{f}_i(x, t) - f_i^{eq}(x, t)}{\tau}
        - \frac{(2 \tau - 1)}{2 \tau}
        \frac{(\mathbf{e}_i - u) \cdot \nabla \psi(\phi)}{RT} 
        \Gamma_i(u) \delta_t,
$$</p>

<p>$$
\begin{aligned}
    &\overline{g}_i(x + \mathbf{e}_i \delta_x, t + \delta_t) - \overline{g}_i(x, t)     \\
    &=   - \frac{\overline{g}_i(x, t) - g_i^{eq}(x, t)}{\tau}
        - \frac{(2 \tau - 1)(\mathbf{e}_i - u)}{2 \tau}
        \cdot   \big[ \, 
            \Gamma_i(u)(F_s + G) - (\Gamma_i(u) - \Gamma_i(0)) \nabla \psi(\rho) \, 
        \big] \delta_t.
\end{aligned}
$$</p>

&emsp;Setting the time step $ \delta_t $ and the space step $ \delta_x $ both equal to 1, and remember that $c_s^2 = RT = 1/3$, we have the time evolution functions as:

<p>$$
    \overline{f}_i(x + \mathbf{e}_i, t + 1) - \overline{f}_i(x, t)
    =   - \frac{\overline{f}_i(x, t) - f_i^{eq}(x, t)}{\tau}
        - \frac{(2 \tau - 1)}{2 \tau}
        \frac{(\mathbf{e}_i - u) \cdot \nabla \psi(\phi)}{c_s^2} 
        \Gamma_i(u),           \label{LBE_f}
$$</p>

<p>$$
\begin{aligned}
    &\overline{g}_i(x + \mathbf{e}_i, t + 1) - \overline{g}_i(x, t) \\
    &=   - \frac{\overline{g}_i(x, t) - g_i^{eq}(x, t)}{\tau}
        - \frac{(2 \tau - 1)(\mathbf{e}_i - u)}{2 \tau}
        \cdot   \big[ \, 
            \Gamma_i(u)(F_s + G) - (\Gamma_i(u) - \Gamma_i(0)) \nabla \psi(\rho) \, 
        \big],          
\end{aligned}       \label{LBE_g}
$$</p>

where $u$ is the marco velocity, $F_s$ is the surface tension force and $G$ is the gravity force, they are all vectors(have component in different direction). $\Gamma(u)$ is a function of u as follows:

<p>$$
\Gamma_i(u) = \omega_i \left[
    1 + \frac{\mathbf{e}_i \cdot u}{c_s^2}
    + \frac{(e_i \cdot u)^2}{2 c_s^4}
    - \frac{u^2}{2 c_s^2}
\right].
$$</p>

$f_i^{eq}$ and $g_i^{eq}$ are the corresponding equilibrium distributions:

<p>$$
f_i^{eq} = \phi \Gamma_i(u) = \omega_i \phi \left[
    1 + \frac{\mathbf{e}_i \cdot u}{c_s^2}
    + \frac{(e_i \cdot u)^2}{2 c_s^4}
    - \frac{u^2}{2 c_s^2}
\right],
$$</p>

<p>$$
g_i^{eq} = \omega_i \left[
    p + \rho c_s^2 \left(
        \frac{\mathbf{e}_i \cdot u}{c_s^2}
        + \frac{(e_i \cdot u)^2}{2 c_s^4}
        - \frac{u^2}{2 c_s^2}
    \right)    
\right].
$$</p>

The index function $\phi$, the pressure $p$ and the velocity $u$ can be calculated using:

<p>$$
\begin{aligned}
    \phi &= \sum \overline{f}_i, \\
    p &= \sum \overline{g}_i - \frac{1}{2} u \cdot \nabla \psi(\rho) \delta_t,   \\
    \rho c_s^2 u &= \sum \mathbf{e}_i \overline{g}_i + \frac{c_s^2}{2} (F_s + G) \delta_t.  
\end{aligned}   \label{macro}
$$</p>

Note that the system has an additional fluid: the index fluid and an additional variable: the density of index fluid $\phi$ which indicate the component of the fluid occupying this lattice node. If $\phi$ equals the index density of light(or heavy) fluid $\phi = \phi_l(\phi_h)$, the density of the real fluid is $\rho = \rho_l(\rho_h)$, and the index density between the light and heavy index fluid $(\phi_l < \phi < \phi_h)$ is the interface reign. So we can linearly map the index density to the density, viscosity of the real fluid as flowers:

</p>$$
\begin{aligned}
    \rho(\phi) &= \rho_l \frac{\phi - \phi_l}{\phi_h - \phi_l} (\rho_h - \rho_l), \\
    \nu(\phi) &= \nu_l + \frac{\phi -\phi_l}{\phi_h - \phi_l} (\nu_h - \nu_l),
\end{aligned}
$$</p>

and the surface tension $F_s$ can be calculated once we know the index density$\phi$:

<p>$$ F_s = \kappa \phi \nabla \nabla^2 \phi, $$</p>

where $\kappa$ can be used to adjust the strength of the surface tension. And the gravity force can be added as:

<p>$$ G = \rho \mathrm{g}, $$</p>

where $\mathrm{g}$ is the [gravitational constant](https://en.wikipedia.org/wiki/Gravitational_constant), of course in lattice unit.

&emsp;We should notice that the $\psi(\phi)$ used in equation (\ref{LBE_f}) is different from the $\psi(\rho)$ used in equation (\ref{LBE_g}) even thorough they both represent the volume effect:

<p>$$
\begin{aligned}
    \psi(\rho) &= p - \rho RT    \\
    \psi(\phi) &= p_{th} - \phi RT
\end{aligned}
$$</p>

where $p$ is the hydrodynamic pressure(real pressure) of the fluid, and can be calculated from the discrete distribution functions using equation (\ref{macro}). However, $p_{th}$ represent the thermodynamic pressure only used to achieve the phase segregation, and can be calculated from the [equation of state](https://en.wikipedia.org/wiki/Equation_of_state), for example, we use the Carnahan-Starling equation of state, then:

<p>$$
p_{th} = \phi RT \frac{
    1 + \frac{b \phi}{4} + \left( \frac{b \phi}{4} \right)^2 - \left( \frac{b \phi}{4} \right)^3 
}{
    \left( 1 - \frac{b \phi}{4} \right)^3     
} - a \phi^2
$$</p>