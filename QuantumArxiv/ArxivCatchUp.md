$$
\newcommand{\Ket}[1]{\left| #1 \right\rangle}
\newcommand{\Bra}[1]{\left\langle #1 \right|}
$$



# Notes on quantum and computational complexity arxiv papers

## 1. Quantum Supremacy

### 1.The Quantum Supremacy Tsirelson Inequality 

[Arxiv: 2008.08721](https://arxiv.org/pdf/2008.08721.pdf)

####1. Backgroud

They look at the problem which is called *Linear Cross-Entropy Benchmark*.

###### Linear Cross-Entropy Benchmark: 

*For an n-qubit quantum circuit $C$ and samples $z_1,\cdots, z_k \in \{0,1\}^{n}$, the benchmark is given by:*
$$
b = \frac{2^n}{k}\cdot\sum_{i=1}^k |\Bra {z_{i}}C\Ket{0^n}|^2
$$
The aim is to do some good samples such that this $b$ can be as big as possible. 

Formally, we can define a problem *$b-$XHOG*.

**Problem** ($b-$XHOG) Given a quantum circuit $C$ on n qubits, output a sample $z\in \{o,1\}^n$ such that $\mathbb{E}[|\Bra zC\Ket{0^n}|^2]\ge \frac{b}{2^n}$, where the expectation is over an implicit distribution over circuits $C$ and over the randomness of the algorithm that outputs $z$.

Here is a fact that under a strong complexity-theoretic conjecture about the classical hardness of nontrivially estimating output probabilities of quantum circuits, Aaronson and Gunn showed that no classical polynomial-time algorithm can $b-$XHOG for any $b\ge 1+\frac{1}{poly(n)}$ on random quantum circuits of polynomial size.

And the question investigated in this paper is whether we can find an efficient quantum algorithm for $b-$XHOG doing substantially better than $b=2$.

#### 2. Main Result

They study this problem in the quantum query model.They studied three types of oracles: 1. Canonical state preparation oracles 2. Hear-random unitaries 3. Fouriere sampling circuits

Here are two results:

1. For first two types of quantum oracles: for any $\epsilon \ge \frac{1}{poly(n)}$, any quantum query algorithm for $(2+\epsilon)-XHOG$ requires at least $\Omega\left(\frac{2^{n/4}}{poly(n)} \right)$.
2. For Fourier sampling circuits oracle: Any $1-$query quantum algorithm for $b-XHOG$ with Fourier Sampling circuits achieves $b\le 3$. (This means the naive algorithm of simply running the circuit is optimal.)

#### 3. Techniques

For canonical state preparation oracle, they use a simple collision-finding algorithm and the result of [[ARU14]](https://arxiv.org/abs/1404.6898) 

For Haar-Random unitary oracle, they show it is equivalent to canonical state preparation oracle as resources.

For Fourier-Sampling circuit oracle, they use the polynomial method of Beals et al..

#### My Comments

Here are some problems from me: It seems this paper does not really provide any evidence that quantum algorithm can give a better than 2 result in polynomial time. I am really curious what the exponential query lower bound implies, as it is obviously the quantum supremacy campare the $b$ got by polynomial-time classical and quantum algorithms, so this can provide a separation for classical and quantum algorithms. But there is no hardness result for classical query complexity of this problem then how could it be used as a separation? 

I also curious about whether their techniques are novel or not, because it seems they just cite some previous techniques and with some observations then they can get the final result.





## 2. Query Complexity

###1. An Optimal Separation of Randomized and Quantum Query Complexity 

[Arxiv:2008.10223](https://arxiv.org/pdf/2008.10223.pdf)

This paper provides an $\mathrm{O}(1)$ and $\mathrm{\Omega}(n^{1-\epsilon})$ separation between Quantum Query Complexity and Randomized Query Complexity.

### 2. Separations in query complexity Based on Pointer Functions

[Arxiv:1506.04719](https://arxiv.org/abs/1506.04719)

