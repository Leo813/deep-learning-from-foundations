# Probability Foundations Part 1

## Probability Models, Random Variables, and Distributions

This folder documents the first completed part of my probability foundations review. It covers the transition from basic probability models to random variables, distributions, joint distributions, conditioning, transformations, convolution, and simulation.

The goal of this part is to build the probability language needed before moving into expectation, statistical inference, likelihood inference, Bayesian inference, and eventually deep learning.

## What to Open

Start with the main notebook:

[`probability_foundations_part_1_lecture_notes.ipynb`](./probability_foundations_part_1_lecture_notes.ipynb)

The notebook contains the structured notes for this part, including definitions, derivations, corrected misunderstandings, examples, questions, reflections, and small Python simulations.

## Topics Included

### Chapter 1: Probability Models

- Probability as a measure on events
- Probability axioms and basic properties
- Inclusion-exclusion
- Uniform probability on finite sample spaces
- Non-uniform probability measures
- Birthday problem
- Conditional probability
- Bayes' theorem
- Independence
- Continuity of probability for increasing and decreasing event sequences

### Chapter 2: Random Variables and Distributions

- Random variables as functions from outcomes to numbers
- Probability mass functions
- Common discrete distributions
- Continuous random variables and density functions
- Cumulative distribution functions
- One-dimensional change of variable
- Joint distributions
- Conditional distributions
- Independence of random variables
- I.i.d. samples
- Multinomial distribution
- Order statistics
- Multidimensional change of variable and Jacobian determinant
- Convolution
- Simulation and inverse-CDF sampling

## Main Takeaways

The most important conceptual shift in this part was understanding probability as a **measure** rather than only as a number expressing uncertainty. This made later ideas such as continuous distributions, densities, and probability continuity more coherent.

A second major idea was that a **random variable is a function**:

```math
X:S\to\mathbb{R}
```

This reframes distributions as probability measures transferred from the original sample space onto numerical values.

A third major takeaway was that **joint distributions contain relationship information that marginal distributions do not**. This became central when studying conditioning, independence, and i.i.d. samples.

Several important intuitions were clarified:

- Bayes' theorem translates between two conditional viewpoints, but `P(A | B)` and `P(B | A)` are not generally equal.
- Independence means conditioning on one event or random variable does not change the probability distribution of the other.
- A density value is not a probability; probability comes from integrating density over an interval or region.
- Convolution becomes intuitive in probability because it sums or integrates over all compatible ways to produce a target sum.
- Simulation often starts from uniform random variables and transforms them into samples from the desired distribution.

## Corrections and Clarifications Preserved

This part includes several corrected or refined understandings:

- Uniform probability is only one possible probability measure on a finite sample space.
- In monotone event sequences, a finite event `A_n` usually does not equal the limiting event; only the probabilities converge in the limit.
- The binomial parameter `p` determines both the center `np` and the spread `np(1-p)`; expectation does not cause variance.
- The geometric distribution has different conventions across textbooks and software. In this textbook it counts failures before the first success, while NumPy's `geometric` counts trials until the first success.

## Implementation Work Completed

The notebook includes small Python examples for:

- inclusion-exclusion counting checks;
- the birthday problem threshold;
- random-variable event mapping;
- binomial PMF and concentration;
- Jacobian determinant example;
- discrete convolution;
- Bernoulli simulation;
- Exercise 2.10.10 distribution simulations.

The simulation exercise compares empirical means and variances against theoretical values for:

- Uniform `[0, 1]`
- Uniform `[5, 8]`
- Bernoulli `(1/3)`
- Binomial `(12, 1/3)`
- Geometric `(1/5)`
- Exponential `(1)`
- Exponential `(13)`
- Normal `N(0, 1)`
- Normal `N(5, 9)`

## Repository Note

This README is intentionally concise. It explains the purpose and contents of the folder, while the notebook contains the substantive mathematical explanations, derivations, examples, and code.
