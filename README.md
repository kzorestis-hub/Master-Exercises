# Master-Exercises

This repository contains a collection of data analysis, statistical modeling, and computational physics exercises completed during my Master's in Astrophysics, Particle Physics, and Cosmology at the University of Barcelona.

---

## 1. Statistical Test Simulation and Comparison
This section contains a Jupyter Notebook that explores the behavior and robustness of parametric and non-parametric statistical tests through Monte Carlo simulations. 

**Key Explorations:**
* Comparing the performance of $t$-tests and Mann-Whitney U-tests under various conditions.
* Evaluating Levene's test for equality of variances using different center estimators (mean, median, and trimmed mean).
* Testing the limits of these methods by introducing skewed data (exponential distributions), unequal sample sizes, and extreme outliers to observe false positive rates.

---

## 2. Classification Analysis of the Wine Dataset
This notebook analyzes the chemical composition of wines derived from three different cultivars in Italy, utilizing the `scikit-learn` Wine Dataset. 

**Key Explorations:**
* **Principal Component Analysis (PCA):** Applying unsupervised dimensionality reduction to visualize variance and underlying structure.
* **K-Means Clustering:** Using unsupervised learning ($k=3$) to discover natural groupings based purely on chemical profiles.
* **Linear Discriminant Analysis (LDA):** Training a supervised predictive classifier to maximize class separation, achieving 100% accuracy on the test set. 

**Conclusion:** The analysis successfully demonstrates how "Terroir" (the natural environment) leaves a measurable chemical footprint, allowing algorithms to perfectly distinguish wine cultivars based solely on earth-derived nutrients.

---

## 3. Cosmological Constraints from DESI BAO Data using MCMC
This notebook performs Bayesian parameter estimation using Markov Chain Monte Carlo (MCMC) to constrain cosmological models based on Baryon Acoustic Oscillation (BAO) measurements from DESI DR2.

**Key Methodologies:**
* **Bayesian Inference:** Built custom log-likelihood and prior functions to evaluate the posterior distribution of cosmological parameters.
* **MCMC Sampling:** Utilized the `emcee` ensemble sampler to explore high-dimensional parameter spaces.
* **Convergence Diagnostics:** Implemented custom Gelman-Rubin ($\hat{R}$) statistics and autocorrelation time checks to ensure chain convergence.
* **Marginalization & Visualization:** Used `getdist` to generate professional triangle (corner) plots and extract 1D marginal constraints and correlation matrices.

**Models Explored:**
1. **Flat $\Lambda$CDM:** Constrained matter density ($\Omega_m$) and the acoustic scale ($H_0 r_d$), demonstrating the geometric degeneracy between them.
2. **Non-Flat $\Lambda$CDM:** Relaxed the flatness assumption, rigorously handling comoving distance integrals with hyperbolic ($\sinh$) and trigonometric ($\sin$) limits for open and closed geometries, showing $\Omega_k$ is consistent with zero.
3. **Physical Parameters + BBN Prior:** Substituted geometric parameters for physical densities ($\Omega_b h^2$, $\Omega_m h^2$) and applied a Big Bang Nucleosynthesis Gaussian prior to break degeneracies, resulting in a direct constraint on the Hubble constant ($H_0$).

---

## 4. Monte Carlo Event Generation and Parameter Estimation
This script performs a comprehensive statistical simulation to explore parameter estimation via Maximum Likelihood Estimation (MLE), Fisher Information, and hypothesis testing.

**Key Methodologies:**
* **Monte Carlo Generation:** Uses the Acceptance-Rejection (Hit-or-Miss) method to generate statistical events following a true Probability Density Function (PDF) $f_0(x)$.
* **Maximum Likelihood Estimation:** Fits a generalized model $f(x; A)$ to the simulated data by numerically minimizing the Negative Log-Likelihood (NLL) using the BFGS algorithm.
* **Error Estimation:** Computes the statistical error on the parameter $\hat{A}$ using both the inverse Hessian matrix and the graphical likelihood method (identifying the bounds where $\text{NLL}_{min} + 0.5$).
* **Minimum Variance Bound (MVB):** Analytically calculates the Fisher Information to determine the theoretical lower bound of the variance, successfully verifying the empirical errors derived from the MLE.
* **Goodness-of-Fit Tests:** Utilizes $\chi^2$ testing to generate p-value distributions for the data tested against both the true model and the fitted model, rigorously adjusting degrees of freedom to account for the estimated parameter.

---

## 5. Simulating Particle Discovery and Statistical Significance
This script simulates a high-energy physics experiment to evaluate the statistical significance of a new particle discovery over time, mimicking the search for a resonance (like the Higgs boson at $m_H = 126.5$) over an exponential background.

**Key Methodologies:**
* **Expected Yields:** Accurately calculates theoretical expected counts for both background (Exponential) and signal (Gaussian) by integrating the Probability Density Functions over the bin widths, rather than relying on midpoint approximations.
* **Toy Monte Carlo Generation:** Simulates tens of thousands of pseudo-experiments (toys) using Poisson fluctuations around the true S+B (Signal + Background) model.
* **Hypothesis Testing:** Computes the chi-squared statistic against the null hypothesis (Background Only) and evaluates the survival function to generate p-values for each toy experiment.
* **Time Evolution Scan:** Projects the expected significance over a 10-year running period, calculating both the mean p-value and the empirical probability of crossing the gold-standard 5-sigma discovery threshold ($2.9 \times 10^{-7}$) in any given year.
