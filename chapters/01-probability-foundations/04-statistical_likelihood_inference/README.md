# Probability Foundations — Part 4: Statistical and Likelihood Inference

This folder documents the transition from **probability theory** to **statistical inference**.

Earlier parts mainly assumed that a probability model was known and asked what could be deduced from it. Here, the direction is reversed: we observe data and use them to reason about an unknown distribution or its parameters.

The material is based primarily on **Chapter 5: Statistical Inference** and **Chapter 6: Likelihood Inference** from the probability textbook used in this learning project. The focus is selective and ML-oriented: the goal is to understand the statistical ideas that will be most useful later in machine learning rather than reproduce every subsection of the text.

## Files in This Folder

### `probability_foundations_part4_statistical_likelihood_inference.ipynb`

The main learning notebook.

It combines the important theory, mathematical derivations, questions raised during the reading, corrected misconceptions, and connections to later machine-learning concepts.

Main topics include:

- statistical models, parameters, and parameter spaces;
- population size `N` versus sample size `n`;
- simple random sampling and approximate i.i.d. sampling;
- empirical distributions and descriptive statistics;
- likelihood and likelihood ratios;
- sufficient and minimal sufficient statistics;
- maximum likelihood estimation;
- log-likelihood, score functions, gradients, and optimization;
- bias, variance, MSE, and consistency;
- standard deviation versus standard error;
- confidence intervals;
- hypothesis testing, z-tests, and P-values;
- statistical versus practical significance;
- power and sample-size planning;
- distribution-free inference and bootstrapping.

### `probability_foundations_part4_computer_exercises.ipynb`

A separate computational-practice notebook.

Rather than reproducing every textbook computer exercise, it selects and adapts the exercises that best reinforce the main ideas from this part. It also adds several small experiments that connect the statistical theory more directly to later ML work.

It includes:

- numerical MLE and likelihood visualization;
- likelihood versus log-likelihood;
- MLE variance versus the unbiased sample variance;
- empirical bias, variance, and MSE;
- standard error under repeated sampling;
- confidence-interval coverage simulations;
- power as a function of sample size;
- sample-size planning;
- bootstrap sampling distributions and standard errors;
- robustness of the mean versus the median;
- bootstrap confidence intervals.

## Core Perspective

The central change in viewpoint is:

`Probability: model -> data`

versus

`Statistics: data -> model / parameter`

A statistical model can be represented as a family of distributions indexed by a parameter:

`{P_theta : theta in Omega}`

where `theta` identifies a candidate distribution in the model family.

After observing data `s`, the likelihood is

`L(theta | s) = f_theta(s)`

with the data held fixed and `theta` allowed to vary.

Maximum likelihood estimation then becomes an optimization problem:

`theta_hat_MLE = argmax_theta L(theta | s)`

or equivalently

`theta_hat_MLE = argmax_theta ell(theta | s)`

where

`ell(theta | s) = log L(theta | s)`.

For i.i.d. data, the log-likelihood becomes a sum:

`ell(theta | x_1:n) = sum_i log f_theta(x_i)`.

This is one of the most direct bridges from classical statistics to optimization-based machine learning.

## Key Takeaways

- A **parameter** `theta` describes the unknown characteristics that identify a distribution within an assumed model family.
- A **statistic** is computed from data; an estimator is random before the sample is observed, while its realized estimate is numerical.
- Larger samples usually reduce estimator variability, while sampling without replacement is approximately i.i.d. when `n/N` is small.
- A **sufficient statistic** reduces the raw data while preserving the likelihood information relevant to `theta`.
- Likelihood is about relative support for different parameter values; it is not the same as `P(theta | s)`.
- The MLE is the parameter value best supported by the observed data within the assumed model.
- Estimator accuracy is not described by bias alone:

  `MSE(T) = Var(T) + Bias(T)^2`

- **Standard deviation** measures the spread of observations, while **standard error** measures the spread of an estimator across repeated samples.
- A P-value measures how extreme the observed result is under the null hypothesis; it is not the probability that the null hypothesis is true.
- Statistical significance and practical significance are different concepts.
- Bootstrapping approximates sampling behavior by resampling from the empirical distribution with replacement.

## Reading Order

Start with the main notebook:

1. [`probability_foundations_part4_statistical_likelihood_inference.ipynb`](probability_foundations_part4_statistical_likelihood_inference.ipynb)

Then use the computational notebook to reinforce the ideas experimentally:

2. [`probability_foundations_part4_computer_exercises.ipynb`](probability_foundations_part4_computer_exercises.ipynb)

The first notebook is the conceptual record of the learning session. The second is intentionally more implementation-oriented and should be read as practice rather than as a replacement for the theory.

## Scope

This folder emphasizes the parts of Chapters 5–6 that are most useful for progressing toward machine learning. Some lower-priority material was skimmed, omitted, or treated only briefly, including several exact-distribution details and more advanced asymptotic derivations.

The purpose is to build a strong working understanding of inference, likelihood, estimation, uncertainty, and resampling before moving further into machine learning.

## Reference

Primary learning material:

- *The Science of Uncertainty* — Chapters 5 and 6
- Session notes, derivations, questions, and computational experiments developed during this learning project
