Agrochemical Classification Using Machine Learning
Project Overview
This project uses machine learning to classify agrochemical records
based on the label column in the dataset. It explores the dataset,
prepares the features, selects relevant features, and compares
classification models.
Dataset
The project uses dataset_final.csv, containing 1,035 rows and 13
columns.

Important columns include:
- name, CID, CAS, SMILES: chemical identification and
  representation fields
- source: source of the record
- year: year associated with the record
- toxicity_type: toxicity category
- herbicide, fungicide, insecticide, other_agrochemical:
  agrochemical category indicators
- label: binary target variable (0 or 1)
- ppdb_level: PPDB level associated with the record
The target variable is label. The current modelling workflow excludes
CID as an identifier and uses source and toxicity_type as
categorical predictors. The name, CAS, and SMILES fields are not
included in the basic preprocessing pipeline.
Important: Check how label was created before modelling. If
ppdb_level was used directly to define the label, including it as a
predictor could cause target leakage and produce misleadingly high
scores.

Project Workflow
1. Load the dataset and inspect its structure.
2. Review descriptive statistics and the target distribution.
3. Check and handle missing values.
4. Check for and remove duplicate rows.
5. Detect and cap numerical outliers using the IQR method.
6. Separate the target (label) from the predictor variables.
7. Split the data into training and testing sets using a stratified
   split.
8. Preprocess numerical and categorical features:
   - Numerical features: median imputation and standardisation
   - Categorical features: most-frequent imputation and one-hot
     encoding
9. Select the top 10 features using SelectKBest with f_classif.
10. Train and compare classification models.
11. Evaluate model performance using accuracy, precision, recall, and
    F1-score.
12. Visualise numerical-feature correlations with a heatmap.
Machine Learning Models
The workflow compares these models:
- Logistic Regression
- Decision Tree Classifier
- Random Forest Classifier
Evaluation Metrics
- Accuracy: Proportion of all predictions that are correct.
- Precision: Proportion of positive predictions that are correct.
- Recall: Proportion of actual positive cases that are correctly
  identified.
- F1-score: Harmonic mean of precision and recall.
The notebook calculates the metric values when the models are trained
and evaluated. No performance values are stated here because they depend
on the executed run.
Technologies and Libraries
- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
How to Run
1. Keep dataset_final.csv in the same folder as the Jupyter Notebook,
   or update the dataset path in the notebook.
2. Open the notebook in Jupyter Notebook or JupyterLab.
3. Run the cells in order, from data loading and preprocessing through
   model evaluation.
4. Review the printed evaluation metrics and the heatmap.
Notes
- The train-test split uses test_size=0.20, random_state=42, and
  stratification.
- Feature selection is fitted on the training data and then applied to
  the test data to avoid using test labels during feature selection.
- The heatmap is intended for exploring correlations; correlation does
  not establish causation.
- Results may vary if the dataset or modelling settings change.
