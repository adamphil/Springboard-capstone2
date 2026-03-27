# Springboard-capstone2
# Predicting the Compressive Strength of High‑Performance Concrete
This project applies machine learning techniques to predict the compressive strength of high‑performance concrete (HPC) based on its material composition and age. The work explores feature engineering, model development, hyperparameter tuning, and optimization to identify the most influential factors affecting concrete strength.

# 📌 Project Overview

High‑performance concrete is an engineered material that incorporates conventional components (cement, water, aggregates) along with supplementary materials such as blast furnace slag, fly ash, and superplasticizers. These additions improve performance but also increase modeling complexity.
This project investigates:
- Which mixture components and ratios most strongly influence compressive strength
- Whether machine learning models can accurately predict strength from composition and age
- How optimized mixtures can be identified using the best‑performing model

# 📂 Dataset
- Source: UCI Machine Learning Repository
- Entries: 1030 (reduced to 996 after deduplication)
- Features (kg/m³ unless noted):
- Cement
- Blast Furnace Slag
- Fly Ash
- Water
- Superplasticizer
- Coarse Aggregate
- Fine Aggregate
- Age (days)
- Target: Compressive Strength (MPa)

# 🧪 Feature Engineering
To better capture known material science relationships, several ratio‑based features were created:
- Water:Cement
- Water:Binder
- Superplasticizer:Binder
- Fly Ash:Binder
- Slag:Binder
- (Slag + Fly Ash):Binder
These ratios help model the chemical and physical interactions that drive strength development.

# ⚙️ Preprocessing
- Row‑wise normalization of mixture components
- Min‑max scaling of Age
- 80/20 train‑test split

# 🤖 Models Used
Three regression models were evaluated:
- Linear Regression
- Random Forest Regressor
- Gradient Boosting Regressor
Hyperparameters
Random Forest
- n_estimators=250
- max_depth=None
- min_samples_leaf=1
- min_samples_split=2
Gradient Boost
- n_estimators=500
- learning_rate=0.2

# 📊 Model Performance
Linear Regression
R²: 0.66
MAE: 7.42
RMSE: 9.25

Random Forest
R²: 0.92
MAE: 3.32
RMSE: 4.52

Gradient Boost
R²: 0.93
MAE: 2.81
RMSE: 4.26

Gradient Boosting achieved the best performance and was used for downstream optimization.

# 🔧 Optimization
Using scipy.optimize, the project explored mixture compositions that maximize predicted compressive strength according to the Gradient Boost model. This demonstrates how machine learning can support practical engineering decisions in mixture design.

# 📌 Key Findings
- Gradient Boosting provides highly accurate predictions of compressive strength.
- Water‑cement ratio and age are the most influential predictors.
- Ratio‑based feature engineering significantly improves model performance.
- Optimization techniques can propose high‑strength mixture designs before physical testing.

# 📈 Recommendations for Clients
- Optimize mix designs virtually to reduce material waste and accelerate R&D.
- Enhance quality control by monitoring water‑cement ratio and using model predictions to flag weak batches early.
- Support engineering proposals with data‑driven strength predictions and mixture comparisons.

# 📁 Repository Structure
├── data/                 # Raw and processed data (not included in repo)
├── notebooks/            # Jupyter notebooks for EDA, modeling, and optimization
├── models/               # Saved model artifacts (optional)
├── metrics/              # Model metrics TXT file
├── src/                  # Source code for preprocessing and modeling
└── README.md             # Project documentation

# 🚀 Future Work
- Incorporate additional performance metrics (tensile strength, durability, thermal resistance)
- Explore deep learning models for nonlinear interactions
- Build a user‑friendly interface for mix design optimization
