Vectors and Vector Spaces
===========================

## 1. Systems of Linear Equations
- Many problems can be formulated as systems of Linear Equations -> Linear Algebra.
- We solve linear eq in high-school but this time, see it in vector pov.
```math
\begin{bmatrix}
a_{11} \\ ... \\ a_{m1} \end{bmatrix} x_{1}
+ \begin{bmatrix} a_{12} \\ ... \\ a_{m2} \end{bmatrix} x_{2}
+ ...
+ \begin{bmatrix} a_{1n} \\ ... \\ a_{mn} \end{bmatrix} x_{n}
= \begin{bmatrix} b_{1} \\ ... \\ b_{m} \end{bmatrix}
```
or
```math
\begin{bmatrix}
a_{11} \ ... \ a_{1n} \\
... \\
a_{m1} \ ... \ a_{mn}
\end{bmatrix} 
\begin{bmatrix} x_{1} \\ ... \\ x_{2} \end{bmatrix}
= \begin{bmatrix} b_{1} \\ ... \\ b_{m} \end{bmatrix}
```

## 2. Matrices
### 2.1 Addition and Multiplication
- Matrices can be added for $A, B \in \mathbb{R}^{m \times n}$
- Dot products can be made if $A \in \mathbb{R}^{m \times n}$ and $B \in \mathbb{R}^{n \times p}$
- **Identity matrix** is n x n matrix containing 1 on the diagonal and 0 everywhere. It has 3 properties:
  - **Associativity**: $\forall{A \in \mathbb{R}^{m \times n}}, B \in \mathbb{R}^{n \times p}, C \in \mathbb{R}^{p \times q}: (AB)C = A(BC)$
  - **Distributivity**: $\forall{A, B \in \mathbb{R}^{m \times n}}, C, D \in \mathbb{R}^{n \times p}: (A+B)C = AC + BC, A(C + D) = AC + AD$
  - **Multiplications with id-mat**: $\forall{A \in \mathbb{R}^{m \times n}}: I_{m}A = AI_{n} = A$

### 2.2 Inverse & Transpose
- **Inverse**: $B$ is the inverse of $A$ if $A, B \in \mathbb{R}^{n \times n}: AB = I_{n} = BA$ and A is called *regular/invertible/nonsingular*, otherwise *singular/noninvertible*.
- For $2 \times 2$ matrices:
$$ A^{-1} = \frac{1}{a_{11}a_{22} - a_{12}a_{21}} \begin{bmatrix} a_{22} \ -a_{12} \\ -a_{21} \ a_{11} \end{bmatrix} $$
if and only if $a_{11}a_{22} - a_{12}a_{21} \ne 0$
- **Transpose**: $B = A^{T}$ if $A \in \mathbb{R}^{m \times n}, B \in \mathbb{R}^{n \times m}$ with $b_{ij} = a_{ji}$
- **Symmetry**: $A$ is symmetric if for $A \in \mathbb{R}^{n \times n}$ and $A = A^{T}$

### 2.3 Multiplication by a Scalar
- With a Scalar, we have:
  - **Associativity**:
    - $C \in \mathbb{R}^{m \times n}, (\lambda\psi)C = \lambda(\psi C)$
    - $B \in \mathbb{R}^{m \times n}, C \in \mathbb{R}^{n \times k}, \lambda(BC) = (\lambda B)C = B(\lambda C) = (BC)\lambda$
    - $\forall{\lambda} \in \R, (\lambda C)^{T} = C^{T}\lambda^{T} = C^{T}\lambda = \lambda C^{T}$
  - Distributivity:
    - $C \in \R^{m \times n}, (\lambda + \psi)C = \lambda C + \psi C$
    - $B, C \in \R^{m \times n}, \lambda(B + C) = \lambda B + \lambda C$

## 3. Solving Systems of Linear Equations
### 3.1 Basic
- They taught me to convert the system of linear equations to augmented matrix > row-echelon form (REF) > all **pivot** = 1 to solve it.
- **Reduced-Echelon Form** must follow these 2 rules:
  - All rows that contain only zeros at the bottom. The ones have at least one nonzero elem are on top of the ones having only zeros.
  - The first nonzero number is called **pivot** or the **leading coefficient**.
- They mentioned **Minus-1 Trick** but I don't pay too much attention to it.
- To calculate an Inverse Matrix, use **Gaussian Elimination**.

### 3.2 Algorithms for Solving a System of Linear Equation
- The flow:
```math
Ax = b \iff A^TAx = A^Tb \iff x = (A^TA)^{-1}A^Tb
```
then use the **Moore-Penrose pseudo-inverse** $(A^TA)^{-1}A^T$
- In practice, they use **Richardson method**, **Jacobi method**, **Gauß-Seidel method**, **successive over-relaxation method**, **Krylov subspace methods** (conjugate gradients, generalised minimal residual, biconjugate gradients)

----------------------------

## 4. Vector Spaces
Flow of understanding:
> Groups > Vector Spaces > Vector Subspaces > Linear Independence

### 4.1 Groups
- A set $\mathcal{G}$ with an operation $\otimes: \mathcal{G} \times \mathcal{G} \rightarrow \mathcal{G}$. Then $G := (\mathcal{G}, \otimes)$ is a group if:
  - **Closure** of $\mathcal{G}$ under $\otimes$: $\forall x, y \in \mathcal{G}: (x \otimes y) \in \mathcal{G}$
  - **Associativity**: $\forall x, y, z \in \mathcal{G}: (x \otimes y)\otimes z = x \otimes(y \otimes z)$
  - **Neutral element**: $\exist e \in \mathcal{G}, \forall x \in \mathcal{G}: x \otimes e = e \otimes x = x$
  - **Inverse element** ($x^{-1}$): $\forall x \in \mathcal{G}, \exist y \in \mathcal{G}: x \otimes y = y \otimes x = e$ with $e$ := **neutral element**.
  - **Abilian group**: $\forall x, y \in \mathcal{G}: x \otimes y = y \otimes x$ (e.g. $(\R \backslash \{0\}, \cdot)$)
- **General linear group**: $GL(n, \R)$ - a set of regular (invertible) matrices $A \in \R^{n \times n}$

### 4.2 Vector Spaces
- **Inner operation** := addition; **Outer operation** := scaling. They have nothing to do with inner/outer products.
- **Vector space**: real-valued $V = (\mathcal{V} , +, \cdot)$ (set $\mathcal{V}$, operations $+: \mathcal{V} \times \mathcal{V} \rightarrow \mathcal{V}$ (**vector addition**) **and** $\cdot: \R \times \mathcal{V} \rightarrow \mathcal{V}$) (**multiplication by scalars**), where:
  - $(\mathcal{V}, +)$ is an **Abelian group**.
  - **Distributivity**:
    - $\forall \lambda \in \R; x, y \in \mathcal{V}: \lambda \cdot (x+y) = \lambda\cdot x + \lambda\cdot y$
    - $\forall \lambda, \psi \in \R; x \in \mathcal{V}: (\lambda + \psi)\cdot x = \lambda\cdot x + \psi\cdot x$
  - **Associativity** (outer op): $\forall\lambda,\psi\in\R; x \in \mathcal{V}: \lambda\cdot(\psi\cdot x) = (\lambda\psi)\cdot x$
  - **Neutral element** (for outer op): $\forall x \in \mathcal{V}: 1\cdot x = x$
  - **Neutral element** (for inner op): $\mathbf{0} = [0,...,0]^{T}$ of $V = (\mathcal{V}, +)$
- $x \in V$ are called **Vectors**. By default, $x$ := **column vector**, $x^{T}$ := **row vector**.
- (Column) Vectors can be treated as $n \times 1$ matrices for multiplications:
  - **Outer product**: $\bm{a}\bm{b}^{T} \in \R^{n \times n}$
  - **Inner product** (scalar/dot product): $\bm{a}^{T}\bm{b} \in \R$

### 4.3 Vector Subspaces
- A **closed** subset in a vector space. We perform ops and will never leave it.
- In ML, Vector subspaces are used for **dimensionality reduction**.
- **Vector subspace**: $\mathcal{U} \subseteq{\mathcal{V}}, \mathcal{U}\ne{\empty}$, then $U = (\mathcal{U}, +, \cdot)$ is a vector subspace (*linear subspace*) of $V$ (denoted $U \subseteq V$) if ops $+$ and $\cdot$ are restricted to $\mathcal{U}\times\mathcal{U}$ and $\R\times\mathcal{U}$.
- A vector subspace inherits properties of its parent set.
- To determine $U$ is a subspace of $V$, we show:
  - $\mathcal{U}\ne\empty$, in particular: $\bf{0}\in\mathcal{U}$
  - **Closure** of $U$:
    - on outer op: $\forall\lambda\in\R, \forall\bm{x}\in\mathcal{U}: \lambda\bm{x}\in\mathcal{U}$
    - on inner op: $\forall\bm{x},\bm{y}\in\mathcal{U}: \bm{x}+\bm{y}\in\mathcal{U}$

### 4.4 Linear Independence
- **Intuition**: find a set of vectors that represent the whole vector space with closure property. That vector is called **basis**.
- **Linear Combination**: $\bm{v}\in V$ if for $\bm{x}_{1},...,\bm{x}_{k} \in V$, and $\lambda_{1},...,\lambda_{k} \in\R$, we have $\bm{v} = \sum_{i=1}^{k}\lambda_{i}\bm{x}_{i} \in V$
- $\bf{0}\in V$ is always a **trivial** combination, for non-trivial ones, not all $\lambda_{i}$ are 0.
- **Linear Independence**:
  - $k$ vectors are either **linearly dependent** or **linearly independent**.
  - $x_{1},...,x_{k}$ are linearly dependent if:
    - at least one of them is *0*.
    - or two of them are *identical*.
    - or none of them is 0, but at least one of them is a *linear combination* of the others ($x_{i} = \lambda x_{j}$).
  - If $k$ vectors are linearly independent, apply *Gaussian elimination* -> REF: All columns are *pivot column*.


> e.g., Given:
> ```math
> x_{1} = \begin{bmatrix}1\\2\\-3\\4\end{bmatrix},
> x_{2} = \begin{bmatrix}1\\1\\0\\2\end{bmatrix},
> x_{3} = \begin{bmatrix}-1\\-2\\1\\1\end{bmatrix}
> ```
> are *linearly independent*. Because let's:
> ```math
> \lambda_{1}x_{1} + \lambda_{2}x_{2} + \lambda_{3}x_{3} = \bm{0}
> ```
> then we have REF:
> ```math
> \begin{bmatrix}
>   1 & 1 & -1 \\
>   0 & 1 & 0 \\
>   0 & 0 & 1 \\
>   0 & 0 & 0
> \end{bmatrix}
> ```
> in which every column is a *pivot column*.

- General form:
```math
x_{1} = \sum_{i=1}^{k}\lambda_{i1}b_{i} \\
\vdots \\
x_{m} = \sum_{i=1}^{k}\lambda_{im}b_{i}
```
for $B = [b_{1},...,b_{k}]$, we have:
```math
x_{j}=B\lambda_{j}, \lambda_{j} = \begin{bmatrix}\lambda_{1j}\\\vdots\\\lambda_{kj}\end{bmatrix},
j=1,...,m
```
To test whether $x_{1},...,x_{m}$ are linearly independent, check if $\exist{\psi}\in\R: \sum_{j=1}^{m}\psi_{j}x_{j} = \bf{0}$.
The LHS is:
```math
\sum_{j=1}^{m}\psi_{j}B\lambda_{j} = B\sum_{j=1}^{m}\psi_{j}\lambda_{j}
```
Now, $\{x_{1},...,x_{m}\}$ are linearly independent *if and only if* $\{\lambda_{1},...,\lambda_{m}\}$ are linearly independent.

> e.g., given $b_{1},...,b_{4}\in\R^{n}$ and
> ```math
> \begin{array}{lcr}
>   x_{1} = b_{1} - 2b_{2} + b_{3} - b_{4} \\
>   x_{2} = -4b_{1} - 2b_{2} + 4b_{4} \\
>   x_{3} = 2b_{1} + 3b_{2} - b_{3} - 3b_{4} \\
>   x_{4} = 17b_{1} - 10b_{2} + 11b_{3} + b_{4}
> \end{array}
> ```
> Now look at these column vectors:
> ```math
> \{
>   \begin{bmatrix}1\\-2\\1\\-1\end{bmatrix},
>   \begin{bmatrix}-4\\-2\\0\\4\end{bmatrix},
>   \begin{bmatrix}2\\3\\-1\\-3\end{bmatrix},
>   \begin{bmatrix}17\\-10\\11\\1\end{bmatrix}
> \}
> ```
> if $x_{1},...,x_{4}$ are linearly independent, the column vectors above must also be linearly independent. The REF of the matrix formed from these vectors is:
> ```math
> A = 
> \begin{bmatrix}
>   1 & -4 & 2 & 17\\
>  -2 & -2 & 3 & -10\\
>   1 & 0 & -1 & 11\\
>   -1 & 4 & -3 & 1
> \end{bmatrix}
> = \begin{bmatrix}
>   1 & 0 & 0 & -7\\
>   0 & 1 & 0 & -15\\
>   0 & 0 & 1 & -18\\
>   0 & 0 & 0 & 0
> \end{bmatrix}
> ```
> Not all columns are *pivot columns* -> Linearly dependent: $x_{4} = -7x_{1} -15x_{2} - 18x_{3}$

------------------------

## 5. Linear Independence

## 6. Basis and Ranks

## 7. Linear Mappings

## 8. Affine Spaces
