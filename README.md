# 2025-Y2-S1-MLB-B8G2-06

# Project Overview

This project implements a comprehensive data preprocessing pipeline for the "Students Performance Dataset." The goal is to clean, transform, and prepare the dataset for downstream tasks such as exploratory data analysis (EDA), machine learning modeling, or predictive analytics. The pipeline handles missing data, encodes categorical variables, creates new features, removes outliers, scales/normalizes data, and performs feature selection and dimensionality reduction.
The dataset includes student-related features such as demographics (e.g., Gender, Department), academic performance (e.g., Midterm_Score, Final_Score, Total_Score, Grade), behavioral factors (e.g., Study_Hours_per_Week, Stress_Level, Sleep_Hours_per_Night), and environmental factors (e.g., Parent_Education_Level, Family_Income_Level, Extracurricular_Activities, Internet_Access_at_Home). It appears to be a synthetic or anonymized dataset for educational purposes, likely containing around 100-1000 rows (exact shape printed during execution).

# Key outcomes:

Intermediate CSV files for each preprocessing step.
EDA visualizations (histograms, heatmaps, boxplots, scatter plots) saved in the results/eda_visualizations/ directory.
Final preprocessed dataset ready for modeling.

This is a group project with contributions from multiple members, each responsible for a specific preprocessing task.

# Dataset Details
Source: data/raw/Students Performance Dataset.csv (not included in this repo; assume it's a CSV file with student performance data).

# Key Columns:
Identifiers: Student_ID, First_Name, Last_Name, Email.
Categorical: Gender, Department, Grade, Parent_Education_Level, Family_Income_Level, Extracurricular_Activities, Internet_Access_at_Home.
Numerical: Midterm_Score, Final_Score, Assignments_Avg, Quizzes_Avg, Participation_Score, Projects_Score, Total_Score, Study_Hours_per_Week, Stress_Level (1-10), Sleep_Hours_per_Night.

# Assumptions:
Missing values are handled via mean (numerical) and mode (categorical) imputation.
Ordinal relationships exist in columns like Grade (A=4 to F=0), Parent_Education_Level (High School=0 to PhD=3), and Family_Income_Level (Low=0 to High=2).
Target variable: Total_Score (for feature selection); Grade is also encoded.

Size: Variable; shapes are printed during runtime (e.g., after outlier removal).
Potential Issues: Possible outliers in scores, zero values in hours (handled in feature creation), and multicollinearity (visualized in heatmap).

# Group Member Roles
Each member contributed a specific Jupyter notebook section, integrated into the combined Combined_Preprocessing_Notebook.ipynb:

IT24102297: Handling missing data (mean/mode imputation).
IT24102257: Encoding categorical variables (one-hot and ordinal encoding).
IT24102306: Feature creation (e.g., Average_Score, Study_Efficiency, Stress_Sleep_Ratio).
IT24102308: Outlier removal (IQR method).
IT24102225: Normalization and scaling (StandardScaler for z-score normalization).
IT24102298: Feature engineering (SelectKBest for selection, PCA for dimension reduction).

# Dependencies
Python 3.x

# Libraries (install via pip install -r requirements.txt):
pandas
numpy
matplotlib
seaborn
scikit-learn

# How to Run the Code

# Setup:
Clone the repository: git clone <repo-url>.
Place the raw dataset in data/raw/Students Performance Dataset.csv.
Create output directories:mkdir -p results/outputs
mkdir -p results/eda_visualizations


# Install Dependencies:
pip install -r requirements.txt


# Run the Notebook:

Open Jupyter: jupyter notebook.
Navigate to and run Combined_Preprocessing_Notebook.ipynb.
The notebook executes sequentially, loading from previous outputs. Each section times its runtime and prints progress.

# Outputs:
Intermediate CSVs: results/outputs/ (e.g., imputed_data.csv, final_preprocessed_data.csv).
Visualizations: results/eda_visualizations/ (e.g., eda_IT24102297_histogram.png).


# Results and Visualizations

Intermediate Files: Chain of CSVs showing transformations.
Visualizations:
Histograms: Distributions of scores (pre- and post-scaling).
Heatmap: Correlations among numerical features.
Boxplot: Numerical features after outlier removal.
Scatter Plot: PCA components (PC1 vs. PC2) colored by at-risk status (Total_Score < 60).


# Limitations and Future Work

Imputation and encoding methods are basic; consider advanced techniques (e.g., KNN imputation, target encoding).
Feature selection assumes linear relationships; explore non-linear methods.
No hyperparameter tuning (e.g., PCA components fixed at 5).
Extend to modeling (e.g., regression on Total_Score) or deployment.
