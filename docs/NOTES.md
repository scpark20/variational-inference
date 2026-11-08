# Implementation notes

The notebooks retain their original code and saved outputs. The following observations come from source inspection; the documentation update does not change or certify the mathematical implementations.

## Linear regression

- The final result cell uses `beta`, `a_0`, and `b_0` without defining them at notebook scope. Function defaults do not define those global names. Set them explicitly and pass the same values to the fitting and ELBO calculations before running from a fresh kernel.
- `get_qw_params` currently adds scalar `E_alpha` to every entry of `beta * design.T @ design`. The isotropic prior precision in the referenced update is an identity-scaled term; review this before using the posterior calculations.
- The plotted band is `mean ± variance`, as written. It should not be read as a standard-deviation or calibrated credible interval.

## Logistic regression

The predictive-probability helper defines `kappa` with a positive one-half power. Review this against the inverse-square-root scaling in the referenced PRML approximation before using the predicted probabilities.

## Gaussian mixtures

The notebook generates five components, initializes ten components with K-means, and plots assignments every ten iterations. Its saved figure illustrates that run; it is not a quantitative convergence or accuracy benchmark. Data generation is stochastic, so a new run may look different.
