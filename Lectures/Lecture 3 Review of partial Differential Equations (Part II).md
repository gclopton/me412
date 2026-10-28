## 2b. Review - Partial Differential Equation (PDE)

## OUTLINE

* $\quad 2^{\text {nd }}$ order PDE
* Classification of PDE
- Eviptic
- Parabolic
- Hyperbolic
* Characteristics of PDE


## RECALL

* Transport eqn: $\quad \frac{\partial \phi}{\partial t}+\vec{u} \cdot \nabla \phi=\nabla \cdot\left(\Gamma_{\phi} \nabla \phi\right)+S_{\phi}$
* Based on the assumptions and known $\phi$ and $\Gamma_{\phi}$, we can. derive fundamental equations in fluid. flow and/or heat transfer, such as steady state heat conduction, advection-diffusion eqn, Navier-ctokes eqn, inviscid incompressible fluid flow equation etc.

Ordinary Differential eqn vs Partial Differential Equation (ODE) (PDE)

ODE → Equations that contain "derivative w.r.t just one independent variable"
e.g. $\frac{\partial \phi}{\partial x}=c, \frac{\partial \phi}{\partial t}=c, \frac{\partial^{2} \phi}{\partial y^{2}}=0$ and so on...

- Here, dependent variable is $\phi$ and independent variable in each equation is $x, t$ and $y$.
- eg. One-dimensional steady state heat conduction: $\frac{\partial^{2} T}{\partial x^{2}}=S_{T}$
$\phi=T \Rightarrow$ dependent variable
$x \Rightarrow$ independendent variable

PDE → Equations that contain "derivatives w.r.t more than one independent variable"
e.g. $\frac{\partial^{2} \phi}{\partial x^{2}}+\frac{\partial \phi}{\partial t}+\frac{\partial \phi}{\partial y}+S_{\phi}=0 \quad\left\{2^{\text {nd }}\right.$ order $\left.P D E\right\}$

- Dependent variable is $\phi$ and independent variables are $x, t$ and $y$ in the above equation.
e.g. $\frac{\partial u}{\partial t}+\frac{\partial u}{\partial y}=0 \quad\left\{1^{\text {st }}\right.$ order PDE\}
- Dependent variable is $u$ and independent variables are $t$ and $y$ in the above equation

PDE's: Let us consider some more examples of PDEs.

$$
\begin{array}{ll}
\frac{\partial \phi}{\partial x}+x \frac{\partial \phi}{\partial y}+y \phi=0 & -2.1 \\
\left(\frac{\partial^{2} \phi}{\partial x^{2}}\right)^{2}+\frac{\partial^{2} \phi}{\partial x \partial y}+\phi \frac{\partial \phi}{\partial y}=0 & -2.2 \\
\phi \frac{\partial^{2} \phi}{\partial x^{2}}+\phi \frac{\partial \phi}{\partial x}+x \frac{\partial \phi}{\partial y}=0 & -2.3 \tag{$-2 \cdot 3$}
\end{array}
$$

Order of PDE: It is defined by the order of highest order derivative
Linear PDE: A PDE is linear if the coefficients of the derivative terms do not contain the dependent variable $(\phi)$ or its derivative
Non-linear PDE: When the coefficients of the derivative terms do contain the dependent variable (D) or its derivative
Quasi-linear PDE: when the equation is linear in the highest partial derivative
CW1 Classify equations 2.1 to 2.3

|  |  | Order | Linear/Non-Linear/ Quasi-linear |  |
| :---: | :---: | :---: | :---: | :---: |
| $E_{q^{n}}$ | 2.1 | 1 | Linear |  |
| $E_{q^{n}}$ | 2.2 | 2 | Non-Linear |  |
| $E_{q^{n}}$ | 2.3 | 2 |  |  |

Discuss

## Mathematical CLassification of PDE ( $2^{\text {nd }}$ order)

- Physical processes such as conduction, advection, momentum transport etc. are governed by PDEs.
- We are interested in identifying "characteristics", which are lines (in 2D-problems) and surfaces (in 3D-problems), that are related to the directions in which information can be propagated in prysical problem governed by these PDEs.
- Along these lines or surfaces certain properties remain constant on certain derivatives may be discontinuous.
- Knowing these characteristics of PDE help us in:
- understanding the physical problem or system
- Designing numerical schemes that are appropriate
- Let's consider a general $2^{\text {nd }}$ order PDE
$a \frac{\partial^{2} \phi}{\partial x^{2}}+b \frac{\partial^{2} \phi}{\partial x \partial y}+c \frac{\partial^{2} \phi}{\partial y^{2}}+d \frac{\partial \phi}{\partial x}+e \frac{\partial \phi}{\partial y}+f \phi=g(x, y)$
or,
$a \phi_{x x}+b \phi_{x y}+c \phi_{y y}+d \phi_{x}+e \phi_{y}+f \phi=g(x, y)-2 \cdot 4$

CW2 Dependent variable: $\phi(x, y)$
Independent variables: $\quad x, y$
Coefficients : $a, b, c, d \ldots$

- In the above eqn,
* $a, b, c, d, e, f$ can be function of $x, y, \phi, \phi_{x}, \phi_{y}$ but for simplicity we consider them fn of $x, y$ i.e. the above PDE is linear
* We are considering 2D PDE i.e. there are two independent variable $x$ and $y$ but same concepts can be applied to 3D problem.
- The classification of $2^{\text {nd }}$ order PDE depends on second derivative terms, therefore the general equation 2.4 can be arranged as:

$$
\begin{aligned}
& a \phi_{x x}+b \phi_{x y}+c \phi_{y y}=\left(-d \phi_{x}-e \phi_{y}-f \phi\right)+g(x, y) \\
\Rightarrow & a \phi_{x x}+b \phi_{x y}+c \phi_{y y}=H-2.5
\end{aligned}
$$

- Assume $\phi$ and first order derivatives to be continuous
* We are interested in finding the characteristics of eqn 2.5
- If characteristics exist and are real curves within the solution domain, then these characteristics are Locus of points along which second derlvative may be discontinuous.
- Let's write $d \phi_{x}$ and $d \phi_{y}$ as fns of $x$ and $y$ using chain rule:

$$
\begin{gathered}
\phi_{x}=\phi_{x}(x, y) \Rightarrow d \phi_{x}=\frac{\partial \phi_{x}}{\partial x} d x+\frac{\partial \phi_{x}}{\partial y} d y=\phi_{x x} d x+\phi_{x y} d y \\
d \phi_{x}=\phi_{x x} d x+\phi_{x y} d y-2.6 \\
\phi_{y}=\phi_{y}(x, y) \Rightarrow d \phi_{y}=\frac{\partial \phi_{y}}{\partial x} d x+\frac{\partial \phi_{y}}{\partial y} d y=\phi_{x y} d x+\phi_{y y} d y \\
d \phi_{y}=\phi_{x y} d x+\phi_{y y} d y-2.7
\end{gathered}
$$

- Arranging eqns $2.5-2.7$ in terms of highest order derivative 1.e.

$$
\left[\begin{array}{lll}
a & \frac{\bar{A}}{b} & c \\
d x & d y & 0 \\
0 & d x & d y
\end{array}\right]\left\{\begin{array}{l}
\vec{x} \\
\phi_{x x} \\
\phi_{x y} \\
\phi_{y y}
\end{array}\right\}=\left\{\begin{array}{l}
\vec{b} \\
H \\
d \phi_{x} \\
d \phi_{y}
\end{array}\right\}
$$

* For $\vec{x}$ to be discontinuous $\operatorname{det}(A)=0$
$\operatorname{det}(\underline{\underline{A}})=a(d y \cdot d y-0)-b(0-d x d y)+c(d x \cdot d x-0)$
$-\quad \operatorname{det}(\stackrel{A}{=})=a d y^{2}+b d x d y+c d x^{2}=0$
or, $\quad a\left(\frac{d y}{d x}\right)^{2}+b\left(\frac{d y}{d x}\right)+c=0$
Scharacteristic/
Quadratic eqn $\}$
Or, $\quad \frac{d y}{d x}=\frac{-b \pm \sqrt{b^{2}-4 a c}}{2 a} \quad\{$ Roots of quadratic eqn?
$\Delta / D=$ Discriminant $]$
→ Characteristic curve of $2^{\text {nd }}$ order PDE $\left\{E q^{m}\right.$ of line $\}$


## Classification of $2^{\text {nd }}$ order PDE

Case-I $b^{2}-4 a c=0 \Rightarrow$ Parabolic equation
one real characteristics, i.e. $\frac{d y}{d x}=\frac{-b}{2 a}$
Case - II $b^{2}-4 a c<0 \Rightarrow$ Elliptic equation
No real characteristics
i.e. $\frac{d y}{d x}=\frac{\text { imaginary }}{\text { roots }}$

Case - III $b^{2}-4 a c>0 \Rightarrow \frac{\text { Hyperbolic equation }}{\text { two real characteristics }}$ i.e $\frac{d y}{d x}=\frac{-b \pm \sqrt{b^{2}-4 a c}}{2 a}$

Example 1. Steady state heat conduction in 2D with heat generation
Governing eqn: $\nabla \cdot(K \nabla T)=S_{T}$

$$
\begin{aligned}
& \Rightarrow\left(\frac{\partial}{\partial x} i+\frac{\partial}{\partial y} j\right) \cdot\left(k \frac{\partial T}{\partial x} i+\frac{k \partial T}{\partial y} j\right)=S_{T} \\
& \Rightarrow \frac{k \partial^{2} T}{\partial x^{2}}+k \frac{\partial^{2} T}{\partial y^{2}}=S_{T} \\
& \Rightarrow \frac{\partial^{2} T}{\partial x^{2}}+\frac{\partial^{2} T}{\partial y^{2}}=\frac{S_{T}}{k} \\
& \Rightarrow T_{x x}+T_{y y}=\frac{S_{T}}{k} \\
& \Rightarrow \phi_{x x}=T_{x x}, \phi_{y y}=T_{y y}, g=\frac{S_{T}}{k}, a=1, b=0, c=1
\end{aligned}
$$

## Note:- 2D.Steady state conduction is an Elliptic equation

![](https://cdn.mathpix.com/cropped/d0ae3915-5c0d-4102-8c2f-236e64bab9b1-06.jpg?height=372&width=225&top_left_y=123&top_left_x=25)

- It has no real characteristic
- i.e. $\frac{d y}{d x}=$ imaginary roots
- Heat source, $S_{T}$, acts as a thermal disturbance and it propagates in all directions at an infinite speed
- Thermal disturbance is felt anywhere and everywhere in the domain
- Boundary condition primarily drives the solution
- Discontinuities may exist along the boundary but
![](https://cdn.mathpix.com/cropped/d0ae3915-5c0d-4102-8c2f-236e64bab9b1-06.jpg?height=359&width=216&top_left_y=632&top_left_x=29)
the governing equation is solved inside the domain
- As the disturbance travels at infinite speed the solution remains continuous inside the domain
- A point inside the domain is influenced by all the neighboring points thus, when designing a numerical scheme the temperature at a given point should be influenced by all the neighboring points
- These type of problems are called equilibrium type or boundary value problem

Example 2 One dimensional transient heat conduction Governing Eqn: $\quad \frac{\rho C_{p}}{\frac{\partial T}{\partial t}}=\nabla \cdot(K \nabla T)$

CW4 CLassification: $\quad \operatorname{lC}^{P} \frac{\partial T}{\partial t}=k \frac{\partial^{2} T}{\partial x^{2}}$
![](https://cdn.mathpix.com/cropped/d0ae3915-5c0d-4102-8c2f-236e64bab9b1-06.jpg?height=160&width=351&top_left_y=1459&top_left_x=1109)
$\Rightarrow \quad \frac{\partial T}{\partial t}=\frac{k}{\rho C_{p}} \frac{\partial^{2} T}{\partial x^{2}}=\frac{\alpha \partial^{2} T}{\partial x^{2}}$
$\Rightarrow \quad \alpha \frac{\partial^{2} T}{\partial x^{2}}-\frac{\partial T}{\partial t}=0$
$\Rightarrow \quad a=\alpha, b=0, c=0$
$\Rightarrow b^{2}-4 a c=0$
⇒ parabolic equation

## Note:- 1D-Transient conduction is an example of Parabolic equation

![](https://cdn.mathpix.com/cropped/d0ae3915-5c0d-4102-8c2f-236e64bab9b1-07.jpg?height=120&width=354&top_left_y=142&top_left_x=0)

- It has one real characteristics
- i.e. $\frac{d t}{d x}=0$
- At $t>0$, a sudden jump in temperature at $x=0$, acts as the thermal disturbance or discontinuity
- Thermal disturbance can only move forward in time i.e. the solution after $t>0$ will be dependent on $T_{1}$ and not $T_{0}$ (applied at $t=0$ )

![](https://cdn.mathpix.com/cropped/d0ae3915-5c0d-4102-8c2f-236e64bab9b1-07.jpg?height=330&width=350&top_left_y=556&top_left_x=0)
Metallic Rod

- Also, thermal disturbance can't influence what has nappened in fast.
- So, time is like one way or unidirectional coordinate system
- $t>0$ acts as the initial condition
- Discontinuity arise due to the disturbance created at initial time as initial condition
- This type of problem is also called time-marching problem
Que Is the transient heat conduction eqn only parabolic?
- What will happen after a long tinne?
"Temperature may reach steady state"

![](https://cdn.mathpix.com/cropped/d0ae3915-5c0d-4102-8c2f-236e64bab9b1-07.jpg?height=267&width=312&top_left_y=1264&top_left_x=0)
$t=0, T[x, L]=T_{0}$

![](https://cdn.mathpix.com/cropped/d0ae3915-5c0d-4102-8c2f-236e64bab9b1-07.jpg?height=267&width=396&top_left_y=1264&top_left_x=473)

$$
\begin{aligned}
t>0 \Rightarrow t=t_{1}, & T(x=0)=T_{1} \\
& T(x, L]=T_{0}
\end{aligned}
$$

$$
\begin{array}{r}
t>t_{1} \Rightarrow t=t_{2}, T(x=0)=T_{1} \\
T(x=L)=T_{0}
\end{array}
$$

$$
\begin{array}{r}
t>t_{2} \Rightarrow t=t_{3}, T(x=0)=T_{1} \\
T(x=L)=T_{0}
\end{array}
$$

![](https://cdn.mathpix.com/cropped/d0ae3915-5c0d-4102-8c2f-236e64bab9b1-07.jpg?height=271&width=506&top_left_y=1264&top_left_x=992)

$$
\text { at } t \gg 0
$$

Steady-state
"Elliptic equation"
∴ Transient heat conduction is parabolic in time and elliptic in space.

Example 3 ID-wave equation (vibrating strings)
Governing eqn: $\frac{\partial^{2} y}{\partial x^{2}}=\frac{1}{c^{2}} \frac{\partial^{2} y}{\partial t^{2}} \quad\{y$ is displacement w.r.t $x \frac{\partial y}{\partial t}$ is velocity of string
$c$ is wave propagation speed?
$\Rightarrow \quad \frac{\partial^{2} y}{\partial t}=c^{2} \frac{\partial^{2} y}{\partial x^{2}}$
or, $\quad y_{t t}=c^{2} y_{x x}$
on, $\quad c^{2} y_{x x}-y_{t t}=0$
$\phi=y, \quad \phi_{x x}=y_{x x}, \quad \phi_{t t}=y_{t t}, \quad a=c^{2}, \quad b=0, c=-1$
Classification: $\quad b^{2}-4 a c=(0)^{2}-4\left(c^{2} \cdot(-1)\right)$

$$
=4 c^{2}>0
$$

∴ Equation is hyperbolic
Note: - 1D. wave equation is an example of hyperbolic equation

- It has two real characteristics
ie. $\quad \frac{d t}{d x}=\frac{0 \pm \sqrt{0-4 c^{2}}}{2 c^{2}}= \pm \frac{2 c}{2 c^{2}}= \pm \frac{1}{c}$
or, $\frac{d x}{d t}= \pm c$
$x=c t+k_{1} \quad$ or $\quad x=-c t+k_{2}$
- $K_{1}$ and $K_{2}$ are constants and they will just shift the solution
- $x-c t$ and $x+c t$ are two real characteristics that are Spatio-temporal dependent
*     - we require two initial conditions in time i.e, displacement and velocity, as the highest order derivative in time is 2.
- eg. shock waves


## $2^{\text {nd }}$ order PDES in more than two dimensions

*     - In mathematics, dimension is defined by number of independent variables.
- Let's see a generalized three dimensional eqn as following: $a \phi_{x x}+b \phi_{y y}+c \phi_{z z}+d \phi_{x y}+e \phi_{x z}+f \phi_{y z}+\ldots=0$
- Dependent variable: $\varnothing(x, y, z)$
- Independent variables: $x, y, z$
- 3 dimensional problem $\{$ as there are three independent variable\}

CW1 Given: Transient heat conduction in three dimensional space

$$
S C_{p} \frac{\partial J}{\partial t}=\nabla \cdot(K \nabla T)
$$

Find: Dependent variable: $T(x, y, z, t)$
Independent variables: $x, y, z, t$
Problem dimension: 4

## Mathematical classification of $2^{\text {nd }}$ onder PDE in $n$-dimensions

![](https://cdn.mathpix.com/cropped/d0ae3915-5c0d-4102-8c2f-236e64bab9b1-09.jpg?height=153&width=1222&top_left_y=1162&top_left_x=129)

- Characteristics of above eqn depends on the eigen values of $\underline{a}$, which can be calculated as:

$$
\operatorname{det}(\underline{a}-\lambda I)=0 \text { to find } \lambda s
$$

$\underline{\underline{a}}=$ matrix of coefficients of $2^{\text {nd }}$ order derivative
$I=$ Identity matrix $\left\{\begin{array}{l}\text { diagonal elements }=1 \\ \text { Non-diagonal element }=0\end{array}\right\}$
$\lambda_{s}=$ eigen values
$\{$ Non-diagonal element $=0\}$

If any of $\lambda_{s}=0 \quad \Rightarrow$ Porabolic equation
If no $\lambda$ is zero and all $\lambda_{s}$ are of same sign ⇒ elliptic equation
If no $\lambda$ is zero and atleast one $\lambda$ is opposite sign than others $\Rightarrow$ Hyperbolic eqn

Example Steady state heat conduction in 3D space.
Governing eqn: $\quad \nabla \cdot(k \nabla T)=0 \Rightarrow \frac{\partial^{2} T}{\partial x^{2}}+\frac{\partial^{2} T}{\partial y^{2}}+\frac{\partial^{2} T}{\partial z^{2}}=0$
Classification: $\quad i=1$ to $3, j=1$ to $3, \phi=\phi(x, y, z)=T(x, y, z)$

$$
\begin{array}{ll}
a_{11}=1, & a_{12}=0, \\
a_{21}=0, & a_{22}=1, \\
a_{31}=0, & a_{23}=0 \\
& a_{32}=0, \\
& a_{33}=1
\end{array}
$$

$$
\begin{aligned}
\underline{a}-\lambda I & =\left[\begin{array}{lll}
a_{11} & a_{12} & a_{13} \\
a_{21} & a_{22} & a_{23} \\
a_{31} & a_{32} & a_{33}
\end{array}\right]-\lambda\left[\begin{array}{ccc}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{array}\right] \\
& =\left[\begin{array}{ccc}
a_{11}-\lambda & a_{12} & a_{13} \\
a_{21} & a_{22}-\lambda & a_{23} \\
a_{31} & a_{32} & a_{33}-\lambda
\end{array}\right]=\left[\begin{array}{ccc}
1-\lambda & 0 & 0 \\
0 & 1-\lambda & 0 \\
0 & 0 & 1-\lambda
\end{array}\right] \\
\operatorname{det}\left(\frac{a}{2}-\lambda I\right) & =(1-\lambda)[(1-\lambda)(1-\lambda)-0]-0[0-0(1-\lambda)]+0[0-0(1-\lambda)] \\
& =(1-\lambda)(1-\lambda)(1-\lambda)
\end{aligned}
$$

$\operatorname{det}(\underline{\underline{a}}-\lambda I)=0 \quad \Rightarrow \quad(1-\lambda)(1-\lambda)(1-\lambda)=0$
or, $\lambda_{1}=1, \lambda_{2}=1, \lambda_{3}=1$
∴ Steady state heat conduction equation in three dimensional space is an example of elliptic equation.

## SUMMARY

1. Genevalized Transport Equation: $\frac{\partial \phi}{\partial t}+\vec{u} \cdot \nabla \phi=\nabla \cdot\left(\Gamma_{\phi} \nabla \phi\right)+S_{\phi}$
2. $2^{\text {nd }}$ order PDE:- Linear/Non-linear/Quasi-linear and dimensionality

- Classification of equations as:
- Parabolic
- Elliplic
- Hyperbolic
- Physical significance of Characteristics of Equations

