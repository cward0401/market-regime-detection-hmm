# Aerospace Engine Operational Regime Analusus & Remaining Useful Life (RUL)

This project analyzes aircraft engine degradation dynamics using the NASA C-MAPSS dataset.
The Objective is to infer latent operational regimes from multivariate sensor data, interpret these regimes geometrically in state space, and link system dynamics to Remaining Useful Life (RUL) in a continuous, physically meaninful way.

Rather than treating failure as a discrete event, this work frames engine health as a trajectory through a high-dimensional operational state space.

---

## Dataset

- **Source:** NASA C_MAPSS (Commercial Modular Aero-Propulsion Systems Simulation)
- **Subset:** FD001
- **Data:** Multivariate time series sensor measurements for multiple engines, recorded until system failure

The dataset is simulated but widely used as a benchmark for prognostics and health management (PHM).

---
## Methodology Overview

1. Feature Engineering
   Raw sensor signals are transformed into rolling statistics (means and standard deviations) to capture trends and instability rather than instantaneous noise. Featuresare standardized prior to modeling.

---

2. Operational Regime Identification (Hidden Markov Model)
   A GAussian Hidden Markov Model (HMM) is used to infer latentt operational regimes from sensor dynamics.
   The model is fit across all engines simultaneously, allowing regimes to emerge as shared statistical states rather than predefined labels.

   Key properties:
   - Regimes are inferred from dynamics, not failure labels
   - Tansitions reflect changes in system behavior, not discrete faults
   - individual engines may occupy a sinle regime for much of their lifetime

---

3. Geometric Interpretation of Regimes
   Engine states are embedded in a high-dimensional feature space.
   Dimensionality reduction (PCA) is used to visualize this space and interpret regimies geomentrically.

   Key obvservations:
   - Regimes correspond to **overlapping regions** of state space, not isolated clusters
   - Degradation manifests as a **directional flow** through state space
   - Regime transiions occur gradually as trajetcories crose fuzzy boundaries

   This framing aligns with physical intuition from aerospace systems where degradation is continuous and irreversible rather than discrete.

---

4. Regime Dwell Time Analysis
   Regime dwell times are computed as contiguous periods during which an engine remains in the same latent state.

   Dwell time captures:
   - Local stability of systems dynamics
   - Persistence of operational behavior
   - Differences between stable, transitional, and degraded regimes

---

5. Distance-to-Degraded Regime
   A continuous health indicator is defined as the Euclidean distance in state space to the cetroid of the most degraded regime.

   This metric:
   - Is geometric rather than temporal
   - Preserves continuity of system health
   - Avoids hard threshholds or binary failure logic

---

6. Linking State Space Geometry to Remaining Useful Life (RUL)
   True RUL is computed from unknown failure cycles.
   Distance -tp-degraded regime is compared against RUL to assess monotonicity.

   Findings:
   - RUL decreases as trajectoris approach The degraded region of state space
   - The relationship is monotonic but nonlinear and heteroskedastic
   - Engine-level trajectories show smooth degradation paths rather than abrupt transitions
   A simple linear model is used only to demonstrate structure, not to optimize prediction accuracy.

## Key Takeaways 
- Engine degredation can be understood as a trajectory through operational state space
- Latent regimes reflect regions of shared dynamics, not discrete operating modes
- Continuous geomentric metrics provide a robust and physical plausibility over black-box prediction

## Limitations
- The C-MAPSS dataset is simulated
- Regimes are inferred, not physically labeled
- Resultsa depend on feature engineering choices
- The RUL model is illustrative rather than production-ready

## Tools & Technologies
- Python
- Numpy, Pandas
- scikit-learn
- hmmlearn
- Matplolib
- Jupyter Notebook

## Author
Charlie Ward
Junior Data Scientist - Applied Analytics & Modeling
