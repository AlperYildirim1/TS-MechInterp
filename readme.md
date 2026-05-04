# TS-MechInterp

Mechanistic interpretability experiments for Time Series Transformers using Sparse Autoencoders (SAEs).

This project investigates whether transformer-based time series forecasting models develop the same kind of dense superposition observed in large language models.

The primary architecture studied is **PatchTST**.

---

# Core Idea

Mechanistic interpretability has focused heavily on language models, where Sparse Autoencoders frequently uncover highly superposed and densely packed representations.

Time series forecasting may be fundamentally different.

Our experiments suggest that competitive forecasting performance can emerge from comparatively sparse and low-complexity internal representations, even in transformer architectures.

In particular:

* Expanding SAE dictionary size produces only minimal downstream forecasting changes
* Many overcomplete latent dimensions remain inactive
* Aggressive latent interventions produce surprisingly small forecast perturbations
* A single transformer layer is often sufficient for strong performance

These findings may help explain why simple linear forecasting models remain highly competitive on standard benchmarks.

---

# Main Findings

* Sparse FFN representations in PatchTST
* Minimal downstream benefit from large SAE dictionary expansion
* Weak evidence for strong superposition
* High dead-latent rates in overcomplete dictionaries
* Small causal effect from dominant latent interventions
* Competitive forecasting performance with shallow transformer architectures

---

# Repository Structure

```text
SAE_Full.ipynb
    Full SAE training pipeline and interpretability experiments.

Time_series_combined_ECL_Traffic.ipynb
    Training notebook for Electricity (ECL) and Traffic datasets.
    Experiments were run on NVIDIA A100 GPUs.

Time_series_combined_pretraining.ipynb
    Training notebook for all remaining forecasting datasets.
    Experiments were run on NVIDIA L4 GPUs.

Pareto_Sweep.ipynb
    Large-scale SAE sparsity sweep.
    Trains 256 SAE models across sparsity coefficients and dictionary scales.
```

---

# Benchmarks

Experiments were conducted on standard long-term forecasting datasets:

* Weather
* Electricity (ECL)
* Traffic
* Exchange
* ETTh1
* ETTh2
* ETTm1
* ETTm2

Prediction horizons:

* 96
* 192
* 336
* 720

---

# Sparse Autoencoder Setup

SAEs are trained on post-GELU FFN activations extracted from PatchTST.

Dictionary scales explored:

* 0.5×
* 1.0×
* 4.0×

Experiments include:

* Reconstruction fidelity analysis
* Dictionary scaling analysis
* Dead latent analysis
* Causal latent intervention experiments
* Sparsity coefficient sweeps

---

# Why This Matters

There has been ongoing debate about whether transformer complexity is actually necessary for standard time series forecasting benchmarks.

This project approaches that question mechanistically rather than purely through benchmark comparisons.

The results suggest that these datasets may not require the kind of rich compositional representations that drive transformer success in language modeling.

---

# Medical Time Series Motivation

Interpretability becomes especially important in medical settings such as:

* EEG monitoring
* ECG analysis
* ICU forecasting
* Seizure prediction
* Physiological monitoring

Sparse Autoencoders may provide a pathway toward identifying clinically meaningful latent features inside forecasting models.

Future work will extend these methods toward medical and physiological time series domains.

---

# Status

Research codebase accompanying an active interpretability project.

Code cleanup, documentation improvements, and additional experiments are ongoing.

---

# Citation

Coming soon
