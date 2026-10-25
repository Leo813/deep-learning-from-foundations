# Probability Foundations — Part 4: Statistical and Likelihood Inference

This folder documents the transition from **probability theory** to **statistical inference**.

Earlier parts mainly assumed that a probability model was known and asked what could be deduced from it. Here, the direction is reversed: we observe data and use them to reason about an unknown distribution or its parameters.

The material is based primarily on **Chapter 5: Statistical Inference** and **Chapter 6: Likelihood Inference** from the probability textbook used in this learning project. The focus is selective and ML-oriented: the goal is to understand the statistical ideas that will be most useful later in machine learning rather than reproduce every subsection of the text.

## Files in This Folder

### [`probability_foundations_part4_statistical_likelihood_inference.ipynb`](./probability_foundations_part4_statistical_likelihood_inference.ipynb)

The main learning notebook.

It combines the important theory, mathematical derivations, questions raised during the reading, corrected misconceptions, and connections to later machine-learning concepts.

Main topics include:

- statistical models, parameters, and parameter spaces;
- population size $N$ versus sample size $n$;
- simple random sampling and approximate i.i.d. sampling;
- empirical distributions and descriptive statistics;
- likelihood, sufficient, and minimal sufficient statistics;
- maximum likelihood estimation;
- log-likelihood, score functions, gradients, and optimization;
- bias, variance, MSE, and consistency;
- standard deviation versus standard error;
- confidence intervals;
- hypothesis testing, z-tests, and P-values;
- distribution-free inference and bootstrapping.

### [`probability_foundations_part4_computer_exercises.ipynb`](./probability_foundations_part4_computer_exercises.ipynb)

A separate computational-practice notebook.

Rather than reproducing every textbook computer exercise, it selects and adapts the exercises that best reinforce the main ideas from this part. It also adds several small experiments that connect the statistical theory more directly to later ML work.

It includes:

1. numerical MLE and likelihood visualization;
2. likelihood versus log-likelihood;
3. MLE variance versus the unbiased sample variance;
4. empirical bias, variance, and MSE;
5. standard error under repeated sampling;
6. confidence-interval coverage simulations;
7. power as a function of sample size;
8. sample-size planning;
9. bootstrap sampling distributions and standard errors;
10. robustness of the mean versus the median.

## Core Perspective

The central change in viewpoint is:

```math
\text{Probability: model} \rightarrow \text{data}
```

versus

```math
\text{Statistics: data} \rightarrow \text{model / parameter}
```

A statistical model is written as

```math
\{P_\theta : \theta \in \Omega\},
```

where $\theta$ indexes the candidate probability distributions.

After observing data $s$, the likelihood is

```math
L(\theta \mid s) = f_\theta(s),
```

with the data held fixed and $\theta$ allowed to vary.

Maximum likelihood estimation then becomes an optimization problem:

```math
\hat{\theta}_{\mathrm{MLE}}
\in
\arg\max_{\theta \in \Omega} L(\theta \mid s)
=
\arg\max_{\theta \in \Omega} \ell(\theta \mid s),
```

where

```math
\ell(\theta \mid s) = \log L(\theta \mid s).
```

For i.i.d. data,

```math
\ell(\theta \mid x_{1:n})
=
\sum_{i=1}^{n}\log f_\theta(x_i),
```

which is one of the most direct bridges from classical statistics to optimization-based machine learning.

## Key Takeaways

- A **parameter** $\theta$ describes the unknown characteristics that identify a distribution within an assumed model family.
- A **statistic** is computed from data; an estimator is random before the sample is observed, while its realized estimate is numerical.
- Larger samples usually reduce estimator variability, while sampling without replacement is approximately i.i.d. when $n/N$ is small.
- A **sufficient statistic** reduces the raw data while preserving the likelihood information relevant to $\theta$.
- Likelihood is about relative support for different parameter values; it is not the same as $P(\theta\mid s)$.
- The MLE is the parameter value best supported by the observed data within the assumed model.
- Estimator accuracy is not described by bias alone:

```math
\mathrm{MSE}(T)
=
\mathrm{Var}(T)
+
\mathrm{Bias}(T)^2.
```

- **Standard deviation** measures the spread of observations, while **standard error** measures the spread of an estimator across repeated samples.
- A P-value measures how extreme the observed result is under the null hypothesis; it is not the probability that the null hypothesis is true.
- Statistical significance and practical significance are different concepts.
- Bootstrapping approximates sampling behavior by resampling from the empirical distribution with replacement.

## Scope

This folder emphasizes the parts of Chapters 5–6 that are most useful for progressing toward machine learning. Some lower-priority material was skimmed, omitted, or treated only briefly, including several exact-distribution details and more advanced asymptotic derivations.

The purpose is to build a strong working understanding of inference, likelihood, estimation, uncertainty, and resampling before moving further into machine learning.

## Connections to Later Topics

Several ideas from this part may reappear in the next chapters or machine learning:

- **Maximum Likelihood Estimation:** many learning objectives are derived by maximizing likelihood or minimizing negative log-likelihood.
- **Optimization:** score functions, gradients, and likelihood maximization lead naturally to gradient-based parameter learning.
- **Loss Functions:** Bernoulli and categorical negative log-likelihoods lead to common classification losses such as binary cross-entropy and softmax cross-entropy.
- **Bias and Variance:** estimator bias and sampling variance provide part of the statistical foundation for later bias-variance reasoning in machine learning.
- **Model Evaluation:** confidence intervals, standard errors, and resampling methods help quantify uncertainty in empirical performance estimates.
- **Bootstrap and Ensembles:** resampling ideas later appear in bootstrap-based uncertainty estimation and ensemble methods such as bagging.
- **Bayesian Inference:** likelihood remains a central component when moving from frequentist inference to posterior inference.

