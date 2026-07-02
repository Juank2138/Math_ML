# Sample size based in Hoeffding inequality
We must consider Hoeffding's inequality defined such that
```math

```
We know that $E_{in}$ is the model's error on the training data and $E_{out}$ is the model's true error on new data.

We want to determine which parameter is best to control in order to manage the amount of data required for the inequality to hold. As we want to control the required amount of data, $N$. Thus, if we fix:

*   A desired precision $\epsilon$
*   A hypothesis set size $M$
*   A failure probability $\delta$

Then, if we require the failure probability to be at most $\delta$, we have:
```math

```
Solving for $N$, we obtain:
