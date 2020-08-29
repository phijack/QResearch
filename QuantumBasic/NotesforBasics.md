$$
\newcommand{\Ket}[1]{\left| #1 \right\rangle}
\newcommand{\Bra}[1]{\left\langle #1 \right|}
$$

# Basics of Quantum

## Quantum Mechanics

### 1. state space

**Postulate 1** Any isolated physical system is associated with a complex vector space with inner product(Hilbert Space), which is called state space. And the state of this system is described by a unit vector of this state space, i.e. its state vector.

Here we can get our states of a qubit $\Ket{0} = \begin{bmatrix}0\\1\end{bmatrix}$ , and $\Ket 1 = \begin{bmatrix}1\\0\end{bmatrix}$. This is an orthogonal base of the state space of a qubit. We can also find another orthogonal base, which are $\Ket + = \begin{bmatrix}\frac{1}{\sqrt{2}}\\\frac{1}{\sqrt{2}}\end{bmatrix}$ and $\Ket - = \begin{bmatrix}\frac{1}{\sqrt{2}}\\-\frac{1}{\sqrt{2}}\end{bmatrix}$. We usually use $\Ket \varphi$ to stand for the state of a common qubit, which is a linear combination of two base states, that is called superposition in quantum. it looks like $\Ket \varphi = \alpha \Ket0+\beta\Ket1$.

### 2. Evolution

**Postulate 2** The evolution of a closed quantum system is described by a *unitary transformation*.

This postulate talks about the quantum gate. It points out that a matrix represents a quantum gate if and only if this matrix is unitary.

*Unitary*: a matrix $U$ is called unitary if $UU^{\dagger} =I$.( $U^{\dagger}$ stands for the conjugate transpose, or say Hermition adjoint, of $U$).

> Why Unitary? Because unitary transformation can keep the length of the vector and we need all the state vector be a unit vector to be legal.

---

Then we can list some important quantum gates:

1. **Pauli Metrices** : It contains four types of gates.

   $I = \begin{bmatrix}1\quad 0\\0\quad 1\end{bmatrix}$, $X = \begin{bmatrix}0\quad 1\\1\quad 0\end{bmatrix}$, $Y = \begin{bmatrix}0\quad -i\\i\quad 0\end{bmatrix}$,$Z = \begin{bmatrix}1\quad 0\\0\quad -1\end{bmatrix}$.

   Here you can notice that $X$ gate is similar to the classical $NOT$ gate.

2. **Hadamard Gate** : It transform $\Ket 0$ to $\Ket +$ and transform $\Ket1$ to $\Ket-$.

   $H=\frac{1}{\sqrt{2}} \begin{bmatrix}1\quad 1\\ 1\quad -1\end{bmatrix}$.

3. 







# PCP Theorem and Its Quantum Edition

# Circuit and Quantum Circuit Lower Bounds

