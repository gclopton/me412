
Grady Clopton
ME 412


> [!Question]
> CW1: Find $f_i^{\prime \prime}$ using Taylor expansions at $i-1, i+1$


Assume a uniform grid with spacing $\Delta x$, and expand about $x_i$ 

$$
\begin{aligned}
& f_{i+1}=f_i+\Delta x f_i^{\prime}+\frac{\Delta x^2}{2!} f_i^{\prime \prime}+\frac{\Delta x^3}{3!} f_i^{\prime \prime \prime}+\frac{\Delta x^4}{4!} f_i^{(4)}+O\left(\Delta x^5\right) \\
& f_{i-1}=f_i-\Delta x f_i^{\prime}+\frac{\Delta x^2}{2!} f_i^{\prime \prime}-\frac{\Delta x^3}{3!} f_i^{\prime \prime \prime}+\frac{\Delta x^4}{4!} f_i^{(4)}+O\left(\Delta x^5\right)
\end{aligned}
$$


Add the two series

$$
\begin{aligned}
f_{i+1}+f_{i-1}= & \left(f_i+f_i\right)+\left(\Delta x f_i^{\prime}-\Delta x f_i^{\prime}\right)+\left(\frac{\Delta x^2}{2} f_i^{\prime \prime}+\frac{\Delta x^2}{2} f_i^{\prime \prime}\right)+\left(\frac{\Delta x^3}{6} f_i^{\prime \prime \prime}-\frac{\Delta x^3}{6} f_i^{\prime \prime \prime}\right) \\
& +\left(\frac{\Delta x^4}{24} f_i^{(4)}+\frac{\Delta x^4}{24} f_i^{(4)}\right)+O\left(\Delta x^5\right) \\
= & 2 f_i+\Delta x^2 f_i^{\prime \prime}+\frac{\Delta x^4}{12} f_i^{(4)}+O\left(\Delta x^5\right)
\end{aligned}
$$


Solve for $f_i^{\prime \prime}$ 

$$
\begin{aligned}
\Delta x^2 f_i^{\prime \prime} & =\left(f_{i+1}-2 f_i+f_{i-1}\right)-\frac{\Delta x^4}{12} f_i^{(4)}+O\left(\Delta x^5\right) \\
f_i^{\prime \prime} & =\frac{f_{i+1}-2 f_i+f_{i-1}}{\Delta x^2}-\frac{\Delta x^2}{12} f_i^{(4)}+O\left(\Delta x^3\right)
\end{aligned}
$$



Solve for $f_i^{\prime \prime}$ 

$$
\begin{aligned}
\Delta x^2 f_i^{\prime \prime} & =\left(f_{i+1}-2 f_i+f_{i-1}\right)-\frac{\Delta x^4}{12} f_i^{(4)}+O\left(\Delta x^5\right) \\
f_i^{\prime \prime} & =\frac{f_{i+1}-2 f_i+f_{i-1}}{\Delta x^2}-\frac{\Delta x^2}{12} f_i^{(4)}+O\left(\Delta x^3\right)
\end{aligned}
$$


So the centered 3-point second-derivative stencil is

$$
f_i^{\prime \prime} \approx \frac{f_{i+1}-2 f_i+f_{i-1}}{\Delta x^2}
$$

with truncation error $O\left(\Delta x^2\right)$.




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