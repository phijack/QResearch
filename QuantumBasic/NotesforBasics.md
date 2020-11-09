$$
\newcommand{\Ket}[1]{\left| #1 \right\rangle}
\newcommand{\Bra}[1]{\left\langle #1 \right|}
$$

# Basics of Quantum

## Quantum Mechanics

### 1. state space

**Postulate 1** Any isolated physical system is associated with a complex vector space with inner product(Hilbert Space), which is called state space. And the state of this system is described by a unit vector of this state space, i.e. its state vector.

Here we can get our states of a qubit $\Ket{0} = \begin{bmatrix}0\\1\end{bmatrix}$ , and $\Ket 1 = \begin{bmatrix}1\\0\end{bmatrix}$. This is an orthogonal base of the state space of a qubit. We can also find another orthogonal base, which are $\Ket + = \begin{bmatrix}\frac{1}{\sqrt{2}}\\\frac{1}{\sqrt{2}}\end{bmatrix}$ and $\Ket - = \begin{bmatrix}\frac{1}{\sqrt{2}}\\-\frac{1}{\sqrt{2}}\end{bmatrix}$. We usually use $\Ket \varphi$ to stand for the state of a common qubit, which is a linear combination of two base states, that is called superposition in quantum. it looks like $\Ket \varphi = \alpha \Ket0+\beta\Ket1$.

**Inner Product**: is a function from $V \times V$ to $\mathbb{R}$, which satisfies the following three properties:

1. Linearity on the second component: $(\Ket v, \sum_i \lambda_i \Ket{w_i}) = \sum_i \lambda_i(\Ket v, \Ket{w_i})$.
2. $(\Ket v, \Ket w) = (\Ket w, \Ket v)^*$.
3. $\forall \Ket v,(\Ket v, \Ket v) \geq 0$. The equality holds if and only if $\Ket v$ is a zero element.

### 2. Evolution

**Postulate 2** The evolution of a closed quantum system is described by a *unitary transformation*.

This postulate talks about the quantum gate. It points out that a matrix represents a quantum gate if and only if this matrix is unitary.

*Unitary*: a matrix $U$ is called unitary if $UU^{\dagger} =I$.( $U^{\dagger}$ stands for the conjugate transpose, or say Hermition adjoint, of $U$).

> Why Unitary? Because unitary transformation can keep the length of the vector and we need all the state vector be a unit vector to be legal.

**Postulate 2'** The time evolution of the state of a closed quantum system is described by *Schrodinger equation*,
$$
i\hbar\frac{d\Ket\psi}{dt}=H\Ket\psi
$$
$H$ is a fixed Hermition operator, called the *Hamiltonian* of the closed system.

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

We can use a way to represent the state $\rho$. $p_i$ stands for the probability of $\Ket{\psi_i}$ result. That is called the *ensemble of pure states*.
$$
\rho = \sum_i p_i\Ket{\psi_i}\Bra{\psi_i}
$$

So we can know that all states can be represented as a Hermitian matrix with its trace is $1$, and all $2\times 2$ Hermitian matrix can be represented by the linear combination of Pauli matrices. So we have $\rho = \frac{I+\vec{r}\cdot \vec{\sigma}}{2}$, for any $\rho$. That means we can use a vector in 3-dimension space $\vec{r}$ represent the state $\rho$.This method is called the Bloch Ball, any pure state will be on the sphere of this ball.

**Unitary freedom in the ensemble for density matrices** 

The sets $\Ket{\psi_i}$ and $\Ket{\varphi_j}$ generate the same density matrix if and only if $\Ket{\psi_i} = \sum_j U_{ij} \Ket{\varphi_j}$. Here $U_{ij}$ is the entry of a unitary matrix $U$, with indices $i$ and $j$.(Does that means the density matrix will not change in the closed quantum system? No, this is right multiplication of $U$, while the change in close system is left multiplication.)

###6. Schmidt decomposition and purification

#####Schmidt decomposition

Suppose $\Ket{\psi}$ is a pure state of a composite system, $AB$. Then there exist orthonormal states $\Ket{i_A}$ for system $A$, and orthonormal states $\Ket{i_B}$ for system $B$ such that 
$$
\Ket{\psi} = \sum_i \lambda_i \Ket{i_A}\Ket{i_B}
$$
where $\lambda_i$ are non-negative real numbers satisfying $\sum_i\lambda_i^2 = 1$ known as *Schmidt co-efficients*.

It is a different name of Singular Value Decomposition.

So the $\lambda_i$ or say Schmidt Number quantifies the entanglement of A and B, because they are invariant under unitary transformation.

#####purification

Suppose we have a state $\rho^A$ of a quantum system $A$, it is possible to introduce a system $R$, and define a pure state $\Ket{AR}$ for the joint system $AR$ such that $\rho^A = tr_R(\Ket{AR}\Bra{AR})$, here $R$ is called the reference system, which is a fictitious system.

In order to get this system $R$, we can directly use the same state space as system $A$ with orthogonal basis states $\Ket{i^R}$ and define
$$
\Ket{AR} \equiv \sum_i \sqrt{p_i} \Ket{i^A}\Ket{i^R}.
$$

### 7. Bell's Inequality



## Quantum Circuit

### 1. Single qubit circuit

Important gates are Pauli matrices, Hadamard gate, phase gate(S) and $\frac{\pi}{8}$ gate(T)

An important class of gates is called *rotation operators*:
$$
R_x(\theta) \equiv e^{-i\theta X/2} = \cos \frac{\theta}{2}I - i\sin \frac{\theta}{2}X\\
R_y(\theta) \equiv e^{-i\theta Y/2} = \cos \frac{\theta}{2}I - i\sin \frac{\theta}{2}Y\\
R_z(\theta) \equiv e^{-i\theta Z/2} = \cos \frac{\theta}{2}I - i\sin \frac{\theta}{2}Z\\
R_{\hat{n}}(\theta) \equiv \exp (-i\theta \hat{n}\cdot \vec{\sigma}/2) = \cos(\frac{\theta}{2})I - i\sin(\frac{\theta}{2})(n_xX+n_yY+n_zZ)
$$
The $\vec{\sigma}$ denotes the three component vector $(X,Y,Z)$ of Pauli matrices in the last line.

**Z-Y decomposition for a single qubit** Suppose $U$ is a unitary operation on a single qubit. Then there exist real numbers $\alpha, \beta, \gamma$ and $\delta$ such that
$$
U = e^{i\alpha}R_z(\beta)R_y(\gamma)R_z(\delta)
$$
 Corollary: Suppose 

### 3. Universal quantum gate



## Quantum Fourier transform and its application 

### 1. Definition

$$
\Ket j \longrightarrow \frac{1}{\sqrt{N}}\sum_{k=0}^{N-1} e^{i2\pi jk/N}\Ket k
$$



The quantum Fourier transform is unitary $FT$. $FT_{jk} = \frac{1}{\sqrt{N}} e^{i2\pi jk/N}$.



So the action on an arbitrary state may be written
$$
\sum_{j=0}^{N-1}x_j\Ket j \longrightarrow \sum_{k=0}^{N-1}y_k\Ket k
$$


And there is another representation of this transformation(Here we set $N=2^n$):
$$
\begin{align*}
\Ket j &\rightarrow \frac{1}{2^{n/2}}\sum_{k=0}^{2^n-1}e^{i2\pi jk/2^n}\Ket k\\
&= \frac{1}{2^{n/2}}\sum_{k_1=0}^{1} \cdots \sum_{k_n=0}^{1}e^{i2\pi j(\sum_{l=1}^n k_l2^{-l})}\Ket{k_1\cdots k_n}\\
&= \frac{1}{2^{n/2}}\sum_{k_1=0}^{1} \cdots \sum_{k_n=0}^{1}\bigotimes_{l=1}^{n} e^{i2\pi jk_l2^{-l}}\Ket{k_l}\\
&= \frac{1}{2^{n/2}}\bigotimes_{l=1}^{n}\left[\sum_{k_l=0}^{1} e^{i2\pi jk_l2^{-l}}\Ket{k_l}\right]\\
&= \frac{1}{2^{n/2}}\bigotimes_{l=1}^{n}\left[\Ket 0 + e^{i2\pi j2^{-l}}\Ket 1\right]\\
&= \frac{(\Ket 0 + e^{i2\pi 0.j_n}\Ket 1)(\Ket 0 + e^{i2\pi 0.j_{n-1}j_n}\Ket 1)\cdots (\Ket 0 + e^{i2\pi 0.j_1j_2\cdots j_n}\Ket 1)}{2^{n/2}}
\end{align*}
$$
Here $j = j_12^{n-1}+j_22^{n-2}+\cdots +j_n$ and $0.j_lj_{l+1}\cdots j_m = j_l/2+j_{l+1}/4+ \cdots +j_m/2^{m-l+1}$.



Because of this representation, we can use Hadamard gate and gate $R_k$s to implement quantum Fourier transformation efficiently. Here $R_k$ is
$$
\begin{bmatrix}
1\quad\quad0\\
0\quad e^{i2\pi/2^k}
\end{bmatrix}
$$
<img src="/Users/jack_wang/Desktop/Screenshot 2020-11-07 at 7.27.17 PM.png" alt="Screenshot 2020-11-07 at 7.27.17 PM" style="zoom:60%;" />

That shows we can implement quantum Fourier transformation in $O(n^2)$ quantum circuits, however the most efficient classical Fourier transformation can be implement in $O(n2^n)$.

### 2. Phase estimation

This is the first application of quantum Fourier transformation. 

The problem of phase estimation is:

Suppose a unitary operator $U$ has an eigenvector $\Ket u$ with an eigenvalue $e^{i2\pi \varphi}$, and we want to estimate the unknown $\varphi$. 

The procedure of this algorithm is: 

It uses two registers. First one has $t$ qubits which are $t$ $\Ket 0$s and use Hadamard gates on each wire, and use $j_{th}$ wire as the control wire to put a $controlled-U^{2^j}$ on the second register.

Then the result is 
$$
\frac{1}{2^{t/2}}\sum_{j=0}^{2^t-1}e^{i2\pi \varphi j}\Ket j\Ket u
$$
Then we can put an inverse of quantum Fourier transform on the first register
$$
\frac{1}{2^{t/2}}\sum_{j=0}^{2^t-1}e^{i2\pi \varphi j}\Ket j\Ket u \longrightarrow \Ket{\tilde{\varphi}}\Ket u
$$
Then we can measure the first register to get a good estimation of $\varphi$.

Here we can estimate the accuracy and success probability, thus to successfully get $\varphi$ accurate to $n$ bits with probability of success at least $1-\epsilon$ we can just choose $t = n+\lceil \log (2+\frac{1}{2\epsilon})\rceil$.

### 3. Order-finding and Factoring

It shows that we can use phase estimation to compute the order with a high-probability. Basically, this is a type of problems which are called *Hidden Subgroup Problems on Abelian Group*. For that kind of problems there are efficient quantum algorithms based on the algorithm for phase estimate problem.

## Grover's Searching Algorithm

### 1. Searching Problem Preliminaries

Here we use a quantum oracle $\Ket x \Ket q \xrightarrow{O} \Ket x \Ket{q\oplus f(x)}$ to represent the function $f$ which we want find the $x$ such that $f(x) = 1$.
$$
\Ket x(\frac{\Ket 0 - \Ket 1}{\sqrt{2}}) \xrightarrow{O} (-1)^{f(x)}\Ket x (\frac{\Ket 0-\Ket1}{\sqrt 2})\\
\Ket x \xrightarrow{O} (-1)^{f(x)}\Ket x
$$
The second line is the easy representative of the first line.

### 2. Core Subroutine

The main subroutine used in Grover's searching algorithm is called the Grover iteration or $G$, which is:

1. Apply the oracle $O$
2. Apply the Hadamard transformation $H^{\otimes n}$
3. Perform a conditional phase shift, with every computational basis state except $\Ket 0$ receiving a phase shift of $-1$, which is $2\Ket 0\Bra 0 -I$.
4. Apply the Hadamard transform $H^{\otimes n}$ again

The latter three steps is equivalent to $2\Ket \psi \Bra \psi - I$. Here $\Ket \psi = \frac{1}{\sqrt N}\sum_k\Ket k$.

If we divide all $k$ into two types. One type makes $f(x) = 0$, which is $\Ket \alpha = \frac{1}{\sqrt{N-M}}\sum_{f(x)=0} \Ket x$. And $\Ket \beta = \frac{1}{\sqrt{M}}\sum_{f(x)=1} \Ket x$. So $\Ket \psi = \sqrt{\frac{N-M}{N}}\Ket \alpha + \sqrt{\frac{M}{N}}\Ket \beta$. If we define $\cos \frac{\theta}{2} = \sqrt{\frac{N-M}{N}}$, then we can have
$$
G\Ket \psi = \cos \frac{3\theta}{2}\Ket \alpha + \sin \frac{3\theta}{2} \Ket \beta
$$
So we can do $G$ several times until it is very close to $\Ket \beta$, then do a computational base measure, we can get a solution for the search problem with a high probability.







# PCP Theorem and Its Quantum Edition

# Circuit and Quantum Circuit Lower Bounds

