# Effective separator lines for 2 labels
We define effective binary separating lines as all possible hyperplanes that classify data using two labels. For example, if we have two data points arranged as follows,
<p align="center">
  <img width="254" height="255" alt="puntos2" src="https://github.com/user-attachments/assets/2af87fe0-6700-479a-97f9-f773dc408ccb" />
</p>
then there are four effective binary separating lines, as shown below.
<p align="center">
  <img width="22%" alt="punto2_sep1" src="https://github.com/user-attachments/assets/99714604-2335-463a-b930-5ac0dc48051b" />
  <img width="22%" alt="punto2_sep2" src="https://github.com/user-attachments/assets/0f7ad21a-6e14-4ac4-8dfc-674c58026b64" />
  <img width="22%" alt="punto2_sep3" src="https://github.com/user-attachments/assets/9b9bae0f-0c56-45ef-a85f-8f6d153877df" />
  <img width="22%" alt="puntos2_sep5" src="https://github.com/user-attachments/assets/988dcc0b-3e80-477d-808e-fb826f102e47" />
</p>
Notice that circles and squares represent different labels, while dashed lines represent hyperplanes that classify the data.

## General Form of a Hyperplane
In $\mathbb{R}^2$, a separating hyperplane can be written as
```math
w^T x + b = 0
```
where
```math
w =\begin{bmatrix}w_1\\w_2\end{bmatrix}\neq 0, \qquad b \in \mathbb{R}.
```
This hyperplane partitions the space into two half-spaces:
```math
w^T x + b > 0 \qquad \text{(label +1)}
```
and
```math
w^T x + b < 0 \qquad \text{(label -1)}
```
## Key Observations
* There are infinitely many effective separating lines, not only four.
* The four separators shown above are only representative examples.
* Any hyperplane that places the two points on opposite sides correctly classifies the data.
* In higher dimensions, separating boundaries are hyperplanes of dimension \(d-1\) in \(\mathbb{R}^d\).
When the data is linearly separable, there are infinitely many hyperplanes that classify very well. Effective binary separating lines partition the input space into two regions, assigning each region to one of the two labels.
In other case, if we have 5 points distributed as follows
<p align="center">
  <img width="330" height="292" alt="puntos5" src="https://github.com/user-attachments/assets/6de8e767-b056-4252-8d22-4178e23b6536" />
</p>
