# Probability Foundations Part 3

## Sampling Distributions and Limits

This folder documents the third completed part of my probability foundations review. It focuses on how statistics behave across repeated samples and how their sampling distributions can be understood through finite-sample calculations, limit theorems, and simulation.

The goal of this part is to connect probability theory to statistical inference: understanding why sample averages stabilize, how their uncertainty can be quantified, how the Central Limit Theorem provides useful approximations, and how the same ideas lead naturally to Monte Carlo methods.

## What to Open

This part contains two complementary notebooks:


Start with the main notebook:

[`Sampling_distributions_and_limits.ipynb`](./Sampling_distributions_and_limits.ipynb)
- **Main learning notebook:** the structured notes for Chapter 4, including definitions, derivations, conceptual explanations, interpretations, and the main mathematical results.

[`Computer_exercises.ipynb`](./Computer_exercises.ipynb)
- **Computer exercises notebook:** implementations of representative textbook exercises, with explanations of the core idea demonstrated by each simulation and what the numerical results illustrate.

The main notebook contains the substantive mathematical explanations and learning notes, while the computer-exercise notebook provides the practical simulation and implementation work.

## Topics Included

### Chapter 4: Sampling Distributions and Limits

- Sampling distributions of statistics
- Convergence in probability and the Weak Law of Large Numbers
- Almost-sure convergence and the Strong Law of Large Numbers
- Convergence in distribution
- Central Limit Theorem
- Standard deviation and standard error
- Monte Carlo approximation
- Normal Distribution Theory

## Main Takeaways

A central idea in this part was that a **statistic computed from random data is itself a random variable**. If

```math
T = h(X_1,\ldots,X_n),
```

then repeated samples produce different values of $T$, and the distribution of those possible values is its **sampling distribution**.

For the sample mean

```math
M_n = \frac{1}{n}\sum_{i=1}^{n} X_i,
```

the Laws of Large Numbers explain why $M_n$ becomes increasingly close to the population mean $\mu$ as the sample size grows. The Weak Law describes this through convergence in probability, while the Strong Law gives the stronger almost-sure convergence result.

The Central Limit Theorem adds another layer. The LLN tells us that the error $M_n-\mu$ becomes small, while the CLT describes the distribution of that error on its natural scale. In distribution,

```math
\frac{\sqrt{n}(M_n-\mu)}{\sigma}
\;\to\;
N(0,1).
```

Thus, for large $n$, the sampling distribution of the sample mean is approximately normal with standard deviation $\sigma/\sqrt{n}$.

This also clarified the distinction between **standard deviation** and **standard error**. Standard deviation describes the spread of a random variable or population, whereas standard error describes the spread of an estimator across repeated samples. For the sample mean,

```math
SE(M_n) = \frac{\sigma}{\sqrt{n}}.
```

Monte Carlo approximation showed that the same convergence theory can be used computationally. If a quantity can be expressed as an expectation, independent simulated values can be averaged to approximate it. This allows randomness to be used to estimate difficult integrals, sums, probabilities, and sampling distributions.

An especially useful connection appeared when approximating a CDF. Since

```math
F_Y(y)
=
P(Y \le y)
=
E[I(Y \le y)],
```

the indicator $I(Y\le y)$ is a Bernoulli random variable whose success probability is exactly $F_Y(y)$. Therefore, estimating a CDF by repeated simulation becomes a Bernoulli sample-mean problem. This is also why the Bernoulli standard-error formula naturally appears in the Monte Carlo error estimate.

The notation in this setting is worth separating carefully: $n$ is the size of the original sample used to construct one value of the statistic, while $N$ is the number of Monte Carlo replications used to approximate its sampling distribution.

Normal distribution theory then provides several exact sampling results. Linear combinations of independent normal random variables remain normal, and for a normal sample the sample mean is exactly normal rather than only approximately normal through the CLT.

The chi-squared, $t$, and $F$ distributions arise naturally from normal random variables and become important building blocks for statistical inference. In particular, for a normal sample,

```math
\frac{(n-1)S^2}{\sigma^2}
\sim
\chi^2(n-1),
```

and $S^2$ is independent of the sample mean. This also connects to why the usual sample variance divides by $n-1$: it makes $S^2$ an unbiased estimator of $\sigma^2$.

## Implementation Work Completed

The computer-exercise notebook uses simulation to reinforce the theory through representative exercises from Sections 4.1–4.5, including:

- generating empirical sampling distributions of statistics;
- estimating their means and standard deviations;
- demonstrating convergence in probability with repeated samples;
- plotting running sample means to visualize almost-sure convergence;
- comparing simulated probabilities with CLT approximations;
- examining the finite-sample shape of sampling distributions;
- using Monte Carlo methods for numerical integration;
- approximating an infinite sum by simulation;
- estimating probabilities through indicator variables.

Each exercise is accompanied by notes explaining the concept it represents and what its result is intended to demonstrate.

## Connections to Later Topics

Several ideas from this part may be involved in later statistics and machine-learning topics:

- **Statistical Inference:** sampling distributions and standard errors provide the basis for reasoning about estimator uncertainty.
- **Maximum Likelihood Estimation:** consistency and asymptotic normality rely on the same convergence ideas developed here.
- **Bayesian Inference:** Monte Carlo methods later become important when expectations or posterior distributions cannot be handled analytically.
- **Stochastic Gradient Descent:** mini-batch gradients are random sample-based estimates of population quantities, making variance and sample-size effects directly relevant.
- **Machine Learning Evaluation:** empirical averages approximate expected performance, while sampling variability determines how stable those estimates are.
- **Modern Probabilistic Computation:** Monte Carlo methods generalize into major computational techniques for approximating otherwise intractable quantities.
