# Probability Foundations — Part 5: Bayesian Inference, Model Checking, and Regression

This folder completes the probability and statistical inference portion of **Deep Learning from Foundations**. Building on likelihood-based inference, it explores how prior information changes statistical conclusions, how loss functions guide decisions, how to check whether a model is trustworthy, and how to model relationships among variables.

The material is based on Chapters 7–10 of *Probability and Statistics: The Science of Uncertainty* by Michael J. Evans and Jeffrey S. Rosenthal. The notebooks follow the broad progression of the textbook while concentrating on ideas that provide a foundation for subsequent machine learning study.

## Notebooks

| File | Purpose |
|:--|:--|
| [**Main Notes — Bayesian Inference to Regression**](probability_foundations_part5_main_notes.ipynb) | A lecture-style walkthrough of the concepts, important derivations, examples, interpretations, and chapter recaps. |
| [**Computer Exercises**](probability_foundations_part5_computer_exercises.ipynb) | Selected textbook exercises and supplementary numerical experiments using NumPy, SciPy, and Matplotlib. Connects the mathematical ideas to computation and interpretation. |

## Topics Covered

| Chapter | Main focus |
|:--|:--|
| **7 — Bayesian Inference** | Priors, likelihoods, posteriors, conjugate updating, posterior estimation and prediction, credible intervals, and Monte Carlo computation. |
| **8 — Optimal Inferences** | Loss functions, decision rules, risk, and why different error criteria lead to different optimal estimates. |
| **9 — Model Checking** | Residual and probability plots, checking sampling assumptions, prior–data conflict, and cross-validation. |
| **10 — Relationships Among Variables** | Dependence and causation, least squares, simple and multiple linear regression, regression diagnostics, ANOVA, categorical predictors, and logistic regression. |

## Key Takeaways

- **Inference requires assumptions.** A posterior or fitted model is meaningful only in the context of its likelihood, prior (when applicable), and modeling assumptions.
- **The objective matters.** Choosing an estimator or prediction depends on the loss being minimized; different loss functions can favor different answers.
- **Model fitting is not model validation.** Residual diagnostics and held-out predictions help reveal problems that training fit alone cannot establish.
- **Regression connects statistics with optimization.** Least squares, design matrices, uncertainty estimates, and likelihood-based binary classification form a useful bridge toward machine learning.

**Requirements:** Jupyter Notebook, Python, NumPy, SciPy, and Matplotlib. The exercise notebook uses self-contained datasets and simulations.

## Reference

Evans, Michael J., and Jeffrey S. Rosenthal. *Probability and Statistics: The Science of Uncertainty*. Chapters 7–10.

---

**Learning progression:** This part follows the earlier foundations in probability, expectation, sampling distributions, and likelihood inference, and prepares for studying machine learning models, objectives, and optimization methods.
