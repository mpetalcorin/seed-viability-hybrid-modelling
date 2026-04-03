# seed-viability-hybrid-modelling
Literature-benchmarked proof-of-concept for modelling seed viability, germination, and dormancy using mechanistic theory, survival-style analysis, and hybrid machine learning.
<img width="1091" height="814" alt="Screenshot 2026-04-02 at 16 48 00" src="https://github.com/user-attachments/assets/43b94853-2c97-412a-b3ab-0fd2934d64f2" />
## Overview

This repository contains a computational proof-of-concept for modelling seed viability decline across storage time using a literature-benchmarked simulation framework, survival-style analysis, and hybrid machine learning. The project was designed to provide an interpretable and extensible analytical scaffold for studying how storage temperature, moisture, oxygen environment, packaging condition, and seed storage behaviour class influence seed persistence.

The workflow explicitly separates three biologically distinct endpoints, viability, germination, and dormancy. It combines a mechanistic baseline inspired by classical seed longevity theory with discrete-time hazard modelling for threshold-based storage failure and a residual-learning layer for improved continuous prediction.

## Objectives

The project has five main aims. First, to simulate realistic longitudinal seed-lot data for orthodox, intermediate, and recalcitrant seed classes. Second, to model viability decline using biologically grounded relationships benchmarked to the seed science literature. Third, to separate viability, germination, and dormancy rather than treating germination alone as a proxy for seed life. Fourth, to estimate time-dependent risk of viability loss using survival-style modelling. Fifth, to test whether a hybrid machine-learning strategy can improve prediction beyond a mechanistic baseline.

## Repository contents

`seed_viability_model_proof_of_concept_fixed-2.ipynb`  
Main notebook containing the full proof-of-concept workflow with explanatory markdown, simulation code, modelling, visualization, and export steps.

`README.md`  
Repository overview, rationale, structure, and usage notes.

`modelcard.md`  
Model card describing the intended use, assumptions, inputs, outputs, limitations, and ethical considerations of the modelling workflow.

`datasheet.md`  
Datasheet describing the simulated dataset structure, variables, generation logic, intended use, and limitations.

`figures/`  
figures exported from the notebook.

`tables/`  
tables exported from the notebook.

## Scientific rationale

Seed longevity is shaped by a combination of environmental and biological factors. Classical storage theory shows that lower temperature and reduced seed moisture can prolong life span for orthodox seeds, but these relationships do not transfer straightforwardly to intermediate and recalcitrant seeds. In practical seed science, viability, germination, and dormancy are also related but not identical endpoints. The present project addresses these issues by using a modular workflow that can support future analysis of real longitudinal seed-lot datasets from conservation, agriculture, restoration, or seed-bank monitoring.

## Analytical workflow

The notebook follows this general structure:

1. Simulate longitudinal seed-lot data across storage duration.
2. Encode seed class, environmental conditions, and initial lot properties.
3. Generate separate trajectories for viability, germination, and dormancy.
4. Define a threshold failure event, viability below 50 percent.
5. Fit a discrete-time hazard model to estimate event risk.
6. Fit a mechanistic baseline model for continuous viability.
7. Learn residual error with gradient boosting to create a hybrid predictor.
8. Evaluate discrimination, calibration, regression fit, and feature importance.
9. Export publication-ready figures and tables.

## Inputs

The notebook uses simulated inputs representing:

- seed storage behaviour class
- storage duration
- storage temperature
- moisture content
- water activity proxy
- oxygen level
- packaging condition
- initial viability
- initial dormancy tendency
- seed-lot identity

## Outputs

The workflow generates:

- longitudinal viability trajectories
- longitudinal germination trajectories
- longitudinal dormancy trajectories
- threshold failure labels for survival-style modelling
- hazard-model predictions
- mechanistic baseline predictions
- hybrid residual-learning predictions
- calibration results
- permutation-importance results
- publication-ready figures and tables

## Intended use

This repository is intended for methodological demonstration, teaching, hypothesis development, and workflow prototyping. It is suitable for researchers who want a transparent starting point for future work on real seed-bank or experimental storage datasets. It is not intended to replace empirical seed testing or species-specific storage recommendations.

## Key limitations

This project is based on simulated rather than observed experimental data. The numerical results are therefore illustrative and should not be interpreted as validated predictions for any species, accession, or storage facility. The framework captures broad literature-consistent behaviour, but it simplifies several real biological complexities, including maternal effects, harvest maturity, pathogen burden, biochemical oxidative markers, and species-specific dormancy mechanisms.

## How to use

Open the notebook and run the cells in order. The notebook will simulate the dataset, perform the analysis, display figures and tables inline, and save exported outputs to local directories. Users can later replace the simulated data with real measurements while preserving much of the analytical structure.

## Suggested future extensions

Future versions could incorporate Bayesian hierarchical survival models, explicit oxygen and water-activity histories, censoring-aware seed-bank monitoring logic, biochemical ageing markers, species-specific parameter estimation, and comparison with alternative machine-learning methods such as gradient boosting survival models or neural time-to-event models.

## Citation
**Petalcorin, M.I.R.** (2026). Seed Viability Modelling Using Survival Analysis and Hybrid Machine Learning. https://github.com/mpetalcorin/seed-viability-hybrid-modelling

If you reuse or adapt this repository, cite the notebook and describe it as a literature-benchmarked computational proof-of-concept for seed viability modelling with mechanistic and hybrid machine-learning components.
