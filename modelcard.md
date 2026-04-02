# Model Card

## Model name

Seed Viability Modelling: Literature-Benchmarked Computational Proof-of-Concept

## Model summary

This modelling workflow predicts seed deterioration patterns under storage by combining a mechanistic baseline, a discrete-time hazard classifier for threshold failure, and a hybrid residual-learning model for continuous viability prediction. It is designed as a proof-of-concept rather than a deployed production model.

## Model status

Research prototype.

## Intended users

The intended users are seed scientists, plant conservation researchers, genebank analysts, crop scientists, restoration ecologists, and data scientists interested in interpretable predictive modelling for seed storage and persistence.

## Intended use

The workflow is intended for exploratory modelling, teaching, workflow prototyping, and hypothesis generation. It can serve as a starting point for future analyses of real longitudinal seed-lot data.

## Out-of-scope use

This workflow should not be used as the sole basis for operational decisions about seed-bank regeneration, seed distribution, conservation triage, commercial seed release, or species-specific storage protocols without empirical validation. It should not be treated as a clinically or commercially validated prediction system.

## Modelling components

The proof-of-concept contains three linked modelling layers.

### 1. Mechanistic baseline

A biologically motivated baseline estimates continuous viability decline as a function of time, temperature, moisture, oxygen-related stress, and seed class. The structure is inspired by classical seed longevity theory.

### 2. Discrete-time hazard model

A classification model predicts the probability that viability falls below a specified threshold, defined in the notebook as 50 percent. This creates an operational survival-style interpretation of storage failure risk.

### 3. Hybrid residual-learning model

A gradient-boosting regressor learns residual error not captured by the mechanistic baseline, producing improved continuous viability estimates.

## Inputs

The main model inputs include:

- seed storage behaviour class
- storage duration
- storage temperature
- moisture content
- water activity proxy
- oxygen level
- packaging condition
- initial viability
- initial dormancy tendency
- lot identifier and related metadata

## Outputs

The model produces:

- continuous viability predictions
- germination and dormancy trajectories in the simulated workflow
- event probabilities for viability dropping below the defined threshold
- calibration summaries
- permutation-importance rankings
- exported figures and tables

## Training and evaluation data

The current version uses simulated longitudinal seed-lot data rather than real observed data. The simulation logic was designed to be qualitatively consistent with the peer-reviewed seed science literature. Because the data are simulated, evaluation metrics measure internal coherence relative to the synthetic ground truth, not generalization to real-world seed lots.

## Performance summary

Performance is reported within the notebook using standard regression and classification metrics such as mean absolute error, root mean squared error, coefficient of determination, AUROC, AUPRC, Brier score, and calibration plots. These values describe performance on the simulated test set only.

## Interpretability

Interpretability is a key design goal. The mechanistic baseline provides biologically understandable structure, and permutation importance summarizes which original input variables most strongly influence classification performance. This is one reason the project uses a hybrid approach rather than a fully opaque model.

## Assumptions

The model assumes that viability generally declines with storage time and that deterioration is accelerated by adverse moisture, temperature, and oxygen conditions. It also assumes that seed storage behaviour class is a major determinant of longevity pattern and that viability, germination, and dormancy should be treated as distinct endpoints.

## Limitations

Several limitations are important.

First, the dataset is simulated.  
Second, the parameters are literature-benchmarked but not species-specific.  
Third, the threshold event, viability below 50 percent, is operational rather than universal.  
Fourth, real storage systems may include additional sources of heterogeneity not captured here, such as harvest maturity, maternal environment, microbial contamination, biochemical state, or fluctuating environment histories.  
Fifth, the model does not yet represent formal uncertainty intervals in a Bayesian sense.

## Risks and cautions

A user could misinterpret the outputs as validated predictions for a specific species or accession. That would be inappropriate. The outputs are best viewed as illustrative and methodological. Any real deployment should use measured data, domain calibration, prospective validation, and species-aware thresholds.

## Ethical and practical considerations

This workflow poses low direct ethical risk because it does not process human data or make decisions about people. The main risk is scientific overinterpretation. Users should avoid presenting simulated performance as empirical validation and should clearly distinguish conceptual modelling from operational recommendation.

## Maintenance

The current workflow is suitable for iterative expansion. Recommended next steps include replacing the simulated dataset with real longitudinal lot data, incorporating hierarchical structure, modelling censoring explicitly, and adding uncertainty quantification.

## Contact

**Petalcorin, M.I.R.** (2026). Seed Viability Modelling Using Survival Analysis and Hybrid Machine Learning. https://github.com/mpetalcorin/seed-viability-hybrid-modelling 
m.petalcorin@gmail.com
