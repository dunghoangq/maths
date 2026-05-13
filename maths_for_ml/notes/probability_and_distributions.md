# Probability and Distributions
- Bayes' Theorem > Chapter 9: Regression
- Gaussian >:
  - Chapter 9: Regression
  - Chapter 10: Dimensionality Reduction
  - Chapter 11: Density Estimation

-------------------------------

## 1. Probability Space

Two major interpretations: **Bayesian** and **Frequentist interpretations**.

**Probability** models process where underying uncertainty occurs. But in **statistics**, we observe something happened and try to figure out the underlying process that explains the obervations. => ML í close to Statistics.

-------------------------------


## 2. Discrete and Continuous Probabilities

**Discrete Probs**: Multidimensional array, joint probability of all dimensions is Cartesian product $x_iy_j$ over $N$ total of events.

**Continuous Probs**: Real-valued random variables with their corresponding Borel $\sigma$-algebra.

**Borel $\sigma$-algebra**: Sets that behave well under set operations and additionally have a topology.

**Probability Density Function**: $f: \mathbb{R}^D \rightarrow \mathbb{R}$ is *pdf* if:
1. $\forall x \in \mathbb{R}^D:f(x) \geq 0$
2. Its integral exists and :

```math
\int_{\mathbb{R}^D}f(x)dx = 1
```

**Probability Mass Function**: In *pmf*, integral is replaced with *sum*.

For $a, b, x \in \mathbb{R}$, random variable $X$.

```math
P(a \leq X \leq b) = \int_{a}^bf(x)dx
```

**Cumulative Distribution Function**: A *cdf* of a multivariate real-valued random var. $X$ with states $x \in \mathbb{R}^D$:

```math
F_X(x) = P(X_1 \leq x_1,...,X_D \leq x_D)
```

where $X = [X_1,...,X_D]^T$ and $x = [x_1,...,x_D]^T$.

A $cdf$ can be represented á the integral of $pdf$.

```math
F_X(x) = \int_{-\infty}^{x_1}\cdots\int_{-\infty}^{x_D}f(\mathcal{z}_1,...,\mathcal{z}_D)dz_1...dz_D
```

-------------------------------

## 3. Bayes' Theorem, Sum Rule, Product Rule

**Sum Rule**: with $\mathcal{Y}$ are the states of the target space of random var. Y

```math
p(x) = \begin{cases}
  \sum_{x \in \mathcal{Y}} p(x,y) & \text{ if } y \text{ is discrete} \\
  \int_{\mathcal{Y}}p(x, y)dy & \text{ if } y \text{ is continuous}
\end{cases}
```

The sum rule relates the joint distribution to a marginal distribution. For $x =[x_1,...,x_D]^T$:

```math
p(x_i) = \int p(x_1,...,x_D)dx_{\backslash i}
```

with $\backslash i$ means reads all except $i$.

**Product Rule**:

```math
p(x,y) = p(y|x)p(x)
```

**Bayes' Rule**:

```math
p(x|y) = \frac{p(y|x)p(x)}{p(y)}
```

-------------------------------

## 4. Summary Statistics and Independence

### 4.1 Means and Covariances

**Expected Value** is central to ML. Expected value of a function $g: \mathbb{R} \rightarrow \mathbb{R}$ of a univariate continuous random var. $X \sim p(x)$ is:

```math
\mathbb{E}_X[g(x)] = \int_{\mathcal{X}}g(x)p(x)dx
```

For descrete random var. $X$:

```math
\mathbb{E}_X[g(x)] = \sum_{x \in \mathcal{X}} g(x)p(x)
```

If $X$ is a vector of univariate random vars. $[X_1,...,X_D]^T$:

```math
\mathbb{E}_X[g(x)] = \begin{bmatrix}
  \mathbb{E}_{X_1}[g(x_1)] \\
  \vdots \\
  \mathbb{E}_{X_D}[g(x_D)]
\end{bmatrix}
\in \mathbb{R}^D
```


**Mean** of a random var $X$ with sates $x \in \mathbb{R}^D$:

```math
\mathbb{E}_X[x] = \begin{bmatrix}
  \mathbb{E}_{X_1}[x_1] \\
  \vdots \\
  \mathbb{E}_{X_D}[x_D]
\end{bmatrix}
\in \mathbb{R}^D
```

where

```math
\mathbb{E}_{X_d}[x_d]:= \begin{cases}
  \int_{\mathcal{X}}x_dp(x_d)dx_d & \text{if } X \text{ is a continuous random var} \\
  \sum_{x_i \in \mathcal{X}}x_ip(x_d=x_i) & \text{if } X \text{ is a discrete random var}
\end{cases}
```

for $d = 1,..., D$.

**Covariance (univariate)**: Two random vars $X,Y \in \mathbb{R}$:

```math
\text{Cov}_{X,Y}[x,y]:= \mathbb{E}_{X,Y}[(x - \mathbb{E}_X[x])(y - \mathbb{E}_Y[y])] \\
\text{Cov}[x,y] = \mathbb{E}[xy] - \mathbb{E}[x]\mathbb{E}[y]
```

Covariance of a var and itself $\text{Cov}[x,x]$ is denoted $\mathbb{V}_X[x]$.

Standard Deviation is the square root of the variance: $\sigma(x)$.

**Covariance (multivariate)**: Two random vars $X,Y$ with states $x \in \mathbb{R}^D$ and $y \in \mathbb{R}^E$. Covariance between $X$ and $Y$:

```math
\text{Cov}[x, y] = \mathbb{E}[xy^T] - \mathbb{E}[x]\mathbb{E}[y^T] = \text{Cov}[y,x]^T \in \mathbb{R}^{D \times E}
```

**Variance** of a random var $X$ with states $x \in \mathbb{R}^D$ and a mean $\mu \in \mathbb{R}^D$:

```math
\mathbb{V}_X[x] = \text{Cov}_X[x,x] \\
= \mathbb{E}_X[(x-\mu)(x-\mu)^T] = \mathbb{E}_X[xx^T] - \mathbb{E}_X[x]\mathbb{E}[x]^T \\
= \begin{bmatrix}
  \text{Cov}[x_1,x_1] & \text{Cov}[x_1,x_2] & \cdots & \text{Cov}[x_1,x_D] \\
  \text{Cov}[x_2,x_1] & \text{Cov}[x_2,x_2] & \cdots & \text{Cov}[x_2,x_D] \\
  \vdots & \vdots & \ddots & \vdots \\
  \text{Cov}[x_D,x_1] & \cdots & \cdots & \text{Cov}[x_D,x_D]
\end{bmatrix}
```

The normalised version of *covariance* is **Correlation**. For two random vars $X,Y$:

```math
\text{corr}[x,y] = \frac{\text{Cov}[x,y]}{\sqrt{\mathbb{V}[x]\mathbb{V}[y]}} \in [-1,1]
```

### 4.2 Empirical Means and Covariances

**Empirical mean** vector is the arithmetic mean. For $x_n \in \mathbb{R}^D$

```math
\overline{x}:= \frac{1}{N}\sum_{n=1}^Nx_n
```

**Empirical Covariance** $D \times D $matrix

```math
\sum:= \frac{1}{N}\sum_{n=1}^N(x_n - \overline{x})(x_n - \overline{x})^T
```

-------------------------------

## 5. Gaussian Distribution