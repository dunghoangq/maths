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
    - $\forall{\lambda} \in \mathbb{R}, (\lambda C)^{T} = C^{T}\lambda^{T} = C^{T}\lambda = \lambda C^{T}$
  - Distributivity:
    - $C \in \mathbb{R}^{m \times n}, (\lambda + \psi)C = \lambda C + \psi C$
    - $B, C \in \mathbb{R}^{m \times n}, \lambda(B + C) = \lambda B + \lambda C$

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
  - **Neutral element**: $\exists e \in \mathcal{G}, \forall x \in \mathcal{G}: x \otimes e = e \otimes x = x$
  - **Inverse element** ($x^{-1}$): $\forall x \in \mathcal{G}, \exists y \in \mathcal{G}: x \otimes y = y \otimes x = e$ with $e$ := **neutral element**.
  - **Abilian group**: $\forall x, y \in \mathcal{G}: x \otimes y = y \otimes x$ (e.g. $(\mathbb{R} \backslash \{0\}, \cdot)$)
- **General linear group**: $GL(n, \mathbb{R})$ - a set of regular (invertible) matrices $A \in \mathbb{R}^{n \times n}$

### 4.2 Vector Spaces
- **Inner operation** := addition; **Outer operation** := scaling. They have nothing to do with inner/outer products.
- **Vector space**: real-valued $V = (\mathcal{V} , +, \cdot)$ (set $\mathcal{V}$, operations $+: \mathcal{V} \times \mathcal{V} \rightarrow \mathcal{V}$ (**vector addition**) **and** $\cdot: \mathbb{R} \times \mathcal{V} \rightarrow \mathcal{V}$) (**multiplication by scalars**), where:
  - $(\mathcal{V}, +)$ is an **Abelian group**.
  - **Distributivity**:
    - $\forall \lambda \in \mathbb{R}; x, y \in \mathcal{V}: \lambda \cdot (x+y) = \lambda\cdot x + \lambda\cdot y$
    - $\forall \lambda, \psi \in \mathbb{R}; x \in \mathcal{V}: (\lambda + \psi)\cdot x = \lambda\cdot x + \psi\cdot x$
  - **Associativity** (outer op): $\forall\lambda,\psi\in\mathbb{R}; x \in \mathcal{V}: \lambda\cdot(\psi\cdot x) = (\lambda\psi)\cdot x$
  - **Neutral element** (for outer op): $\forall x \in \mathcal{V}: 1\cdot x = x$
  - **Neutral element** (for inner op): $\mathbf{0} = [0,...,0]^{T}$ of $V = (\mathcal{V}, +)$
- $x \in V$ are called **Vectors**. By default, $x$ := **column vector**, $x^{T}$ := **row vector**.
- (Column) Vectors can be treated as $n \times 1$ matrices for multiplications:
  - **Outer product**: $ab^{T} \in \mathbb{R}^{n \times n}$
  - **Inner product** (scalar/dot product): $a^{T}b \in \mathbb{R}$

### 4.3 Vector Subspaces
- A **closed** subset in a vector space. We perform ops and will never leave it.
- In ML, Vector subspaces are used for **dimensionality reduction**.
- **Vector subspace**: $\mathcal{U} \subseteq{\mathcal{V}}, \mathcal{U}\ne{\emptyset}$, then $U = (\mathcal{U}, +, \cdot)$ is a vector subspace (*linear subspace*) of $V$ (denoted $U \subseteq V$) if ops $+$ and $\cdot$ are restricted to $\mathcal{U}\times\mathcal{U}$ and $\mathbb{R}\times\mathcal{U}$.
- A vector subspace inherits properties of its parent set.
- To determine $U$ is a subspace of $V$, we show:
  - $\mathcal{U}\ne\emptyset$, in particular: $\bf{0}\in\mathcal{U}$
  - **Closure** of $U$:
    - on outer op: $\forall\lambda\in\mathbb{R}, \forall x\in\mathcal{U}: \lambda x\in\mathcal{U}$
    - on inner op: $\forall x,y \in\mathcal{U}: x+y\in\mathcal{U}$

### 4.4 Linear Independence
- **Intuition**: find a set of vectors that represent the whole vector space with closure property. That vector is called **basis**.
- **Linear Combination**: $v\in V$ if for $x_{1},...,x_{k} \in V$, and $\lambda_{1},...,\lambda_{k} \in\mathbb{R}$, we have $v = \sum_{i=1}^{k}\lambda_{i}x_{i} \in V$
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
> \lambda_{1}x_{1} + \lambda_{2}x_{2} + \lambda_{3}x_{3} = 0
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
To test whether $x_{1},...,x_{m}$ are linearly independent, check if $\exists{\psi}\in\mathbb{R}: \sum_{j=1}^{m}\psi_{j}x_{j} = \bf{0}$.
The LHS is:
```math
\sum_{j=1}^{m}\psi_{j}B\lambda_{j} = B\sum_{j=1}^{m}\psi_{j}\lambda_{j}
```
Now, $\{x_{1},...,x_{m}\}$ are linearly independent *if and only if* $\{\lambda_{1},...,\lambda_{m}\}$ are linearly independent.

> e.g., given $b_{1},...,b_{4}\in\mathbb{R}^{n}$ and
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
- Find a set of vectors that can represent any vector in a space -> **Basis** of the space.
- Recall the **Linear combination** definition in section *4.4 Linear Independence*.

## 6. Basis and Ranks
- **Generating Set and Span**: A vector space $V = (\mathcal{V}, +, \cdot)$ and a set of vectors $\mathcal{A} = \{ x_{1},...,x_{k} \subseteq \mathcal{V} \}$.
  - If every vector $v \in \mathcal{V}$ is a linear combination of $x_{i}$ -> $\mathcal{A}$ is a **generating set** of $V$.
  - The set of all linear combinations of vectors in $\mathcal{A}$ is the span of $\mathcal{A}$, $\mathcal{A}$ spans $V$, or $V = \text{span}[\mathcal{A}]$ or $V = \text{span}[x_{1},...,x_{k}]$.
- **Basis**: Given $V = (\mathcal{V},+,\cdot)$ and $\mathcal{A} \subseteq{\mathcal{V}}$:
  - If there's no smaller set $\~{\mathcal{A}}\nsubseteq{\mathcal{A}}\subseteq{\mathcal{V}}$ that spans $V$ -> $\mathcal{A}$ is **minimal**.
  - Every linearly independent generating set of $V$ is minimal and is called a **basis** of $V$.
- $\mathcal{A}$ is: a **basis** of $V$ = a **minimal generating set** = **maximal linearly independent** set = every $x \in V$ is a **linear combination** of vectors from $\mathcal{A}$.

### 6.1 How to determine a Basis
For a subspace $U \subseteq{\mathbb{R}^{5}}$, spanned by vectors
```math
x_{1} = \begin{bmatrix}
  1 \\ 2 \\ -1 \\ -1 \\ -1
\end{bmatrix},
x_{2} = \begin{bmatrix}
  2 \\ -1 \\ 1 \\ 2 \\ -2
\end{bmatrix},
x_{3} = \begin{bmatrix}
  3 \\ -4 \\ 3 \\ 5 \\ -3
\end{bmatrix},
x_{4} = \begin{bmatrix}
  -1 \\ 8 \\ -5 \\ -6 \\ 1
\end{bmatrix} \in \mathbb{R}^{5}
```
But which ones in the vectors above are a basis of $U$???
By trying to solve:
```math
\sum_{i=1}^{4}\lambda_{i}x_{i} = 0
```
we derive a homogeneous system of equations
```math
[x_{1}, x_{2}, x_{3}, x_{4}] = 
\begin{bmatrix}
  1 & 2 & 3 & -1 \\
  2 & -1 & -4 & 8 \\
  -1 & 1 & 3 & 5 \\
  -1 & 2 & 5 & -6 \\
  -1 & -2 & -3 & 1
\end{bmatrix} \leadsto ... \leadsto
\begin{bmatrix}
  1 & 2 & 3 & -1 \\
  0 & 1 & 2 & -2 \\
  0 & 0 & 0 & 1 \\
  0 & 0 & 0 & 0 \\
  0 & 0 & 0 & 0
\end{bmatrix}
```
The pivot columns are $x_{1}, x_{2}, x_{4}$, which means the equation $\lambda_{1}x_{1} + \lambda_{2}x_{2} + \lambda_{4}x_{4} = 0$ can only be solved with $\lambda_{1} = \lambda_{2} = \lambda_{4} = 0$ -> $\{ x_{1}, x_{2}, x_{4} \}$ is a basis of $U$.

### 6.2 Rank
- **Rank** ($\text{rk}(\mathbf{A})$): # linearly independent columns = # linearly independent rows of matrix $A \in \mathbb{R}^{m \times n}$
- Some properties of rank:
  - $\text{rk}(A) = \text{rk}(A^{T})$
  - Columns of $A \in \mathbb{R}^{m \times n}$ span a subspace $U \subseteq \mathbb{R}^{m}$ <-> $\text{dim}(U) = \text{rk}(A)$.
  - Rows of $A \in \mathbb{R}^{m \times n}$ span a subspace $V \subseteq \mathbb{R}^{n}$ <-> $\text{dim}(V) = \text{rk}(A)$
  - $A \in \mathbb{R}^{n \times n}$ is regular (invertible) <-> $\text{rk}(A) = n$.
  - $A \in \mathbb{R}^{m \times n}$, $b \in \mathbb{R}^{m}$: $Ax = b$ can be solved <-> $\text{rk}(A) = \text{rk}(A|b)$.
  - $A \in \mathbb{R}^{m \times n}$, the subspace of solutions for $Ax = 0$ has dimension $n - \text{rk}(A)$ (aka **kernel** or **null space**).
  - A matrix $A \in \mathbb{R}^{m \times n}$ has **full rank** if it has the largest possible rank for its dimensions. Or $\text{rk}(A) = \text{min}(m, n)$.

## 7. Linear Mappings
- Recall two vectors in a vector space and be added together or multiplied by a scalar (closure). Imagine a mapping $\Phi: V \rightarrow W$ preserves the structure of a vector space if
```math
\Phi(x+y) = \Phi(x) + \Phi(y) \\
\Phi(\lambda x) = \lambda\Phi(x)
```
- **Linear mapping**: For vector spaces $V, W$, a mapping $\Phi: V \rightarrow W$ is a linear mapping (or **vector space homomorphism** / **linear transformation**) if
```math
\forall x,y \in V, \forall \lambda,\psi \in \mathbb{R}: \Phi(\lambda x + \psi y) = \lambda\Phi(x) + \psi\Phi(y)
```
- $\mathcal{V}$, $\mathcal{W}$ are arbitrary sets, mapping $\Phi: \mathcal{V} \rightarrow \mathcal{W}$ is called:
  - **Injective**: $\forall x,y \in \mathcal{V}: \Phi(x) = \Phi(y) \Rightarrow x=y$.
  - **Surjective**: $\Phi(\mathcal{V}) = \mathcal{W}$.
  - **Bijective**: both *injective* and *surjective*. (can be *undone*, there exists a mapping $\Psi: \mathcal{W} \rightarrow \mathcal{V}: \Psi \circ \Phi(x) = x$, or $\Psi$ is inverse $\Phi^{-1}$).
- Special cases of linear mappings:
  - **Isomorphism**: $\Phi: V \rightarrow W$ linear and bijective.
  - **Endomorphism**: $\Phi: V \rightarrow V$ linear.
  - **Automorphism**: $\Phi: V \rightarrow V$ linear and bijective.
  - $\text{id}_{V}: V \rightarrow V, x \mapsto x$ is the **identity mapping** or **identity automorphism** in $V$.
> **Theorem 2.17** (Axler 2015): Finite-dimensional vector spaces $V$ and $W$ are isomorphic if and only if $\text{dim}(V) = \text{dim}(W)$.

To understand theorem 2.17, recall Isomorphism = Linear + Bijective =
- **Linear** ($\Phi(\lambda x + \psi y) = \lambda\Phi(x) + \psi\Phi(y)$) + 
- **Injective** (one x can only produce one $\Phi(x)$) + 
- **Surjective** (all $V$ can be mapped to all $\Phi(V) = W$).

Which means $W$ is a perfect map of $V$, nothing is lost, nothing is duplicated. Denote $V \cong W$ for isomorphism.

*Proof:*

If V and W are isomorphic -> It maps a basis of V to a basis of W. So $\text{dim}(V) = \text{dim}(W)$.

In contrast, suppose $\text{dim}(V) = \text{dim}(W) = n$, let $\{ v_{1},...,v_{n} \}$ and $\{ w_{1},...,w_{n} \}$ are bases of $V$ and $W$ respectively, then we define a map $T(v_{i}) = w_{i}$. This map is:
- linear
- 1-to-1
- onto

Hence, it's isomorphism.

> **Note**: Any n-dimensional vector space is isomorphic to $\mathbb{R}^{n}$.

### 7.1 Matrix Representation of Linear Mappings
- n-tuple form of an **ordered basis** of $V$: $B = (b_{1},...,b_{n})$. Tuple because order of basis vectors matters, unlike set {} form is **unordered basis**.
- **Coordinates**: Vector space $V$ and an ordered basis $B = (b_{1},...,b_{n})$ of $V$. For any $x \in V$, we have $x = \sum_{i=1}^{n}\alpha_{i}b_{i}$. Then **coordinate vector** / **coordinate representation** of $x$ with respect to the ordered basis $B$, is:
```math
\alpha = \begin{bmatrix}
  \alpha_{1} \\ \vdots \\ \alpha_{n}
\end{bmatrix} \in \mathbb{R}^{n}
```
- **Transformation Matrix**: $B=(b_{1},...,b_{n})$ and $C=(c_{1},...,c_{m})$ are ordered bases of $V, W$. A linear mapping $\Phi: V \rightarrow W$ and for $j \in \{1,...,n\}$,
```math
\Phi(b_{j}) = \sum_{i=1}^{m}\alpha_{ij}c_{i} \\
```
is the unique representation of $\Phi(b_{j})$ with respect to $C$. Let $m\times x$-matrix $A_{\Phi}$ is the **transformation matrix** for linear mapping $\Phi$ with elements $A_{\Phi}(i,j)=\alpha_{ij}$ (i=row for C, j=column for B).
- If $\hat{x}$ is the coordinate vector of $x \in V$ and $\hat{y}$ with respect to $B$ is the coordinate vector of $y = \Phi(x) \in W$ with respect to $C$, then:
```math
\hat{y} = A_{\Phi}\hat{x}
```

*e.g., $\Phi: V \rightarrow W$ and ordered bases $B=(b_{1},...,b_{3})$ of V and $C=(c_1,...,c_4)$ of W* with:
```math
\begin{array}{lcr}
  \Phi(b_1) = c_1 - c_2 + 3c_3 - c_4 \\
  \Phi(b_2) = 2c_1 + c_2 + 7c_3 + 2c_4 \\
  \Phi(b_3) = 3c_2 + c_3 + 4c_4
\end{array}
```
the transformation matrix must satisfy $\Phi(b_k) = \sum_{i=1}^4\alpha_{ij}c_i$ for k = 1,2,3.
```math
A_{\Phi} = [\alpha_1, \alpha_2, \alpha_3] = \begin{bmatrix}
  1 & 2 & 0 \\
  -1 & 1 & 3 \\
  3 & 7 & 1 \\
  -1 & 2 & 4
\end{bmatrix}
```

## 8. Affine Spaces
