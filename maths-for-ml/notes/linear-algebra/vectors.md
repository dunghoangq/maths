# Vectors and Vector Spaces
===========================

## 1. Systems of Linear Equations
- Many problems can be formulated as systems of Linear Equations -> Linear Algebra.
- We solve linear eq in high-school but this time, see it in vector pov.
$$
\begin{bmatrix}
a_{11} \\ ... \\ a_{m1} \end{bmatrix} x_{1}
+ \begin{bmatrix} a_{12} \\ ... \\ a_{m2} \end{bmatrix} x_{2}
+ ...
+ \begin{bmatrix} a_{1n} \\ ... \\ a_{mn} \end{bmatrix} x_{n}
= \begin{bmatrix} b_{1} \\ ... \\ b_{m} \end{bmatrix}
$$
or
$$
\begin{bmatrix}
a_{11} \ ... \ a_{1n} \\
... \\
a_{m1} \ ... \ a_{mn}
\end{bmatrix} 
\begin{bmatrix} x_{1} \\ ... \\ x_{2} \end{bmatrix}
= \begin{bmatrix} b_{1} \\ ... \\ b_{m} \end{bmatrix}
$$

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
$$ Ax = b \iff A^TAx = A^Tb \iff x = (A^TA)^{-1}A^Tb $$
then use the **Moore-Penrose pseudo-inverse** $(A^TA)^{-1}A^T$
- In practice, they use **Richardson method**, **Jacobi method**, **Gauß-Seidel method**, **successive over-relaxation
method**, **Krylov subspace methods** (conjugate gradients, generalised minimal residual, biconjugate gradients)

## 4. Vector Spaces

## 5. Linear Independence

## 6. Basis and Ranks

## 7. Linear Mappings

## 8. Affine Spaces
