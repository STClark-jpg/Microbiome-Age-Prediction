# Predicting Host Age from Gut Microbiome Composition (HMP WGS)
## Project Overview
  This project uses the HMP Phase I WGS dataset to build regression models that predict chronological age from microbial abundance profiles. The dataset includes participant level metadata (including age) and a large metagenomic sequencing table. 
The workflow includes:
  Data Import (participant and assay table)
  Cleaning and filtering
  Selecting an adult-only subset (n=80)
  Converting counts to relative abundance
  Dimensionality reduction (PCA)
  Regression Modeling (Linear Regression, Random Forest)
  Evaluation with MAE and R^2
  Visualization of model predictions
## Repository Structure
Microbiome-Age-Prediction
|
|-README.md
|-Ai.Usage.md
|Week1Notebook.pynb
|Week2Notebook.pynb
## Tools/Environment
  Python 3m10 (Anaconda)
  pandas
	dfskdfsd
  numpy
  sckit-learn
  matplotlib
