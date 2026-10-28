


* FDM - Introduction
* Approximating derivatives using Taylor's Series expansion

RECAP OF CFD ANALYSIS
OBJECTIVE → To solve Thermo-fluidics problem governed by $2^{\text {nd }}$ order PDEs using FDM or FVM
![](https://cdn.mathpix.com/cropped/9e1e3448-d974-4071-b5a0-123651a993aa-01.jpg?height=466&width=1475&top_left_y=594&top_left_x=96)

Step $3 \rightarrow$ set up the discrete equations from the governing PDE at grid nodes excluding boundary nodes

Step $4 \rightarrow$ input material properties and parameter nelevant to problem
Step $5 \rightarrow$ Boundary Conditions and Initial Condition
step $6 \rightarrow$ solve the set of linear algebraic equations
Step $7 \rightarrow$ check accuracy of results

1. GRIDS

- Cartesian groids
- Curvilinear grids
- Unstructured grids
![](https://cdn.mathpix.com/cropped/9e1e3448-d974-4071-b5a0-123651a993aa-02.jpg?height=491&width=460&top_left_y=288&top_left_x=16)

→ Lines of constant $x$ and 4
Lines are
→ Orthogonal to each other (orthogonal Gried)
→ Simple and easy to implement
→ Boundaries may not align with the guid nodes
→ Easy to implement FDM
![](https://cdn.mathpix.com/cropped/9e1e3448-d974-4071-b5a0-123651a993aa-02.jpg?height=489&width=468&top_left_y=286&top_left_x=552)

→ Boundary alingned
→ Use co.ordinate transformation

→ Governing eqn abo needs to transformed
→ Moderate difficulty
→ Difficult to generate for complex geometry

UNSTRUCTURED
![](https://cdn.mathpix.com/cropped/9e1e3448-d974-4071-b5a0-123651a993aa-02.jpg?height=453&width=453&top_left_y=324&top_left_x=1109)

→ Boundary aligned
→ Easy to generote
→ Convergence issue
→ Diffinet to irplement FDM

For the course and programming, one discussions in FDM will be limbed to Cartesian Grids only. You can try using curbilinear on unstructured nesh in ANSYS

## 2. Grid Nodes/points

→ For the sake of simplicity, the grid nodes are the points where the grid lines intersect (vertices of each cell/volume...)
→ In general they can also lie at the cell centre or face centre.
→ These nodes are the discrete points where we discretize the exact or partial derivatives and subsequenty the partial differential equation-

## FINITE DIFFERENCE METHOD

- It is the oldest method to discretize a derivative on grid
- Discretization is based on Taylor's series expansion
- Mainly applicable to structured placement of variables on the grid (Cartesian on Curvilinear) but there have been development in order to make it applicable using unstructured grids.
- PDE is converted to set of finite difference equations at discrete points

→ For simplicity consider a one dimensional bar (length L) discretized by uniformly $n$-uniprmly spaced gend points.
![](https://cdn.mathpix.com/cropped/9e1e3448-d974-4071-b5a0-123651a993aa-03.jpg?height=322&width=866&top_left_y=711&top_left_x=372)
![](https://cdn.mathpix.com/cropped/9e1e3448-d974-4071-b5a0-123651a993aa-03.jpg?height=326&width=774&top_left_y=707&top_left_x=791)

→ Assume the function and all the required derivatives are finite objective To estimate the derivatives of $f$ at $x$
consider, estimating $\frac{d f}{d x}$ or $f^{\prime}(x)($ ODE since its first order eqn) but will be applicable for PDE
Using, Taylor's series expansion, we can write.

$$
\begin{align*}
& f(x+\Delta x)=f(x)+\frac{\Delta x}{1!} f^{\prime}(x)+\frac{\Delta x^{2}}{2!} f^{\prime \prime}(x)+\frac{\Delta x^{3}}{3!} f^{\prime \prime \prime}(x)+\ldots  \tag{1}\\
& f(x-\Delta x)=f(x)-\frac{\Delta x}{1!} f^{\prime}(x)+\frac{\Delta x^{2}}{2!} f^{\prime \prime}(x)-\frac{\Delta x^{3}}{3!} f^{\prime \prime \prime}(x)+\ldots \tag{2}
\end{align*}
$$

From (1)

$$
\begin{equation*}
\frac{d f}{d x}=f^{\prime}(x)=\frac{f(x+\Delta x)-f(x)}{\Delta x}-\frac{\Delta x}{2!} f^{\prime \prime}(x)-\frac{\Delta x^{2}}{3!} f^{\prime \prime \prime}(x)-\cdots \tag{$-3$}
\end{equation*}
$$

from (2)

$$
\begin{equation*}
\frac{d f}{d x}=f^{\prime}(x)=\frac{f(x)-f(x-\Delta x)}{\Delta x}+\frac{\Delta x}{2!} f^{\prime \prime}(x)+\frac{\Delta x^{2}}{3!} f^{\prime \prime \prime}(x)+\cdots \tag{4}
\end{equation*}
$$

Now, subtract (2) from (1)

$$
\begin{equation*}
\frac{d f}{d x}=f^{\prime}(x)=\frac{f(x+h)-f(x-h)}{2 \Delta x}+\frac{\Delta x^{2}}{3!} f^{\prime \prime \prime}(x)+\frac{\Delta x^{4}}{5!}+\ldots \tag{5}
\end{equation*}
$$

If we ignore or truncate the higher order derivatives, we can write the finst onder derivative $\left(\frac{d f}{d x}\right)$ in finite difference form as:

$$
\begin{array}{ll}
\frac{d f}{d x}=f^{\prime}(x)=\frac{f(x+\Delta x)-f(x)}{\Delta x} & \text { FDS } \\
& \text { (For ward Difference Scheme) } \\
\frac{d f}{d x}=f^{\prime}(x)=\frac{f(x)-f(x-\Delta x)}{\Delta x} & \text { BDS } \\
\frac{d f}{d x}=f^{\prime}(x)=\frac{f(x+\Delta x)-f(x-\Delta x)}{2 \Delta x} & \text { (Backward Difference Scheme) } \\
& \text { CDS }
\end{array}
$$

CW1 Express $\frac{d^{2} f}{d x^{2}}$ or $f^{\prime \prime}(x)$ in terms of finite difference form

$$
\begin{aligned}
& f(x+\Delta x)=f(x)+\Delta x f^{\prime}(x)+\frac{\Delta x^{2}}{2!} f^{\prime \prime}(x)+\frac{\Delta x^{3}}{3!} f^{\prime \prime \prime}(x) \\
& f(x-\Delta x)=f(x)-\Delta x f^{\prime}(x)+\frac{\Delta x^{2}}{2!} f^{\prime \prime}(x)-\frac{\Delta x^{3}}{3!} f^{\prime \prime \prime}(x) \\
& f(x+\Delta x)+f(x-\Delta x)=2 f(x)+\frac{2 \cdot \Delta x^{2}}{2!} f^{\prime \prime}(x)+\frac{x^{\prime} \Delta x^{4}}{4!} f^{\prime \prime}(x)+\cdots \\
& f^{\prime \prime}(x)=\frac{f(x+\Delta x)-2 f(x)+f(x-\Delta x)}{\Delta x^{2}}+\cdots
\end{aligned}
$$

## TRUNCATION ERROR AND ORDER OF ACCURACY

The error in the Taylo's series approcimation of the derivative caused by ignoring the other terms (higher order terms) is Known as the truncation error.

And, the leading term in the truncation error is used to characterize the order of the scheme. If $\Delta x^{2}$ is the multiplier in the leading term, $n$ is the order of accuracy.
eqn
(3) FDS $\frac{d f}{d x}=\frac{f(x+\Delta x)-f(x)}{\Delta x}+\frac{\Delta x}{2} ; f^{\prime \prime}(x)$ Order of accuracy $O(\Delta x)$ - 1st order
(4) BDS $\frac{d f}{d x}=\frac{f(x)-f(x-\Delta x)}{\Delta x}+\frac{\Delta x^{T}}{2}, f^{\prime \prime}(x) O(\Delta x)-1$ st order
(5) CDS: $\quad \frac{d f}{d x}=\frac{f(x+\Delta x)-f(x-\Delta x)}{2 \Delta x}+\frac{\Delta x^{2}}{6}, f^{\prime \prime \prime}(x) O\left(\Delta x^{2}\right)$ - 2nd order
(6) CDS: $\frac{d^{2} f}{d x^{2}}=\frac{f(x+\Delta x)-2 f(x)+f(x-\Delta x)}{\Delta x^{2}}+\frac{\Delta x^{2}}{12} ; f^{\prime \prime}(x) O\left(\Delta x^{2}\right)-2$ nd ader

## NATURE OF ERROR

Dissipative Error: If the leading derivative in the truncation error is even order, the error is dissipative.
Dissipative errors dampen the signal and broaden the signal

Dispersive Error: If the leading derivative in the truncation error is odd order, the error is dispersive.
They generate oscillations and unboundedness. They generate waves for a signal (mumerical solution) in space or time. They can cause max-min problem.

In your truncation error, there would be both disperswe and dissipative error. so, signal may be dampened even though the leading berm is dispersive in nature.

## STENCIL-WIDTH

The number of discrete points used in the finite difference discribization to obtain the value of derivative including the grid point at which derivative is computed.

## CW2

| Derivative | Scheme | order of accuracy | Nature of error | Stencil width |
| :---: | :---: | :---: | :--- | :--- |
| $\frac{\partial f}{\partial x}$ | FDS | $O(\Delta x)$ | Dissipative | $i, i+1 \rightarrow 2$ |
| $\frac{\partial f}{\partial x}$ | BDS | $O(\Delta x)$ | Dissipative | $i, i-1 \rightarrow 2$ |
| $\frac{\partial f}{\partial x}$ | CDS | $O\left(\Delta x^{2}\right)$ | Dispersive | $i, i+1, i-1 \rightarrow 3$ |
| $\frac{\partial^{2} f}{\partial x^{2}}$ | CDS | $O\left(\Delta x^{2}\right)$ | Dissipative | $i-1, i, i+1 \rightarrow 3$ |

Discussion on error (T.E)
Example FDS, $\frac{d t}{d x}=\frac{f(x+\Delta x)-f(x)}{\Delta x}+O(\Delta x)$

$$
\begin{aligned}
& \left.\left.\frac{d f}{d x}\right)_{\text {exact }}=\frac{d t}{d x}\right)_{F D}+O(\Delta x) \\
& \text { Error, } \left.\varepsilon=\left.\frac{d f}{d x}\right|_{\text {exact }}-\frac{d t}{d x}\right)_{F D}=O(\Delta x) \\
& \log \varepsilon=\log [O(\Delta x)]
\end{aligned}
$$

$$
\begin{aligned}
C D S, \frac{d f}{d x} & =\frac{f(x+\Delta x)-2 f(x)+f(x-\Delta x)}{\Delta x^{2}}+O\left(\Delta x^{2}\right) \\
\varepsilon & =O\left(\Delta x^{2}\right) \\
\log \varepsilon & =2 \log [O(\Delta x)]
\end{aligned}
$$

Similarly, For $p^{\text {th }}$ order accuracy:

$$
\log \varepsilon=p \log [0(\Delta x)]
$$

CW1 Draw $\log \varepsilon$ vs $\log [0(x)]$ plot for $p=1$ and 2 and discuss your results
![](https://cdn.mathpix.com/cropped/9e1e3448-d974-4071-b5a0-123651a993aa-07.jpg?height=504&width=799&top_left_y=982&top_left_x=247)

Error decreases with reduction in grid-spacing with faster convergence rate for $2^{\text {nd }}$ order scheme than $1^{\text {st }}$ order scheme.

## Transient term discretization and notation $\left(\frac{d f}{d t}\right)$

I $\Delta t=$ time - step

$$
\begin{aligned}
& f(t+\Delta t)=f(t)+\Delta t f^{\prime}(t)+\frac{\Delta t^{2}}{2!} f^{\prime \prime}(t)+\ldots \\
& f(t-\Delta t)=f(t)-\Delta t f^{\prime}(t)+\frac{\Delta t^{2}}{2!} f^{\prime \prime}(t)+\ldots
\end{aligned}
$$

size\}
or, $f^{n+1}=f^{n}+\Delta t\left(f^{\prime}\right)^{n}+\frac{\Delta t^{2}}{2!}\left(f^{\prime \prime}\right)^{n}+\ldots$

$$
f^{n-1}=f^{n}-\Delta t\left(f^{\prime}\right)^{n}+\frac{\Delta t^{2}}{2!}\left(f^{\prime \prime}\right)^{n}+\ldots
$$

$$
\begin{aligned}
\therefore \quad \frac{d f^{n}}{d t} & =\frac{f^{n+1}-f^{n}}{\Delta t}+O(\Delta t) \quad\{F D S\} \\
& =\frac{f^{n}-f^{n-1}}{\Delta t}+O(\Delta t) \quad\{B D S\} \\
& =\frac{f^{n+1}-f^{n-1}}{2 \Delta t}+O\left(\Delta t^{2}\right) \quad\{C D S\}
\end{aligned}
$$

$1 D$-transient heat conduction, $S_{p} \frac{\partial T}{\partial t}=\frac{\partial}{\partial x}\left(K \frac{\partial T}{\partial x}\right)$, in a rod/bar $\{T(x, t)\}$
Assume: Material properties are constant
Initial condition:

$$
T(x, 0)=300 \mathrm{~K}
$$

B.C

$$
\begin{aligned}
& T(0, t)=400 k \\
& T(L, t)=300 k
\end{aligned}
$$

![](https://cdn.mathpix.com/cropped/9e1e3448-d974-4071-b5a0-123651a993aa-08.jpg?height=267&width=616&top_left_y=1463&top_left_x=958)

Discretization: $\frac{\partial T}{\partial t}=\frac{K}{s c_{p}} \frac{\partial^{2} T}{\partial x}=\alpha \frac{\partial^{2} T}{\partial x^{2}}$

$$
\Delta x=\frac{L}{N x-1}
$$

For temporal term: FDS,
$i=$ spatial node
$n+1=$ next time step
$n=$ present time step

→ Time marching problem can be solved using explicit or implicit scheme

→ Explicit scheme
![](https://cdn.mathpix.com/cropped/9e1e3448-d974-4071-b5a0-123651a993aa-09.jpg?height=142&width=634&top_left_y=129&top_left_x=866)

$$
\begin{equation*}
\frac{T_{i}{ }^{n+1}-T_{i}{ }^{n}}{\Delta t}=\alpha \frac{T_{i+1}^{n}-2 T_{i}{ }^{n}+T_{i-1}{ }^{n}}{\Delta x^{2}} \tag{1}
\end{equation*}
$$

* In explicit scheme, spatial derivatives are defined at present time-step
$\varepsilon q^{n} 1$ is rearranged to find $\tau_{i}^{n+1}$

$$
\begin{aligned}
T_{i}^{n+1} & =T_{i}^{n}+\frac{\alpha \Delta t}{\Delta x^{2}}\left(T_{i+1}^{n}-2 T_{i}^{n}+T_{i-1}^{n}\right) \\
& =\frac{\alpha \Delta t}{\Delta x^{2}} T_{i+1}^{n}+\left(1-\frac{2 \Delta t}{\Delta x^{2}}\right) T_{i}^{n}+\frac{\alpha \Delta t}{\Delta x^{2}} T_{i}^{n-1} \\
& =a_{E} T_{i+1}^{n}+\left[1-\left(a_{E}+a_{w}\right)\right] T_{i}^{n}+a_{w} T_{i}^{n-1} \\
& =a_{E} T_{i+1}^{n}+a_{p} T_{i}^{n}+a_{w} T_{i}^{n-1}
\end{aligned}
$$

Initial condition: $\quad T[0: N X-1]=300$
Boundary condition: $\quad T_{0}=T_{\text {left }}=400$

$$
T_{N \times-1}=T_{\text {right }}=300 \mathrm{~K}
$$

solving goverining eqn at internal nodes. \{Assembly of $F \cdot D$ equation\}

$$
\begin{aligned}
& T_{1}^{n+1}=a_{w} T_{0}^{n}+a_{p} T_{1}^{n}+a_{E} T_{T_{2}}^{n} \\
& T_{2}{ }^{n+1}=a_{w} T_{1}^{n}+a_{p} T_{2}^{n}+a_{E} T_{3}^{n} \\
& \vdots \\
& T_{N \times-2}{ }^{n+1}=a_{w} T_{N \times-3}^{n}+a_{p} T_{N \times-2}^{n}+a_{E} T_{N \times-1}^{n}
\end{aligned}
$$

i.e. For $(i=2 ; \quad i<N X-1 ; \quad i+t) \frac{s}{2}$

$$
T_{\text {new }}[i]=a_{w} T[i-1]+a_{p} T[i]+a_{E}[T i+1]
$$

## CFD Analysis

Pre-processing:

1) Input material properties $\left(k, \rho, C_{p}\right)$
2) Discretize rod in gridnodes: Define $\Delta x$, $\Delta t$
3) Chose discretization schemes, and find coefficients: $a_{E}, a_{P}, a_{w}$
4) Initial conditions
5) Boundary condition

Processing: 1) Solve system of algebraic equations → Explicit scheme at internal grid nodes to find $T^{n+1}\left\{T_{n e w}\right\}$
2) Update Temperature i.e. $T^{n}=T^{n+1}$

$$
\text { For } \begin{aligned}
{[i=1 ;} & i<N x-1 ; i++) \mathcal{E} \\
& T[i]=\text { Tnew }[i]
\end{aligned}
$$

3) Apply Boundary conditions

Post processing!

1) Write output
2) Visualize results
