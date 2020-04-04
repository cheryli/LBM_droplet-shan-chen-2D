---
layout: default
title: Derivation of Equilibrium Moments
---

[**Back to the introduction.**](https://cheryli.github.io/LBM_droplet-shan-chen-2D)

Recall that the discrete equilibrium distribution function is:

<p> $$ f_i^{eq} = \rho w_i \left[1 + \frac{e_i u}{c_s^2} + \frac{(e_i u)^2}{2c_s^4} - \frac{u^2}{2c_s^2} \right] ,$$</p>
where $c_s^2 = 1/3$ for most cases.
<br/><br/>

The equilibrium Moments as:

<p> $$ m^{eq} = M f^{eq} \label{Transform}$$ </p>

---

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

Don't forget that: $u^2 = u_x^2 + u_y^2$.And use equation (\ref{Transform}), we have:

<p> $$
\begin{aligned}
f_0^{eq} &= \frac{4}{9} \rho \left(1 - \frac{3 u^2}{2} \right)   \\
m_0^{eq} &= \rho \left[ 
    \frac{4}{9} \left(
        1 - \frac{3 u^2}{2} 
    \right)
    + \frac{1}{9} \left(
        4 + 9 u_x^2 + 9 u_y^2 - 6 u^2
    \right)
    + \frac{1}{36} \left(
        4 + 18 u_x^2 + 18 u_y^2 - 6 u^2
    \right)
\right] \\
        &=  \rho    \\
m_1^{eq} &= \rho \left[
    - \frac{16}{9} \left(
        1 - \frac{3u^2}{2} 
    \right)
    - \frac{1}{9} \left(
        4 + 9 u_x^2 + 9 u_y^2 - 6 u^2
    \right)
    + \frac{1}{18} \left(
        4 + 18 u_x^2 + 18 u_y^2 - 6 u^2
    \right)
\right] \\
        &= \rho \left( -2 + 3 u^2\right)    \\
m_2^{eq} &= \rho \left[
    \frac{16}{9} \left(
        1 - \frac{3u^2}{2} 
    \right)
    - \frac{2}{9} \left(
        4 + 9 u_x^2 + 9 u_y^2 - 6 u^2
    \right)
    + \frac{1}{36} \left(
        4 + 18 u_x^2 + 18 u_y^2 - 6 u^2
    \right)
\right] \\
        &= \rho \left(1 - 3 u^2\right)  \\
m_3^{eq} &= \rho \left(
    0 + \frac{6 u_x}{9} + \frac{12 u_x}{36}
\right) = \rho u_x \\
m_4^{eq} &= \rho \left(
    0 - \frac{12 u_x}{9} + \frac{12 u_X}{36}
\right) = - \rho u_x   \\
m_5^{eq} &= \rho \left(
    0 + \frac{6 u_y}{9} + \frac{12 u_y}{36}
\right) = \rho u_y \\
m_6^{eq} &= \rho \left(
    0 - \frac{12 u_y}{9} + \frac{12 u_y}{36}
\right) = - \rho u_y    \\
m_7^{eq} &= \rho \left(
    0 + u_x^2 - u_y^2 + 0
\right) = \rho \left(u_x^2 - u_y^2\right)   \\
m_8^{eq} &= \rho \left(
    0 + 0 + u_x u_y
\right) = \rho u_x u_y  \\
\end{aligned}
$$</p>

Thus,
<p>$$
m^{eq} = \rho \left[
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
\right]
$$ </p>