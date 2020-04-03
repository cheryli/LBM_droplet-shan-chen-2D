---
layout: default
title: Derivation of Equilibrium Moments
---

Recall that the discrete equilibrium distribution function is:

<p> $$ f_i^{eq} = \rho w_i \left[1 + \frac{e_i u}{c_s^2} + \frac{(e_i u)^2}{2c_s^4} - \frac{u^2}{2c_s^2} \right] ,$$</p>

The equilibrium Moments as:

<p> $$ m^{eq} = M f^{eq} $$ </p>

### For $D2Q9$ model:

the component of the distribution function can be written as:
<p> $$
\begin{aligned}
f_0^{eq} &= \frac{4}{9} \rho \left(1 - \frac{3 u^2}{2} \right)   \\
f_1^{eq} &= \frac{1}{9} \rho \left( 1 + 3u_x + \frac{9 u_x^2}{2} - \frac{3 u^2}{2} \right)    \\
f_2^{eq} &= \frac{1}{9} \rho \left( 1 + 3u_y + \frac{9 u_y^2}{2} - \frac{3 u^2}{2} \right)    \\
f_3^{eq} &= \frac{1}{9} \rho \left( 1 - 3u_x + \frac{9 u_x^2}{2} - \frac{3 u^2}{2} \right)    \\
f_4^{eq} &= \frac{1}{9} \rho \left( 1 - 3u_y + \frac{9 u_y^2}{2} - \frac{3 u^2}{2} \right)    \\
f_5^{eq} &= \frac{1}{36} \rho \left(  1 + 3 u_x + 3 u_y + \frac{9 u_x^2 + 9u_y^2 + 18 u_x u_y}{2} - \frac{3 u^2}{2} \right)     \\
f_6^{eq} &= \frac{1}{36} \rho \left(  1 - 3 u_x + 3 u_y + \frac{9 u_x^2 + 9u_y^2 - 18 u_x u_y}{2} - \frac{3 u^2}{2} \right)     \\
f_7^{eq} &= \frac{1}{36} \rho \left(  1 - 3 u_x - 3 u_y + \frac{9 u_x^2 + 9u_y^2 + 18 u_x u_y}{2} - \frac{3 u^2}{2} \right)     \\
f_8^{eq} &= \frac{1}{36} \rho \left(  1 + 3 u_x - 3 u_y + \frac{9 u_x^2 + 9u_y^2 - 18 u_x u_y}{2} - \frac{3 u^2}{2} \right)
\end{aligned}
$$</p>


