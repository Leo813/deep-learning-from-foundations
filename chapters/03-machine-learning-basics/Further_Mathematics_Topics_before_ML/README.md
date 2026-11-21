# Mathematic Topics toward Machine Learning

This folder explores three mathematical foundations that connect probability theory with machine learning: **stochastic processes**, **information theory and structured probabilistic models**, and **numerical computation**. The notebook combines mathematical explanations, derivations, and small NumPy experiments to develop both intuition and a deeper understanding of the methods.

## Notebook

**[Mathematic Topics toward Machine Learning.ipynb](./Mathematic_Topics_toward_Machine_Learning.ipynb)** — the complete set of notes, worked examples, and computational demonstrations.

## Topics Covered

| Part | Main topics |
| --- | --- |
| **I. Stochastic Processes** | Random walks and gambler's ruin; Markov chains and stationary distributions; Metropolis–Hastings and Gibbs sampling; MCMC and neural generative models. |
| **II. Information Theory and Structured Probabilistic Models** | Self-information and Shannon entropy; cross-entropy and KL divergence; forward versus reverse KL; graphical models, factorization, and conditional independence. |
| **III. Numerical Computation** | Numerical stability and conditioning; gradients, Hessians, and Taylor approximations; gradient descent, Newton's method, and coordinate-wise learning rates; constrained optimization and KKT conditions. |

## Key Takeaways

- **Stochastic processes provide models of evolution and tools for sampling.** A stationary distribution describes equilibrium, but convergence and mixing determine how useful samples from a Markov chain are in practice.
- **Information theory connects probability distributions to learning objectives.** Entropy measures average information, while cross-entropy and KL divergence quantify predictive mismatch; the direction of KL matters.
- **Probabilistic structure makes complex distributions more manageable.** Graphical models express factorization and conditional independence, but some representations still require difficult normalization or inference.
- **Optimization depends on numerical stability and curvature.** Gradients determine local descent directions; Hessians explain curvature and motivate Newton's method and diagonal learning-rate approximations.
- **Constraints change the optimality conditions.** KKT conditions extend stationarity by accounting for feasible directions, multiplier signs, and complementary slackness.

## Main References

- Michael J. Evans and Jeffrey S. Rosenthal, *Probability and Statistics: The Science of Uncertainty*, Chapter 11, Sections 11.1–11.3.
- Ian Goodfellow, Yoshua Bengio, and Aaron Courville, *Deep Learning*, Sections 3.13–3.14 and Chapter 4 (primarily Sections 4.1–4.4).

The notebook can be viewed directly on GitHub. To run its examples locally, use Jupyter with **NumPy** and **Matplotlib** installed.
