# Entropy in data science
We must bear in mind that the formulation of data entropy takes the following form:
```math
H(X) = - \sum_{i=1}^{n} \mathbb{P}(X=i) \log_2 \mathbb{P}(X=i)
```
But let's look at the explanation of the previous equation.
## Amount of information related to an event
Let X any event with probability $\mathbb{P}(X)$, we define the amount of the information of X as:
```math
I(X)=\log_2 (\frac{1}{\mathbb{P}(X)})=-\log_2 \mathbb{P}(X)
```
Now, the two following questions naturally arise:
1. What is the role of $log_2$?
2. Why is $\mathbb{P}(X)$ used?

Let's see the answers
### Role of $log_2$?
