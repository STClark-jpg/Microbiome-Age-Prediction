# Predicting Host Age from Gut Microbiome Composition (HMP WGS)
## Project Overview
  This project uses the HMP Phase I WGS dataset to build regression models that predict chronological age from microbial abundance profiles. The dataset includes participant level metadata (including age) and a large metagenomic sequencing table. 
The workflow includes:
1) Data Import (participant and assay table)
2) Cleaning and filtering
3) Selecting an adult-only subset (n=80)
4) Converting counts to relative abundance
5) Dimensionality reduction (PCA)
6) Regression Modeling (Linear Regression, Random Forest)
7) Evaluation with MAE and R^2
8) Visualization of model predictions
## Repository Structure
Microbiome-Age-Prediction
|
|-README.md
|-Ai.Usage.md
|-Week1_Microbiome.pynb
|-Week2_Microbiome.pynb
|-Week3_Microbiome
## Tools/Environment
1) Python 3.10 (Anaconda)
2) pandas
3) numpy
4) sckit-learn
5) matplotlib
# How to Reproduce
## Requirements
This project was developed using: 
1) Anaconda Distribution (Python 3.10)
2) JupyterLab (recommended) or Jupyter Notebook
3) Python packages (pandas, numpy, matplotlib, scikit-learn)
You can install missing packages using: pip install pandas numpy matplotlib scikit-learn
# Files Needed
Download the following WGS files from MicrobiomeDB (HMP Phase I) and place them in the same directory as the notebook
1) HMPWgs_Participant.txt
2) HMPWgs_Metagenomic_sequencing_assay.txt
# How to Run Week 1 Notebook
Step 1: Launch JupyterLab (From the Anaconda Navigator)
Step 2: Open the Notebook Week1_Microbiome.ipynb
Step 3: Run all Cells (Go to Run menu, Click Run all Cells)
The notebook will automatically
1) Load both HMP WGS fiiles
2) Extract and clean the age column
3) Merge participant metadata with assay
4) Filter to adults
5) Randomly select 80 participants
6) Convert microbial counts to relative abundance
7) Remove rare bactertial features
8) Generate plots: Age distribution histogram and PCA of microbiome features (colored by age) 
# Expected Outcome
Running the notebook will generate two figures: 
1) Age Distribution Histogram (shows age distrobution of the 80 selected adult participants)
2) PCA Colored by Age (Visualized sample clustering and age gradients in reduced dimensional space. 
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
The notebook will automatically: 
1) Load participant and WGS assay files
2) Extract the "Age (year)" column
3) Merge assay table with participant age
4) Remove unusable or missing rows
5) Convert microbial features to numeric
6) Downsample to 80 adult samples
7) Filter out zero features
# Model Training
1) Split data into training/test sets
2) Train Linear Regression
3) Train Random Forest
4) Compute performance metrics (MAE, R^2)
5) Plot True Age vs. Predicted Age
6) Generate plots: 1) Age distribution histogram 2) PCA scatterplot of WGS microbiome features 3) Random Forest True vs. Predicted Age plot
# Expected Outcome
Running this notebook will generate three figures: 
1) Age Distribution Histogram (shows ages of the subset of WGS participants used for modeling)
2) PCA Colored by Age (shows how WGS microbiome compositions vary across individuals)
3) Random Forest True vs. Predicted Age (scatter plot comparing model predictions to real ages) 
# Troubleshooting
Problem: "ValueError: could not convert string to float" (some assay columns contain non numeric annotations. This notebook filters these out
Problem: R^2 is negative (this is normal for high dimensional microbiome regression and small sample sizes
Problem: Notebook won't run in browser (Pyodide kernel) (switch to Python 3.10 (Anaconda) kernel
Problem: Files won't load (ensure filenames match exactly)
# Notes
Week 2 integrates machine learning, unlike Week 1 (only handled preprocessing and PCA)
Random Forest model generally performs better than Linear Regression
Week 3 will expand on hyparameter tuning and feature importance. 
# How to Run Week 3 Notebook
Step 1: Launch JupyterLab (from Anaconda Navigator)
Step 2: Open the Notebook (Week3_Microbiome.ipynb)
Step 3: Run All Cells (Go to Run menu, Click Run All Cells)
The notebook will automatically
1) Load all three WGS data files (Participant, Sample, and WGS assay table)
2) Clean column names and extract participant age
3) Merge participant metadata with microbial WGS abundance data
4) Convert microbial counts into numeric values
5) Drop non numeric or invalid rows that cause conversion errors
6) Randomly select 80 adults for modeling (same adult range used in Week 1 & Week 2)
7) Remove bactertial features that are zero across all samples
8) Standardize microbial abundance values for PCA and modeling
9) Generate PCA scatter plot colored by age
10) Train a Random Forest regressor to predict age
11) Plot predicted vs. actual age for the test set
12) Output performance metrics (MAE and R^2)
# Expected Outcome
Running the notebook will generate two figures:
1) PCA (WGS Microbiome Data (80 samples)
Visualizes clustering based on WGS abundance features, Color gradient corresponds to participant age.
2) Predicted vs. Actual Age (Random Forest)
Shows how well the model predicted chronological age. A diagonal reference line is added for comparison.
The notebook will also print:
1) Mean Absolute Error (MAE)
2) R^2 score
3) Shape of the filter feature matrix
4) Number of bacterial features retained after cleaning
# Troubleshooting
Problem: ValueError: could not convert strong to float
Cause: a microbial feature column contains non numeric text like "SRS024140 (WGS)". 
Fix: The notebook already applies:
1) assay_numeric = assay.apply(pd.to_numeric, error='coerce')
2) assay_numeric = assay_numeric.dropna()
If it still appears, verify that the correct WGS assay file is used.
Problem: PCA error - "Input X contains NaN"
Cause: Some rows still contain NaN after cleaning.
Fix: Esnure the notebook includes: X = X.dropna()
Problem: "Found array with 0 samples"
Cause: All rows were filtered out.
Fix: Usually caused by using the wrong filename or wrong column merge key. Verify filenames:
1) HMPWgs_Participant.txt
2) HMPWgs_Sample.txt
3) HMPWgs_Metagenomic_sequencing_assay.txt
Problem: Module errors (pands, skilearn, matplotlib not found)
Fix: Run in terminal: pip install pandas numpy matplotlib scikit-learn
# Notes
Week 3 focuses on final cleanup, dimensional reduction, and predictive modeling. 
Week 1 = Data Loading and Cleaning and Filtering
Week 2 = Modeling with early WGS dataset
Week 3 = Final WGS only modeling pipeline
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
Week 3 complete (tuning) /unfinished (feature inportance) due to error encountered 
