# Turing-Patterns
The _Strong Formulation_ of the problem:

$$\begin{cases}
\frac{\partial X}{\partial t}=a(X-h)+b(Y-k)+\mu \nabla^2 X \\\\
\frac{\partial X}{\partial t}=c(X-h)+d(Y-k)+\nu \nabla^2 Y \qquad (1)\\
+\text{Pure NC}\\
+\text{Periodic BC}
\end{cases}$$

while its _weak formulation_ is:
```math
\begin{align}
\int_{\Omega} (X^{n+1}-X^n)v+\mu \Delta t \nabla X^{n+1}\nabla v- \Delta t(aX^{n+1}+bY^{n+1})v\thinspace d\Omega &=0 \qquad (2)\\
\int_{\Omega} (Y^{n+1}-Y^n)v+\nu \Delta t \nabla Y^{n+1}\nabla v- \Delta t(cX^{n+1}+dY^{n+1})v\thinspace d\Omega &=0 \qquad (3)
\end{align}
```
From [FEniCS](https://fenicsproject.org/) Leveragin the ```GMRES``` algorithm and the ```ilu``` preconditioner $(2),(3)$ can be assembled and solved. The outcome I got are in ```/media```, whereas one extract is:




https://github.com/96mat/Turing-Patterns/assets/66094732/c5b18860-a128-4f6c-bcc9-0ca398c55b08

