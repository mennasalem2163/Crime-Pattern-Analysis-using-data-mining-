# LA Crime Pattern Analysis

**Crime Pattern and Behavior Analysis in Los Angeles Using Data Mining and Machine Learning**

An academic project exploring spatial and temporal crime patterns in Los Angeles and their associations with community-level socioeconomic and health indicators. The workflow covers data integration, exploratory analysis, clustering, time-series analysis, predictive modeling, and association rule mining.

## Overview

The notebook integrates crime incident data with seven community profile themes: demographics, social determinants of health, physical activity and nutrition, housing and health, community safety, behavioral health, and healthcare access. A saved visualization stage operates on 1,002,705 incident rows.

The analysis explores:

- Frequent crime categories and their distribution across areas and time
- Associations between crime measures and community characteristics
- Neighborhood, temporal, and victim-demographic clusters
- Unusual weeks, seasonal trends, and recurring temporal motifs
- Classification of historically high-volume spatial cells
- A Part I/II classification experiment described in the report as severity prediction
- Crime-code regression experiments and SHAP explanations
- Co-occurring incident attributes using Apriori association rules

## Methods

| Area | Techniques |
|---|---|
| Data preparation | Merging, nearest-centroid neighborhood assignment, missing-value handling, encoding, scaling |
| Dimensionality reduction | Principal Component Analysis |
| Clustering | K-Means and hierarchical clustering |
| Temporal analysis | Isolation Forest, STL decomposition, STUMPY motif discovery |
| Classification | LightGBM and HistGradientBoostingClassifier |
| Regression | OLS, Linear Regression, Ridge, Lasso, Random Forest, XGBoost |
| Pattern mining | Apriori and association rules |
| Interpretation | Feature importance, SHAP, charts, and network visualizations |

## Repository Structure

- `notebooks/LA_Crime_Analysis.ipynb`: original notebook, including saved outputs
- `docs/Project_Report.pdf`: supplied academic project report
- `data/README.md`: expected dataset names and path setup
- `requirements.txt`: dependency list
- `.gitignore`: excludes datasets and generated model files

## Saved Experimental Results

The table uses outputs saved in the notebook. Training was not rerun during repository preparation. These tasks use different targets and cannot be ranked against one another.

| Experiment | Saved result |
|---|---|
| LightGBM Part I/II classification | Accuracy: 74.90%; macro F1: 0.7489 |
| HistGradientBoosting spatial hotspot classification | Accuracy: approximately 85%; ROC AUC: 0.9322 |
| XGBoost crime-code regression, including `part 1-2` | R²: 0.6834; RMSE: 0.1381 |
| XGBoost after removing `part 1-2` | R²: 0.1528; RMSE: 0.2260 |
| Tuned XGBoost with 20 selected features, without `part 1-2` | R²: 0.1605; RMSE: 0.2249 |

Regression errors use the notebook's transformed crime-code target scale. They are not errors in original crime-code units. The supplied report contains some different values and metric labels; use the notebook outputs when referring to the experiments packaged here.

## Setup

Google Colab is the most direct starting point because the notebook uses `/content/` paths and Google Drive mounting.

1. Open `notebooks/LA_Crime_Analysis.ipynb` in Colab.
2. Upload `requirements.txt` and install dependencies:

   ```python
   %pip install -r requirements.txt
   ```

3. Obtain the input datasets separately. See `data/README.md` for the exact file references.
4. Upload the inputs or mount your Google Drive.
5. Update the hardcoded file paths and `dataset_path`. Reconcile the inconsistent intermediate filenames described in the data notes.
6. Run the notebook in stages, checking each stage's outputs before continuing.

For local Jupyter, install the same dependencies, remove or replace Google Colab Drive-mount cells, and update all file paths. A large dataset, pairwise clustering, motif discovery, tuning, and SHAP calculations can require substantial memory and time.

The requirements list is not a locked or independently tested reproduction environment. The original notebook is preserved rather than rewritten as a standalone application.

## Interpretation and Evaluation Notes

- **Historical hotspots:** labels are constructed from full-data grid counts before a random split. This experiment does not establish future crime forecasting. A forecasting evaluation needs time-separated training and testing and labels defined for a future interval.
- **Crime codes:** these are categorical identifiers. Numerical regression is exploratory; crime-category classification would be a more interpretable target for further work.
- **Part I/II labels:** do not assume these categories are equivalent to violent versus nonviolent crime. The notebook uses inconsistent descriptive labels, which require checking against source definitions.
- **Associations:** community-level correlations do not establish causation or individual behaviour. Results about victims do not identify offender characteristics.
- **Spatial assignment:** nearest-centroid mapping approximates neighborhood membership; it does not use polygon boundaries.
- **Evaluation:** fit preprocessing and feature selection only on training data, sample only within training folds, and validate with held-out periods or areas before making generalization claims.
- **Association rules:** some rules contain original and cleaned versions of the same attribute. Remove duplicate representations before interpreting their lift as a substantive finding.

## Team

Hala Ahmed, Malak Amgad, Mena Osman, Menna Salem, Sama AbdelTawab, and Arwa Ahmed.

## Course

Data Mining - Artificial Intelligence & Computer Engineering. Instructor: Dr. Mohamed Abd Elaziz.

## Project Status

Academic exploratory analysis with saved experimental outputs. Raw data and trained model artifacts are not included.
