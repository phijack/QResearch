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

**Postulate 2'** The time evolution of the state of a closed quantum system is described by *Schrodinger equation*,
$$
i\hbar\frac{d\Ket\psi}{dt}=H\Ket\psi
$$
$H$ is a fixed Hermition operator( unitary operator), called the *Hamiltonian* of the closed system.

---

Then we can list some important quantum gates:

1. **Pauli Metrices** : It contains four types of gates.

   $I = \begin{bmatrix}1\quad 0\\0\quad 1\end{bmatrix}$, $X = \begin{bmatrix}0\quad 1\\1\quad 0\end{bmatrix}$, $Y = \begin{bmatrix}0\quad -i\\i\quad 0\end{bmatrix}$,$Z = \begin{bmatrix}1\quad 0\\0\quad -1\end{bmatrix}$.

   Here you can notice that $X$ gate is similar to the classical $NOT$ gate.

2. **Hadamard Gate** : It transform $\Ket 0$ to $\Ket +$ and transform $\Ket1$ to $\Ket-$.

   $H=\frac{1}{\sqrt{2}} \begin{bmatrix}1\quad 1\\ 1\quad -1\end{bmatrix}$.

3. **Controlled-NOT**: This is a two-qubit gate, as all legal quantum gate must be unitary, so it must output two qubits
   $$
   \Ket {A,B} \rightarrow \Ket {A,B\oplus A}
   $$
   So, its matrix representation is:
   $$
   U_{CN}=\begin{bmatrix}1\quad0\quad0\quad0\\
   0\quad1\quad0\quad0\\
   0\quad0\quad0\quad1\\
   0\quad0\quad1\quad0
   \end{bmatrix}
   $$

4. **Swap gate**: This is gate which swaps the states of two qubits
   $$
   \Ket{A,B} \rightarrow \Ket{B,A}
   $$
   So, its matrix representation is:
   $$
   U_{Swap}=\begin{bmatrix}
   1\quad0\quad0\quad0\\
   0\quad0\quad1\quad0\\
   0\quad1\quad0\quad0\\
   0\quad0\quad0\quad1
   \end{bmatrix}
   $$

5. **Toffoli Gate**: This is a three-qubit gate, which is control-control-NOT gate
   $$
   \Ket{A,B,C} \rightarrow \Ket{A,B,C\oplus AB}
   $$
   So, its matrix representation is:
   $$
   U_T = \begin{bmatrix}
   1\quad0\quad0\quad0\quad0\quad0\quad0\quad0\\
   0\quad1\quad0\quad0\quad0\quad0\quad0\quad0\\
   0\quad0\quad1\quad0\quad0\quad0\quad0\quad0\\
   0\quad0\quad0\quad1\quad0\quad0\quad0\quad0\\
   0\quad0\quad0\quad0\quad1\quad0\quad0\quad0\\
   0\quad0\quad0\quad0\quad0\quad1\quad0\quad0\\
   0\quad0\quad0\quad0\quad0\quad0\quad0\quad1\\
   0\quad0\quad0\quad0\quad0\quad0\quad1\quad0\\
   \end{bmatrix}
   $$
   Here is thing that you can use Toffoli gate to implement a universal classical compute as when you set $C=1$ then this is equivalent to an $NAND$ gate for input $A$ and $B$. So it can simulate classical computing as all classical gate can be represented by $NAND$ gate. 



6. **Fredkin Gate**: This is a three-qubit gate which is controlled swap, means if $C=1$ then swap, if $C=0$, then do nothing.
   $$
   \Ket{A,B,C} \rightarrow \Ket{A\bar C+BC, AC+B\bar C, C}
   $$
   So, its matrix representation is:
   $$
   U_F = \begin{bmatrix}
   1\quad0\quad0\quad0\quad0\quad0\quad0\quad0\\
   0\quad1\quad0\quad0\quad0\quad0\quad0\quad0\\
   0\quad0\quad1\quad0\quad0\quad0\quad0\quad0\\
   0\quad0\quad0\quad1\quad0\quad0\quad0\quad0\\
   0\quad0\quad0\quad0\quad1\quad0\quad0\quad0\\
   0\quad0\quad0\quad0\quad0\quad0\quad1\quad0\\
   0\quad0\quad0\quad0\quad0\quad1\quad0\quad0\\
   0\quad0\quad0\quad0\quad0\quad0\quad0\quad1\\
   \end{bmatrix}
   $$
   

### 3. Measurement

**Postulate 3** Quantum measurements are described by a collection of $\{M_m\}$ of *measurement operators*. These are operators acting on the state space of the system being measured. The index $m$ refers to the measure result.

If the state of the quantum system is $\Ket \psi$ before measurement, then the probability of the result $m$ is
$$
p(m) = \Bra\psi M_{m}^{\dagger}M_m\Ket \psi
$$
And the state of the system after measurement is 
$$
\frac{M_m\Ket \psi}{\sqrt{\Bra\psi M_{m}^{\dagger}M_m\Ket \psi}}
$$
the measurement operator satisfy the *completeness equation*:
$$
\sum_m M_m^{\dagger}M_m =I.
$$
The completeness equation helps confirm that $\sum_m p(m) =1$.

### 4. Composite system

**Postulate 4** The state space of composite system is the tensor product of the state space of the component physical systems.

**Entanglement**, *Bell states*, *Bell pairs*, *EPR pairs*.
$$
00: \Ket \psi \rightarrow \frac{\Ket{00}+\Ket{11}}{\sqrt{2}}\\
01: \Ket \psi \rightarrow \frac{\Ket{00}-\Ket{11}}{\sqrt{2}}\\
10: \Ket \psi \rightarrow \frac{\Ket{01}+\Ket{10}}{\sqrt{2}}\\
11: \Ket \psi \rightarrow \frac{\Ket{01}-\Ket{10}}{\sqrt{2}}
$$
These also provide a coding which called superdense code. This means that Alice can use an entangled pair such that Alice can transmit two bits by sending one qubit.

### 5. Density operator

If 

# PCP Theorem and Its Quantum Edition

# Circuit and Quantum Circuit Lower Bounds

