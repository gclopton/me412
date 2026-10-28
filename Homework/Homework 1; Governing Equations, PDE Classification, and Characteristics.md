
Grady Clopton
Homework #1
ME 412

# Problem 1: 1D Transient Heat Conduction from a First-Order System

Consider a one-dimensional rod of length $L$ with constant material properties: thermal conductivity $k$, density $\rho_1$ and specific heat $C_p$. Let $T(x, t)$ denote the temperature field and let $q(x, t)$ be an auxiliary variable. Assume that $T$ and $q$ satisfy the coupled system


$$\frac{\partial T}{\partial t}=\alpha \frac{\partial q}{\partial x} \tag{1},$$

$$\frac{\partial T}{\partial x}=q \tag{2}$$


where $\alpha=\frac{k}{\beta C_p}$ is the thermal diffusivity. Since the density was defined above as $\rho_1$, we take $\beta=\rho_1$, so equivalently
$$
\alpha=\frac{k}{\rho_1 C_p}.
$$



## 1.1 Derivation of the Governing PDE


> [!Question]
> (a) Eliminate the auxiliary variable $q(x, t)$ from Eqs. (1)-(2) to obtain a single partial differential equation governing the temperature field $T(x, t)$.


Equation (2) defines the auxiliary variable as the spatial derivative (slope) of the temperature field. Since Eq. (1) involves $\frac{\partial q}{\partial x}$, we differentiate Eq. (2) with respect to $x$ (assuming $T$ is sufficiently smooth so that $\frac{\partial^2 T}{\partial x^2}$ exists)
$$
q=\frac{\partial T}{\partial x}
\quad\Longrightarrow\quad
\frac{\partial q}{\partial x}=\frac{\partial}{\partial x}\left(\frac{\partial T}{\partial x}\right)=\frac{\partial^2 T}{\partial x^2}.
$$
Substituting this expression for $\frac{\partial q}{\partial x}$ into Eq. (1) eliminates $q$ and yields a single PDE for $T$
$$
\frac{\partial T}{\partial t}=\alpha\,\frac{\partial q}{\partial x}=\alpha\,\frac{\partial^2 T}{\partial x^2}.
$$


So the governing PDE for $T(x, t)$ is

$$
\boxed{\frac{\partial T}{\partial t}=\alpha \frac{\partial^2 T}{\partial x^2}}
$$




> [!Question]
> (b) Show that the resulting equation can be written in the standard form of the one-dimensional transient heat-conduction equation.



From part (a), the temperature field satisfies $\frac{\partial T}{\partial t}=\alpha\,\frac{\partial^2 T}{\partial x^2}$. The standard form of the 1D transient heat-conduction equation is often written to explicitly show the material properties by replacing $\alpha$ with its definition and clearing the denominator. Since $k$, $\rho_1$, and $C_p$ are constants here, this is done by substituting $\alpha=\frac{k}{\rho_1 C_p}$ and then multiplying both sides by $\rho_1 C_p$.

$$
\begin{aligned}
\frac{\partial T}{\partial t} & =\alpha \frac{\partial^2 T}{\partial x^2} \\
\alpha & =\frac{k}{\rho_1 C_p} \\
\Longrightarrow \frac{\partial T}{\partial t} & =\frac{k}{\rho_1 C_p} \frac{\partial^2 T}{\partial x^2} \\
\Longrightarrow \rho_1 C_p \frac{\partial T}{\partial t} & =k \frac{\partial^2 T}{\partial x^2}
\end{aligned}
$$


Thus the equation is in the standard 1D transient heat-conduction form

$$
\rho_1 C_p \frac{\partial T}{\partial t}=k \frac{\partial^2 T}{\partial x^2}
$$

In this form, $\rho_1 C_p$ acts as the volumetric heat capacity multiplying the transient (storage) term, and $k\,\frac{\partial^2 T}{\partial x^2}$ is the conduction (diffusion) term.






> [!Question]
> (c) Explain the physical meaning of the auxiliary variable $q(x, t)$.



From Eq. (2), the auxiliary variable is simply the spatial temperature gradient,
$$
q(x,t)=\frac{\partial T}{\partial x}(x,t),
$$
so it measures the local slope of the temperature field along the rod. In standard heat-conduction notation, the (one-dimensional) heat flux is given by Fourier’s law
$$
\phi(x,t)=-k\,\frac{\partial T}{\partial x}(x,t),
$$
so $q(x,t)$ is proportional to the negative of the heat flux:
$$
\phi(x,t)=-k\,q(x,t).
$$
With this, Eq. (1) is the energy balance statement written in first-order form. Multiplying Eq. (1) by $\rho_1 C_p$ and using $\alpha=\frac{k}{\rho_1 C_p}$ gives
$$
\rho_1 C_p\,\frac{\partial T}{\partial t}=k\,\frac{\partial q}{\partial x}=-\frac{\partial \phi}{\partial x},
$$
which says the rate of change of thermal energy is driven by the divergence of the heat flux.






## 1.2 Classification and Characteristics


> [!Question]
> (a) Classify the governing partial differential equation obtained in Problem 1.1 as elliptic, parabolic, or hyperbolic. Justify your answer.


Starting from the governing equation from 1.1,

$$
\frac{\partial T}{\partial t}=\alpha \frac{\partial^2 T}{\partial x^2},
$$

rewrite it in the second-order PDE in two variables by moving everything to one side

$$
\begin{aligned}
\frac{\partial T}{\partial t} & =\alpha \frac{\partial^2 T}{\partial x^2} \\
0 & =\alpha \frac{\partial^2 T}{\partial x^2}-\frac{\partial T}{\partial t}
\end{aligned}
$$


Compare this with the standard linear second-order form showing only the second-order terms explicitly

$$
A T_{x x}+2 B T_{x t}+C T_{t t}+(\text { lower-order terms })=0 .
$$


For the heat equation,

$$
A=\alpha, \quad B=0, \quad C=0 .
$$


The classification is determined by the discriminant $B^2-A C$ :

$$
\begin{aligned}
B^2-A C & =0^2-(\alpha)(0) \\
& =0
\end{aligned}
$$


Therefore the PDE is parabolic.


> [!Question]
> (b) Derive the characteristic curve equation associated with the governing PDE and explain its physical significance in the context of transient heat conduction.




For a second-order PDE in ( $x, t$ ) with second-order coefficients $A, B, C$, the characteristic curves satisfy the quadratic differential equation

$$
A(d t)^2-2 B d x d t+C(d x)^2=0 .
$$


Substitute $A=\alpha, B=0, C=0$ to get

$$
\begin{aligned}
A(d t)^2-2 B d x d t+C(d x)^2 & =0 \\
\alpha(d t)^2-2(0) d x d t+0 \cdot(d x)^2 & =0 \\
\alpha(d t)^2 & =0 \\
(d t)^2 & =0 \\
d t & =0 .
\end{aligned}
$$


Integrating $d t=0$ gives the characteristic family

$$
t=\text { constant }
$$


This double characteristic $t=$ const reflects the parabolic (degenerate) nature of diffusion. Unlike hyperbolic wave equations where characteristics $x \pm c t=$ const represent wavefronts and finite-speed signal propagation, these characteristics do not represent propagating fronts. Instead, they indicate that initial-time lines are the natural surfaces for prescribing initial data. For the heat equation, the temperature at any $t>0$ is influenced by the temperature distribution over space (and boundary conditions), with the classical model implying no sharp propagation front and a smoothing/diffusive spread of thermal information.



## 1.3 Initial and Boundary Conditions


> [!Question]
> (a) State how many initial conditions in time are required to obtain a well-posed problem and specify where they must be prescribed.


The governing PDE is parabolic

$$
\frac{\partial T}{\partial t}=\alpha \frac{\partial^2 T}{\partial x^2} .
$$


It is first order in time, so it requires one initial condition in time. That initial condition must be prescribed on an initial-time slice, i.e. at a fixed time (conventionally $t=0$ ) for all points along the rod

$$
T(x, 0)=T_0(x), \quad 0 \leq x \leq L .
$$


> [!Question]
> (b) State how many boundary conditions in space are required and specify where they must be prescribed.



The PDE is second order in space (contains $T_{x x}$ ), so it requires two spatial boundary conditions. They must be prescribed at the two ends of the rod; one BC at $x=0$, and one BC at $x=L$, for $t>0$.




> [!Question]
> (c) Provide one physically realistic initial condition and one complete set of physically realistic boundary conditions, written mathematically.


A common physically realistic choice is that the rod starts uniformly at some temperature $T_i$, and then both ends are held at a fixed temperature $T_s$ (Dirichlet conditions), modeling contact with large thermal reservoirs.

**Initial condition (uniform):**

$$
\boxed{T(x, 0)=T_i, \quad 0 \leq x \leq L}
$$


**Boundary conditions (prescribed end temperatures):**



$$\boxed{\begin{array}{lll}T(0, t) & =T_s, & \\ T(L, t) & =T_s, & \end{array}}$$




# Problem 2: Prandtl-Glauert Equation - Classification and Characteristics

The linearized compressible small-disturbance potential equation governing inviscid compressible flow over slender bodies is

$$
\left(1-M_{\infty}^2\right) \frac{\partial^2 \phi}{\partial x^2}+\frac{\partial^2 \phi}{\partial y^2}=0
$$

where $M_{\infty}$ is the uniform freestream Mach number and $\phi$ is the perturbation velocity potential.





## 2.1 Classification and Characteristics


> [!Question]
> (a) Write the governing equation in the general second-order PDE form
> 
> $$
> a \phi_{x x}+b \phi_{x y}+c \phi_{y y}=0,
> $$
> 
> and identify the coefficients $a, b$, and $c$.
> 



$$
\begin{aligned}
\left(1-M_{\infty}^2\right) \phi_{x x}+\phi_{y y} & =0 \\
\left(1-M_{\infty}^2\right) \phi_{x x}+0 \cdot \phi_{x y}+1 \cdot \phi_{y y} & =0 .
\end{aligned}
$$


So

$$
a=1-M_{\infty}^2, \quad b=0, \quad c=1
$$


> [!Question]
> (b) Derive the characteristic equation and classify the governing equation as elliptic, parabolic, or hyperbolic.



For

$$
a \phi_{x x}+b \phi_{x y}+c \phi_{y y}=0
$$

the characteristic curves satisfy

$$
a(d y)^2-b d x d y+c(d x)^2=0
$$


Dividing by $(d x)^2$ (with $d x \neq 0$ ) gives the slope form:

$$
a\left(\frac{d y}{d x}\right)^2-b\left(\frac{d y}{d x}\right)+c=0 .
$$


The type is determined by the discriminant $\Delta=b^2-4 a c$ :

$$
\begin{aligned}
\Delta & =b^2-4 a c \\
& =0^2-4\left(1-M_{\infty}^2\right)(1) \\
& =-4\left(1-M_{\infty}^2\right) \\
& =4\left(M_{\infty}^2-1\right) .
\end{aligned}
$$


Therefore,

$$
\begin{aligned}
& M_{\infty}<1 \Rightarrow \Delta<0 \Rightarrow \text { elliptic } \\
& M_{\infty}=1 \Rightarrow \Delta=0 \Rightarrow \text { parabolic } \\
& M_{\infty}>1 \Rightarrow \Delta>0 \Rightarrow \text { hyperbolic. }
\end{aligned}
$$



> [!Question]
> (c) For $M_{\infty}>1$, determine the slopes of the characteristic curves and comment on their physical interpretation.


With $a=1-M_{\infty}^2, b=0, c=1$, the characteristic-slope equation becomes

$$
\begin{aligned}
\left(1-M_{\infty}^2\right)\left(\frac{d y}{d x}\right)^2+1 & =0 \\
\left(1-M_{\infty}^2\right)\left(\frac{d y}{d x}\right)^2 & =-1 \\
\left(\frac{d y}{d x}\right)^2 & =\frac{-1}{1-M_{\infty}^2} \\
& =\frac{1}{M_{\infty}^2-1} \\
\frac{d y}{d x} & = \pm \frac{1}{\sqrt{M_{\infty}^2-1}}
\end{aligned}
$$


So the two characteristic families have slopes

$$
\frac{d y}{d x}= \pm \frac{1}{\sqrt{M_{\infty}^2-1}} \quad\left(M_{\infty}>1\right)
$$


Physically, in supersonic flow the governing equation is hyperbolic and information propagates along these characteristic lines. Those lines correspond to Mach lines which are the directions along which small disturbances travel in the linearized theory. If $\mu$ is the Mach angle, $\sin \mu=1 / M_{\infty}$, then

$$
\tan \mu=\frac{\sin \mu}{\cos \mu}=\frac{1 / M_{\infty}}{\sqrt{1-1 / M_{\infty}^2}}=\frac{1}{\sqrt{M_{\infty}^2-1}}
$$




So the characteristic slopes are $\pm \tan \mu$. This means that disturbances are confined to a downstream Mach wedge/cone (in 2D, a wedge) rather than influencing the entire field the way they do in subsonic (elliptic) potential flow.



# Problem 3: Advection, Derived Wave Equation, and Characteristics

A disturbance in the $x$-component of velocity, denoted by $u(x, t)$, is transported by a constant freestream velocity $u_{\infty}>0$. The governing equation is

$$
\frac{\partial u}{\partial t}+u_{\infty} \frac{\partial u}{\partial x}=0 .
$$

## 3.1 Physical Interpretation

> [!Question]
> (a) Briefly explain the physical meaning of the above advection equation.



The equation

$$
\frac{\partial u}{\partial t}+u_{\infty} \frac{\partial u}{\partial x}=0
$$

says that the disturbance field $u(x, t)$ is simply carried downstream by a uniform flow moving at speed $u_{\infty}>0$, without being created, destroyed, or diffused. You can see this by looking at the change in $u$ as you move with the flow. Along a trajectory $x(t)$ moving at the freestream speed,

$$
\begin{aligned}
x(t) & =x_0+u_{\infty} t \\
\frac{d}{d t} u(x(t), t) & =\frac{\partial u}{\partial t}+\frac{d x}{d t} \frac{\partial u}{\partial x} \\
& =\frac{\partial u}{\partial t}+u_{\infty} \frac{\partial u}{\partial x} \\
& =0
\end{aligned}
$$


So $u$ stays constant along lines $x-u_{\infty} t=$ const. Physically whatever shape the disturbance has initially just translates rigidly to the right at speed $u_{\infty}$, with no change in amplitude or form. This pure advection/convection, with no diffusion or wave steepening terms included.


## 3.2 Derivation of a Second-Order PDE

Since characteristics have been studied primarily for second-order PDEs in the lectures, the transient advection equation is converted to a second-order equation.


> [!Question]
> (a) Differentiate the advection equation with respect to time $t$.


Start from

$$
u_t+u_{\infty} u_x=0 .
$$


Differentiate both sides with respect to $t$

$$
\begin{aligned}
\frac{\partial}{\partial t}\left(u_t+u_{\infty} u_x\right) & =\frac{\partial}{\partial t}(0) \\
u_{t t}+u_{\infty} u_{x t} & =0 .
\end{aligned}
$$


So

$$
u_{t t}+u_{\infty} u_{x t}=0 .
$$



> [!Question]
> (b) Differentiate the advection equation with respect to space $x$.



Again start from

$$
u_t+u_{\infty} u_x=0
$$


Differentiate both sides with respect to $x$ 

$$
\begin{aligned}
\frac{\partial}{\partial x}\left(u_t+u_{\infty} u_x\right) & =\frac{\partial}{\partial x}(0) \\
u_{t x}+u_{\infty} u_{x x} & =0
\end{aligned}
$$


So

$$
u_{t x}+u_{\infty} u_{x x}=0
$$




> [!Question]
> (c) Using the original advection equation together with the results of parts (a) and (b), eliminate the mixed derivative terms, assuming sufficient smoothness so that $u_{x t}=u_{t x}$. Show that $u(x, t)$ satisfies
> 
> $$
> u_{t \mathrm{t}}-u_{\infty}^2 u_{x x}=0
> $$




From part (a)

$$
\begin{aligned}
u_{t t}+u_{\infty} u_{x t} & =0 \\
u_{t t} & =-u_{\infty} u_{x t}
\end{aligned}
$$


From part (b)

$$
\begin{aligned}
u_{t x}+u_{\infty} u_{x x} & =0 \\
u_{t x} & =-u_{\infty} u_{x x}
\end{aligned}
$$


Assuming sufficient smoothness so that $u_{x t}=u_{t x}$, substitute $u_{x t}=u_{t x}=-u_{\infty} u_{x x}$ into the expression for $u_{t t}$ 

$$
\begin{aligned}
u_{t t} & =-u_{\infty} u_{x t} \\
& =-u_{\infty} u_{t x} \\
& =-u_{\infty}\left(-u_{\infty} u_{x x}\right) \\
& =u_{\infty}^2 u_{x x}
\end{aligned}
$$


Bring terms to one side

$$
u_{t t}-u_{\infty}^2 u_{x x}=0
$$


Therefore,

$$
u_{t t}-u_{\infty}^2 u_{x x}=0
$$



## 3.3 Characteristics and Initial Conditions


> [!Question]
> (a) Derive the characteristic curves of the second-order PDE and explain their physical significance.


Start with

$$
u_{t t}-u_{\infty}^2 u_{x x}=0
$$


Rewrite in the standard second-order form in variables $(x, t)$ 

$$
A u_{x x}+2 B u_{x t}+C u_{t t}=0
$$

so that

$$
-u_{\infty}^2 u_{x x}+0 \cdot u_{x t}+1 \cdot u_{t t}=0,
$$

hence

$$
A=-u_{\infty}^2, \quad B=0, \quad C=1 .
$$


The characteristic curves satisfy

$$
A(d t)^2-2 B d x d t+C(d x)^2=0 .
$$


Substitute $A=-u_{\infty}^2, B=0, C=1$ 

$$
\begin{aligned}
A(d t)^2-2 B d x d t+C(d x)^2 & =0 \\
\left(-u_{\infty}^2\right)(d t)^2-2(0) d x d t+1 \cdot(d x)^2 & =0 \\
(d x)^2-u_{\infty}^2(d t)^2 & =0 \\
\left(d x-u_{\infty} d t\right)\left(d x+u_{\infty} d t\right) & =0
\end{aligned}
$$


Therefore either

$$
d x-u_{\infty} d t=0 \quad \Longrightarrow \quad \frac{d x}{d t}=u_{\infty} \quad \Longrightarrow \quad x-u_{\infty} t=\mathrm{const},
$$

or

$$
d x+u_{\infty} d t=0 \quad \Longrightarrow \quad \frac{d x}{d t}=-u_{\infty} \quad \Longrightarrow \quad x+u_{\infty} t=\text { const } .
$$


So the two characteristic families are

$$
x-u_{\infty} t=\text { const } \quad \text { and } \quad x+u_{\infty} t=\text { const. }
$$


These are the lines along which information propagates for the wave equation. Disturbances travel at speeds $\pm u_{\infty}$. In this particular problem, the wave equation was manufactured from the first-order advection equation, so only the $x-u_{\infty} t=$ const family corresponds to the original physical advection (right-going transport). The left-going family $x+u_{\infty} t=$ const appears because converting the first-order equation into a second-order one introduces extra solutions that were not present in the original advection model unless you restrict the initial data appropriately.



> [!Question]
> (b) State how many initial conditions are required to uniquely determine the solution of this second-order PDE, and write them explicitly.




Because

$$
u_{t t}-u_{\infty}^2 u_{x x}=0
$$

is second order in time, a unique solution (for a well-posed IVP on an infinite/periodic domain) requires two initial conditions at an initial time (take $t=0$ )

$$
\begin{aligned}
u(x, 0) & =f(x), \\
u_t(x, 0) & =g(x) .
\end{aligned}
$$


If you want the solution of the wave equation to coincide with the solution of the original right-going advection equation, those initial conditions cannot be arbitrary. They must be compatible with $u_t+ u_{\infty} u_x=0$ at $t=0$.

$$
\begin{aligned}
u_t(x, 0)+u_{\infty} u_x(x, 0) & =0 \\
g(x)+u_{\infty} f^{\prime}(x) & =0 \\
g(x) & =-u_{\infty} f^{\prime}(x)
\end{aligned}
$$


So, to recover pure advection within the wave-equation description, you may take

$$
u(x, 0)=f(x), \quad u_t(x, 0)=-u_{\infty} f^{\prime}(x) .
$$




