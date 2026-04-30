# 📘 Probability & Statistics — Formula Reference Sheet

---

## 1. Basic Probability

### 1.1 Introduction & Sample Space

- **Sample Space**: $S = \{all\ possible\ outcomes\}$
- **Event**: $A \subseteq S$
- **Complement**: $A^c = S \setminus A$

---

### 1.2 Probability Defined on Events (Axioms)

- **Non-negativity**: $P(A) \geq 0$
- **Normalization**: $P(S) = 1$
- **Additivity** (mutually exclusive events): $P(A \cup B) = P(A) + P(B),\quad \text{if } A \cap B = \emptyset$
- **General Addition Rule**: $P(A \cup B) = P(A) + P(B) - P(A \cap B)$
- **Complement Rule**: $P(A^c) = 1 - P(A)$

---

### 1.3 Algebra of Events

- **De Morgan's Laws**:
  - $(A \cup B)^c = A^c \cap B^c$
  - $(A \cap B)^c = A^c \cup B^c$
- **Inclusion-Exclusion (3 events)**:

$$P(A \cup B \cup C) = P(A)+P(B)+P(C) - P(A\cap B) - P(B\cap C) - P(A\cap C) + P(A\cap B\cap C)$$

---

### 1.4 Conditional Probability

$$P(A \mid B) = \frac{P(A \cap B)}{P(B)}, \quad P(B) > 0$$

- **Multiplication Rule**: $P(A \cap B) = P(A \mid B)\cdot P(B)$
- **Chain Rule**:

$$P(A_1 \cap A_2 \cap \cdots \cap A_n) = P(A_1)\cdot P(A_2\mid A_1)\cdot P(A_3\mid A_1 \cap A_2)\cdots$$

---

### 1.5 Independent Events

- $A$ and $B$ are **independent** iff:

$$P(A \cap B) = P(A)\cdot P(B)$$

- Equivalently: $P(A \mid B) = P(A)$
- **Mutual Independence** of $A_1, A_2, \ldots, A_n$:

$$P\!\left(\bigcap_{i \in S} A_i\right) = \prod_{i \in S} P(A_i), \quad \forall\, S \subseteq \{1,\ldots,n\}$$

---

### 1.6 Bayes' Theorem

- **Law of Total Probability** (partition $B_1, B_2, \ldots, B_n$):

$$P(A) = \sum_{i=1}^{n} P(A \mid B_i)\cdot P(B_i)$$

- **Bayes' Theorem**:

$$P(B_i \mid A) = \frac{P(A \mid B_i)\cdot P(B_i)}{\displaystyle\sum_{j=1}^{n} P(A \mid B_j)\cdot P(B_j)}$$

---

---

## 2. Random Variables

### 2.1 Introduction

- **Discrete RV**: takes countable values
- **Continuous RV**: takes values in an interval

---

### 2.2 PMF / PDF / CDF

#### Probability Mass Function (PMF) — Discrete
$$p(x) = P(X = x), \quad \sum_x p(x) = 1$$

#### Probability Density Function (PDF) — Continuous
$$f(x) \geq 0, \quad \int_{-\infty}^{\infty} f(x)\,dx = 1$$
$$P(a \leq X \leq b) = \int_a^b f(x)\,dx$$

#### Cumulative Distribution Function (CDF)
$$F(x) = P(X \leq x) = \begin{cases} \displaystyle\sum_{t \leq x} p(t) & \text{(discrete)} \\[6pt] \displaystyle\int_{-\infty}^{x} f(t)\,dt & \text{(continuous)} \end{cases}$$

- $F(-\infty) = 0,\quad F(\infty) = 1$
- $f(x) = \dfrac{d}{dx}F(x)$ (continuous case)

---

### 2.3 Discrete Distributions

#### 2.3.1 Bernoulli Distribution — $X \sim \text{Bernoulli}(p)$
$$P(X=1)=p,\quad P(X=0)=1-p$$
$$E[X]=p,\quad \text{Var}(X)=p(1-p)$$

#### 2.3.2 Binomial Distribution — $X \sim B(n, p)$
$$P(X=k) = \binom{n}{k} p^k (1-p)^{n-k},\quad k=0,1,\ldots,n$$
$$E[X]=np,\quad \text{Var}(X)=np(1-p)$$

#### 2.3.3 Poisson Distribution — $X \sim \text{Poisson}(\lambda)$
$$P(X=k) = \frac{e^{-\lambda}\lambda^k}{k!},\quad k=0,1,2,\ldots$$
$$E[X]=\lambda,\quad \text{Var}(X)=\lambda$$

#### 2.3.4 Multinomial Distribution — $(X_1,\ldots,X_k)\sim \text{Multinomial}(n; p_1,\ldots,p_k)$
$$P(X_1=n_1,\ldots,X_k=n_k) = \frac{n!}{n_1!\,n_2!\cdots n_k!}\,p_1^{n_1}p_2^{n_2}\cdots p_k^{n_k}$$
$$\sum_{i=1}^k n_i = n,\quad \sum_{i=1}^k p_i = 1$$
$$E[X_i]=np_i,\quad \text{Var}(X_i)=np_i(1-p_i)$$

#### 2.3.5 Geometric Distribution — $X \sim \text{Geometric}(p)$
$$P(X=k) = (1-p)^{k-1}p,\quad k=1,2,3,\ldots$$
$$E[X]=\frac{1}{p},\quad \text{Var}(X)=\frac{1-p}{p^2}$$
- **Memoryless Property**: $P(X > m+n \mid X > m) = P(X > n)$

---

### 2.4 Continuous Distributions

#### Uniform Distribution — $X \sim U(a, b)$
$$f(x) = \frac{1}{b-a},\quad a \leq x \leq b$$
$$F(x) = \frac{x-a}{b-a},\quad a \leq x \leq b$$
$$E[X]=\frac{a+b}{2},\quad \text{Var}(X)=\frac{(b-a)^2}{12}$$

#### Exponential Distribution — $X \sim \text{Exp}(\lambda)$
$$f(x) = \lambda e^{-\lambda x},\quad x \geq 0$$
$$F(x) = 1 - e^{-\lambda x},\quad x \geq 0$$
$$E[X]=\frac{1}{\lambda},\quad \text{Var}(X)=\frac{1}{\lambda^2}$$
- **Memoryless Property**: $P(X > s+t \mid X > s) = P(X > t)$

#### Normal Distribution — $X \sim \mathcal{N}(\mu, \sigma^2)$
$$f(x) = \frac{1}{\sigma\sqrt{2\pi}}\exp\!\left(-\frac{(x-\mu)^2}{2\sigma^2}\right),\quad -\infty < x < \infty$$
$$E[X]=\mu,\quad \text{Var}(X)=\sigma^2$$

- **Standardization**: $Z = \dfrac{X - \mu}{\sigma} \sim \mathcal{N}(0,1)$
- **Standard Normal CDF**: $\Phi(z) = \dfrac{1}{\sqrt{2\pi}}\displaystyle\int_{-\infty}^{z} e^{-t^2/2}\,dt$
- **68-95-99.7 Rule**: $P(\mu \pm \sigma)\approx 68\%$, $P(\mu \pm 2\sigma)\approx 95\%$, $P(\mu \pm 3\sigma)\approx 99.7\%$

---

### 2.8 Expectation, Variance & Inequalities

#### Expectation
$$E[X] = \begin{cases} \displaystyle\sum_x x\,p(x) & \text{(discrete)} \\[6pt] \displaystyle\int_{-\infty}^{\infty} x\,f(x)\,dx & \text{(continuous)} \end{cases}$$

#### Expectation of a Function
$$E[g(X)] = \begin{cases} \displaystyle\sum_x g(x)\,p(x) & \text{(discrete)} \\[6pt] \displaystyle\int_{-\infty}^{\infty} g(x)\,f(x)\,dx & \text{(continuous)} \end{cases}$$

#### Variance
$$\text{Var}(X) = E[(X - \mu)^2] = E[X^2] - (E[X])^2$$
$$\text{SD}(X) = \sqrt{\text{Var}(X)}$$

#### Linearity of Expectation
$$E[aX + b] = aE[X] + b$$
$$\text{Var}(aX + b) = a^2\,\text{Var}(X)$$

#### Moment Generating Function (MGF)
$$M_X(t) = E[e^{tX}],\quad E[X^n] = M_X^{(n)}(0)$$

#### Markov's Inequality
$$P(X \geq a) \leq \frac{E[X]}{a},\quad a > 0,\ X \geq 0$$

#### Chebyshev's Inequality
$$P(|X - \mu| \geq k\sigma) \leq \frac{1}{k^2},\quad k > 0$$
$$P(|X - \mu| \geq \varepsilon) \leq \frac{\text{Var}(X)}{\varepsilon^2}$$

#### Central Limit Theorem (CLT)
Let $X_1, X_2, \ldots, X_n$ be i.i.d. with mean $\mu$ and variance $\sigma^2$. Then:
$$Z_n = \frac{\bar{X}_n - \mu}{\sigma/\sqrt{n}} \xrightarrow{d} \mathcal{N}(0,1) \quad \text{as } n \to \infty$$

#### Weak Law of Large Numbers (WLLN)
$$\bar{X}_n = \frac{1}{n}\sum_{i=1}^n X_i \xrightarrow{P} \mu \quad \text{as } n \to \infty$$
$$\forall\,\varepsilon > 0:\quad P\!\left(|\bar{X}_n - \mu| \geq \varepsilon\right) \to 0$$

#### Strong Law of Large Numbers (SLLN)
$$P\!\left(\lim_{n\to\infty}\bar{X}_n = \mu\right) = 1$$

---

---

## 3. Joint Distributions

### 2.5.1 Joint PMF / PDF

#### Discrete
$$p(x,y) = P(X=x,\, Y=y), \quad \sum_x\sum_y p(x,y) = 1$$

#### Continuous
$$\iint f(x,y)\,dx\,dy = 1,\quad P((X,Y)\in A)=\iint_A f(x,y)\,dx\,dy$$

---

### 2.5.2 Marginal Distributions

$$p_X(x) = \sum_y p(x,y), \qquad f_X(x) = \int_{-\infty}^{\infty} f(x,y)\,dy$$

---

### 2.5.3 Independent Random Variables

$$X \perp Y \iff f(x,y) = f_X(x)\cdot f_Y(y)$$

---

### 3.1 Joint Distribution Functions

$$F(x,y) = P(X \leq x,\, Y \leq y)$$
$$f(x,y) = \frac{\partial^2 F(x,y)}{\partial x\,\partial y}$$

---

### 3.2 Independent Random Variables

$$P(X \leq x,\, Y \leq y) = P(X \leq x)\cdot P(Y \leq y)$$
$$E[g(X)\,h(Y)] = E[g(X)]\cdot E[h(Y)]$$

---

### 3.3 Covariance & Correlation

#### Covariance
$$\text{Cov}(X,Y) = E[(X-\mu_X)(Y-\mu_Y)] = E[XY] - E[X]E[Y]$$

**Properties:**
- $\text{Cov}(X,X) = \text{Var}(X)$
- $\text{Cov}(aX+b,\,cY+d) = ac\,\text{Cov}(X,Y)$
- $\text{Var}(X+Y) = \text{Var}(X) + \text{Var}(Y) + 2\,\text{Cov}(X,Y)$
- $\text{Var}\!\left(\sum_i X_i\right) = \sum_i \text{Var}(X_i) + 2\sum_{i<j}\text{Cov}(X_i,X_j)$

#### Correlation Coefficient
$$\rho(X,Y) = \frac{\text{Cov}(X,Y)}{\sqrt{\text{Var}(X)\cdot\text{Var}(Y)}} = \frac{\text{Cov}(X,Y)}{\sigma_X\,\sigma_Y},\quad -1 \leq \rho \leq 1$$

---

### 3.4 Conditional Expectation

$$E[X \mid Y=y] = \begin{cases} \displaystyle\sum_x x\,\frac{p(x,y)}{p_Y(y)} & \text{(discrete)} \\[8pt] \displaystyle\int_{-\infty}^{\infty} x\,\frac{f(x,y)}{f_Y(y)}\,dx & \text{(continuous)} \end{cases}$$

- **Tower Property (Law of Total Expectation)**:
$$E[X] = E[E[X \mid Y]]$$

- **Law of Total Variance**:
$$\text{Var}(X) = E[\text{Var}(X\mid Y)] + \text{Var}(E[X\mid Y])$$

---

---

## 4. Markov Chains & Information Theory

### 4.1 Stochastic Processes

- **Markov Property**:
$$P(X_{n+1}=j \mid X_n=i,\, X_{n-1},\ldots,X_0) = P(X_{n+1}=j \mid X_n=i)$$

- **Transition Probability**:
$$p_{ij} = P(X_{n+1}=j \mid X_n=i)$$

- **Transition Matrix** $P = [p_{ij}]$ where:
$$p_{ij} \geq 0,\quad \sum_j p_{ij} = 1 \quad (\text{each row sums to 1})$$

---

### 4.2 Chapman–Kolmogorov Equations

- **$n$-step transition probability**:
$$p_{ij}^{(n)} = P(X_{n+m}=j \mid X_m=i)$$

- **Chapman–Kolmogorov**:
$$p_{ij}^{(m+n)} = \sum_{k} p_{ik}^{(m)}\,p_{kj}^{(n)}$$

- **Matrix form**: $P^{(n)} = P^n$ (matrix power)

---

### 4.3 Classification of States

- **Accessible**: state $j$ is accessible from $i$ if $\exists\, n \geq 0 : p_{ij}^{(n)} > 0$
- **Communicating**: $i \leftrightarrow j$ if $i \to j$ and $j \to i$
- **Recurrent** state $i$: $\displaystyle\sum_{n=1}^{\infty} p_{ii}^{(n)} = \infty \iff P(\text{return to }i) = 1$
- **Transient** state $i$: $\displaystyle\sum_{n=1}^{\infty} p_{ii}^{(n)} < \infty \iff P(\text{return to }i) < 1$
- **Period** of state $i$: $d(i) = \gcd\{n \geq 1 : p_{ii}^{(n)} > 0\}$
  - $d(i)=1$: **aperiodic**; $d(i)>1$: **periodic**

---

### 4.4 Limiting & Stationary Probabilities

- **Stationary Distribution** $\boldsymbol{\pi}$:
$$\boldsymbol{\pi} P = \boldsymbol{\pi},\quad \sum_j \pi_j = 1,\quad \pi_j \geq 0$$

- **Balance Equations**:
$$\pi_j = \sum_i \pi_i\, p_{ij},\quad \forall\, j$$

- **Limiting Probability** (ergodic chain):
$$\lim_{n\to\infty} p_{ij}^{(n)} = \pi_j = \frac{1}{m_j}$$

  where $m_j$ is the mean recurrence time of state $j$.

- **Detailed Balance (Reversibility)**:
$$\pi_i\, p_{ij} = \pi_j\, p_{ji},\quad \forall\, i,j$$

---

### 4.5 Random Number Generation

- **Linear Congruential Generator (LCG)**:
$$X_{n+1} = (aX_n + c) \mod m$$
  - $a$: multiplier, $c$: increment, $m$: modulus, $X_0$: seed
  - Generates pseudo-random integers in $[0, m-1]$
  - Normalized: $U_n = X_n / m \in [0,1)$

- **Inverse Transform Method** (generating RV with CDF $F$):
$$X = F^{-1}(U),\quad U \sim U(0,1)$$

- **Acceptance-Rejection Method**: Accept $X$ from $g(x)$ if $U \leq \dfrac{f(x)}{c\,g(x)}$

---

> **Reference:** [1] Sheldon Ross, *Introduction to Probability Models*, Academic Press.
