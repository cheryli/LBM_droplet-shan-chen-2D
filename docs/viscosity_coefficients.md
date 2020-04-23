---
layout: default
title: Different Kinds of Viscosity Coefficients
---

[**Back to the introduction.**](https://cheryli.github.io/LBM_droplet-shan-chen-2D)
  
  &emsp;Let's have a look of four different kinds of viscosity coefficients which we used very often. Note that all kind of viscosity coefficients are positive due to the [second law of thermodynamics](https://en.wikipedia.org/wiki/Second_law_of_thermodynamics). Moreover, if viscosity doesn't play an important role, we can neglect it to treat the fluid as *ideal or inviscid fluid*.<br/>

  1. coefficient of *Shear viscosity* or *dynamic viscosity* or *absolute viscosity*  $\eta$ : <br/>

  2. coefficient of *longitudinal viscosity* or *second coefficient of viscosity* $\zeta$ :<br/>
  
  3. coefficient of *bulk viscosity* $\eta_B$ :<br/>
  
  4. coefficient of *kinematic viscosity* or *momentum diffusivity* $\nu$ :<br/>

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