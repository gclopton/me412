


A second-order partial differential equation becomes a boundary value problem once sufficient boundary data are supplied on the domain boundary. The boundary specification is not merely a numerical "detail": it determines whether the continuous problem has a meaningful solution and it determines how the discrete linear system must be assembled so that the computed field respects the physics at the boundary.

## 1. Types of Boundary Conditions for Second-Order PDEs

Three boundary-condition families are central for second-order problems:

==Dirichlet boundary conditions== prescribe the value of the dependent variable on the boundary. In a heat-conduction setting, this means prescribing temperature.

==Neumann boundary conditions== prescribe the value of the gradient (equivalently, a flux) of the dependent variable on the boundary. In heat transfer, this is commonly written as a specified heat flux $q^{\prime \prime}$, which is proportional to $-k d T / d x$.

==Mixed boundary conditions== (often called *==Robin conditions==*) prescribe the dependent variable as a function of its gradient. The canonical heat-transfer example is convection at a surface, where the conductive flux at the boundary balances a convective heat loss or gain to an ambient environment.

## 2. Dirichlet Boundary Conditions in a Discrete 1D Grid

A standard one-dimensional discretization places nodal unknowns along the domain, indexed from the left boundary node 0 to the right boundary node $n_{x}-1$. A Dirichlet condition fixes boundary nodal values directly.


![[Pasted image 20260209124959.png|]]


**Figure 1 (Dirichlet example)** The schematic shows a 1D line of grid points with the two boundary nodes highlighted. The left boundary value is prescribed as $T_{0}=C_{1}$ at $x=$ 0 , and the right boundary value is prescribed as $T_{n_{x}-1}=C_{2}$ at $x=L$. Interior nodes remain unknown and are solved from the discretized PDE. Lecture 7 Boundary Conditions (...

When assembling a linear system of the form

$$
\mathbf{A} \mathbf{T}=\mathbf{b},
$$

Dirichlet data typically enter by moving known boundary contributions into the righthand side for the first and last interior equations. For example, the first interior node equation (associated with node 1) and the last interior node equation (associated with node $n_{x}-2$ ) are modified as

$$
b_{1}=S_{1}-a_{W} T_{0}, \quad b_{n_{x}-2}=S_{n_{x}-2}-a_{E} T_{n_{x}-1},
$$

where $a_{W}$ and $a_{E}$ are the west/east neighbor coefficients that multiply the boundary temperatures in the discrete stencil, and $S_{i}$ denotes the remaining source/known terms for the $i$-th equation. Lecture 7 Boundary Conditions (...

## 3. Neumann Boundary Conditions, One-Sided Differences, and Boundary Accuracy

A Neumann condition prescribes a gradient at the boundary. Because a boundary node does not have grid points outside the domain, the discrete approximation must use a one-sided stencil (unless ghost points or other constructions are introduced). A basic one-sided difference is typically first-order accurate, i.e. it introduces an $O(\Delta x)$ boundary truncation error. Increasing the number of stencil points can improve accuracy by raising the order of the boundary approximation, at the cost of larger stencils.

Figure 2 (Neumann example). The schematic shows prescribed flux at the left boundary and an adiabatic (zero-flux) condition at the right boundary. The left boundary is labeled $q_{0}^{\prime \prime}=C_{1}$. The right boundary is labeled $q_{L}^{\prime \prime}=0$, indicating an adiabatic boundary. Lecture 7 Boundary Conditions (...

### 3.1 Derivation of a One-Sided Flux Boundary Discretization (Derivation Mode)

Assume a 1D conduction relation between heat flux and temperature gradient,

$$
q^{\prime \prime}=-k \frac{d T}{d x},
$$

and approximate the boundary gradient with a one-sided finite difference.

At the left boundary $x=0$, with $q_{0}^{\prime \prime}=C_{1}$ :

$$
\begin{aligned}
q_{0}^{\prime \prime} & =C_{1} \\
-\left.k \frac{d T}{d x}\right|_{x=0} & =C_{1} \\
-k\left(\frac{T_{1}-T_{0}}{\Delta x}\right) & =C_{1} \\
\frac{T_{1}-T_{0}}{\Delta x} & =-\frac{C_{1}}{k} \\
T_{1}-T_{0} & =-\frac{C_{1} \Delta x}{k} \\
-T_{0} & =-\frac{C_{1} \Delta x}{k}-T_{1} \\
T_{0} & =\frac{C_{1} \Delta x}{k}+T_{1} .
\end{aligned}
$$

(Equivalently, the boundary value $T_{0}$ is expressed directly in terms of the interior value $T_{1}$ and the prescribed flux.)

At the right boundary $x=L$, with an adiabatic condition $q_{L}^{\prime \prime}=0$ (written at node $n_{x}-$ 1):

$$
\begin{aligned}
q_{L}^{\prime \prime} & =0 \\
-\left.k \frac{d T}{d x}\right|_{x=L} & =0 \\
-k\left(\frac{T_{n_{x}-1}-T_{n_{x}-2}}{\Delta x}\right) & =0 \\
\frac{T_{n_{x}-1}-T_{n_{x}-2}}{\Delta x} & =0 \\
T_{n_{x}-1}-T_{n_{x}-2} & =0 \\
T_{n_{x}-1} & =T_{n_{x}-2} .
\end{aligned}
$$

Lecture 7 Boundary Conditions (...

This boundary closure enforces zero gradient by tying the boundary node to the nearest interior node.

## 4. Mixed (Robin) Boundary Conditions from Conduction-Convection Balance

A mixed condition arises when the boundary flux depends on the boundary value itself. In heat transfer, a convective boundary at $x=L$ balances conduction inside the solid with convection to an ambient environment at temperature $T_{\infty}$ with heat-transfer coefficient $h$ :

$$
-\left.k \frac{d T}{d x}\right|_{x=L}=h\left(T_{L}-T_{\infty}\right) .
$$

The ambient temperature is interpreted as the temperature "very close" to the boundary in the surrounding fluid, and the boundary temperature is typically greater than the ambient ( $T_{n_{x}-1}>T_{\infty}$ ) when heat is leaving the solid into cooler air.

Figure $\mathbf{3}$ (Conduction-convection boundary). The diagram shows a metal bar ending at $x=L$ exposed to air. The right boundary node is adjacent to a region labeled "air," with $T_{\infty}$ identified as the ambient temperature near the boundary. The boundary temperature node $T_{n_{x}-1}$ is depicted as exceeding $T_{\infty}$, consistent with outward convective heat loss. Lecture 7 Boundary Conditions (...

### 4.1 Discrete Robin Condition at the Right Boundary (Derivation Mode)

Approximating the boundary gradient by a one-sided difference between nodes $n_{x}-2$ and $n_{x}-1$ gives:

$$
\begin{aligned}
-\left.k \frac{d T}{d x}\right|_{x=L} & =h\left(T_{L}-T_{\infty}\right) \\
-k\left(\frac{T_{n_{x}-1}-T_{n_{x}-2}}{\Delta x}\right) & =h\left(T_{n_{x}-1}-T_{\infty}\right) \\
-\frac{k}{\Delta x} T_{n_{x}-1}+\frac{k}{\Delta x} T_{n_{x}-2} & =h T_{n_{x}-1}-h T_{\infty} \\
\frac{k}{\Delta x} T_{n_{x}-2}+h T_{\infty} & =h T_{n_{x}-1}+\frac{k}{\Delta x} T_{n_{x}-1} \\
\frac{k}{\Delta x} T_{n_{x}-2}+h T_{\infty} & =\left(h+\frac{k}{\Delta x}\right) T_{n_{x}-1} \\
T_{n_{x}-1} & =\frac{\frac{k}{\Delta x} T_{n_{x}-2}+h T_{\infty}}{h+\frac{k}{\Delta x}} .
\end{aligned}
$$

This formula supplies a boundary-node value consistent with convection without prescribing temperature or flux alone.

## 5. Well-Posedness: When Boundary Specifications Produce Meaningful Solutions

Correctly coding a boundary condition into a numerical method is not sufficient to guarantee a "right" solution, because some boundary value problems are not well
posed. A well-posed boundary value problem satisfies three requirements:

1. A solution exists.
2. The solution is unique.
3. Small perturbations in the boundary conditions produce only small changes in the solution (stability with respect to boundary data).

Lecture 7 Boundary Conditions (...

These criteria can be illustrated using steady 1D conduction with no internal sources,

$$
\frac{d^{2} T}{d x^{2}}=0
$$

which implies a linear temperature profile.

### 5.1 Nonexistence from Incompatible Flux Conditions

Figure 4 (No solution). The figure shows a 1D domain labeled with $d^{2} T / d x^{2}=0$ and two different prescribed fluxes at the ends, e.g. $q^{\prime \prime}=2$ on one side and $q^{\prime \prime}=1$ on the other, accompanied by the annotation "NO SOLUTION." In steady state without internal generation, the heat flux must be spatially constant; prescribing unequal end fluxes violates heat conservation and makes the boundary value problem inconsistent.

### 5.2 Nonuniqueness from Pure Neumann Data and the Role of Essential Conditions

If the derivative is specified but no absolute temperature level is fixed, the solution can fail to be unique. Since

$$
\frac{d^{2} T}{d x^{2}}=0 \quad \Rightarrow \quad \frac{d T}{d x}=c_{1} \quad \Rightarrow \quad T(x)=c_{1} x+c_{2},
$$

a Neumann condition can determine $c_{1}$ (the slope) but not necessarily $c_{2}$ (the additive constant), leaving infinitely many solutions differing only by a vertical shift.

Figure 5 (No unique solution). The diagram shows multiple parallel straight lines (multiple linear temperature fields) all satisfying the same slope constraint, annotated "NO UNIQUE SOLN" and "Infinite soln." This represents the family of solutions that occur when only gradient information is supplied. The remedy emphasized here is that at least one boundary should be Dirichlet, also called an "essential" boundary condition, to anchor the absolute level of $T$. Lecture 7 Boundary Conditions (...

## 6. Discretization Error and Richardson Extrapolation for Estimating Order of Accuracy

Local truncation error can be discussed derivative by derivative, but a practical numerical method for a PDE involves many coupled derivative approximations, often with different behavior near boundaries. A common approach to quantify overall discretization error is grid refinement paired with Richardson extrapolation.

A model for the discretization error at grid spacing $\Delta x$ is

$$
\varepsilon_{h}=\alpha \Delta x^{p}+H
$$

where $p$ is the method's order of accuracy, $\alpha$ is a constant (representing the leading truncation-error coefficient), and $H$ denotes higher-order terms neglected in the leading-order model. Solutions are computed on three systematically refined grids with spacings $\Delta x, 2 \Delta x$, and $4 \Delta x$, where $\Delta x$ is the finest grid and $4 \Delta x$ is the coarsest.

Let $\phi$ denote the exact solution quantity of interest and $\phi_{\Delta x}, \phi_{2 \Delta x}, \phi_{4 \Delta x}$ the corresponding numerical approximations. Then:

$$
\phi=\phi_{\Delta x}+\alpha \Delta x^{p}+H, \quad \phi=\phi_{2 \Delta x}+\alpha(2 \Delta x)^{p}+H, \quad \phi=\phi_{4 \Delta x}+\alpha(4 \Delta x)^{p}+F
$$

### 6.1 Solving for $p$ from Three Grids (Derivation Mode)

$$
\begin{aligned}
\phi & =\phi_{\Delta x}+\alpha \Delta x^{p}+H \\
\phi & =\phi_{2 \Delta x}+\alpha(2 \Delta x)^{p}+H \\
\phi & =\phi_{4 \Delta x}+\alpha(4 \Delta x)^{p}+H
\end{aligned}
$$

$$
\begin{aligned}
\phi_{2 \Delta x}-\phi_{\Delta x} & =\left(\phi-\alpha(2 \Delta x)^{p}-H\right)-\left(\phi-\alpha \Delta x^{p}-H\right) \\
& =-\alpha(2 \Delta x)^{p}+\alpha \Delta x^{p} \\
& =\alpha \Delta x^{p}\left(1-2^{p}\right)
\end{aligned}
$$

$$
\begin{aligned}
\phi_{4 \Delta x}-\phi_{2 \Delta x} & =\left(\phi-\alpha(4 \Delta x)^{p}-H\right)-\left(\phi-\alpha(2 \Delta x)^{p}-H\right) \\
& =-\alpha(4 \Delta x)^{p}+\alpha(2 \Delta x)^{p} \\
& =\alpha \Delta x^{p}\left(2^{p}-4^{p}\right) \\
& =\alpha \Delta x^{p}\left(2^{p}-\left(2^{2}\right)^{p}\right) \\
& =\alpha \Delta x^{p}\left(2^{p}-2^{2 p}\right) \\
& =\alpha \Delta x^{p} 2^{p}\left(1-2^{p}\right),
\end{aligned}
$$

$$
\begin{aligned}
\frac{\phi_{4 \Delta x}-\phi_{2 \Delta x}}{\phi_{2 \Delta x}-\phi_{\Delta x}} & =\frac{\alpha \Delta x^{p} 2^{p}\left(1-2^{p}\right)}{\alpha \Delta x^{p}\left(1-2^{p}\right)} \\
& =2^{p}
\end{aligned}
$$

$$
\begin{aligned}
\log \left(\frac{\phi_{4 \Delta x}-\phi_{2 \Delta x}}{\phi_{2 \Delta x}-\phi_{\Delta x}}\right) & =\log \left(2^{p}\right) \\
& =p \log 2
\end{aligned}
$$

$$
p=\frac{\log \left(\frac{\phi_{4 \Delta x}-\phi_{2 \Delta x}}{\phi_{2 \Delta x}-\phi_{\Delta x}}\right)}{\log 2}
$$

Lecture 7 Boundary Conditions (...

This procedure estimates the observed order of accuracy of the overall numerical method, rather than only a single derivative approximation.

## 7. Polynomial Fitting as a Route to Finite-Difference Stencils

Finite-difference stencils can be constructed by fitting a polynomial of chosen degree through a set of grid points and then differentiating the polynomial analytically. Forward and backward differences correspond to fitting a straight line through two points, while
higher-order schemes correspond to fitting higher-degree polynomials through more points.

Figure 6 (Piecewise polynomial intuition). The figure depicts a smooth curve (labeled as an "exact" function) and a piecewise linear approximation drawn through discrete samples (shown as straight green segments). A refined sampling is shown as a closer approximation to the curve than a coarse mesh. The picture emphasizes two routes to reducing error: decreasing $\Delta x$ by using more grid points (which increases computational and memory cost) and increasing the order of accuracy by increasing stencil size (which raises polynomial degree and enlarges the local coupling).

### 7.1 Central Difference for the Second Derivative from a Quadratic Fit (Derivation Mode)

Consider a uniform grid with spacing $\Delta x$, and center the coordinate system at node $i$ so that $x_{i}=0, x_{i+1}=+\Delta x$, and $x_{i-1}=-\Delta x$. Fit a quadratic:

$$
f(x)=a+b x+c x^{2}
$$

Impose interpolation at the three points:

$$
f_{i}=f(0), \quad f_{i+1}=f(\Delta x), \quad f_{i-1}=f(-\Delta x) .
$$

$$
\begin{aligned}
f_{i} & =a+b(0)+c(0)^{2}=a \\
& \Rightarrow a=f_{i} \\
f_{i+1} & =a+b \Delta x+c \Delta x^{2}, \\
f_{i-1} & =a-b \Delta x+c \Delta x^{2}, \\
f_{i+1}+f_{i-1} & =\left(a+b \Delta x+c \Delta x^{2}\right)+\left(a-b \Delta x+c \Delta x^{2}\right) \\
& =2 a+2 c \Delta x^{2}, \\
f_{i+1}+f_{i-1}-2 a & =2 c \Delta x^{2}, \\
c & =\frac{f_{i+1}+f_{i-1}-2 a}{2 \Delta x^{2}}=\frac{f_{i+1}+f_{i-1}-2 f_{i}}{2 \Delta x^{2}}, \\
\frac{d^{2} f}{d x^{2}} & =\frac{d^{2}}{d x^{2}}\left(a+b x+c x^{2}\right)=2 c, \\
\left.\frac{d^{2} f}{d x^{2}}\right|_{x=0} & =2 c=2\left(\frac{f_{i+1}+f_{i-1}-2 f_{i}}{2 \Delta x^{2}}\right) \\
& =\frac{f_{i+1}+f_{i-1}-2 f_{i}}{\Delta x^{2}} .
\end{aligned}
$$

Lecture 7 Boundary Conditions (...

This is the standard central-difference scheme (CDS) for the second derivative, interpreted directly as differentiating a fitted second-order polynomial through ( $i- 1, i, i+1)$.

### 7.2 Second-Order Forward Difference for the First Derivative from a Quadratic Fit (Derivation Mode)

A second-order forward-difference approximation for $f^{\prime}\left(x_{i}\right)$ can be obtained by fitting a quadratic through the points $i$, $i+1$, and $i+2$ with $x_{i}=0$, $x_{i+1}=\Delta x$, $x_{i+2}=2 \Delta x$ , again using

$$
f(x)=a+b x+c x^{2},
$$

so that $f^{\prime}(0)=b$.

$$
\begin{aligned}
f_{i} & =a, \\
f_{i+1} & =a+b \Delta x+c \Delta x^{2}, \\
f_{i+2} & =a+b(2 \Delta x)+c(2 \Delta x)^{2} \\
& =a+2 b \Delta x+4 c \Delta x^{2}, \\
4 f_{i+1} & =4 a+4 b \Delta x+4 c \Delta x^{2}, \\
f_{i+2}-4 f_{i+1} & =\left(a+2 b \Delta x+4 c \Delta x^{2}\right)-\left(4 a+4 b \Delta x+4 c \Delta x^{2}\right) \\
& =-3 a-2 b \Delta x, \\
-2 b \Delta x & =f_{i+2}-4 f_{i+1}+3 a, \\
b & =\frac{-f_{i+2}+4 f_{i+1}-3 a}{2 \Delta x}=\frac{-f_{i+2}+4 f_{i+1}-3 f_{i}}{2 \Delta x}, \\
f^{\prime}\left(x_{i}\right)=f_{i}^{\prime} & =\frac{-f_{i+2}+4 f_{i+1}-3 f_{i}}{2 \Delta x} .
\end{aligned}
$$

Lecture 7 Boundary Conditions (...

In general, an $n$-th degree polynomial fit uses $n+1$ points (and $n+1$ equations) and can be used to build higher-order accurate stencils. This extends naturally to nonuniform spacing, though the algebra changes because $\Delta x$ is no longer constant between points. Lecture 7 Boundary Conditions (...

## 8. Compact Finite Differences: High Order with Small Stencils

Polynomial fitting suggests that $n$-th order accuracy typically requires $n+1$ points. Compact finite differences pursue high order with fewer points by introducing derivative values at neighboring nodes as additional unknowns, thereby increasing the number of equations without increasing the stencil's point count. A representative goal is fourthorder accuracy for $d f / d x$ at node $i$ using only the three points $i-1, i, i+1$, supplemented by derivative information at $i-1$ and $i+1$.

A stated fourth-order compact relation for the first derivative at $i$ is:

$$
f_{i}^{\prime}=-\frac{1}{4} f_{i+1}^{\prime}-\frac{1}{4} f_{i-1}^{\prime}+\frac{3}{4}\left(\frac{f_{i+1}-f_{i-1}}{\Delta x}\right)
$$

where $f_{i+1}^{\prime}$ and $f_{i-1}^{\prime}$ can be supplied from an implicit solve or from a previous time step in transient contexts.

Lecture 7 Boundary Conditions (...

### 8.1 Quartic Polynomial Setup Used to Derive a Compact Scheme (Derivation Mode)

A fourth-order construction is consistent with fitting a quartic

$$
f(x)=a_{0}+a_{1} x+a_{2} x^{2}+a_{3} x^{3}+a_{4} x^{4}
$$

about node $i$ with $x_{i}=0, x_{i \pm 1}= \pm \Delta x$. The nodal values and neighboring derivatives expand as:

$$
\begin{aligned}
f_{i} & =a_{0} \\
f_{i+1} & =a_{0}+a_{1} \Delta x+a_{2} \Delta x^{2}+a_{3} \Delta x^{3}+a_{4} \Delta x^{4} \\
f_{i-1} & =a_{0}-a_{1} \Delta x+a_{2} \Delta x^{2}-a_{3} \Delta x^{3}+a_{4} \Delta x^{4} \\
f_{i+1}^{\prime} & =a_{1}+2 a_{2} \Delta x+3 a_{3} \Delta x^{2}+4 a_{4} \Delta x^{3} \\
f_{i-1}^{\prime} & =a_{1}-2 a_{2} \Delta x+3 a_{3} \Delta x^{2}-4 a_{4} \Delta x^{3}
\end{aligned}
$$

Lecture 7 Boundary Conditions (...

These relations provide five equations for the five coefficients $a_{0}, \ldots, a_{4}$ when $f_{i}, f_{i \pm 1}, f_{i \pm 1}^{\prime}$ are treated as known data, which is the mechanism enabling fourth-order accuracy with only three grid points.

## 9. Applied Exercises: Well-Posedness, Grid Convergence, and Iterative Solvers

A sequence of applied tasks ties the boundary-condition concepts, well-posedness criteria, and accuracy estimation tools to concrete conduction and potential-flow-type models.

## Exercise Set A: Classifying PDE Type

One model problem is

$$
\left(1-M_{\infty}\right)^{2} \frac{\partial^{2} \phi}{\partial x^{2}}+\frac{\partial^{2} \phi}{\partial y^{2}}=0
$$

to be classified for the regimes $M_{\infty}=1, M_{\infty}<1$, and $M_{\infty}>1$.

A coupled-equation prompt is also posed in the form
$\frac{\partial u}{\partial x}=\frac{\partial v}{\partial y}, \quad$ and a second relation between the fields (as stated in the prompt).
A further prompt is the transient advection-source equation

$$
\frac{\partial T}{\partial t}+u_{\infty} \frac{\partial T}{\partial x}=S, \quad T=T(x, t),
$$

along with instruction to determine the nature of the PDE. Lecture 7 Boundary Conditions (...

## Exercise Set B: Composite Conduction, Interfaces, and Richardson Extrapolation

Figure 7 (2D composite square). The figure shows a square domain partitioned into three vertical subregions labeled 1,2 , and 3 , representing a three-material composite. A temperature of $T=400 \mathrm{~K}$ is indicated on the left boundary and $T=300 \mathrm{~K}$ on the right boundary. An adiabatic condition $q^{\prime \prime}=0$ is indicated along (at least) the bottom boundary in the sketch. The task is to solve the steady conduction equation

$$
\nabla^{2} T=0
$$

on this geometry with the shown boundary conditions and to address how thermal conductivity is handled at interfaces. Lecture 7 Boundary Conditions (...

Two conductivity orderings are specified:
Case I:

$$
k_{1}=210 \mathrm{~W} / \mathrm{mK}, \quad k_{2}=200 \mathrm{~W} / \mathrm{mK}, \quad k_{3}=190 \mathrm{~W} / \mathrm{mK}
$$

Case II:

$$
k_{1}=190 \mathrm{~W} / \mathrm{mK}, \quad k_{2}=200 \mathrm{~W} / \mathrm{mK}, \quad k_{3}=210 \mathrm{~W} / \mathrm{mK} .
$$

For Case I, three grids are prescribed- $31 \times 31,61 \times 61$, and $121 \times 121$-with the goal of estimating observed order of accuracy using Richardson extrapolation. For Case II, the $61 \times 61$ grid is used, with explanation requested for differences between Cases I and II on the same grid. Attention is also directed to the near-boundary behavior, asking explicitly about the $O(\Delta x)$ character near boundaries and which boundary discretization scheme is used. Lecture 7 Boundary Conditions (...

A separate validation-style task prescribes an analytical solution of the sinusoidal form

$$
T(x, y)=A \sin (k \pi x) \sin (k \pi x),
$$

with $A=1$ and $k \in\{2,4,8\}$, on a unit square $L_{x}=L_{y}=1$ with all boundary temperatures set to zero and a nominal grid $n_{x}=n_{y}=33$. The task requests the root mean square error (RMSE) for each $k$, an interpretation of RMSE trends as $k$ changes, and a strategy for improving accuracy if the error becomes large.

Lecture 7 Boundary Conditions (...

## Exercise Set C: SOR and Red-Black SOR with Internal Sources

An iterative-solver development task requests implementation of SOR and RB-SOR on a $65 \times 65$ grid, including determination of an optimal relaxation parameter $\omega$. The boundary condition is stated as all boundaries fixed at $T=0$, and the source magnitude is varied across

$$
S \in\left\{10^{7}, 10^{8}, 10^{9}\right\} \mathrm{W} / \mathrm{m}^{3},
$$

with interpretation of the resulting behavior.

Figure 8 (source layout for solver test). The figure shows a square domain with both diagonals drawn as dashed lines and several marked red source locations distributed along the diagonals, including a central point and additional off-center points. This picture specifies where internal heating (or forcing) is applied within the domain while the boundary remains fixed, creating a nontrivial field intended to stress and compare iterative solver performance and convergence as $\omega$ varies.

Lecture 7 Boundary Conditions (...

## Exercise Set D: Geometry Effects in ANSYS

A final applied prompt calls for an ANSYS-based comparison on a unit-sized setting ( $L_{x}=L_{y}=1$ ) across hollow geometries-square and cylindrical-under a prescribed temperature difference: the outside surface at 300 K and the inside surface at 400 K . The task requests explanation of differences in the computed solution across geometries and justification of the chosen grid spacing.

Sources
$\wedge \approx \ldots$

