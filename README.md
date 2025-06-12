# Turing-Patterns
Model from the following [article](https://royalsocietypublishing.org/doi/10.1098/rstb.1952.0012).

The _Strong Formulation_ of the problem:

$$\begin{cases}
\frac{\partial X}{\partial t}=a(X-h)+b(Y-k)+\mu \nabla^2 X \\\\
\frac{\partial Y}{\partial t}=c(X-h)+d(Y-k)+\nu \nabla^2 Y \qquad (1)\\
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
From [FEniCS](https://fenicsproject.org/) leveraging the ```GMRES``` algorithm and the ```ilu``` preconditioner $(2),(3)$ can be assembled and solved. The code can be found in ```/src```. The outcomes I got are in ```/media```, whereas one extract is:




https://github.com/96mat/Turing-Patterns/assets/66094732/c5b18860-a128-4f6c-bcc9-0ca398c55b08

in 2D what it looks like:

https://github.com/96mat/Turing-Patterns/assets/66094732/39c321db-0f0d-4dc3-a8b7-6b46a79cd793

## Possibility to extend to the non-linear case
Equations in weak form:

```math
\begin{align}
F= & +\int_{\Omega} \frac{u_1^{n+1}\cdot v_1}{dt}\thinspace d\Omega\\
& +\int_{\Omega} \frac{u_2^{n+1}\cdot v_2}{dt}\thinspace d\Omega\\
& +\int_{\Omega} \nabla u_1^{n+1} : \nabla v_1 \thinspace d\Omega\\
& +\int_{\Omega} \nabla u_2^{n+1} : \nabla v_2 \thinspace d\Omega\\
& -\bigg(\int_{\Omega} \frac{u_{n_1}^{n} \cdot v_1}{dt}+\int_{\Omega} \frac{u_{n_2}^{n}\cdot v_2}{dt}\bigg) \thinspace d\Omega\\
& -\int_{\Omega} (u_1^{n}_{n_1}-\alpha u_2^n_{n_2} +\gamma u_1^n_{n_1}u_2^n_{n_2}-u_1^3_{n_1}) \cdot v_1 + (u_1^{n}_{n_1}-\beta u_2^{n}_{n_2}) \cdot v_2)\thinspace d\Omega =0\\
& + \text{Pure Neuman BC}
\end{align}
```




