# Matrix Decompositions
- Determinant > Invertibility > Cholesky > Chap 6 - Probability & Distributions
- Determinant > Eigenvalues > 
  - Eigenvectors > Orthogonal matrix
  - Diagonalisation > SVD > Chap 10 - Dimensionality Reduction.

-----------------------------------------------

## 1. Determinant and Trace

### 1.1 Determinant

Only applied to square matrices. It maps $A \in \mathbb{R}^{n\times n}$ onto *real number*.
```math
\text{det}(A) = |A| = \begin{vmatrix}
    a_{11} & a_{12} & \cdots & a_{1n} \\
    a_{21} & a_{22} & \cdots & a_{2n} \\
    \vdots & & \ddots & \vdots \\
    a_{n1} & a_{n2} & \cdots & a_{nn}
\end{vmatrix}
```

> **Theorem 4.1.** For any square matrix $A \in \mathbb{R}^{n\times n}$ it holds that $A$ is invertible if and only if $\text{det}(A) \neq 0$ 

We prove theorem 4.1 by induction. It is easy for $n=1,2$. For $n=3$ (*Sarrus' rule*):
```math
\begin{vmatrix}
    a_{11} & a_{12} & a_{13} \\
    a_{21} & a_{22} & a_{23} \\
    a_{31} & a_{32} & a_{33}
\end{vmatrix}
= a_{11}a_{22}a_{33} + a_{21}a_{31}a_{13} + a_{31}a_{12}a_{23} - a_{31}a_{22}a_{13} - a_{11}a_{32}a_{23} - a_{21}a_{12}a_{33}
```

For **upper-triangular matrix** $T$ ($T_{ij}=0$ for $i>j$)
```math
\text{det}(T) = \prod_{i=1}^nT_{ii}
```

> **Theorem 4.2** (Laplace Expansion). Consider a matrix $A \in \mathbb{R}^{n\times n}$. Then, for all $j=1,...,n$:
> 1. Expansion along column j: $\text{det}(A) = \sum_{k=1}^n(-1)^{k+j}a_{kj}\text{det}(A_{k,j})$
> 2. Expansion along row j: $\text{det}(A) = \sum_{k=1}^n(-1)^{k+j}a_{jk}\text{det}(A_{j,k})$

> **Theorem 4.3**. A square matrix $A \in \mathbb{A}^{n\times n}$ has $\text{det}(A) \neq 0$ if and only if $\text{rk}(A)=n$. In other words, $A$ is invertible if and only if it is full rank.

### 1.2 Trace

Sum of diagonal elements of $A \in \mathbb{A}^{n\times n}$
```math
\text{tr}(A):= \sum_{i=1}^n a_{ii}
```

**Characteristic Polynomial**: $\lambda \in \mathbb{R}, A\in \mathbb{R}^{n\times n}, c_i \in \mathbb{R}$:
```math
p_A(\lambda):= \text{det}(A-\lambda I) = c_0 + c_1\lambda + c_2\lambda^2 + ... + c_{n-1}\lambda^{n-1} + (-1)^n\lambda^n
```
or
```math
c_0 = \text{det}(A) \\
c_{n-1} = (-1)^{n-1}\text{tr}(A)
```

------------------------------------

## 2. Eigenvalues and Eigenvectors

------------------------------------

## 3. Cholesky Decomposition

------------------------------------

## 4. Eigendecomposition & Diagonalisation

------------------------------------

## 5. Singular Value Decomposition (SVD)