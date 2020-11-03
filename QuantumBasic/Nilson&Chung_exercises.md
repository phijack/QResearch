$$
\newcommand{\Ket}[1]{\left| #1 \right\rangle}
\newcommand{\Bra}[1]{\left\langle #1 \right|}
$$



## Chapter 2

**Exercise 2.24** Show that a positive operator is necessarily Hermitian.

Solution: Notice that for any operator $A$, we have $B = \frac{A+A^{\dagger}}{2}$ and $C = -i\frac{A-A^{\dagger}}{2}$, both of which are Hermitian, and $A = B+iC$. By definition of positive operator, we should look at $\Bra v A \Ket v$ for any vector $\Ket v$. So we can have $\Bra v A \Ket v = \Bra v B \Ket v + i\Bra v C\Ket v$. Because $B$ and $C$ are Hermitian, we have $(\Bra v B \Ket v)^* = (\Bra v B \Ket v)^{\dagger} = \Bra v B^{\dagger} \Ket v = \Bra v B \Ket v$, that is, $\Bra v B \Ket v$ is a real number. So is $\Bra v C \Ket v$. That means if $A$ is not Hermitian, $\Bra v A \Ket v$ will be a complex number with non-zero imaginary part for some $\Ket v$. So the only possible positive operator must be Hermitian.



## Chapter 4

**Exercise 4.4** Express the Hadamard gate $H$ as a product of $R_x$ and $R_z$ rotations and $e^{i\varphi}$ for some $\varphi$.

Solution: $H = e^{i\frac{\pi}{2}}R_z(\frac{\pi}{2})R_x(\frac{\pi}{2})R_z(\frac{\pi}{2})$. Basic thoughts are Hadamard gate is a change from z-axis to x-axis. $R_x(\theta)$ is a rotation with x-axis as the axis and $R_z(\theta)$ is a rotation with z-axis as the axis.

