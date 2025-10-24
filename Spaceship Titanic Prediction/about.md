Overview
This folder contains a complete, reproducible solution for the Kaggle “Spaceship Titanic” challenge, including a notebook, modeling approach, and generated submission CSVs for the classification task of predicting whether passengers were transported by the anomaly.​

Problem statement
Predict the binary label Transported for each passenger using structured tabular data recovered from the ship, optimizing for classification accuracy as defined by Kaggle’s metric.​

Dataset
Train/Test: Provided by the competition; do not commit raw data.​

Key fields commonly used: PassengerId, HomePlanet, CryoSleep, Cabin, Destination, Age, VIP, RoomService, FoodCourt, ShoppingMall, Spa, VRDeck, Name, Transported.​

Submission format: a CSV with two columns PassengerId and Transported, one row per test passenger.​

Evaluation
Metric: Classification accuracy, i.e., proportion of correct Transported predictions.​

Model selection and thresholding steps target improved accuracy on validation folds before generating the final submission.​

Approach summary
Preprocessing: type-safe parsing, missing-value imputation, categorical encoding, and scaling via sklearn pipelines/ColumnTransformer.​

Feature engineering: numeric aggregation of expenditures (e.g., RoomService, FoodCourt, ShoppingMall, Spa, VRDeck), cabin-derived features, and selective transformations to improve separability.​

Models: gradient boosting ensemble stack with LightGBM, XGBoost, and CatBoost as base learners, optionally a Random Forest baseline.​

Ensembling: meta-model with Logistic Regression on out-of-fold base predictions; optional weighted voting/averaging and decision threshold tuning.​

Validation: Stratified K-Fold cross-validation to preserve class balance and estimate generalization.​

Reproducibility
Environment: requirements.txt lists core dependencies (pandas, numpy, scikit-learn, lightgbm, xgboost, catboost, scipy).​

Running: open the notebook in notebooks/ and Run All; it will read train/test from data/, fit models, and write a dated submission into submissions/.​

Outputs: submission CSVs named like submission-YYYYMMDD.csv stored under submissions/.​

Folder structure
notebooks/: main analysis and training notebook for Spaceship Titanic.​

submissions/: generated submission CSVs for Kaggle upload.​

data/: expected location for train/test CSVs (excluded from version control).​

Optionally src/: reusable preprocessing and training scripts if the notebook is refactored.​

Results snapshot
The notebook logs out-of-fold performance and final submission creation; keep the best run’s metrics noted here along with the corresponding submission filename.​

Include your public leaderboard score and date once submitted to Kaggle to track progress across iterations.​

How to use
Place competition CSVs into data/ following Kaggle’s dataset layout.​

Install dependencies with pip install -r requirements.txt.​

Execute the notebook to reproduce features, training, validation, and submission file generation.​

Notes and best practices
Do not commit raw data or kaggle.json; instruct users to configure the Kaggle API locally.​

Keep submissions versioned and named by date/score to trace experiments.​

Document any deviations (e.g., alternative imputers, different encoders, or modified fold strategies) in a short changelog within this about.md.​

Citation
MEHER BAMRAH and Kanchan Rai. Weekly ML Challenge: Spaceship Titanic Prediction. “https://kaggle.com/competitions/spaceship-titanic-dataset”, 2025. Kaggle.