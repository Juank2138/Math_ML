# Concentration bounds
Concentration bounds are probabilistic inequalities that quantify how likely a random variable is to deviate from a specific expected value. In this file, we explore three fundamental concentration inequalities: Markov's inequality, Chebyshev's inequality, and Hoeffding's inequality. In addition, we discuss the proofs of each of these results and the intuition behind them.
## Markov's inequality
Let X a continuos random variable and we know that its expected value is defined as:
```math
\mathbb{E}[X]=\int_{0}^{\infty} Xf_{X}(X) dX
```
In addition, if we have a constant $\alpha > 0$. Then
```
\mathbb{E}[X]=\int_{0}^{\infty} Xf_{X}(X) dX \gcd \int_{\alpha}^{\infty} Xf_{X}(X) dX
```
