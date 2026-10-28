


BOUNDARY CONDITIONS (WELL POSED BOUNDARY VALUE PROBLEM) For $2^{\text {nd }}$ order PDE
(1) Dirichlet $B \circ C$ (when the value of the dependent variable is specifies)
(2) Neumain B.C (when the value of the gradient of the depondent variable is specticd)
(3) Mixed BoC (value of the dependent variable is expessed as a fn of the gradient)

## (1) Dirichlet B.C.


![[Pasted image 20260209124959.png|]]

**Figure 1:**

## (2) Neumann B.C
ex, sux bound ary condition.
adiabatic b.C


![[Screenshot 2026-02-09 at 12.51.16 PM.png]]

**Figure 2:**

(adiabiatic

Since, we do not have points outside the boundary then one-sided differencing will be used.

So, in the legt boundary, let's say we know the flux,

$$
\begin{aligned}
& q_{0}^{\prime \prime}=C_{1} \\
& \Rightarrow-k \frac{d T}{d x}=C_{1} \\
& \Rightarrow-k\left(\frac{T_{1}-T_{0}}{\Delta x}\right)=C_{1} \\
& \Rightarrow T_{0}=\frac{-C_{1} \Delta x}{k}-T_{1} \\
& q_{L}^{\prime \prime}=0 \text { or } q_{n x-1}^{\prime \prime}=0 \\
& \Rightarrow-k \frac{d T}{d x}=0 \\
& \Rightarrow-\frac{k}{\Delta x}\left(T_{n x-1}-T_{n x-2}\right)=0 \\
& \Rightarrow \frac{T_{n x-1}}{T_{n x-2}}
\end{aligned}
$$

$\mathcal{O}(\Delta x) \Rightarrow$ accuracy
How can you improve it?
By adding more no. of points iss the stencil

In $A \vec{x}=\vec{b}$ system.
$b_{1}=S_{1}-a_{\omega} T_{0}$
$b_{n x-2}=s_{n x-2}-a_{E} T_{n x-1}$
## (3) Mixed b,c
eq. Conduction - convection

![[Pasted image 20260209125324.png|500]]

**Figure 3:**
$$
\begin{aligned}
& -k \frac{d T}{d x}=h\left(T_{L}-T_{\infty}\right) \\
& -k\left(\frac{T_{n x-1}-T_{n x-2}}{\Delta x}\right)=h\left(T_{n x-1}-T_{\infty}\right) \\
& \left(h+\frac{k}{\Delta x}\right) T_{n x-1}=\frac{k T_{n x-2}}{\Delta x}+h T_{\infty} \\
& T_{n x-1}=\left(\frac{k}{\Delta x} T_{n x-2}+h T_{\infty}\right) /\left(h+\frac{k}{\Delta x}\right)
\end{aligned}
$$

Tos
air
→ Ambient temperature very close to the boundary at $L$ 。
$T_{n x-1}>T_{\infty}$

Are specifying the $B \cdot C$ correctly in the numerical method ensures that the BVP has a rigert soln! or any condition is BC?

→ NO, you need to chech if your problem is well posed
→ Three conditions need to be satisfied:

1. Existence of the solution
2. Uniqueness of the solution
3. A small perturbation in the B.C should not result in largo change in solution

$$
\frac{d^{2} T}{d \times 2}=0
$$

![[Pasted image 20260209125404.png|500]]


**Figure 4:**

(1) Existence of sot ${ }^{n} \rightarrow$ violates the heat conservation law at steady-state.
(2) Uniqueness of $\mathrm{sel}^{n}$

$$
\frac{d T}{d x}=c_{1} \Rightarrow T=c_{1} x+c_{2}
$$

at $x=0, \quad-K \frac{d T}{d x}=1 \Rightarrow C_{1}=$ known and at $x=L$ but $c_{2}$ cannot

$$
\rightarrow q^{n}=1
$$

$$
\rightarrow q^{\prime \prime}=1
$$


 ![[Pasted image 20260209125512.png]]
**Figure 5:**
 
 
 be determined
∵ One of the boundaries must be Dinchlet B.C also known as "Essential B.C".

## DISCRETIZATION ERROR (RICHARDSON EXTRAPOLATION)

so far we have determined error in terms of derivatives only but how to quantify it when jou have a whole bunch of partial derivatives in your P.D.E.

→ We do grid refinement and estimate orror. ( $\varepsilon_{k}$ )
Let $\quad \varepsilon_{h}=\alpha \Delta x^{p}+H$
$p$ is order, $H$ is higher order terms that are ignored in the discretization and $\alpha$ is constant (derivatives and factorials/constants)
$\Delta x$ is grid spacing

## OBJECTIVE Find $p$ (order of accuracy of method not just individual derivatives)

Lets say we find solution on three grids $\Delta x, 2 \Delta x, 4 \Delta x$ where $\Delta x$ is finest mesh/grid and $4 \Delta x$ is coarsest mesh.

$$
\begin{align*}
& \phi=\phi_{\Delta x}+\alpha \Delta x^{p}+H  \tag{1}\\
& \phi=\phi_{2 \Delta x}+\alpha(2 \Delta x)^{p}+H  \tag{2}\\
& \phi=\phi_{4 \Delta x}+\alpha(4 \Delta x)^{p}+H \tag{3}
\end{align*}
$$

So, we have exact $\operatorname{sun}^{n} \phi$ approximate solm:
$\phi_{\Delta x}$ for finest mesh $(\Delta x) \phi_{2 \Delta x}$ for medium mesh $(2 \Delta x)$
$\phi_{4 \Delta x}$ for coarsest mesh (4M)
eqn (2) -(1) $\Rightarrow \phi_{2 \Delta x}-\phi_{\Delta x}=\alpha \Delta x^{p}-\alpha(2 \Delta x)^{p}=\alpha \Delta x^{p}\left(1-2^{p}\right)$
$e^{n}$ (3) - (2) $\Rightarrow \phi_{4 \Delta x}-\phi_{2 \Delta x}=\alpha(2 \Delta x)^{p}-\alpha(4 \Delta x)^{p}=\alpha \Delta x^{p} 2^{p}\left(1-2^{p}\right)$

Divide (5) by (4) $\Rightarrow \frac{\phi_{4 \Delta x}-\phi_{2 \Delta x}}{\phi_{2 \Delta x}-\phi_{\Delta x}}=2^{p}$
Take $\log$ on both sides,

$$
\Rightarrow \log \left(\frac{\phi_{4 \Delta x}-\phi_{2 \Delta x}}{\phi_{2 \Delta x}-\phi_{\Delta x}}\right)=p \log 2
$$

or, $p \log 2=\log \left(\frac{\phi_{2 \Delta x}-\phi_{4 \Delta x}}{\phi_{\Delta x}-\phi_{2 \Delta x}}\right)$ or,

$$
p=\log \left(\frac{\phi_{2 \Delta x}-\phi_{\Delta \Delta x}}{\phi_{\Delta x}-\phi_{2 \Delta x}}\right) / \log 2
$$

## POLYNOMIAL FITTING

Another way to construct a stencil is to fit a polynomial of a certain order through a set of points and then differentiate that polynomial.

Let us consider first $\frac{d f}{d x}$. So, the backward and forward differencing schemes are nothing but fitting a straight lines through $i-1$ and $i$, and $i+1$ and $i$ respectively
Lets say you have of $f$ which is curve (T)
and you are using $1^{\text {st }}$ order differencing scheme. so, you are in a way fitting the curve using piecewise linear fuctions (Green lines)


![[Pasted image 20260209125546.png|500]]


**Figure 6:**

To improve the accuracy you have to increase
the grid points so that error can be minimized by increasing mesh points but, this would required more computations and memory.
So, we increase Onder of accuracy by increasing stencil size.

$$
f=a+b x+c x^{2}
$$

(1) $\left[f_{i+1}=a+b \Delta x+c \Delta x^{2}\right.$
(2) $\forall i-1=a+b(-\Delta x)+c(-\Delta x)^{2}$
(3) $L f_{i}=a+b(0)+c(0)^{2}$

→ 3 eqn 3 variables, solve $a=f_{i}$
$f_{i+1}-f_{i-1}=2 b \Delta x$

$$
\begin{aligned}
& b=\frac{f_{i+1}-f_{i-1}}{2 \Delta x} \\
& c=\frac{f_{i+1}+f_{i-1}-2 a}{2 \Delta x^{2}}
\end{aligned}
$$

at $i, x=0$ or $x$ is centred at $i$

$$
\begin{aligned}
& i+1, x=0+\Delta x \\
& i+2, x=0+2 \Delta x \\
& i-1, x=0-\Delta x \\
& i-2, x=0-2 \Delta x
\end{aligned}
$$

and, so on for uniform grid spacing.
You can do this for nonuniform spacing to but $\Delta x$ will change

Since, $f=a+b x+c x^{2}$

$$
\frac{d^{2} f}{d x^{2}}=2 c
$$

and, $c=\frac{f_{i+1}+f_{i-1}-2 a}{2 \Delta x^{2}}, a=f_{i}$

$$
\Rightarrow \frac{d^{2} f}{d x^{2}}=\frac{f_{i+1}+f_{i-1}-2 f_{1}}{\Delta x^{2}}
$$

→ CDS
So CDS is nothing but fitting $2^{\text {nd }}$ order poly. nomial using $i-1, i$ and $i+1$
Let's try 2nd order FDS points.
$f=a+b x+c x, \quad \frac{d f}{d x}=b+2 c x$ at $i, x=0$
$f_{i+1}=a+b(\Delta x)+c(\Delta x)^{2}$

$$
\begin{equation*}
\because \frac{d f}{d x}=b \tag{1}
\end{equation*}
$$

$$
\begin{equation*}
f_{i+2}=a+b(2 \Delta x)+c(2 \Delta x)^{2} \tag{- -}
\end{equation*}
$$

$$
\begin{equation*}
f_{i}=a+b(0)+c(0) \tag{3}
\end{equation*}
$$

$\Rightarrow a=f_{i}$, Multiply eqn (1) by 4 and subtract from (2)
$\Rightarrow f_{i+2}-4 f_{i+1}=-3 a-2 b \Delta x$
$\Rightarrow-2 b \Delta x=f_{i+2}-4 f_{i+1}+3 a$
$\Rightarrow b=\frac{-f i+2+4 f i+1-3 f i}{2 \Delta x}$
Similarly, you can approximate the derivatives by considering a polynomial of order by using $(n+1)$ eqns. $^{n}$. where one of the eqn will always be $f_{i}=a$.
$n+1 \Rightarrow$ no. of points in the stencil

So, with polynomial fit we can obtain higher order accurate schemes with $n+1$ points for nith order accuracy.

But, what if we want to obtain $n^{\text {th }}$ order accuracy with less than $n+1$ point?

## COMPACT FINITE DIFFERENCE

Lets say we want $4^{\text {th }}$ order accuracy for $\frac{d f}{d x}$ using 3 points, $i-1, i$ and $i+1$ at $i$

$$
\begin{aligned}
& f=a_{0}+a_{1} x+a_{2} x^{2}+a_{3} x^{3}+a_{4} x^{4} \\
& f_{i}=a_{0} \\
& f_{i+1}=a_{0}+a_{1} \Delta x+a_{2} \Delta x^{2}+a_{3} \Delta x^{3}+a_{4} \Delta x^{4} \\
& f_{i-1}=a_{0}-a_{1} \Delta x+a_{2} \Delta x^{2}-a_{3} \Delta x^{3}+a_{4} \Delta x^{4}
\end{aligned}
$$

we don't have more points, but "what if we knew $\frac{d f}{d x}$ at $i+1$ and $l-1$ ?"

$$
\begin{aligned}
& f_{i+1}^{\prime}=a_{1}+2 a_{2} \Delta x+3 a_{3} \Delta x^{2}+4 a_{4} \Delta x^{3} \\
& f_{i-1}^{\prime}=a_{1}-2 a_{2} \Delta x+3 a_{3} \Delta x^{2}-4 a_{4} \Delta x^{3}
\end{aligned}
$$

Now, for $4^{\text {th }}$ order accuracy, we have 5 eqn with 3 points only, so, 5 constants $\left(a_{0}, a_{1} \ldots a_{4}\right)$ and 5 eqn. Solve them.

$$
\frac{d f}{d x} \text { at } i=f_{i}^{\prime}=-\frac{1}{4} f_{i+1}^{\prime}-\frac{1}{4} f_{i-1}^{\prime}+\frac{3}{4}\left(\frac{f_{i+1}-f_{i-1}}{\Delta x}\right)
$$

$f_{i+1}^{l}$ and $f_{i-1}^{\prime}$ can be computed from previous timestep or implicitly

## ASSIGNMENT 1

(1) Find the nature of PDE

- 15 marks
(1) $\left(1-M_{\infty}\right)^{2} \frac{\partial^{2} \phi}{\partial x^{2}}+\frac{\partial^{2} \phi}{\partial y^{2}}=0$ for $M_{\infty}=1, M_{\infty}<1, M_{\infty}>1$
(2) For the coupled eqns. $\frac{\partial u}{\partial x}=\frac{\partial v}{\partial y}$ and $\frac{\partial y}{\partial y}=v$
(3) $\frac{\partial T}{\partial t}+u_{\infty} \frac{\partial T}{\partial x}=S, T=T(x, t)$
(2) (1) $T(x, y)=A \sin (k \pi x) \sin (k \pi x) \rightarrow$ Analytical solution Use $A=1, k=2,4,8$
solve steady state heat conduction on shown geometry and B.CS
$L_{x}=L_{y}=1$, Temperature at all boundary $=0, n_{x}=n_{y}=33$
(RMSE)
→ Find Root mean square error for each $k$ ?
→ what is happening to RMSE with changing $k$ ?
→ How can you improve the accuracy if for any of the $k$, you are getting high error?
(2) Given a 2D composite square of $L_{x}=L_{y}=1$ and shown b.c, solve the heat conduction eqn $\left(\nabla^{2} T=0\right) q^{\prime \prime}=0$


![[Pasted image 20260209125615.png|500]]


**Figure 7:**

Case I $\Rightarrow K_{1}=210 \mathrm{~W} / \mathrm{mK}$
$k_{2}=200 \omega / m k$
$k_{3}=190 \omega / m k$
case II
$k_{1}=190 \mathrm{w} / \mathrm{mK}$
$\mathrm{K}_{2} 200 \mathrm{w} / \mathrm{mK}$
$k_{3}=210 \mathrm{w} / \mathrm{mk}$

→ What thermal conductivity you have used at interfaces
→ Use 3 grids for case $I, 31 \times 31,61 \times 61,121 \times 121$ Find order of accuracy using Richardson Extrapolation
→ Use $61 \times 61$ for case II
→ Explain the results in I and II ( $61 \times 61$ )
→ What is the $O(\Delta x)$ near the boundaries, which discretization scheme are you using for B.C.
(3) Develop SOR and RB-SOR solver and Find optimum $\omega$ (omega) for $65 \times 65$ grid in the following case

$$
L x=L y=0
$$

Ale boundaries, $T=0$

$$
S=1 e 7,1 e 8,1 e 9 \omega / \mathrm{m}^{3}
$$

→ Explain your results


![[Pasted image 20260209125632.png|500]]


**Figure 8:**


(3) Ansys
$L_{x}=L_{y}=1$
Hollow, square and cylinder

Temperature: Outside surface 300 K inside surface 400 K

Explain the differences in the strudlation.
Use grid spacing which you think is appropriate and mention that why you chose it

