---
layout: default
title: Notes of programming -- for HCZ model
---

Firstly, note that a vectors should be represented and calculated using its components.

---

## Gradient of scalar field

&emsp;On the lattice mesh, the **_gradient $\nabla$ of the scalar field_** can be calculated as:

### Use a second-order scheme(1):

<p>$$
    \nabla_\alpha\,\rho = \frac{1}{c_s^2 \Delta x} \sum_i \omega_i \rho(x+e_{\alpha i} \Delta t),
$$</p>
i.e.
<p>$$
\begin{aligned}
    \nabla_x \, \rho(i,j) =& \frac{1}{3}\big(\rho(i+1, j) - \rho(i-1, j)\big)
        + \frac{1}{12}\big(\rho(i+1, j+1) - \rho(i-1, j-1)\big) \\ 
        &+ \frac{1}{12}\big(\rho(i+1, j-1) - \rho(i-1, j+1)\big),\\
    \nabla_y \, \rho(i,j) =& \frac{1}{3}\big(\rho(i, j+1) - \rho(i, j-1)\big)
        + \frac{1}{12}\big(\rho(i+1, j+1) - \rho(i-1, j-1)\big) \\
        &+ \frac{1}{12}\big(\rho(i-1, j+1) - \rho(i+1, j-1)\big),\\
    \nabla \, \rho(i,j) =& \nabla_x \, \rho(i,j) \, \vec{i} +\nabla_y \, \rho(i,j) \, \vec{j}. \nonumber
\end{aligned}
$$</p>

### Use a forth-order scheme(2):

<p>$$
\nabla_\alpha \, \rho = \frac{1}{36 \Delta x} \sum_{i = 1}^8 \big[ 8\rho(x+e_i \Delta t) - \rho(x + 2e_i\Delta t) \big] \frac{e_{i\alpha}}{c},
$$</p>
i.e.
<p>$$
\begin{aligned}
    \nabla_x \, \rho =& \frac{2}{9} \big( 
            \rho(i+1,j) - \rho(i-1, j) + \rho(i+1,j+1) - \rho(i-1, j+1) - \rho(i-1, j-1) + \rho(i+1, j-1)
        \big) \\
        &- \frac{1}{36} \big(
            \rho(i+2,j) - \rho(i-2, j) + \rho(i+2,j+2) - \rho(i-2, j+2) - \rho(i-2, j-2) + \rho(i+2, j-2)
        \big),   \\
    \nabla_y \, \rho =& \frac{2}{9} \big(
            \rho(i, j+1) - \rho(i, j-1) + \rho(i+1, j+1) + \rho(i-1, j+1) - \rho(i-1, j-1) - \rho(i+1, j-1)
        \big)   \\
        &- \frac{1}{36} \big(
            \rho(i, j+2) - \rho(i, j-2) + \rho(i+2, j+2) + \rho(i-2, j+2) - \rho(i-2, j-2) - \rho(i+2, j-2)
        \big),   \\
    \nabla \, \rho =& \nabla_x \, \rho \,\vec{i} + \nabla_y \, \rho \, \vec{j}. \nonumber
\end{aligned}
$$</p>

### Use a sixth-order scheme(3):

<p>$$
\begin{aligned}
    \nabla_x \, \rho =& \frac{1}{60 \Delta x}\big[
        -\rho(i-3,j) + 9\rho(i-2,j)-45\rho(i-1,j)+45\rho(i+1,j)-9\rho(i+2,j)+\rho(i+3,j)
    \big],   \\
    \nabla_y \, \rho =& \frac{1}{60 \Delta x}\big[
        -\rho(i,j-3) + 9\rho(i,j-2)-45\rho(i,j-1)+45\rho(i,j+1)-9\rho(i,j+2)+\rho(i,j+3)
    \big],  \\
    \nabla \, \rho =& \nabla_x \, \rho \,\vec{i} + \nabla_y \, \rho \, \vec{j}.
\end{aligned}
$$</p>

---

## Laplacian of a scalar field

&emsp;The **_laplacian $\Delta$ or $\nabla^2$ of the scaler field_** can calculated as:

### Use a second-order scheme(1):

<p>$$
\Delta \rho = \nabla^2 \rho
    = \frac{2}{c_s^2 \Delta x^2} \sum_i \omega_i \big[\rho(x+e_i \Delta t) - \rho(x)\big],
$$</p>
i.e.
<p>$$
\begin{aligned}
    \Delta \rho =& \frac{4}{6}\big( \rho(i+1,j) + \rho(i-1,j) + \rho(i,j+1) + \rho(i,j-1) \big)\\
        &+ \frac{1}{6}\big( \rho(i+1,j+1) + \rho(i-1,j-1) + \rho(i+1,j-1) + \rho(i-1,j+1) \big)\\
        &- \frac{20}{6} \rho(i,j).  \nonumber
\end{aligned}
$$</p>

### Use another second-order scheme(2):

<p>$$
\Delta \rho = \nabla^2 \rho =  \frac{1}{3 \Delta x^2} \sum_{i=1}^{8} \big[\rho(x + e_i \Delta t) - \rho(x) \big],
$$</p>
i.e.
<p>$$
\begin{aligned}
    \Delta \rho =& \frac{1}{3}\big( \rho(i+1,j) + \rho(i-1,j) + \rho(i,j+1) + \rho(i,j-1) \big)\\
        &+ \frac{1}{3}\big( \rho(i+1,j+1) + \rho(i-1,j-1) + \rho(i+1,j-1) + \rho(i-1,j+1) \big)\\
        &- \frac{8}{3} \rho(i,j).  \nonumber
\end{aligned}
$$</p>

---

---