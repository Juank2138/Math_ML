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
```≤
Now, using Markov's inequality
```math
\mathbb{P}((X-\mathbb{E}[X])^{2}≥\alpha^{2}) ≤ \frac{\mathbb{E}[(X-\mathbb{E}[X])^{2}]}{\alpha^{2}}
```
We define the variance of a continuos random variable as $Var[X]=\mathbb{E}[(X-\mathbb{E}[X])^{2}]$. Then, we obtain Chebyshev's inequality such that
```math
\mathbb{P}((X-\mathbb{E}[X])^{2}≥\alpha^{2}) ≤ \frac{Var[X]}{\alpha^{2}}
```
