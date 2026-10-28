

# OUTLINE
* General procedure to derive stencils
* Non-Uniform Grids
* FD discretization in $2 D$ space


# RECALL
* FDM - Taylor's series
* Truncation Error
- Nabure of enror
- order of accuracy
* Transient I-D heat conduction - Explicit scheme
* Assembly and solution of system of FD algebraic Equation.



# General procedure to derive stencil for a given derivative
- Taylor's series expansion:

$$
\begin{aligned}
& f_{i+1}=f_i+\Delta x f_i^{\prime}+\frac{\Delta x^2}{2!} f_i^{\prime \prime}+\frac{\Delta x^3}{3!} f_i^{\prime \prime \prime}+\frac{\Delta x^4}{4!} f_i^{\prime \prime}+\cdots \\
& f_{i-1}=f_i-\Delta x f_i^{\prime}+\frac{\Delta x^2}{2!} f_i^{\prime \prime}-\frac{\Delta x^3}{3!} f_i^{\prime \prime \prime}+\frac{\Delta x^4}{4!} f_i^{\prime \prime}+\cdots
\end{aligned}
$$

- To derive a stencil for a given derivative, it is necessary to manipulate these expressions such that coefficients of other derivatives become zero. or can be neglected
- Multiply eqn (1) by $a$ and eqn (2) by $b$ and add them.

$$
\begin{aligned}
& a f_{i+1}=a f_i+a \Delta x f_i^{\prime}+\frac{a \Delta x^2}{2!} f^{\prime \prime} i+\frac{a \Delta x^3}{3!} f_i^{\prime \prime \prime}+\cdots \\
& b f_{i-1}=b f_i-b \Delta x f_i^{\prime}+b \frac{\Delta x^2}{2!} f^{\prime \prime} i-b \frac{\Delta x^3}{3!} f^{\prime \prime \prime} i+\cdots
\end{aligned}
$$


Add:

$$
a f_{i+1}-(a+b) f_i+b f_{i-1}=(a-b) \Delta x f_i^{\prime}+(a+b) \frac{\Delta x^2}{2!} f_i^{\prime \prime}+(a-b) \frac{\Delta \Delta^3}{3!} f_i^{\prime \prime \prime}+\cdots
$$

- Let's say we want to find $f_i^{\prime}$ using $P+1$ and $i-1$



$$
\begin{aligned}
& \therefore \quad(a-b) \Delta x=1 \\
& \text { and, } \quad(a+b) \frac{\Delta x^2}{2}=0 \\
& \Rightarrow \quad a=-b \text { and } a=\frac{1}{\Delta x}+b \\
& \text { or, } a=\frac{1}{\Delta x}-a \\
& \text { or, } 2 a=\frac{1}{\Delta x} \\
& \text { or } a=\frac{1}{2 \Delta x} \\
& b=-\frac{1}{2 \Delta x}
\end{aligned}
$$


Plug $a$ and $b$ in $e q^n$ (3)

$$
\begin{aligned}
\frac{1}{2 \Delta x} f_{i+1}-0 \cdot f_i & -\frac{1}{2 \Delta x} f_{i-1}=\left(\frac{1}{2 \Delta x}+\frac{1}{2 \Delta x}\right) \Delta x f_i^{\prime}+0 f_i^{\prime \prime}+\left(\frac{1}{2 \Delta x}+\frac{1}{2 \Delta x}\right) \frac{\Delta x^2}{3!} f_i^{\prime} \\
\text { or } f_i^{\prime} & =\frac{f_{i+1}-f_{i-1}}{2 \Delta x}+o\left(\Delta x^2\right)
\end{aligned}
$$

- Conversely, if we are interested in $f^{\prime \prime} i$ cw1 Find $f^{\prime \prime}{ }_t$ using general procedure and Taylor's series expansion at it, in



- Let's focus on 1st order derivatives: $\frac{d f}{d x}$
$f_i^{\prime}=\frac{f_{i+1}-f_i}{\Delta x}, F D S-O(\Delta x), 2 p t$ stencil, dissipative $\operatorname{error}\left(f_i^{\prime \prime}\right)$
$f_i^{\prime}=\frac{f_i-f_{i-1}}{\Delta x}, B D S-O(\Delta x), 2 p t$ stencil, dissipative error $\left(f_i^{\prime \prime}\right)$
$f_i^{\prime}=\frac{f_{i+1}-f_{i-1}}{2 \Delta x}, C D S-O\left(\Delta x^2\right), 3 p t$ stencil, dispersive error $\left(f^{\prime \prime \prime}\right)$


![[Figure 1.png]]

- $\frac{d t}{d x}$ is similar to derivative in advection term of the transport eqn.
* CDS is not suited for discretizing advected term
* However, Using $1^{\text {st }}$ order scheme reduces accuracy and we add false diffusion to N.S equation as the truncation error has $2^{\text {nd }}$ order derivative as the leading term.
* We can improve global accuracy by Increasing no. of grid points (mesh refinement) but it increases the computational cost.
- So, to improve accuracy and remove false diffusion what showd be done?
$\Rightarrow 3$ point FDS or BDS based on the flow direction.
i.e. $\quad u>0, \longrightarrow$, BDS
$u<0, \leftarrow, F D S$


# 3 point FDS : $l, l+1, l+2$ for $f_i^{\prime}$


$$
\begin{aligned}
& f_{i+1}=f_i+\Delta x f_i^{\prime}+\frac{\Delta x^2}{2!} f_i^{\prime \prime}+\frac{\Delta x^3}{3!} f_i^{\prime \prime \prime}+\frac{\Delta x^4}{4!} f_i^{\prime \prime}+\cdots \\
& f_{i+2}=f_i+2 \Delta x f_i^{\prime}+\frac{(2 \Delta x)^2}{2!} f_i^{\prime \prime}+\frac{(2 \Delta x)^3}{2!}+\frac{(2 \Delta x)^4}{4!} f_i^{\prime \prime}+\cdots
\end{aligned}
$$



Multiply eqn (4) by $a$ and eqn (5) by $b$ and add the equations.

[The equations are formatted as gathered. remove this formatting. They should not be displayed gathered.]
$$
\begin{gathered}
a f_{i+1}=a f_i^{\circ}+a \Delta x f_i^{\prime \circ}+\frac{a \Delta x^2}{2!} f_i^{\prime \prime \circ}+\frac{a \Delta x^3}{3!} f_i^{\prime \prime \prime \circ}+\frac{a \Delta x^4}{4!} f_i^{\mathrm{i} \circ}+\cdots \\
b f_{i+2}=b f_i^{\circ}+b(2 \Delta x) f_i^{\prime \circ}+\frac{b(2 \Delta x)^2}{2!} f_i^{\prime \prime \circ}+\frac{b(2 \Delta x)^3}{3!} f_i^{\prime \prime \prime \circ}+\frac{b(2 \Delta x)^4}{4!} f_i^{\mathrm{iv} \circ}+\cdots \\
a f_{i+1}-(a+b) f_i^{\circ}+b f_{i+2}=(a+2 b) \Delta x f_i^{\prime \circ}+\frac{(a+4 b) \Delta x^2}{2!} f_i^{\prime \prime \circ}+\frac{(a+8 b) \Delta x^3}{3!} f_i^{\prime \prime \prime \circ}+\cdots \\
\therefore(a+2 b) \Delta x=1 \quad \text { and } \quad(a+4 b) \frac{\Delta x^2}{2!}=0 \\
a=-4 b \quad \text { and } \quad a=\frac{1}{\Delta x}-2 b \\
b=-\frac{1}{2 \Delta x}, \quad a=\frac{2}{\Delta x}
\end{gathered}
$$

$$
\begin{gathered}
\therefore \frac{2}{\Delta x} f_{i+1}-\left(\frac{2}{\Delta x}-\frac{1}{2 \Delta x}\right) f_i^{\circ}-\frac{1}{2 \Delta x} f_{i+2}=\left[\frac{2}{\Delta x}+2\left(-\frac{1}{2 \Delta x}\right)\right] \Delta x f_i^{\prime \circ}+\left[\frac{2}{\Delta x}+8\left(-\frac{1}{2 \Delta x}\right)\right] \frac{\Delta x^3}{3!} f_i^{\prime \prime \prime \circ}+\cdots \\
\therefore \frac{2}{\Delta x} f_{i+1}-\left(\frac{4-1}{2 \Delta x}\right) f_i^{\circ}-\frac{1}{2 \Delta x} f_{i+2}=\left[\frac{1}{\Delta x}\right] \Delta x f_i^{\prime \circ}+\left[\frac{4+8}{2 \Delta x}\right] \frac{\Delta x^3}{3!} f_i^{\prime \prime \prime \circ} \\
\frac{2}{\Delta x} f_{i+1}-\frac{3}{2 \Delta x} f_i^{\circ}-\frac{1}{2 \Delta x} f_{i+2}=f_i^{\prime \circ}+\frac{6 \Delta x^2}{3!} f_i^{\prime \prime \prime \circ}+\cdots \\
f_i^{\prime \circ}=\frac{4 f_{i+1}-3 f_i^{\circ}-f_{i+2}}{2 \Delta x}+\alpha\left(\Delta x^2\right) f_i^{\prime \prime \prime \circ}
\end{gathered}
$$

or,

$$
f_i^{\prime \circ}=\frac{-3 f_i^{\circ}+4 f_{i+1}-f_{i+2}}{2 \Delta x}+O\left(\Delta x^2\right) f_i^{\prime \prime \prime \circ} \rightarrow \text { dispersive error }
$$


↓ order of accuracy



> [!Question]
> CW2: Derive the 3-point backward-difference stencil for $f_i^{\prime}$ using $i, i-1, i-2$


Taylor expand $f_{i-1}$ and $f_{i-2}$ about $x_i$ 

$$
\begin{aligned}
f_{i-1} & =f_i-\Delta x f_i^{\prime}+\frac{\Delta x^2}{2} f_i^{\prime \prime}-\frac{\Delta x^3}{6} f_i^{\prime \prime \prime}+\frac{\Delta x^4}{24} f_i^{(4)}+O\left(\Delta x^5\right) \\
f_{i-2} & =f_i-2 \Delta x f_i^{\prime}+\frac{(2 \Delta x)^2}{2} f_i^{\prime \prime}-\frac{(2 \Delta x)^3}{6} f_i^{\prime \prime \prime}+\frac{(2 \Delta x)^4}{24} f_i^{(4)}+O\left(\Delta x^5\right) \\
& =f_i-2 \Delta x f_i^{\prime}+2 \Delta x^2 f_i^{\prime \prime}-\frac{4}{3} \Delta x^3 f_i^{\prime \prime \prime}+\frac{2}{3} \Delta x^4 f_i^{(4)}+O\left(\Delta x^5\right)
\end{aligned}
$$


Seek coefficients $A, B, C$ such that

$$
A f_i+B f_{i-1}+C f_{i-2}=\Delta x f_i^{\prime}+O\left(\Delta x^3\right)
$$


Substitute the expansions

$$
\begin{aligned}
A f_i+B f_{i-1}+C f_{i-2} & =A f_i+B\left(f_i-\Delta x f_i^{\prime}+\frac{\Delta x^2}{2} f_i^{\prime \prime}-\frac{\Delta x^3}{6} f_i^{\prime \prime \prime}+\cdots\right)+C\left(f_i-2 \Delta x f_i^{\prime}+2 \Delta x^2 f_i^{\prime \prime}-\frac{4}{3} \Delta x^3 f_i^{\prime \prime \prime}+\cdots\right) \\
& =(A+B+C) f_i+(-B-2 C) \Delta x f_i^{\prime}+\left(\frac{B}{2}+2 C\right) \Delta x^2 f_i^{\prime \prime}+\left(-\frac{B}{6}-\frac{4}{3} C\right) \Delta x^3 f_i^{\prime \prime \prime}+\cdots
\end{aligned}
$$


Match coefficients to enforce: (i) no constant term, (ii) the $\Delta x f_i^{\prime}$ coefficient equals 1 , (iii) cancel the $\Delta x^2 f_i^{\prime \prime}$ term

$$
\begin{aligned}
A+B+C & =0 \\
-(B+2 C) & =1 \\
\frac{B}{2}+2 C & =0
\end{aligned}
$$


Solve

$$
\begin{aligned}
\frac{B}{2}+2 C & =0 \Longrightarrow B=-4 C, \\
-(B+2 C) & =1 \Longrightarrow-(-4 C+2 C)=1 \Longrightarrow 2 C=1 \Longrightarrow C=\frac{1}{2}, \\
B & =-4\left(\frac{1}{2}\right)=-2, \\
A+B+C & =0 \Longrightarrow A=-(B+C)=-\left(-2+\frac{1}{2}\right)=\frac{3}{2}
\end{aligned}
$$


Thus

$$
\begin{aligned}
\Delta x f_i^{\prime} & =\frac{3}{2} f_i-2 f_{i-1}+\frac{1}{2} f_{i-2}+O\left(\Delta x^3\right) \\
f_i^{\prime} & =\frac{\frac{3}{2} f_i-2 f_{i-1}+\frac{1}{2} f_{i-2}}{\Delta x}+O\left(\Delta x^2\right) \\
& =\frac{3 f_i-4 f_{i-1}+f_{i-2}}{2 \Delta x}+O\left(\Delta x^2\right)
\end{aligned}
$$

So the 3-point backward stencil is

$$
f_i^{\prime} \approx \frac{3 f_i-4 f_{i-1}+f_{i-2}}{2 \Delta x}
$$

with truncation error $O\left(\Delta x^2\right)$.


---


# General procedure to approximate a derivative with n -stencil points
Step 1: Decide no. of grid points to be included in the stencil
Step 2: Write Taylor's series for the values at these grid points in terms of the derivative at the desired location

Step 3: Multiply each terms in step-2 with constants $(a, b, c \ldots)$ and add them. → multipliers
Step 4: Solve the set of simultaneous eqn's to obtain the multipliers
Step 5: Substitute the multipliers in step3 and simplify the equation to obtain the required derivative
Step 6: Verify that coefficient of other leading derivative is zero
Step 7: Evaluate the truncation error and nature of error



# Some other Stencils
- $f_i^{\prime \prime}$ using five point stencil CDS $\quad i-2, i-1, i^{\circ}, i+1, i+2$

$$
f_i^{\prime \prime}=\frac{f_{i+2}+16 f_{i+1}-30 f_i+16 f_{i-1}+f_{i-2}}{12 \Delta x^2}+O\left(\Delta x^4\right)
$$

- $f_i^{\prime \prime}$ using four point stencil , BDS $, \quad i-3, i-2, i-1, i$

$$
f_i^{\prime \prime}=\frac{2 f_i-5 f_{i-1}+4 f_{i-2}-f_{i-3}}{\Delta x^2}+O\left(\Delta x^2\right)
$$



# Non-UniformGrids
- To increase granularity near the boundaries or in the region where gradients are high, non-uniform grids are employed.
- i.e. grid spacing is no more constant
- Consider a 3pt stencil


Consider the stencil shown below. $\Delta x_{+} \neq \Delta x_{-}, \quad$ Assume $\frac{\Delta x_{+}}{\Delta x_{-}}=\alpha$

![[Figure 2.png|500]]


- Taylor series expansion:

$$
\begin{aligned}
& f_{i+1}=f_i^{\circ}+\Delta x_{+} f_i^{\prime \circ}+\frac{\left(\Delta x_{+}\right)^2}{2!} f_i^{\prime \prime \circ}+\frac{\left(\Delta x_{+}\right)^3}{3!} f_i^{\prime \prime \prime \circ}+\frac{\left(\Delta x_{+}\right)^4}{4!} f_i^{\mathrm{iv} \mathrm{\circ}} \\
& f_{i-1}=f_i^{\circ}-\Delta x_{-} f_i^{\prime \circ}+\frac{\left(\Delta x_{-}\right)^2}{2!} f_i^{\prime \prime \circ}-\frac{\left(\Delta x_{-}\right)^3}{3!} f_i^{\prime \prime \prime \circ}+\frac{\left(\Delta x_{-}\right)^4}{4!} f_i^{\mathrm{iv} \mathrm{\circ}}
\end{aligned}
$$


Let's estimate $f_i^{\prime \circ}$, subtracting eqn (7) from (6)

$$
\begin{gathered}
f_{i+1}-f_{i-1}=0+\left(\Delta x_{+}+\Delta x_{-}\right) f_i^{\prime \circ}+\frac{\Delta x_{+}^2-\Delta x_{-}^2}{2!} f_i^{\prime \prime \circ}+\frac{\Delta x_{+}^3+\Delta x_{-}^3}{3!} f_i^{\prime \prime \prime \circ}+\cdots \\
f_i^{\prime \circ}=\frac{f_{i+1}-f_{i-1}}{\Delta x_{+}+\Delta x_{-}}+\frac{\left(\Delta x_{+}+\Delta x_{-}\right)\left(\Delta x_{+}-\Delta x_{-}\right)}{2!\left(\Delta x_{+}+\Delta x_{-}\right)} f_i^{\prime \prime \circ}+\frac{\Delta x_{+}^3+\Delta x_{-}^3}{3!\left(\Delta x_{+}+\Delta x_{-}\right)} f_i^{\prime \prime \prime \circ}+\cdots \\
=\frac{f_{i+1}-f_{i-1}}{\Delta x_{+}+\Delta x_{-}}+\frac{\Delta x_{+}-\Delta x_{-}}{2} f_i^{\prime \prime \circ}+\cdots \\
=\frac{f_{i+1}-f_{i-1}}{\Delta x_{+}+\Delta x_{-}}+\frac{\Delta x_{-}}{2}\left(\frac{\Delta x_{+}}{\Delta x_{-}}-1\right) f_i^{\prime \prime \circ}+\cdots
\end{gathered}
$$

order of accuracy : $1\left[\Delta x_{-}(\alpha-1)\right]$
nature of error : Dispersive



Follow general procedure to approximate $f_i^{\prime \circ}$

$$
\begin{gathered}
a f_{i+1}=a f_i^{\circ}+a\left(\Delta x_{+}\right) f_i^{\prime \circ}+\frac{a\left(\Delta x_{+}\right)^2}{2!} f_i^{\prime \prime \circ}+\frac{a\left(\Delta x_{+}\right)^3}{3!} f_i^{\prime \prime \prime \circ}+\cdots \\
b f_{i-1}=b f_i^{\circ}-b\left(\Delta x_{-}\right) f_i^{\prime \circ}+\frac{b\left(\Delta x_{-}\right)^2}{2!} f_i^{\prime \prime \circ}-\frac{b\left(\Delta x_{-}\right)^3}{3!} f_i^{\prime \prime \prime \circ}+\cdots \\
a f_{i+1}-(a+b) f_i^{\circ}+b f_{i-1}=\left(a \Delta x_{+}-b \Delta x_{-}\right) f_i^{\prime \circ}+\frac{1}{2}\left(a \Delta x_{+}^2+b \Delta x_{-}^2\right) f_i^{\prime \prime \circ}+\cdots \\
\therefore a \Delta x_{+}-b \Delta x_{-}=1 \Rightarrow a \alpha-b=\frac{1}{\Delta x_{-}} \\
\frac{1}{2}\left(a \Delta x_{+}^2+b \Delta x_{-}^2\right)=0 \Rightarrow a \alpha^2+b=0
\end{gathered}
$$

solving these,

$$
\begin{gathered}
b=-a \alpha^2, \quad a=\frac{1}{\alpha(1+\alpha) \Delta x_{-}} \\
\frac{1}{\alpha(1+\alpha) \Delta x_{-}} f_{i+1}-\left(\frac{1}{\alpha(1+\alpha) \Delta x_{-}}-\frac{\alpha^2}{\alpha(1+\alpha) \Delta x_{-}}\right) f_i^{\circ}-\frac{\alpha^2}{\alpha(1+\alpha) \Delta x_{-}} f_{i-1}=f_i^{\prime \circ}+\frac{1}{2}\left[\frac{\Delta x_{+}^2}{\alpha(1+\alpha) \Delta x_{-}}-\frac{\alpha \Delta x_{-}^2}{\alpha(1+\alpha) \Delta x_{-}}\right] f_i^{\prime \prime \circ}+\cdots \\
f_i^{\prime \circ}=\frac{f_{i+1}-\left(1-\alpha^2\right) f_i^{\circ}-\alpha^2 f_{i-1}}{\alpha(1+\alpha) \Delta x_{-}}+O\left(\Delta x^2\right)
\end{gathered}
$$