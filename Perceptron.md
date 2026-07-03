# Perceptron

The perceptron is the simplest form of an artificial neural network and can be viewed as a linear classifier. Its prediction is based on four components:

- An input vector \(\mathbf{x}\),
- A weight vector \(\mathbf{w}\),
- A bias term \(b\),
- An activation function.

The perceptron computes a linear score
```math
z = \mathbf{w}^\top \mathbf{x} + b
```
and applies an activation function to obtain the final prediction. In the classical perceptron, the activation function is the step function
```math
f(\mathbf{x})=\begin{cases} 1, & \mathbf{w}^\top \mathbf{x}+b ≥ 0,\\ 0, & \mathbf{w}^\top \mathbf{x}+b < 0. \end{cases}
```
The decision boundary is therefore the hyperplane
```math
\mathbf{w}^\top \mathbf{x}+b=0
```

## Perceptron Learning Algorithm
The perceptron learning algorithm updates the weights whenever a training example is misclassified
```text
P ← inputs with label 1
N ← inputs with label 0
Initialize w randomly
while not converged do
    Pick a random sample x from P or N
    if x ∈ P and wᵀx < 0 then
        w ← w + x
    end
    if x ∈ N and wᵀx ≥ 0 then
        w ← w - x
    end
end
```
The algorithm converges when every training example is classified correctly.

## Interpretation of the Update Rule
Let
```math
\mathbf{x}^{(t)}
```
be a misclassified training example at iteration $t$, and let
```math
y^{(t)}\in\{-1,+1\}
```
denote its true label.
The perceptron update rule can be written compactly as
```math
\mathbf{w}^{(t+1)}=\mathbf{w}^{(t)}+y^{(t)}\mathbf{x}^{(t)}.
```

### (a) Misclassified Samples Satisfy
Since the sample is misclassified, the prediction has the opposite sign of the true label. Therefore,
```math
y^{(t)}\mathbf{w}^{(t)\top} \mathbf{x}^{(t)}<0
```
This means that the current weight vector places the sample on the wrong side of the decision boundary.

### (b) The Update Improves Classification
After updating the weights,
```math
\mathbf{w}^{(t+1)}=\mathbf{w}^{(t)}+y^{(t)}\mathbf{x}^{(t)}
```
Multiplying by $y^{(t)}\mathbf{x}^{(t)}$ gives
```math
y^{(t)}\mathbf{w}^{(t+1)\top}\mathbf{x}^{(t)}=y^{(t)}\left(\mathbf{w}^{(t)}+y^{(t)}\mathbf{x}^{(t)}\right)^\top\mathbf{x}^{(t)}
```
Expanding,
```math
y^{(t)}\mathbf{w}^{(t+1)\top}\mathbf{x}^{(t)}=y^{(t)}\mathbf{w}^{(t)\top}\mathbf{x}^{(t)}+y^{(t)2}\mathbf{x}^{(t)\top}\mathbf{x}^{(t)}
```
Since
```math
y^{(t)2}=1
```
we obtain
```math
y^{(t)}\mathbf{w}^{(t+1)\top}\mathbf{x}^{(t)}=y^{(t)}\mathbf{w}^{(t)\top}\mathbf{x}^{(t)}+\|\mathbf{x}^{(t)}\|^2
```
Because
```math
\|\mathbf{x}^{(t)}\|^2>0,
```
it follows that
```math
y^{(t)}\mathbf{w}^{(t+1)\top}\mathbf{x}^{(t)}>y^{(t)}\mathbf{w}^{(t)\top}\mathbf{x}^{(t)}
```

### (c) Moving in the Right Direction
The update increases the signed margin of the misclassified example by exactly
```math
\|\mathbf{x}^{(t)}\|^2
```
Consequently, the updated weight vector moves the decision boundary toward correctly classifying the sample.
Geometrically,

- if a positive sample is classified as negative, the update moves the hyperplane toward the positive class;
- if a negative sample is classified as positive, the update moves the hyperplane toward the negative class.

Thus, the perceptron learning rule always modifies the weights in the direction that improves the classification of the current example, which explains why the update rule is often described as moving the decision boundary in the right direction.
