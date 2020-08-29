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

They study this problem in the quantum query model.

## 2. Query Complexity

###1. An Optimal Separation of Randomized and Quantum Query Complexity 

[Arxiv:2008.10223](https://arxiv.org/pdf/2008.10223.pdf)

