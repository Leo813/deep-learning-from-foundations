# Probability Foundations Part 2

## Expectations

This folder documents the second completed part of my probability foundations review. It focuses on expectation and the quantities built from it, including variance, covariance, correlation, moments, generating functions, and conditional expectation.

The goal of this part is to understand how probability distributions can be summarized, transformed, and conditioned, and to build the tools needed for later work on sampling distributions, limit theorems, statistical inference, machine learning, and deep learning.

## What to Open

Start with the main notebook:

[`expectations.ipynb`](./expectations.ipynb)

The notebook contains the structured notes for this part, including definitions, derivations, examples, conceptual explanations, and small Python experiments.

## Topics Included

### Chapter 3: Expectations

- Expected value for discrete and absolutely continuous random variables
- Expectation of functions of random variables (LOTUS)
- Linearity and monotonicity of expectation
- Variance and standard deviation
- Covariance and correlation
- Probability-generating functions
- Moment-generating functions
- Characteristic functions
- Conditional expectation
- Conditional variance
- General expectation
- Expected loss and conditional expectation in prediction

## Main Takeaways

The central idea in this part was that **expectation is a probability-weighted average**. It provides a way to summarize a random variable and also serves as the foundation for many other quantities in probability.

Expectation becomes especially useful when applied to functions of random variables. Instead of only considering `E[X]`, we can study quantities such as `E[X^2]`, expected losses, or other transformations without first deriving a new distribution for every transformed variable.

A second major idea was distinguishing different ways of describing variability and relationships:

- **Variance** measures how far a random variable tends to spread around its mean.
- **Covariance** measures how two variables vary together on their original scales.
- **Correlation** normalizes covariance to describe linear association on a scale from `-1` to `1`.
- Independence implies zero covariance, but zero covariance does not generally imply independence.

The variance of a sum also showed why dependence matters:

```math
\mathrm{Var}\left(\sum_i X_i\right)
=
\sum_i \mathrm{Var}(X_i)
+
2\sum_{i<j}\mathrm{Cov}(X_i,X_j).
```

For independent random variables, the covariance terms vanish, so their variances add. This result becomes especially important when working with sums and sample means.

Generating functions provide another way to represent information about distributions. Probability-generating functions encode the probabilities of nonnegative integer-valued random variables, moment-generating functions generate raw moments through differentiation, and characteristic functions retain similar transform properties even when an MGF does not exist.

Conditional expectation introduced the idea that an expected value can change when additional information is observed. In particular,

```math
E[X\mid Y]
```

is itself a random variable because its value depends on `Y`. The laws of total expectation and total variance show how unconditional quantities can be decomposed through conditional structure.

The St. Petersburg paradox also clarified that a mathematically defined expected monetary payoff is not automatically the same as a practical or subjective value. Its infinite expectation comes from infinitely many payoff levels whose increasing rewards exactly offset their decreasing probabilities.

## Implementation Work Completed

The notebook includes small Python examples for:

- discrete expectations and second moments;
- expectations of transformed normal random variables;
- expected ReLU activations;
- nonlinear dependence with approximately zero covariance and correlation;
- bivariate normal samples with different correlation values;
- numerical checks of the law of total expectation;
- numerical checks of the law of total variance;
- the tail-integral formula for an exponential distribution;
- convergence of Bernoulli sample means toward the theoretical expectation;
- comparison of population risk and empirical risk;
- conditional expectation as a predictor under squared-error loss.

## Connections to Later Topics

Several ideas from this part will be used directly later in the learning path:

- **Sampling Distributions and Limits:** expectation and variance of sums and sample means lead directly to the Law of Large Numbers and Central Limit Theorem.
- **Relationships among Variables:** covariance, correlation, and conditional expectation provide core tools for studying dependence between random variables.
- **Bayesian Inference:** conditioning and conditional expectation become central when updating distributions after observing data.
- **Information Theory:** entropy and cross-entropy are expectations of functions of probability distributions.
- **Learning Algorithms and Stochastic Gradient Descent:** expected loss is approximated by finite-sample and mini-batch averages during training.
- **Parameter Initialization in Deep Networks:** means and variances are used to analyze how activations and gradients propagate across layers.

## Repository Note

This README is intentionally concise. It explains the purpose, scope, and main results of the folder, while the notebook contains the substantive mathematical explanations, derivations, examples, and code.
