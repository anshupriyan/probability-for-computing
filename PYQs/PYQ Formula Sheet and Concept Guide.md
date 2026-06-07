---
title: "PYQ Formula Sheet and Concept Guide"
date: 2026-06-08
tags:
  - Maths/Probability/Reference
  - Maths/Probability/Formula-Sheet
summary: "Comprehensive formula sheet and concept guide containing all mathematical principles, probability distributions, theorems, and equations used in solving Probability for Computing PYQs (1235, 5816, 4152)."
---

# PYQ Formula Sheet & Concept Guide

This document aggregates all the foundational concepts, definitions, probability distributions, inequalities, theorems, and formulas required to solve the **Probability for Computing** Previous Year Questions (PYQs 1235, 5816, and 4152).

---

## 🟩 Unit 1: Basic Probability

### 1. Sample Space and Set Operations
* **Sample Space ($S$):** The set of all possible outcomes of a random experiment.
  * *Continuous example (car lifetime):* $S = [0, \infty)$.
  * *Discrete example (rolling two dice and taking the sum):* $S = \{2, 3, \dots, 12\}$.
* **Event Set Notation:**
  * Both $E$ and $F$ but not $G$ occur: $E \cap F \cap G'$ (where $G'$ is the complement).
  * At least one of $E, F, G$ occurs: $E \cup F \cup G$.
  * At most two of $E, F, G$ occur: $(E \cap F \cap G)' = E' \cup F' \cup G'$.
  * All three occur: $E \cap F \cap G$.
* **Mutually Exclusive Events:** Events $A$ and $B$ are mutually exclusive if $A \cap B = \emptyset$. 
  * Any event $E$ and its complement $E'$ are always mutually exclusive since $E \cap E' = \emptyset$.

### 2. Conditional Probability & Independence
* **Conditional Probability:** The probability of event $A$ given that event $B$ has occurred.
  $$\text{P}(A \mid B) = \frac{\text{P}(A \cap B)}{\text{P}(B)} \quad \text{for } \text{P}(B) > 0$$
* **Independence:** Two events $A$ and $B$ are independent if and only if:
  $$\text{P}(A \cap B) = \text{P}(A)\text{P}(B)$$
* **Joint Independence:** Events $X$, $Y$, and $Z$ are jointly independent if they are pairwise independent and:
  $$\text{P}(X \cap Y \cap Z) = \text{P}(X)\text{P}(Y)\text{P}(Z)$$

### 3. Law of Total Probability & Bayes' Formula
* **Law of Total Probability:** For a partition of the sample space $A_1, A_2, \dots, A_n$:
  $$\text{P}(B) = \sum_{i=1}^n \text{P}(B \mid A_i)\text{P}(A_i)$$
* **Bayes' Formula:** For finding the posterior probability of a cause $A_i$ given an effect $B$:
  $$\text{P}(A_i \mid B) = \frac{\text{P}(B \mid A_i)\text{P}(A_i)}{\sum_{j=1}^n \text{P}(B \mid A_j)\text{P}(A_j)}$$
  * *Typical Exam Applications:* Target shooting, multiple-choice guessing models, coin-toss/bag selection, factory defective rate source tracing.

---

## 🟦 Unit 2: Random Variables & Standard Distributions

### 1. Cumulative Distribution Function (CDF)
* **Definition:** $F(x) = \text{P}(X \le x)$ for all $x \in \mathbb{R}$.
  * For discrete random variables: $F(x) = \sum_{x_i \le x} p(x_i)$.
  * For continuous random variables: $F(x) = \int_{-\infty}^x f(t) \, dt$.

### 2. Expectation ($\text{E}[X]$) and Variance ($\text{Var}(X)$)
* **Expectation (Mean):**
  * *Discrete:* $\text{E}[X] = \sum_x x \, p(x)$
  * *Continuous:* $\text{E}[X] = \int_{-\infty}^{\infty} x \, f(x) \, dx$
* **Expectation of a Function $g(X)$:**
  * *Discrete:* $\text{E}[g(X)] = \sum_x g(x) \, p(x)$
  * *Continuous:* $\text{E}[g(X)] = \int_{-\infty}^{\infty} g(x) \, f(x) \, dx$
* **Linearity of Expectation (holds whether or not variables are independent):**
  $$\text{E}[aX + b] = a\text{E}[X] + b$$
  $$\text{E}\left[\sum_{i=1}^n X_i\right] = \sum_{i=1}^n \text{E}[X_i]$$
* **Variance:**
  $$\text{Var}(X) = \text{E}[(X - \text{E}[X])^2] = \text{E}[X^2] - (\text{E}[X])^2$$
  * *Properties of Variance:*
    * $\text{Var}(cX) = c^2 \text{Var}(X)$
    * $\text{Var}(c + X) = \text{Var}(X)$

### 3. Key Discrete Distributions

| Distribution | Probability Mass Function (PMF) | Mean ($\text{E}[X]$) | Variance ($\text{Var}(X)$) | Description / Usage |
| :--- | :--- | :---: | :---: | :--- |
| **Binomial** | $p(k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k \in \{0, \dots, n\}$ | $np$ | $np(1-p)$ | Number of successes in $n$ independent trials. |
| **Poisson** | $p(k) = \frac{e^{-\lambda} \lambda^k}{k!}, \quad k \in \{0, 1, 2, \dots\}$ | $\lambda$ | $\lambda$ | Counts of rare, independent events over intervals. |
| **Geometric** | $p(k) = (1-p)^{k-1} p, \quad k \in \{1, 2, \dots\}$ | $\frac{1}{p}$ | $\frac{1-p}{p^2}$ | Number of trials until the first success. |

### 4. Key Continuous Distributions

| Distribution | Probability Density Function (PDF) | Cumulative Distribution Function (CDF) | Mean ($\text{E}[X]$) | Description / Usage |
| :--- | :--- | :--- | :---: | :--- |
| **Uniform** | $f(x) = \frac{1}{\beta - \alpha}, \quad x \in (\alpha, \beta)$ | $F(x) = \begin{cases} 0 & x < \alpha \\ \frac{x-\alpha}{\beta-\alpha} & \alpha \le x \le \beta \\ 1 & x > \beta \end{cases}$ | $\frac{\alpha + \beta}{2}$ | Equally likely values within a finite interval. |
| **Normal** | $f(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2}$ | $F(x) = \Phi\left(\frac{x-\mu}{\sigma}\right)$ | $\mu$ | Symmetric, bell-shaped distribution. |

---

## 🟨 Unit 3: Joint Distributions & Conditioning

### 1. Continuous Joint Densities & Normalization
* **Normalization Condition:** The volume under any joint density function must equal $1$.
  $$\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(x, y) \, dx \, dy = 1$$
* **Marginal Densities:**
  $$f_X(x) = \int_{-\infty}^{\infty} f(x, y) \, dy, \quad f_Y(y) = \int_{-\infty}^{\infty} f(x, y) \, dx$$

### 2. Covariance and Sums
* **Covariance Definition:**
  $$\text{Cov}(X, Y) = \text{E}[(X - \text{E}[X])(Y - \text{E}[Y])] = \text{E}[XY] - \text{E}[X]\text{E}[Y]$$
* **Properties of Covariance:**
  * $\text{Cov}(X, Y) = \text{Cov}(Y, X)$
  * $\text{Cov}(X, X) = \text{Var}(X)$
  * $\text{Cov}(aX + b, cY + d) = ac\,\text{Cov}(X, Y)$
  * If $X$ and $Y$ are independent, then $\text{Cov}(X, Y) = 0$ (the converse is not generally true).
* **Variance of Sums:**
  $$\text{Var}(X+Y) = \text{Var}(X) + \text{Var}(Y) + 2\,\text{Cov}(X, Y)$$

### 3. Conditional Expectation and Variance by Conditioning
* **Conditional Density:**
  $$f_{X \mid Y}(x \mid y) = \frac{f(x, y)}{f_Y(y)}$$
* **Conditional Expectation:**
  $$\text{E}[X \mid Y = y] = \int_{-\infty}^{\infty} x \, f_{X \mid Y}(x \mid y) \, dx$$
* **Law of Total Expectation (Adam's Law):**
  $$\text{E}[X] = \text{E}[\text{E}[X \mid Y]]$$
  * *For discrete cases:* $\text{E}[X] = \sum_y \text{E}[X \mid Y=y] \text{P}(Y=y)$.
  * *Typical Application:* Trapped miner door problem, expected number of typos based on book selection.
* **Law of Total Variance (Eve's Law):**
  $$\text{Var}(X) = \text{E}[\text{Var}(X \mid Y)] + \text{Var}(\text{E}[X \mid Y])$$

---

## 🟪 Unit 4: Limit Theorems, Inequalities & Simulation

### 1. Probability Bounds
* **Markov's Inequality:** For any non-negative random variable $X$ and a constant $a > 0$:
  $$\text{P}(X \ge a) \le \frac{\text{E}[X]}{a}$$
* **Chebyshev's Inequality:** For any random variable $X$ with mean $\mu$ and variance $\sigma^2$, and any $k > 0$:
  $$\text{P}(|X - \mu| \ge k) \le \frac{\sigma^2}{k^2}$$
  * *Proof Technique:* Apply Markov's Inequality to the non-negative variable $Y = (X - \mu)^2$ with threshold $a = k^2$.

### 2. Limit Theorems & Approximations
* **Central Limit Theorem (CLT):** If $X_1, X_2, \dots, X_n$ are i.i.d. with mean $\mu$ and finite variance $\sigma^2$, then the standardized sample mean converges in distribution to the standard normal distribution $N(0, 1)$ as $n \to \infty$:
  $$Z_n = \frac{\bar{X}_n - \mu}{\sigma / \sqrt{n}} \xrightarrow{d} N(0, 1)$$
* **Normal Approximation to the Binomial (with Continuity Correction):**
  If $X \sim \text{Binomial}(n, p)$, we approximate it using $Y \sim N(np, np(1-p))$:
  $$\text{P}(X = k) \approx \text{P}\left(k - 0.5 \le Y \le k + 0.5\right) = \Phi\left(\frac{k + 0.5 - np}{\sqrt{np(1-p)}}\right) - \Phi\left(\frac{k - 0.5 - np}{\sqrt{np(1-p)}}\right)$$
* **Poisson Approximation to the Binomial:**
  If $n$ is large and $p$ is small, $X \sim \text{Binomial}(n, p)$ can be approximated by a Poisson variable with parameter $\lambda = np$.

---

## 🔴 Unit 5: Markov Chains & Simulation

### 1. Transition Probabilities & Chapman-Kolmogorov
* **One-Step Transition Probability:** $P_{ij} = \text{P}(X_{n+1} = j \mid X_n = i)$.
* **Chapman-Kolmogorov Equations:** Used to compute $n$-step transition probabilities:
  $$P_{ij}^{(n+m)} = \sum_{k} P_{ik}^{(n)} P_{kj}^{(m)}$$
  In matrix form, the $n$-step transition matrix is the $n$-th power of the 1-step transition matrix:
  $$P^{(n)} = P^n$$

### 2. Classification of States
* **Accessibility and Communication:**
  * State $j$ is accessible from state $i$ ($i \to j$) if $P_{ij}^{(n)} > 0$ for some $n \ge 0$.
  * States $i$ and $j$ communicate ($i \leftrightarrow j$) if they are mutually accessible.
* **Absorbing State:** State $i$ is absorbing if $P_{ii} = 1$.
* **Irreducible Markov Chain:** A chain is irreducible if there is only one communicating class (all states communicate with each other).
* **Recurrence vs. Transience:** Let $f_i$ be the probability of ever returning to state $i$:
  * **Recurrent State:** $f_i = 1$ (equivalent to $\sum_{n=1}^{\infty} P_{ii}^{(n)} = \infty$).
  * **Transient State:** $f_i < 1$ (equivalent to $\sum_{n=1}^{\infty} P_{ii}^{(n)} < \infty$).

### 3. Limiting Probabilities
For an irreducible, ergodic Markov chain, the limiting (stationary) probabilities $\pi_j = \lim_{n \to \infty} P_{ij}^{(n)}$ exist and are independent of the initial state. They are found by solving the system:
$$\pi = \pi P \quad \text{and} \quad \sum_{j} \pi_j = 1$$

### 4. Random Number Generation
* **Linear Congruential Generator (LCG):**
  Generates a deterministic sequence of pseudo-random numbers using a seed value $X_0$:
  $$X_{n+1} = (aX_n + c) \pmod m$$
  Where:
  * $X_0$ is the seed.
  * $a$ is the multiplier.
  * $c$ is the increment.
  * $m$ is the modulus.
  * The numbers are scaled to $(0,1)$ using $U_n = \frac{X_n}{m}$.
