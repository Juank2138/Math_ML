# KNN
We know that this learning algorithm is instance-based; that is, it does not build a model from the data but instead stores all the data in order to compare the existing information with new information. 
Let us look at how the hypothesis set and the learning algorithm are defined.
## hypothesis set
This set includes all the functions that assign a label to each data point based on the $k$ training samples closest to the point being labeled, using a distance metric.
We have two distinct approaches for the two types of problems we may encounter.
### Classification
Let's look at the form a hypothesis takes. So, we have
```math
h_{D}=mode\{y_{i} | x_{i} \in N_{k}(x)\}
```
where 
* $D$:=set of the training data
* $N_{k}(x)$:=set of the $k$ nearest neighbours to x
* $mode$:=classifies the data using the most frequent labels among its neighbors
Then, hypothesis set for classification problems is:
```math
H=\{h_{D} | h_{D}=mode\{y_{i} | x_{i} \in N_{k}(x)\}\}
```
