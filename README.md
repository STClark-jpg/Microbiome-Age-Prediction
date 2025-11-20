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
  numpy
  sckit-learn
  matplotlib
# How to Reproduce
## Requirements
This project was developed using: 
Anaconda Distribution (Python 3.10)
JupyterLab (recommended) or Jupyter Notebook
Python packages (pandas, numpy, matplotlib, scikit-learn)
You can install missing packages using: pip install pandas numpy matplotlib scikit-learn
# Files Needed
Download the following WGS files from MicrobiomeDB (HMP Phase I) and place them in the same directory as the notebook: 1) HMPWgs_Particpant.txt 2) HMPWgs_Metagenomic_sequencing_assay.txt
# How to Run Week 1 Notebook
Step 1: Launch JupyterLab (From the Anaconda Navigator)
Step 2: Open the Notebook Week1_Microbiome.ipynb
Step 3: Run all Cells (Go to Run menu, Click Run all Cells)
    The notebook will automatically: 1) Load both HMP WGS fiiles 2) Extract and clean the age column 3) Merge participant metadata with assay 4) Filter to adults 5) Randomly select 80 participants 6) Convert microbial counts to relative abundance 7) Remove rare bactertial features 8) Generate plots: Age distribution histogram and PCA of microbiome features (colored by age) 
# Expected Outcome
Running the notebook will generate two figures: 1) Age Distribution Histogram (shows age distrobution of the 80 selected adult participants) 2) PCA Colored by Age (Visualized sample clustering and age gradients in reduced dimensional space. 
# Troubleshooting
Problem: "ModuleNotFoundError: no module named pandas" (install missing modules using pip install pandas numpy matplotlib scikit-learn)
Problem: Kernal errors in the browser (switch to Anaconda Python 3.10 kernal, not Pyodide)
Problem: Cannot load the files (ensure filenames match exactly)
# Notes
This notebook performs no modeling. It focuses entirely on data import, cleaning, filteting, and visualization. Modeling is performed in Week 2.
# How to Run Week 2 Notebook
Step 1: Launch JupyterLab (from Anaconda Navigator)
Step 2: Open the Notebook Week2_Microbiome.ipynb
Step 3: Run all Cells (Go to Run menu, Click Run all Cells)
    The notebook will automatically: 1) Load participant and WGS assay files 2) Extract the "Age (year)" column 3) Merge assay table with participant age 4) Remove unusable or missing rows 5) Convert microbial features to numeric 6) Downsample to 80 adult samples 7) Filter out zero features
# Model Training
1) Split data into training/test sets
2) Train Linear Regression
3) Train Random Forest
4) Compute performance metrics (MAE, R^2)
5) Plot True Age vs. Predicted Age
6) Generate plots: 1) Age distribution histogram 2) PCA scatterplot of WGS microbiome features 3) Random Forest True vs. Predicted Age plot
# Expected Outcome
Running this notebook will generate three figures: 1) Age Distribution Histogram (shows ages of the subset of WGS participants used for modeling) 2) PCA Colored by Age (shows how WGS microbiome compositions vary across individuals) 3) Random Forest True vs. Predicted Age (scatter plot comparing model predictions to real ages) 
# Troubleshooting
Problem: "ValueError: could not convert string to float" (some assay columns contain non numeric annotations. This notebook filters these out
Problem: R^2 is negative (this is normal for high dimensional microbiome regression and small sample sizes
Problem: Notebook won't run in browser (Pyodide kernel) (switch to Python 3.10 (Anaconda) kernel
Problem: Files won't load (ensure filenames match exactly)
# Notes
Week 2 integrates machine learning, unlike Week 1 (only handled preprocessing and PCA)
Random Forest model generally performs better than Linear Regression
Week 3 will expand on hyparameter tuning and feature importance. 
# Data Source
Human Microbiome Project (HMP) Phase I
Whole Genome Shotgun (WGS) dataset
Accessed via MicrbiomeDB: https://microbiomedb.org
# References
MicrobiomeDB (2024). https://microbiomedb.org
scikit-learn Developers (2024). https://scikit-learn.org
# Status
Week 1 complete (data cleaning and PCA)
Week 2 complete (regression modeling)
Week 3 in progress (feature importance and tuning) 
