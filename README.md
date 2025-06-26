# Turing-Patterns
Model from the following [article](https://royalsocietypublishing.org/doi/10.1098/rstb.1952.0012).

The _Strong Formulation_ of the problem:

$$\begin{cases}
\frac{\partial X}{\partial t}=a(X-h)+b(Y-k)+\mu \nabla^2 X \\\\
\frac{\partial Y}{\partial t}=c(X-h)+d(Y-k)+\nu \nabla^2 Y \qquad (1)\\
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


$\blacktriangleright$ https://github.com/96mat/Turing-Patterns/media/3D-Turing-linear-gmres.mp4


https://github.com/96mat/Turing-Patterns/assets/66094732/c5b18860-a128-4f6c-bcc9-0ca398c55b08

in 2D what it looks like:

https://github.com/96mat/Turing-Patterns/assets/66094732/39c321db-0f0d-4dc3-a8b7-6b46a79cd793

## Possibility to extend to the non-linear case
Schnakenberg’s nonlinear revision of the original Turing instability reads as follows

$$\begin{cases}
\frac{\partial u}{\partial t} -a(u-h) -b(v-k) -\mu \nabla^2 u  =u -\alpha v^2 +\gamma uv -u^3 \\\\
\frac{\partial v}{\partial t}-c(u-h)-d(v-k)-\nu \nabla^2 v  =u-\beta v\qquad (4)\\
+\text{Periodic BC}
\end{cases}$$

Equations in weak form:

```math
\begin{align}
F= & +\int_{\Omega} \frac{u_1^{n+1}}{dt}\cdot v_1\thinspace d\Omega\\
& +\int_{\Omega} \frac{u_2^{n+1}}{dt}\cdot v_2\thinspace d\Omega\\
& +\mu\int_{\Omega} \nabla u_1^{n+1} : \nabla v_1 \thinspace d\Omega\\
& +\nu\int_{\Omega} \nabla u_2^{n+1} : \nabla v_2 \thinspace d\Omega\\
& -a\int_{\Omega} \frac{u_{n_1}^{n} }{dt}\cdot v_1 \thinspace d\Omega -b\int_{\Omega} \frac{u_{n_2}^{n}}{dt}\cdot v_1 \thinspace d\Omega\\
& -c\int_{\Omega} \frac{u_{n_1}^{n}}{dt} \cdot v_2 \thinspace d\Omega -d\int_{\Omega} \frac{u_{n_2}^{n}}{dt}\cdot v_2 \thinspace d\Omega\\
& -\int_{\Omega} (u^{n}_{n_1}-\alpha u^n_{n_2} +\gamma u^n_{n_1}u^n_{n_2}-u^{3,n}_{n_1}) \cdot v_1 \thinspace d\Omega\\
& -\int_{\Omega}  (u^{n}_{n_1}-\beta u^{n}_{n_2}) \cdot v_2\thinspace d\Omega\\
& + \text{Periodic BC}
\end{align}
```

Solution of the nonlinear problem


https://github.com/user-attachments/assets/9b19874c-0895-48f0-be03-8f2c561ffe15


