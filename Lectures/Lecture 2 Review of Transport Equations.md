## 2a. Review - Transport equations

## OUTLINE

* Review of thermal and fluid flow equations
* General transport equation
* Pryssical Interpretation of traneport equation


## RECALL

* CFD is numerical techniques applied to solve transport equations governed by partial differential equations on computers
* We will be dealing with thermal and fluid transport governed by $2^{\text {nd }}$ order PDEs.

Let's quickly revisit heat and fluid flow equations

1. Steady state heat conduction: $\nabla \cdot(k \nabla T)+C=0$
where, $\nabla=$ gradient operator $\left(\frac{\partial}{\partial x} \hat{i}+\frac{\partial}{\partial y} \hat{\jmath}+\frac{\partial}{\partial z} \hat{k}\right)$
$k=$ thermal conductivity ( $\omega / m k$ )
$T=$ Temperature
$S_{T}=$ Heat generation/remad $\left(\mathrm{w} / \mathrm{m}^{3}\right)$

- 2nd order PDE.
- $S_{T}=0 \Rightarrow$ Laplace equation
- $S_{\tau} \neq 0 \Rightarrow$ Poisson equation
- Heat +ransfer due to molecular transport due to a gradient

Examples: Wall, Fin, Chip at steady power
2. Transient heat conduction: $\quad \rho C_{p} \frac{\partial T}{\partial t}=\nabla \cdot(k \nabla T)$
where, $S=$ Density $\left(\mathrm{kg} / \mathrm{m}^{3}\right)$
$C_{p}=$ Heat capacity
( $J / k g k$ )
$t=$ time

- Time dependence enters as a storage term

3. Steady state advection-Diffusion: $\quad \rho C_{p} \vec{u} \nabla T=\nabla \cdot(k \nabla T)$ where, $\vec{u}=$ fluid velocity $=u \hat{i}+v \hat{j}+w \hat{k}$

- Heat is carried by bulk fluid motion, in addition to molecular motion due to a gradient
- steady state i.e. Temperature doesn't change with time at a fixed position $(\partial T / \partial t=0)$ but flow may still be moving and carry heat along the way

4. Transient advection-diffusion: $\rho C_{p}\left(\frac{\partial T}{\partial t}+\vec{u} \cdot \nabla T\right)=\nabla \cdot(k \nabla T)$

- Also, known as energy equation
- Heat is transferred by all three mechanisms:

1. Storage or accumulation
2. Bulk fluid motion
3. molecular motion in presence of a gradient
4. Mass transport: $\frac{\partial \rho}{\partial t}+\nabla \cdot(\rho \vec{u})=0$

- For incompressible flow, $\mathcal{I}=$ constant

$$
\nabla \cdot \vec{u}=0
$$

6. Momentum transport (Naviev-Stoked: $\rho\left(\frac{\partial \vec{u}}{\partial t}+\vec{u} \cdot \nabla \vec{u}\right)=-\nabla p+\mu \nabla^{2} \vec{u}+\rho g$
where, $P=$ pressure $\left(\mathrm{N} / \mathrm{m}^{2}\right.$ or $\left.P a\right)$
$\mu=$ dynamig viscosity ( $\mathrm{Ns} / \mathrm{m}^{2}$ or Pa.s)
$g=$ acceleration due to gravity $\left(\mathrm{m} / \mathrm{s}^{2}\right)$

- Incompressible fluid flow assumption
$x$ or $u$ momentum: $\frac{\partial u}{\partial t}+(\vec{u} \cdot \nabla) u=\frac{-\partial p}{\partial x}+u \nabla^{2} u$
4 or $v$ nomentum: $\frac{\partial v}{\partial t}+(\vec{u} \cdot \nabla) v=\frac{-\partial p}{\partial y}+\mu \nabla^{2} v$
\{Ignoring body torces \}

Cw1 Which term makes the Navier-stokes equation:

1. Non-linear → advection term $\Rightarrow \rho(\vec{u} \cdot \nabla \vec{u})$
2. $2^{\text {nd }}$ order PDE - viscous diffusion term $\Rightarrow \mu \nabla^{2} \ddot{u}$

## General Transport Equation

- In principle, we can represent the heat and fluid flow equations reviewed before as a transport equation quien as:

$$
\begin{gathered}
\frac{\partial \phi}{\partial t}+\begin{array}{c}
\vec{u} \cdot \nabla \phi=\nabla \cdot\left(\Gamma_{\phi}, \nabla \phi\right)+S_{\phi} \\
\downarrow \\
\downarrow \\
\text { Transient term } \\
\downarrow \\
\text { CAccumulation or storage) } \\
\phi=\text { transported physical quantify } \\
\phi \\
\Gamma_{\phi}=\text { exchange coefficient for the field } \phi
\end{array}
\end{gathered}
$$

- Transport $=$ movement + redistribution of physical quantity in space and time
- The physical quantity can be mass, momentum, heat, species, charge etc.
- Physical quantity can be scalar $(T, u, v, \omega)$ or vector $(\vec{u})$
- We will try to apply numerical techniques to solve the above non-linear, $2^{\text {nd }}$ order PDE in some form or other.

CW2 Fill in the missing terms:

| Phenomenon | $\phi$ | $\Gamma_{\phi}$ | $S_{\phi}$ |
| :--- | :---: | :---: | :---: |
| Heat transfer | $T$ | $K / \rho C_{p}$ | Heat generation/Rejection |
| Momentum | $\vec{u}$ | $\frac{\mu}{\rho}=v$ | Gravity (body force) |

Discerning the transport equation

$$
\begin{array}{r}
\frac{\partial \phi}{\partial t}+\vec{u} \cdot \nabla \phi=\nabla \cdot\left(\Gamma_{\phi} \nabla \phi\right)+S_{\phi} \\
(1) \quad(2) \quad(3) \quad \text { (4) }
\end{array}
$$

→ Terms (1), (2) and (3) are the three mechanisms of transport and every transport process is built from these three physical processes.

1. Storage (Accumulation) - $\frac{\partial \phi}{\partial t}$

- change of physical quantity (D) with time at a fixed location
- Quantity builds up or depletes
- Nothing has to move
- Example: - A rock heating in the sun
- warming of a room after heater turns on

2. Advection - $\vec{u} \cdot \nabla \phi$

- Transport due to bulk fluid motion
- Example: - Warm air blown by a fan
- Pollutant carried by wind

3. Diffusion - $\nabla \cdot\left(\Gamma_{\phi} \nabla \phi\right)$

- Individual particles move randomly but spread out collectively in presence of a gradient
- Driving force is the difference in $\phi$ with movement occuring down the gradient
- It is a passive process
- Example: Tea infusion

Dye spreading in water

Discussion on Eulerian vs Lagrangian approaches
$\frac{D \phi}{D t}=\frac{\partial \phi}{\partial t}+\vec{u} \cdot \nabla \phi$

Example $\cdot \quad \frac{D T}{D t}=\frac{\partial T}{\partial t}+\vec{u} \cdot \nabla T$

