# Probability Foundations Part 4

## Statistical and Likelihood Inference

This folder documents the fourth part of my probability foundations review. It focuses on the transition from probability theory to statistical inference: using observed data to learn about an unknown probability distribution, its parameters, and the uncertainty associated with statistical estimates.

The goal of this part is to build the statistical foundation needed for later machine-learning topics. In particular, it develops the ideas behind likelihood, maximum likelihood estimation, estimator uncertainty, confidence intervals, hypothesis testing, and bootstrap methods.

## What to Open

This part contains two complementary notebooks:

Start with the main notebook:

[`probability_foundations_part4_statistical_likelihood_inference.ipynb`](./probability_foundations_part4_statistical_likelihood_inference.ipynb)
- **Main learning notebook:** the structured learning notes for Chapters 5 and 6, including definitions, mathematical derivations, conceptual explanations, corrected misunderstandings, and connections to machine learning.

[`probability_foundations_part4_computer_exercises.ipynb`](./probability_foundations_part4_computer_exercises.ipynb)
- **Computer exercises notebook:** selected and adapted textbook exercises together with additional simulations that demonstrate likelihood optimization, estimator behavior, confidence-interval coverage, power, and bootstrap methods.

The main notebook contains the substantive theory and learning notes, while the computer-exercise notebook provides the practical simulation and implementation work.

## Topics Included

### Chapter 5: Statistical Inference

- Statistical models and parameter spaces
- Population size $N$ and sample size $n$
- Random sampling and approximate i.i.d. sampling
- Empirical distributions
- Sample mean, sample variance, and quantiles
- Robust summaries such as the median and IQR
- Basic forms of statistical inference

### Chapter 6: Likelihood Inference

- Likelihood and likelihood ratios
- Sufficient statistics
- Maximum likelihood estimation
- Log-likelihood and score functions
- Bias, variance, and mean-squared error
- Standard deviation and standard error
- Consistency
- Confidence intervals
- Hypothesis testing and P-values
- Statistical significance and practical significance
- Power and sample-size planning
- Distribution-free methods
- Method of moments
- Bootstrap inference

## Main Takeaways

The major conceptual shift in this part is the change in direction between probability and statistics.

In probability, the model is treated as known and we reason about possible data:

```math
\text{model}
\;\longrightarrow\;
\text{data}.
```

In statistical inference, the data are observed and we reason about an unknown model or parameter:

```math
\text{data}
\;\longrightarrow\;
\text{model / parameter}.
```

A statistical model is a family of candidate probability distributions,

```math
\{P_\theta : \theta \in \Omega\},
```

where $\theta$ indexes the possible distributions in the model family.

After observing data $s$, the likelihood is

```math
L(\theta \mid s) = f_\theta(s).
```

Here, the observed data are fixed while $\theta$ varies. Likelihood therefore measures the relative support that the observed data provide for different parameter values. It should not be interpreted as the posterior probability $P(\theta\mid s)$.

Maximum likelihood estimation chooses the parameter value that maximizes the likelihood:

```math
\hat{\theta}_{\mathrm{MLE}}
\in
\arg\max_{\theta \in \Omega}
L(\theta \mid s).
```

Because the logarithm is strictly increasing, the same estimate can be obtained by maximizing the log-likelihood:

```math
\ell(\theta \mid x_{1:n})
=
\sum_{i=1}^{n}
\log f_\theta(x_i).
```

This product-to-sum transformation is one of the strongest connections between classical statistics and optimization-based machine learning.

Another important theme is that an estimator is itself a random variable before the sample is observed. Its quality can therefore be studied through its sampling distribution.

For an estimator $T$ of a target $\psi(\theta)$,

```math
\operatorname{MSE}_\theta(T)
=
\operatorname{Var}_\theta(T)
+
\left(
E_\theta[T]-\psi(\theta)
\right)^2.
```

This separates estimation error into **variance** and **squared bias**.

The distinction between standard deviation and standard error was also important. Standard deviation describes the spread of observations, whereas standard error describes the spread of an estimator across repeated samples. For the sample mean,

```math
SE(\bar X)
=
\frac{\sigma}{\sqrt{n}}.
```

Thus, increasing the sample size reduces the uncertainty of the sample mean even though the population standard deviation $\sigma$ itself does not shrink.

Confidence intervals and hypothesis tests use sampling distributions to quantify uncertainty. A confidence level describes the repeated-sampling coverage of the interval-producing procedure; it is not a posterior probability for the fixed parameter.

Similarly, a P-value measures how extreme the observed result would be under the null hypothesis. It is not the probability that the null hypothesis is true.

Bootstrap methods provide a computational alternative when an estimator's sampling distribution is difficult to derive analytically. The empirical distribution is used as an approximation to the unknown population distribution, and repeated resampling with replacement is used to approximate estimator variability.

## Implementation Work Completed

The computer-exercise notebook reinforces these ideas through a set of representative experiments, including:

- plotting nontrivial likelihood functions and locating their numerical MLEs;
- comparing likelihood and log-likelihood;
- comparing the Normal variance MLE with the unbiased sample variance;
- estimating bias, variance, and MSE through repeated simulation;
- demonstrating how standard error decreases as sample size increases;
- measuring empirical confidence-interval coverage;
- plotting statistical power as a function of sample size;
- determining sample sizes from a target confidence-interval width;
- estimating bootstrap sampling distributions and standard errors;
- comparing the robustness of the mean and median under outliers;
- constructing bootstrap percentile confidence intervals.

The exercises were selected and adapted from the textbook rather than reproduced exhaustively, with additional simulations included where they better reinforce the concepts emphasized in the main learning notebook.

## Connections to Later Topics

Several ideas from this part will reappear directly in machine learning:

- **Maximum Likelihood Estimation:** many learning objectives are derived by maximizing likelihood or minimizing negative log-likelihood.
- **Optimization:** score functions, gradients, and likelihood maximization lead naturally to gradient-based parameter learning.
- **Loss Functions:** Bernoulli and categorical negative log-likelihoods lead to common classification losses such as binary cross-entropy and softmax cross-entropy.
- **Bias and Variance:** estimator bias and sampling variance provide part of the statistical foundation for later bias-variance reasoning in machine learning.
- **Model Evaluation:** confidence intervals, standard errors, and resampling methods help quantify uncertainty in empirical performance estimates.
- **Bootstrap and Ensembles:** resampling ideas later appear in bootstrap-based uncertainty estimation and ensemble methods such as bagging.
- **Bayesian Inference:** likelihood remains a central component when moving from frequentist inference to posterior inference.
