HW-1:
HW-1: Given, $\frac{\partial T}{\partial t}=\alpha \frac{\partial q}{\partial x}$; where $q=$ auxiliany variable $=\frac{\partial T}{\partial x}$
![](https://cdn.mathpix.com/cropped/4d2de3a3-ed8d-4828-94a7-b8284596e5c7-1.jpg?height=304&width=2384&top_left_y=888&top_left_x=259)
$\frac{1.1}{(\text { a })} \frac{\partial T}{\partial t}=\alpha \frac{\partial q}{\partial x} \Rightarrow \frac{\partial T}{\partial t}=\alpha \frac{\partial T_{T}}{\partial x^{2}}$
$\stackrel{L}{\text { thermal diffusivity. }} \quad \alpha=\frac{k}{\rho c}$
Here is the 2nd order PDE.
![](https://cdn.mathpix.com/cropped/4d2de3a3-ed8d-4828-94a7-b8284596e5c7-1.jpg?height=651&width=2644&top_left_y=1819&top_left_x=194)
(c) Auxiliany variable, $q(x, t)=\frac{\partial T}{\partial x}$

The physical meaning of the auxiliany variable is temperatate gradient.
units of $q$ is $(k / m)$. It can also be dencribed by slope of the spatial temperature change.
$\frac{1.2}{\text { (a) Governing PDE, } \alpha T_{x x}=T_{t}}$
$\Rightarrow \alpha T_{x x}-T_{t}=0$
$\alpha, b=0, c=0$
Here, $a=\alpha, b=0, c=0$, as $b^{2}-4 a c=0$
So, the governining PDE is parabolic.
(6) also, $d T_{x}=\frac{\partial T_{x}}{t} d t+\frac{\partial T_{x}}{\partial x} d x$
$d T_{t}=\frac{\partial T_{t}}{t} d t+\frac{\partial T_{t}}{\partial x} d x$
$d T_{t}=\frac{2 T_{t}}{2 t} d t+\frac{\partial T_{t}}{\partial x} d x$
$d T_{t}=T_{t t} d t+T_{t x} d x-$ (3)
Here, (1),(2) 2 (3),
matrix formation,
$\vec{A}$
$\left.\left[\begin{array}{ccc}\alpha & 0 & 0 \\ d x & d t & 0 \\ 0 & d x & d t\end{array}\right]\left\{\begin{array}{c}\vec{b} \\ T_{x x} \\ T_{x t} \\ T_{t t}\end{array}\right\}=\left\{\begin{array}{c}\vec{x} \\ T_{t} \\ d T_{x} \\ d T_{t}\end{array}\right\}\right\}$
here, $\operatorname{det}(\bar{A})=0$
$\Rightarrow \quad \alpha(d t)^{2}=0$
$\Rightarrow \quad(d t)^{2}=$
This is the characteriest
Phynical significance:
Parabolic equations only have one (1) real characteristics.
If is a for wand marching in time problem, where there for be
in time, (at $t=0, T[x, 0]=T_{0}$ ). For a finite time $(t>0)$, temperature will vary along the rod. But after a lood time, it will reach steady state vary along the rod. But, after a
1.3
(a) To obtain a well-posed problem, one-initial condition is requived. (at time $t=0$ ) $T(x, 0)=T_{0} ; 0<x<L$
(b) 2 Boundary conditions are required in space at two ends of
at $x=0$
at $x=L$
(c) Initial condition: $T(x, 0)=T_{1} x=0$
Boundary conditions:
$(t>0) \quad\left[\begin{array}{l}\text { Considering } \\ \text { diricellet }\end{array}\right.$
diricillet
Boundary condns]
Problem 2:
$2 \cdot 1$ (a) linearized compressible small-disturbance potential equation,

$$
\left(1-M_{\infty}^{2}\right)^{2} \frac{V_{\phi} \phi}{2 x^{2}}+\frac{\partial^{2} \phi}{2 y^{2}}=0
$$

if I write it in the genercal 2nd ordere PDE form,
(b) Characteristic eqn derivation:

2nd, $\quad\left(1-M_{\infty}^{2}\right) \phi_{x x}+\phi_{y y}=0$-(1)

$$
\begin{aligned}
& d \phi_{x}=\frac{\partial \phi_{x}}{\partial x} d x+\frac{\partial \phi_{x}}{\partial y} d y \\
& \Rightarrow d \phi_{x}=\phi_{x x} d x+\phi_{x y} d y \\
& d \phi_{y}=\frac{\partial \phi_{y}}{\partial x} d x+\frac{\partial \phi_{y}}{\partial y} d y \\
& \Rightarrow d \phi_{y}=\phi_{x y} d x+\phi_{y y} d y
\end{aligned}
$$

Now, $\left.\left.\underset{\vec{A}}{\left[\begin{array}{ccc}1-M_{0}^{2} & 0 & 1 \\ d x & d y & 0 \\ 0 & d x & d y\end{array}\right]_{\vec{x}}^{\{ } \underset{\vec{b}}{\phi_{x y}} \phi_{x y}}\right\}_{\vec{b}}=\underset{\vec{b}}{\{ } \frac{0}{d \phi_{x}}\right\}$

$$
\begin{aligned}
\operatorname{det}(\vec{A}) & =0 \\
& \Rightarrow\left(1-M_{\infty}^{2}\right)(d y)^{2}+(d x)^{2}=0 \\
& \Rightarrow\left(\frac{d y}{d x}\right)^{2}=-\frac{1}{1-M_{\infty}^{2}}=\frac{1}{M_{\infty}^{2}-1} \\
& =\frac{d y}{d x}= \pm \frac{1}{\sqrt{M_{\infty}^{2}-1}} \quad \begin{array}{l}
\text { This is the characteriestic } \\
\text { curve equation, an equation } \\
\text { of a line }
\end{array}
\end{aligned}
$$

So, from this eqn, 3 cases
subsonic i) $M_{\infty}<1 ; \frac{d y}{d x}= \pm \frac{i}{\sqrt{1-M_{\infty}^{2}}} ;$ imaginarey value, elliptic eqn (no veal characteristics)
Sonic iii) $M_{\infty}=1 ; \begin{aligned} & d x= \pm \sqrt{M_{\infty^{2}}-1} \\ & d x=0 \rightarrow \frac{d y}{d x}= \pm \frac{1}{0} \Rightarrow d x=0 \text { parabolic equation (two real characteristics) }\end{aligned}$
$d x= \pm \frac{1}{0} \Rightarrow d x=0 \rightarrow$ para equation, only I real characteristics
(c) For $M_{\infty}>1$, (supersonic flow)

$$
\frac{d y}{d x}= \pm \frac{1}{\sqrt{M_{\infty}{ }^{2}-1}} ; \quad \rightarrow \frac{y= \pm \frac{1}{\sqrt{M_{\infty}{ }^{2}-1}} x+c}{2 \text { set of linax }}
$$

$$
\begin{aligned}
& 2 \text { set of lineare equations } \\
& \text { (streaight line) }
\end{aligned}
$$

The slope of the characteristic curves are
$m_{1}=\frac{1}{\sqrt{M_{\infty}^{2}-1}} ; \quad m_{2}=-\frac{1}{\sqrt{M_{\infty}^{2}-1}}$
![](https://cdn.mathpix.com/cropped/4d2de3a3-ed8d-4828-94a7-b8284596e5c7-1.jpg?height=910&width=2211&top_left_y=16919&top_left_x=129)

This is a hyperbolic equation, which characterizes that for compressible flow over a slender
body, the perturbation travel along body, the perturballich
a line (called the chanacterisitic line) without distontion.

![](https://cdn.mathpix.com/cropped/4d2de3a3-ed8d-4828-94a7-b8284596e5c7-1.jpg?height=1041&width=2839&top_left_y=17872&top_left_x=216)
Problem 3:

3.1
(a) $\frac{\partial u}{\partial t}+u_{\infty} \frac{\partial u}{\partial x}=0$ where, $u_{\infty}>0$ and $u=u(x, t)$

This equation states that the disturbance, $u(x, t)$ is transported in the $x+$ direction 3.2
$\frac{\partial u}{\partial t}+u \infty \frac{\partial u}{\partial x}=0 \quad$ (lst order advection equation)
(a) diff. wrt time (t): $\frac{\partial^{2} u}{\partial t^{2}}+u_{\infty} \frac{\partial^{2} u}{\partial x \partial t}=0$
$\Rightarrow u_{t t}+u_{\infty} u_{x t}=0$ - (1)
(b) diff wrat $x_{i} \quad \frac{\partial^{2} u}{\partial x^{2} t}+u_{\infty} \frac{\partial^{2} u}{\partial x^{2}}=0$
$\Rightarrow u_{x t}+u_{\infty} u_{x x}=0$ - (2)
(c) (1) $-u_{\infty}$ (2); $\quad u_{t t}-u_{\infty}^{2} u_{x x}=0$ Derived
$\frac{3.3}{\text { (a) }}$
Characteristics curve:

$$
\begin{aligned}
& u_{\infty}^{2} u_{x x}-u_{t t}=0 \\
& u_{x x} d x+u_{x t} d t=d u_{x} \\
& u_{x t} d x+u_{t t} d t=d u_{t}
\end{aligned}
$$

$$
\begin{aligned}
& \text { matrix: } \\
& \underbrace{\left[\begin{array}{ccc}
u_{\infty}^{2} & 0 & -1 \\
d x & d t & 0 \\
0 & d x & d t
\end{array}\right]}_{\rightarrow}\left\{\begin{array}{l}
u_{x x} \\
u_{x t} \\
u_{x t}
\end{array}\right\}=\left\{\begin{array}{c}
0 \\
d u_{x} \\
d u_{t}
\end{array}\right\} \\
& \text { To solve the eqn, } \operatorname{det}(\bar{A})=0 \\
& \Rightarrow \quad u_{e}^{2}(d t)^{2}-(d x)^{2}=0 \\
& \Rightarrow\left(\frac{d t}{d x}\right)^{2}=+\frac{1}{u_{\infty}^{2}} \\
& \text { 2nd order PDE is a hyperbolic equation, which means }
\end{aligned}
$$

It has two chance corcess. It models intormation propagation at a finite speed, $U_{\infty}$. These two eqn's represent two waves travelling in opposite
directions, ine seepresenting paths along which the information propagates.
(b) Two initial equations are required, to determine the soln as its a

2nd order PDE,
$u(x, 0)=f(x)$
$\frac{\partial u}{\partial t}(x, 0)=g(x)$

