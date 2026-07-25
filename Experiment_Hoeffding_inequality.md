# Hoeffding's inequality
The main idea behind the following experiment is to show that Hoeffding's inequality does not hold in certain cases. However, before describing the experiment, we must recall Hoeffding's inequality
```math
  \mathbb{P}(|\nu-\mu| ≥ \epsilon) ≤ 2e^{-2N\epsilon^{2}}
```
where
* $\nu$ is the empirical mean 
* $\mu$ is the expected mean of the variale
* $N$ is the number of independent observations
* $\epsilon$ is the maximum allowed deviation between the empirical and expected means

In addition, this inequality holds only when certain assumptions are met, including that the random variable being analyzed is fixed before the observations are made.

## Description of the experiment
The experiment consists of repeatedly flipping a large number of fair coins and comparing the empirical frequencies of three different coins. 
The procedure is as follows:
1. Consider 1,000 fair coins
2. Flip each coin 10 independent times
3. From the 1,000 coins, select the following three coins:
- $C_1:$ the first coin
- $C_{rand}:$ a coin selected uniformly at random
- $C_{min}:$ the coin with the smallest fraction of heads (if several coins tie, choose the first one)
4. For each selected coin, compute the fraction of heads where $\nu$ represents the empirical probability of obtaining heads
  
```math
  \nu=\frac{\text{Number of Heads}}{10}
```

According to the experiment, we have to answer the next points

### (a) What is $\mu$ for the three coins selected?
Since all 1,000 coins are assumed to be fair, the probability of obtaining heads is
```math
  \mu=\mathbb{P}(\text{heads})=0.5
```
Therefore, the expected value is the same for all three coins

### (b) Perform the experiment independently 100,000 times
We can define $\nu$ for each coin in the experiment such that
* $\nu_{1}$ of the coin $C_1$
* $\nu_{rand}$ of the coin $C_{rand}$
* $\nu_{min}$ of the coin $C_{min}$

we use the following code to simulate the experiment and find the results
```python
import numpy as np
import matplotlib.pyplot as plt

#parameters
num_coins = 1000 #number of coins
num_flips = 10 #number of flips per coin
num_exp = 100000 #number of independent experiments

#variables to store empirical mean
v1 = []
vrand = []
vmin = []

#experiment
for _ in range(num_exp):
    #simulate the coin flips
    #1 = Heads
    #0 = Tails
    flips = np.random.randint(0, 2, size=(num_coins, num_flips))

    # Number of heads obtained by each coin
    heads = np.sum(flips, axis=1)

    # Fraction of heads for every coin
    frequencies = heads / num_flips

    # First coin
    v1.append(frequencies[0])

    # Randomly selected coin
    random_index = np.random.randint(num_coins)
    vrand.append(frequencies[random_index])

    # Coin with the minimum fraction of heads
    vmin.append(np.min(frequencies))

v1 = np.array(v1)
vrand = np.array(vrand)
vmin = np.array(vmin)

#plot histograms
bins = np.arange(-0.05, 1.15, 0.1)
fig, axes = plt.subplots(1, 3, figsize=(16, 5))

#first coin
axes[0].hist(v1, bins=bins, edgecolor='black')
axes[0].set_title(r'First Coin ($\nu_1$)')
axes[0].set_xlabel('Fraction of Heads')
axes[0].set_ylabel('Frequency')
axes[0].set_xlim(0, 1)

#random coin
axes[1].hist(vrand, bins=bins, edgecolor='black')
axes[1].set_title(r'Random Coin ($\nu_{rand}$)')
axes[1].set_xlabel('Fraction of Heads')
axes[1].set_ylabel('Frequency')
axes[1].set_xlim(0, 1)

#minimum coin
axes[2].hist(vmin, bins=bins, edgecolor='black')
axes[2].set_title(r'Minimum Coin ($\nu_{min}$)')
axes[2].set_xlabel('Fraction of Heads')
axes[2].set_ylabel('Frequency')
axes[2].set_xlim(0, 1)

plt.tight_layout()
plt.show()

#summary statistics
print("Average fraction of heads:")
print(f"First coin   : {np.mean(v1):.4f}")
print(f"Random coin  : {np.mean(vrand):.4f}")
print(f"Minimum coin : {np.mean(vmin):.4f}")
```
If we run it, we get the values of the empirical risk of each coin and its histograms of distributions. Let's see the results of the experiment  
<p align="center">
  <img width="829" height="305" alt="resultados" src="https://github.com/user-attachments/assets/4f5b02fb-7d3b-45dc-8d6a-794d7e0dc7ec" />
</p>
