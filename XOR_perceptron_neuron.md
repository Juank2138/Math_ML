# Modeling XOR with Perceptrons
In the first place, it is necessary to understand how the XOR logic gate works. Then, We are going to explain what the network architecture of the logic gate might look like. Finally, we model XOR using perceptrons.

## What is the XOR Function?
The XOR logic gate outputs **1** if and only if its two inputs are different.

### Truth Table
| x₁ | x₂ | XOR |
|:--:|:--:|:---:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

The logical expression of XOR can be seen as
```math
XOR(x_1,x_2)= (x_1 \land \neg x_2)\lor(\neg x_1\land x_2)
```

## Why Can't a Single Perceptron Solve XOR?
A perceptron computes
```math
y=f(w_1x_1+w_2x_2+b)
```
where

- $w_1,w_2$ are the weights
- $b$ is the bias
- $f(\cdot)$ is the step activation function

A single perceptron creates only a linear decision boundary, while the XOR function is not linearly separable. Therefore, a single perceptron cannot correctly classify all XOR inputs. To model XOR, a multilayer perceptron with one hidden layer is required.

## XOR Network Architecture
The network consists of

- Two input neurons
- Two hidden perceptrons
- One output perceptron

```
           x1 -----------\
                           \
                            > H1 ----\
                           /          \
           x2 -----------/            \
                                        > Output
           x1 -----------\            /
                           \          /
                            > H2 ----/
                           /
           x2 -----------/
```

### Hidden Perceptron 1
The first hidden neuron computes
```math
H_1=x_1\land\neg x_2
```
Weights and bias:

- w_1=1
- w_2=-1
- b=-0.5


Its output is
```math
H_1=f(x_1-x_2-0.5)
```

#### Verification

| x₁ | x₂ | z | H₁ |
|:--:|:--:|:--:|:--:|
|0|0|-0.5|0|
|0|1|-1.5|0|
|1|0|0.5|1|
|1|1|-0.5|0|

# Hidden Perceptron 2
The second hidden neuron computes
```math
H_2=\neg x_1\land x_2
```
Weights and bias:


-w_1=-1
-w_2=1
-b=-0.5


Its output is
```math
H_2=f(-x_1+x_2-0.5)
```

#### Verification

| x₁ | x₂ | z | H₂ |
|:--:|:--:|:--:|:--:|
|0|0|-0.5|0|
|0|1|0.5|1|
|1|0|-1.5|0|
|1|1|-0.5|0|

# Output Perceptron
The output neuron performs the logical OR of the hidden neurons,
```math
XOR = H_1 \lor H_2
```
Weights and bias:


-w_1=1
-w_2=1
-b=-0.5


The output is computed as
```math
y=f(H_1+H_2-0.5)
```

# Complete Verification

| x₁ | x₂ | H₁ | H₂ | Output |
|:--:|:--:|:--:|:--:|:------:|
|0|0|0|0|0|
|0|1|0|1|1|
|1|0|1|0|1|
|1|1|0|0|0|

The final output exactly matches the XOR truth table.
