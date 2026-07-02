# Concentration bounds
Concentration bounds are probabilistic inequalities that quantify how likely a random variable is to deviate from a specific expected value. In this file, we explore three fundamental concentration inequalities: Markov's inequality, Chebyshev's inequality, and Hoeffding's inequality. In addition, we discuss the proofs of each of these results and the intuition behind them.
## Markov's inequality
Let $X$ a continuos random variable and we know that its expected value is defined as:
```math
\mathbb{E}[X]=\int_{0}^{\infty} Xf_{X}(X) dX
```
In addition, if we have a constant $\alpha > 0$. Then
```math
\mathbb{E}[X]=\int_{0}^{\infty} Xf_{X}(X) dX ≥ \int_{\alpha}^{\infty} Xf_{X}(X) dX
```
We observe that if we fix $X$ as $X≥\alpha$, then we always get the following inequality
```math
\mathbb{E}[X] ≥ \int_{\alpha}^{\infty} \alpha f_{X}(X) dX
```
We can write the last inequality as:
```math
\mathbb{E}[X] ≥ \int_{\alpha}^{\infty} \alpha f_{X}(X) dX = \alpha \int_{\alpha}^{\infty} f_{X}(X) dX = \alpha \mathbb{P}(X>=\alpha)
```
Finally, we obtain Markov's inequality:
```math
\frac{\mathbb{E}[X]}{\alpha} ≥ \mathbb{P}(X≥\alpha)
```
## Chebyshev's inequality
Let $X$ a continuos random variable and Markov's inequality such that:
```math
\frac{\mathbb{E}[X]}{\alpha} ≥ \mathbb{P}(X≥\alpha)
```
If we have the inequality $\mathbb{P}(X≥\alpha)$, then $\mathbb{P}(X^{2}≥\alpha^{2})$ holds. Moreover, given that $X$ is a continuous random variable, we know that $X-\mathbb{E}[X]$ is one as well.
Taking the preceding statements into account, we can define the next probability such that:
```math
\mathbb{P}((X-\mathbb{E}[X])^{2}≥\alpha^{2})
```
Now, using Markov's inequality
```math
\mathbb{P}((X-\mathbb{E}[X])^{2}≥\alpha^{2}) ≤ \frac{\mathbb{E}[(X-\mathbb{E}[X])^{2}]}{\alpha^{2}}
```
We define the variance of a continuos random variable as $Var[X]=\mathbb{E}[(X-\mathbb{E}[X])^{2}]$. Then, we obtain Chebyshev's inequality such that
```math
\mathbb{P}(|(X-\mathbb{E}[X])|≥\alpha) ≤ \frac{Var[X]}{\alpha^{2}}
```
## Hoeffding's inequality
Let $(X_1, X_2, \dots, X_n)$ be independent random variables satisfying $a_i \leq X_i \leq b_i$,
and define 
```math
\mu_i = \mathbb{E}[X_i].
```
Our goal is to bound the probability
```math
\mathbb{P}\left(\sum_{i=1}^{n}(X_i-\mu_i) ≥ t\right).
```
For any (\lambda > 0)
```math
\mathbb{P}\left(\sum_{i=1}^{n}(X_i-\mu_i)≥ t\right)=\mathbb{P}\left(e^{\lambda\sum_{i=1}^{n}(X_i-\mu_i)}≥ e^{\lambda t}\right).
```
Applying Markov's inequality to the exponential yields
```math
\mathbb{P}(\sum_{i=1}^{n}(X_i-\mu_i)≥ t)≤e^{-\lambda t}\mathbb{E}[e^{\lambda\sum_{i=1}^{n}(X_i-\mu_i)}]
```
Step 2: Use independence

Since the random variables are independent,

\mathbb{E}\left[
e^{\lambda\sum_{i=1}^{n}(X_i-\mu_i)}
\right]
=
\prod_{i=1}^{n}
\mathbb{E}\left[
e^{\lambda(X_i-\mu_i)}
\right].

Hence,

\mathbb{P}\left(\sum_{i=1}^{n}(X_i-\mu_i)\geq t\right)
\leq
e^{-\lambda t}
\prod_{i=1}^{n}
\mathbb{E}\left[
e^{\lambda(X_i-\mu_i)}
\right].
Step 3: Apply Hoeffding's lemma

Hoeffding's lemma states that if a random variable (X) satisfies

a \leq X \leq b,

then

\mathbb{E}\left[e^{\lambda(X-\mathbb{E}[X])}\right]
\leq
\exp\left(
\frac{\lambda^2(b-a)^2}{8}
\right).

Applying the lemma to each (X_i),

\mathbb{E}\left[
e^{\lambda(X_i-\mu_i)}
\right]
\leq
\exp\left(
\frac{\lambda^2(b_i-a_i)^2}{8}
\right).

Therefore,

\prod_{i=1}^{n}
\mathbb{E}\left[
e^{\lambda(X_i-\mu_i)}
\right]
\leq
\exp\left(
\frac{\lambda^2}{8}
\sum_{i=1}^{n}(b_i-a_i)^2
\right).

Substituting into the previous inequality gives

\mathbb{P}\left(\sum_{i=1}^{n}(X_i-\mu_i)\geq t\right)
\leq
\exp\left(
-\lambda t
+
\frac{\lambda^2}{8}
\sum_{i=1}^{n}(b_i-a_i)^2
\right).
Step 4: Optimize with respect to (\lambda)

Define

S = \sum_{i=1}^{n}(b_i-a_i)^2.

We minimize the exponent

f(\lambda)
=
-\lambda t
+
\frac{\lambda^2 S}{8}.

Differentiating with respect to (\lambda),

f'(\lambda)
=
-t
+
\frac{\lambda S}{4}.

Setting the derivative equal to zero,

\lambda^\star
=
\frac{4t}{S}.

Substituting this value into the exponent,

f(\lambda^\star)
=
-\frac{2t^2}{S}.

Therefore,

\mathbb{P}\left(
\sum_{i=1}^{n}(X_i-\mu_i)
\geq t
\right)
\leq
\exp\left(
-\frac{2t^2}
{\sum_{i=1}^{n}(b_i-a_i)^2}
\right).

This is the one-sided version of Hoeffding's inequality.

Two-sided Hoeffding inequality

Applying the same argument to (-X_i) gives

\mathbb{P}\left(
\sum_{i=1}^{n}(X_i-\mu_i)
\leq -t
\right)
\leq
\exp\left(
-\frac{2t^2}
{\sum_{i=1}^{n}(b_i-a_i)^2}
\right).

Using the union bound, we obtain

\mathbb{P}\left(
\left|
\sum_{i=1}^{n}(X_i-\mu_i)
\right|
\geq t
\right)
\leq
2\exp\left(
-\frac{2t^2}
{\sum_{i=1}^{n}(b_i-a_i)^2}
\right).

which is the classical two-sided Hoeffding inequality.
