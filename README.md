# stochastic-logistic-estimation
Comparative implementation of parameter estimation methods for the logistic stochastic differential equation (SDE), contrasting closed-form estimators (Eqs. 50–54) with method-of-moments estimators (Eqs. 55–57) under Monte Carlo simulation.
# Comparison of Parameter Estimation Methods for the Logistic SDE

This repository provides a reproducible framework for simulating and estimating parameters in the **logistic stochastic differential equation (SDE)** using two methodological approaches:

1. **Closed-form estimators (Eqs. 50–54)** derived from the analytical form of the SDE in log-space, based on discrete Itô calculus.
2. **Method-of-Moments estimators (Eqs. 55–57)** obtained from moment-matching relationships analogous to those of the Jacobi process.

Both methods are applied under identical simulation conditions using the **Euler–Maruyama scheme** to ensure positivity and numerical stability. A **Monte Carlo procedure** quantifies estimator dispersion and convergence as the time horizon (T), step size (dt), and replication count (K) increase.

---

## 📘 Model Overview

The logistic SDE is defined as:

\[
dY_t = [r - \eta Y_t]Y_t\,dt + \sigma Y_t\,dB_t, \quad Y(0) > 0
\]

where:
- \(r > 0\): intrinsic growth rate  
- \(\eta > 0\): strength of density dependence  
- \(\sigma > 0\): diffusion coefficient  

The stationary distribution of \(Y_t\) is Gamma(\(u, v\)) with parameters  
\(u = 2r/\sigma^2 - 1\) and \(v = 2\eta/\sigma^2\), provided \(2r/\sigma^2 > 1\).

---

## ⚙️ Estimation Frameworks

### 1. Closed-form Estimators (Eqs. 50–54)
Derived from transformations in log-space using:
- Equation (50): estimator of σ based on log-increments.  
- Equation (53): estimator of η via discrete integrals of \(Y\) and \(Y^2\).  
- Equation (54): estimator of r combining \(\hat{\sigma}\) and \(\hat{\eta}\).

### 2. Method-of-Moments Estimators (Eqs. 55–57)
Estimated from empirical moments of simulated trajectories.  
These provide an alternative approach based solely on sample mean and variance relationships.

---

## 🎲 Monte Carlo Design

Each Monte Carlo experiment follows the pipeline:

\[
(46)+(47) \rightarrow (50)+(53)+(54) \text{ or } (55)+(57)
\]

- Replicates \(K\) trajectories with different seeds.  
- Computes \(\hat{\sigma}, \hat{\eta}, \hat{r}\) for each trajectory.  
- Reports mean, standard deviation, and ±2·sd bands (dispersion of the estimator).

---

## 📊 Visualization

Three-panel figures display the evolution of each estimator (\(\hat{\sigma}, \hat{\eta}, \hat{r}\)) across scenarios, comparing:
- **Black lines:** Closed-form estimators (Eqs. 50–54)  
- **Blue lines:** Method-of-Moments estimators (Eqs. 55–57)  
- **Red dashed line:** True parameter value

Dispersion decreases as \(T\) and \(K\) increase, confirming consistency and convergence of both methods.

---

## 🧠 Interpretation

Both estimation frameworks demonstrate asymptotic equivalence under long time horizons, though the closed-form estimators exhibit smaller variance for short samples.  
The method-of-moments provides a simpler, computationally efficient alternative with comparable accuracy.

---

## 🧩 Repository Structure

├── logistic_SDE_estimators.R      # Main script (simulation + estimation)
├── figures/                       # Plots comparing both methods
├── data/                          # (Optional) Monte Carlo results
├── README.md                      # This documentation


---

## 📚 References

- Stochastic population dynamics and inference methods as described in:  
  *Introduction to Stochastic Models in Biology* (2020).  
- Analytical estimators derived from equations (46)–(57) in the referenced study.

---

