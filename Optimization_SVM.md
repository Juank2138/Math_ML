# Support Vector Machine (SVM)

## What is a Support Vector Machine?

A Support Vector Machine (SVM) is a supervised machine learning algorithm primarily used for binary classification, although it can also be applied to regression problems. Given a set of training samples, the objective of an SVM is to find a linear hyperplane that separates the feature vectors of two classes while maximizing the distance between the hyperplane and the closest training samples.

The intuition behind SVM is that a classifier with a larger margin tends to generalize better to unseen data. Given a training dataset
```math
\mathcal{D}=\{(x_i,y_i)\}_{i=1}^{N}
```
where

- $\(x_i\in\mathbb{R}^d\)$ is the feature vector
- $\(y_i\in\{-1,+1\}\)$ is the class label

the separating hyperplane is defined by
```math
w^Tx+b=0
```
where

- \(w\) is the weight vector
- \(b\) is the bias

A new sample \(x\) is classified according to
```math
\hat{y}=sign(w^Tx+b)
```

# Maximum Margin Principle
Among all separating hyperplanes, the SVM selects the one that maximizes the geometric margin, defined as the minimum distance between the decision boundary and the closest training samples.

The geometric margin is
```math
\gamma=\frac{2}{\|w\|}
```
where \(\|\cdot\|\) denotes the Euclidean norm. Since the margin is inversely proportional to the norm of the weight vector, maximizing the margin is equivalent to minimizing
```math
\|w\|
```
Because the Euclidean norm is always non-negative and the function \(x^2\) is strictly increasing for \(x\ge0\), minimizing \(\|w\|\) is equivalent to minimizing \(\|w\|^2\). Therefore, the optimization problem is commonly written using the squared norm, as it leads to a simpler mathematical formulation while preserving the same optimal solution.

The closest samples to the separating hyperplane are called support vectors since they completely determine the optimal classifier.

# Optimization Problem
Assuming that the training data are perfectly linearly separable (Hard-Margin SVM), the optimization problem is formulated as
```math
\boxed{
\begin{aligned}
\min_{w,b}\quad & \frac12\|w\|^2\\
\text{subject to}\quad &
y_i(w^Tx_i+b)\ge1,
\qquad i=1,\ldots,N
\end{aligned}
}
```
where

- \(w\) is the weight vector
- \(b\) is the bias

The objective minimizes the squared Euclidean norm of the weight vector, which is equivalent to maximizing the geometric margin. The factor \(\frac12\) is included only for mathematical convenience, since it simplifies the derivatives without changing the location of the optimum.

The constraints ensure that every training sample is correctly classified and lies on the correct side of the margin.

# Lagrangian Formulation
The optimization problem is constrained because every training sample must satisfy the classification inequalities. To analyze this problem, the constraints are incorporated into the objective function through the Lagrangian.

The Lagrangian is
```math
L(w,b,\alpha)
=
\frac12\|w\|^2
-
\sum_{i=1}^{N}
\alpha_i
\left(
y_i(w^Tx_i+b)-1
\right)
```
The associated dual function is defined as
```math
g(\alpha)
=
\inf_{w,b}
L(w,b,\alpha)
```
where the infimum is taken over the primal variables \(w\) and \(b\).

The corresponding dual optimization problem is
```math
\max_{\alpha\ge0}
g(\alpha)
```
Rather than solving the original constrained problem directly, the dual formulation provides an equivalent optimization problem whose solution satisfies the same optimality conditions. Moreover, the dual formulation reveals that only a subset of the training samples influences the final classifier.

# Karush-Kuhn-Tucker (KKT) Conditions
The optimal solution must satisfy the Karush-Kuhn-Tucker (KKT) conditions.

### 1. Primal Feasibility
The original constraints must hold
```math
y_i(w^Tx_i+b)\ge1,
\qquad i=1,\ldots,N
```

### 2. Dual Feasibility
The Lagrange multipliers must satisfy
```math
\alpha_i\ge0,
\qquad i=1,\ldots,N
```

### 3. Stationarity
The gradient of the Lagrangian with respect to the primal variables must vanish.

Differentiating with respect to \(w\)
```math
\nabla_wL
=
w-
\sum_{i=1}^{N}
\alpha_i y_i x_i
=0
```
which gives
```math
w=
\sum_{i=1}^{N}
\alpha_i y_i x_i
```
Differentiating with respect to \(b\)
```math
\frac{\partial L}{\partial b}
=
-\sum_{i=1}^{N}
\alpha_i y_i
=0
```
yielding
```math
\sum_{i=1}^{N}\alpha_i y_i=0
```

### 4. Complementary Slackness
Finally
```math
\alpha_i
\left(
y_i(w^Tx_i+b)-1
\right)
=0,
\qquad i=1,\ldots,N
```
This condition implies that only the samples satisfying
```math
y_i(w^Tx_i+b)=1
```
can have nonzero Lagrange multipliers.

These samples are called support vectors since they completely determine the position of the optimal separating hyperplane and, consequently, the final classifier.
