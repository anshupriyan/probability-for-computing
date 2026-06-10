---
title: "Probability Cheat Sheet: Formulas, Concepts, and Tricks"
date: 2026-06-10
tags:
  - Maths/Probability/Formula-Sheet
  - Maths/Probability/PYQ
summary: "A consolidated master reference of all formulas, core concepts, distributions, proofs, limits, and exam tricks across all PYQs."
---

# Probability Cheat Sheet: Formulas, Concepts, and Tricks

This note is a consolidated, master cheat sheet containing all key formulas, continuous/discrete distributions, integration/derivation tricks, card systems, and conceptual guidelines compiled from **PYQs 1849, 2046, 2466, 2999, and 6917**.

---

## 1. Core Set Theory & Axioms

### A. Set Identities & De Morgan's Laws
* **De Morgan's Laws**:
  $$(A \cup B)' = A' \cap B'$$
  $$(A \cap B)' = A' \cup B'$$
* **Mutually Exclusive Subtraction**:
  If $A$ and $B$ are mutually exclusive, $A \cap B = \varnothing$, which means $A \subseteq B'$ (event $A$ is entirely inside the complement of $B$):
  $$\text{P}(A \cap B') = \text{P}(A)$$

### B. Kolmogorov's Three Axioms of Probability
For any events in sample space $S$:
1. **Axiom of Non-negativity**: $\text{P}(A) \ge 0$ for every event $A$.
2. **Axiom of Certainty (Normalization)**: $\text{P}(S) = 1$.
3. **Axiom of Countable Additivity**: For any sequence of mutually exclusive (disjoint) events $A_1, A_2, \dots$:
   $$\text{P}\left(\bigcup_{i=1}^{\infty} A_i\right) = \sum_{i=1}^{\infty} \text{P}(A_i)$$

---

## 2. Expectation, Variance, & Covariance

### A. Linear Combinations
* **Expected Value Properties**:
  $$\text{E}[c] = c$$
  $$\text{E}[aX + bY + c] = a\text{E}[X] + b\text{E}[Y] + c$$
  $$\text{E}[aX^2 + bY^2] = a\text{E}[X^2] + b\text{E}[Y^2]$$
* **Variance Properties**:
  $$\text{Var}(c) = 0$$
  $$\text{Var}(aX + b) = a^2 \text{Var}(X)$$
  $$\text{Var}(aX + bY) = a^2 \text{Var}(X) + b^2 \text{Var}(Y) + 2ab\,\text{Cov}(X, Y)$$
  * *Note:* If $X$ and $Y$ are independent, $\text{Var}(aX \pm bY) = a^2 \text{Var}(X) + b^2 \text{Var}(Y)$.

### B. Covariance & Bilinearity
* **Definition**:
  $$\text{Cov}(X, Y) = \text{E}[XY] - \text{E}[X]\text{E}[Y]$$
* **Bilinearity Property**:
  $$\text{Cov}\left(\sum_{i} a_i X_i, \sum_{j} b_j Y_j\right) = \sum_{i} \sum_{j} a_i b_j \text{Cov}(X_i, Y_j)$$
  * *Identity:* $\text{Cov}(X, X) = \text{Var}(X)$.
  * *Cauchy-Schwarz Limit:* $|\text{Cov}(X, Y)| \le \sigma_X \sigma_Y$.

### C. Mean vs Variance Relationship for Discrete Distributions
* **Poisson**: $\text{Mean} = \text{Variance} = \lambda$
* **Binomial**: $\text{Mean} > \text{Variance}$ (since $np > npq$ as $q < 1$)
* **Negative Binomial** (failures model): $\text{Mean} < \text{Variance}$ (since $\text{Var}(X) = \frac{rq}{p^2} = \frac{\text{Mean}}{p} > \text{Mean}$ as $p < 1$)

---

## 3. Moment Generating Functions (MGFs)

* **Definition**:
  $$M_X(t) = \text{E}[e^{tX}]$$
* **Linear Shift / Transformation**:
  $$M_{aX + b}(t) = e^{bt} M_X(at)$$
* **MGF of Independent Sum**:
  If $X$ and $Y$ are independent, $M_{X+Y}(t) = M_X(t) \cdot M_Y(t)$.
* **Taylor Series MGF Expansion**:
  $$M_X(t) = 1 + t \text{E}[X] + \frac{t^2}{2!} \text{E}[X^2] + \frac{t^3}{3!} \text{E}[X^3] + \dots$$
* **Normal Distribution MGF Match Trap**:
  If given $M_X(t) = e^{\alpha + \beta t + \gamma t^2}$ for a random variable $X$:
  * $M_X(0) = 1 \implies e^\alpha = 1 \implies \alpha = 0$.
  * Comparing to $e^{\mu t + \frac{1}{2}\sigma^2 t^2} \implies \text{Mean } \mu = \beta$ and $\text{Variance } \sigma^2 = 2\gamma$.

---

## 4. Probability Distributions Master Reference Table

| Distribution | PMF / PDF ($f(x)$) | MGF ($M(t)$) | Mean ($\text{E}[X]$) | Variance ($\text{Var}(X)$) | Key Concepts / Limits |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Discrete Uniform** | $\frac{1}{k}, \quad x \in \{1,\dots,k\}$ | $\frac{e^t(1-e^{kt})}{k(1-e^t)}$ | $\frac{k+1}{2}$ | $\frac{k^2-1}{12}$ | Equiprobable. |
| **Binomial** | $\binom{n}{x}p^x q^{n-x}$ | $(q + pe^t)^n$ | $np$ | $npq$ | $n-X \sim \text{Bin}(n, q)$. |
| **Poisson** | $\frac{e^{-\lambda}\lambda^x}{x!}$ | $e^{\lambda(e^t-1)}$ | $\lambda$ | $\lambda$ | **Limit of Binomial** when $n \to \infty, p \to 0, np = \lambda$. |
| **Geometric** | $q^{x-1}p, \quad x \in \{1,2,\dots\}$ | $\frac{pe^t}{1-qe^t}$ | $\frac{1}{p}$ | $\frac{q}{p^2}$ | Number of trials. **Memoryless**. |
| **Negative Binomial** | $\binom{x-1}{r-1}p^r q^{x-r}$ | $\left(\frac{pe^t}{1-qe^t}\right)^r$ | $\frac{r}{p}$ | $\frac{rq}{p^2}$ | Number of trials until $r$-th success. |
| **Hypergeometric** | $\frac{\binom{M}{x}\binom{N-M}{n-x}}{\binom{N}{n}}$ | (Complex) | $n\frac{M}{N}$ | $n\frac{M}{N}\frac{N-M}{N}\frac{N-n}{N-1}$ | **Without replacement**. Binomial is **with replacement**. |
| **Continuous Uniform** | $\frac{1}{b-a}, \quad x \in [a,b]$ | $\frac{e^{tb}-e^{ta}}{t(b-a)}$ | $\frac{a+b}{2}$ | $\frac{(b-a)^2}{12}$ | Constant density (rectangle). |
| **Exponential** | $\lambda e^{-\lambda x}$ | $\frac{\lambda}{\lambda - t}$ | $\frac{1}{\lambda}$ | $\frac{1}{\lambda^2}$ | CDF $F(x) = 1 - e^{-\lambda x}$. **Memoryless**. |
| **Normal** | $\frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{(x-\mu)^2}{2\sigma^2}}$ | $e^{\mu t + \frac{1}{2}\sigma^2 t^2}$ | $\mu$ | $\sigma^2$ | Standardized $Z = \frac{X-\mu}{\sigma} \sim N(0,1)$. |
| **Beta (1st Kind)** | $\frac{x^{a-1}(1-x)^{b-1}}{\text{B}(a,b)}$ | (Intensive) | $\frac{a}{a+b}$ | $\frac{ab}{(a+b)^2(a+b+1)}$ | Interval $x \in (0, 1)$. |
| **Gamma** | $\frac{1}{\beta^\alpha \Gamma(\alpha)} x^{\alpha-1} e^{-x/\beta}$ | $(1-\beta t)^{-\alpha}$ | $\alpha\beta$ | $\alpha\beta^2$ | General $r$-th moment $\mu'_r = \frac{\beta^r\Gamma(\alpha+r)}{\Gamma(\alpha)}$. |

---

## 5. Limits & Convergence Definitions

* **Convergence in Probability** ($X_n \xrightarrow{p} X$):
  $$\lim_{n \to \infty} \text{P}(|X_n - X| \ge \epsilon) = 0 \quad \text{for any } \epsilon > 0$$
* **Almost Sure Convergence** ($X_n \xrightarrow{a.s.} X$):
  $$\text{P}\left(\left\{\omega \in \Omega \,\,\middle|\,\, \lim_{n \to \infty} X_n(\omega) = X(\omega)\right\}\right) = 1$$
* **Chebyshev's Bounds Evaluation**:
  Use the inequality form $\text{P}(|X - \mu| < k\sigma) \ge 1 - \frac{1}{k^2}$ to solve for the boundary coefficient $k$.

---

## 6. Core Derivation & Calculation Tricks

### Trick 1: Beta Parameter Extraction via Mean and Variance
If given Mean ($\mu$) and Variance ($\sigma^2$), extract parameters $\alpha$ and $\beta$ of the Beta distribution of the 1st kind using:
$$\alpha = \mu \left[ \frac{\mu(1-\mu)}{\sigma^2} - 1 \right] \quad \text{and} \quad \beta = (1-\mu) \left[ \frac{\mu(1-\mu)}{\sigma^2} - 1 \right]$$

### Trick 2: Memoryless Property Algebraic Proof (Geometric)
To show that the Geometric distribution is memoryless:
$$\text{P}(X - k = t \mid X \ge k) = \frac{\text{P}(X = k + t \cap X \ge k)}{\text{P}(X \ge k)} = \frac{\text{P}(X = k + t)}{\text{P}(X \ge k)} = \frac{q^{k+t-1}p}{q^{k-1}} = q^{t-1}p = \text{P}(X = t)$$

### Trick 3: Sum of Squares Factorial Moments for Poisson Variance
When deriving Poisson variance, instead of expanding $\text{E}[X^2]$ directly, calculate the factorial moment $\text{E}[X(X-1)]$ to cancel terms in $x!$ cleanly:
$$\text{E}[X(X-1)] = \sum_{x=2}^{\infty} x(x-1) \frac{e^{-\lambda}\lambda^x}{x!} = \lambda^2 \sum_{y=0}^{\infty} \frac{e^{-\lambda}\lambda^y}{y!} = \lambda^2 \implies \text{Var}(X) = \text{E}[X(X-1)] + \text{E}[X] - \text{E}[X]^2 = \lambda$$
