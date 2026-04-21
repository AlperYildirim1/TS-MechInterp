# TS-MechInterp

This project investigates the internal representations of Time Series Transformers (specifically **PatchTST**) using **Sparse Autoencoders (SAEs)**.

## Core Idea

Mechanistic interpretability has focused heavily on language models, but time series models operate under different structural constraints. We study whether their internal representations are similarly complex, or whether they admit simpler structure.

Our experiments suggest that the FFN activations of PatchTST can be approximated with a highly sparse dictionary (**L0 ≈ 3.1**) while incurring only a small reconstruction penalty (~2% MSE increase, dataset-dependent).

This indicates that, at least in our setting, the model may rely on a small number of dominant, interpretable features rather than highly entangled representations.

## Connection to Linear Models

There has been ongoing discussion about whether Transformer-based models outperform simpler approaches such as **DLinear** in time series forecasting.

Our results provide a possible mechanistic perspective:  
PatchTST may internally construct a sparse, approximately linear representation of the input signal, which could explain why linear baselines remain competitive.

We refer to this hypothesis informally as the **"Hidden DLinear"** effect.

## Key Findings

- **Sparse structure:** FFN activations can be reconstructed with very low L0 sparsity (~3.1)
- **Low reconstruction penalty:** ~2% increase in MSE (depending on dataset and setup)
- **Interpretable features:** Identified components corresponding to patterns such as:
  - Daily cycles
  - Peak demand periods
  - Low-activity intervals
- **Reduced feature overlap:** Features appear more separable than expected, though further validation is needed

## Why Interpretability Matters (Medical Time Series)

Interpretability is especially critical in domains such as healthcare, where time series models are used to monitor patients, forecast clinical events, and support decision-making.

Applications such as ICU monitoring, ECG/EEG analysis, and continuous glucose tracking require models whose predictions can be understood and trusted by clinicians.

While this repo does not yet evaluate medical datasets, our results about medical time series and interpretability will be added soon.

## Status

This is an early-stage research project. Results are currently limited to specific datasets and model configurations.  
A full paper with detailed methodology, ablations, and broader evaluation is in preparation.

## Citation

coming soon
(coming soon via Zenodo DOI for codes, paper via arXiv)
