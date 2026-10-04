# Hurricane Analysis: A Comprehensive Data Science Project

<div align="center">

![Hurricane Analysis](https://img.shields.io/badge/Python-Data%20Science-blue?style=flat-square)
![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat-square)
![Status](https://img.shields.io/badge/Status-Active-green?style=flat-square)

A complete end-to-end data science pipeline analyzing hurricane characteristics, intensity patterns, and predictive modeling of hurricane severity.

</div>

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Dataset Description](#dataset-description)
- [Repository Structure](#repository-structure)
- [Key Findings](#key-findings)
- [Technologies & Dependencies](#technologies--dependencies)
- [Workflow & Reproducibility](#workflow--reproducibility)
- [Skills Demonstrated](#skills-demonstrated)
- [Future Enhancements](#future-enhancements)
- [Contributing & Contact](#contributing--contact)

---

## 🌀 Project Overview

This repository demonstrates a **professional-grade data science workflow** applied to hurricane meteorological data. The project encompasses the complete data science lifecycle:

### Core Objectives
- **Understand hurricane characteristics** through exploratory data analysis
- **Identify key predictors** of hurricane intensity and classification
- **Engineer meaningful features** from raw meteorological and environmental variables
- **Build predictive models** to classify hurricane severity
- **Compare multiple algorithms** to determine optimal approaches
- **Evaluate model performance** using rigorous statistical methods

### Workflow Stages
1. **Data Cleaning & Preprocessing**: Transform raw records into analysis-ready datasets
2. **Exploratory Data Analysis (EDA)**: Investigate distributions, correlations, and patterns
3. **Feature Engineering & Selection**: Identify and rank predictive variables
4. **Dimensionality Reduction**: Apply PCA to reduce feature space while preserving variance
5. **Clustering Analysis**: Group hurricanes by similar characteristics
6. **Predictive Modeling**: Compare machine learning algorithms
7. **Model Evaluation**: Assess performance across multiple metrics

---

## 📊 Dataset Description

The hurricane dataset contains **3,883–5,100 observations** (depending on processing stage) with **25 variables** describing storm characteristics and environmental conditions.

### Storm Characteristics
| Variable | Range | Mean | Description |
|----------|-------|------|-------------|
| **Wind Speed** | 65–160 knots | ~87 knots | Maximum sustained winds |
| **Atmospheric Pressure** | 882–1,005 mb | ~968 mb | Central pressure measurement |
| **TS Force Diameter** | 50–870 nm | — | Tropical storm force wind extent |
| **H Force Diameter** | 10–300 nm | — | Hurricane force wind extent |
| **Hurricane Category** | 1–5 | — | Saffir-Simpson scale (1=weakest, 5=strongest) |
| **Hurricane Class** | 0 or 1 | — | Binary: 0 = Category 1–2, 1 = Category 3–5 |

### Environmental Variables (SHIPS Metadata)
| Variable | Range | Description |
|----------|-------|-------------|
| **CSST** | 111–300°K | Climatological Sea Surface Temperature |
| **COHC** | 0–141 kJ/cm² | Ocean Heat Content |
| **SHRD** | 1–650 knots | Vertical Wind Shear |
| **RHMD** | 23–87% | Mid-level Relative Humidity |
| **MTPW** | 289–709 mm | Mean Total Precipitable Water |
| **VMPI** | 0–183 knots | Maximum Potential Intensity |
| **DTL** | 0–2,431 km | Distance to Land |

### Temporal & Geographic Data
- **Time**: Year, month, day, hour of observation
- **Location**: Latitude and longitude coordinates

### Data Quality & Characteristics
- **Class Imbalance**: Category 1 hurricanes dominate (52–53%), while Category 5 are rare (2–3%)
- **Major Hurricanes**: Categories 3–5 represent 27.3% of observations
- **Missing Values**: Handled through multiple imputation and removal strategies
- **Feature Scaling**: Variables standardized for model compatibility

---

## 📁 Repository Structure

```
hurricane-analysis/
│
├── README.md                           # Project documentation (this file)
├── .gitignore                          # Git ignore rules
│
├── data/                               # Data directory
│   ├── hurricane_data.csv              # Original raw dataset
│   ├── cleaned_data.csv                # Cleaned baseline dataset
│   ├── cleaned_hurricanes.csv          # Cleaned data with environmental metadata
│   ├── train.csv & test.csv            # Initial train/test split
│   └── final_train.csv & final_test.csv # Final processed train/test sets
│
├── data_cleaning/                      # Data preprocessing notebooks
│   ├── data_cleaning.ipynb             # Primary data cleaning pipeline
│   │   └── Handles missing values, standardizes formats, merges datasets
│   └── ships.ipynb                     # Environmental variable integration
│       └── Adds SHIPS meteorological metadata
│
├── phase1/                             # Phase 1 analysis notebooks
│   ├── EDA.ipynb                       # Initial exploratory analysis
│   ├── metadata_exploration.ipynb      # Environmental data investigation
│   ├── feature_selection.ipynb         # Feature importance analysis
│   ├── Clustering & PCA.ipynb          # Dimensionality reduction & clustering
│   ├── RandomForest_GradientBoosting.ipynb # Ensemble model comparison
│   ├── Lin&EN.ipynb                    # Linear & Elastic Net models
│   └── hurricane_data.csv              # Phase 1 dataset
│
└── final_notebooks/                    # Final comprehensive analyses
    ├── final_eda.ipynb                 # Comprehensive exploratory analysis
    │   └── Summary statistics, distributions, correlations
    └── final_feature_selection.ipynb   # Final feature importance evaluation
        └── Top predictive features, feature space guidance
```

---

## 🔍 Key Findings

### Strong Predictors of Hurricane Intensity
The analysis identified the following variables as most predictive of major hurricane classification:

```
Wind Speed              r = +0.85  (Very Strong Positive)
Atmospheric Pressure   r = -0.77  (Very Strong Negative)
Latitude               r = -0.30  (Moderate Negative)
SHIPS Environmental Variables: Meaningful relationships with wind speed
```

**Interpretation**: 
- Higher wind speeds and lower atmospheric pressure are primary indicators of intensity
- Latitude shows moderate influence (e.g., latitude effects on storm dynamics)
- Environmental factors (temperature, humidity, shear) provide supplementary predictive power

### Data Distribution Insights
- **Wind Speed**: Right-skewed (most hurricanes 65–100 knots, few extreme events)
- **Pressure**: Left-skewed (most 950–995 mb)
- **Distance to Land**: Strong right skew (coastal concentration, few offshore systems)
- **SHIPS Variables**: Highly varied distributions reflecting diverse environmental conditions

### Class Imbalance
- Weak hurricanes (Category 1–2) dominate at ~73% of observations
- Major hurricanes (Category 3–5) represent ~27% of observations
- Addressed through stratified splitting, appropriate evaluation metrics, and potential class weighting

### Dimensionality & Feature Space
- Initial feature space: 16+ dimensions
- PCA analysis explores variance explained at different component levels
- Trade-offs identified between interpretability and dimensionality reduction

---

## 🛠️ Technologies & Dependencies

### Core Environment
- **Python 3.x**
- **Jupyter Notebook**: Interactive analysis and documentation

### Data Processing & Analysis
- **Pandas**: Data manipulation, cleaning, and transformation
- **NumPy**: Numerical computation and array operations
- **SciPy**: Statistical functions and advanced computations

### Visualization
- **Matplotlib**: Base plotting and figure generation
- **Seaborn**: Statistical data visualization and correlation heatmaps

### Machine Learning & Modeling
- **scikit-learn**: 
  - Classification algorithms (Random Forest, Gradient Boosting)
  - Regression models (Linear Regression, Elastic Net)
  - Dimensionality reduction (PCA)
  - Clustering (K-Means, Hierarchical)
  - Model evaluation (cross-validation, metrics)
  - Data preprocessing (scaling, train/test split)

### Installation
```bash
pip install pandas numpy scipy matplotlib seaborn scikit-learn jupyter
```

---

## 📖 Notebooks Walkthrough

### Data Preparation Phase

#### `data_cleaning/data_cleaning.ipynb`
- **Purpose**: Primary preprocessing pipeline
- **Tasks**:
  - Inspect raw data structure and quality
  - Handle missing values (imputation or removal)
  - Standardize variable formats and types
  - Address outliers and anomalies
  - Generate cleaned baseline dataset
- **Output**: `cleaned_data.csv`

#### `data_cleaning/ships.ipynb`
- **Purpose**: Integrate SHIPS environmental metadata
- **Tasks**:
  - Merge environmental variables with core storm data
  - Validate data consistency
  - Create enriched dataset with full feature set
- **Output**: `cleaned_hurricanes.csv`

### Exploratory Data Analysis Phase

#### `phase1/EDA.ipynb`
- **Purpose**: Initial exploratory analysis
- **Analysis**:
  - Univariate distributions and summary statistics
  - Histograms, box plots, and density plots
  - Correlation matrix and heatmap
  - Pairwise relationships of key variables

#### `final_eda.ipynb`
- **Purpose**: Comprehensive final exploratory analysis
- **Analysis**:
  - Extended summary statistics (including SHIPS variables)
  - Distribution analysis for all 25+ features
  - Correlation analysis with visualization
  - Insight generation and pattern discovery
  - Class distribution analysis

### Feature Engineering & Selection Phase

#### `phase1/metadata_exploration.ipynb`
- **Purpose**: Investigate environmental variable behavior
- **Analysis**:
  - SHIPS variable distributions and relationships
  - Temporal patterns and seasonal effects
  - Correlation with storm intensity

#### `phase1/feature_selection.ipynb`
- **Purpose**: Initial feature ranking and selection
- **Methods**:
  - Correlation-based filtering
  - Mutual information scoring
  - Feature importance from tree-based models
  - Statistical significance testing

#### `final_feature_selection.ipynb`
- **Purpose**: Final feature importance evaluation
- **Analysis**:
  - Comprehensive feature importance across multiple models
  - Ranking of predictive features
  - Guidance for feature space reduction
  - Interpretation and justification

### Dimensionality Reduction & Clustering Phase

#### `phase1/Clustering & PCA.ipynb`
- **Purpose**: Dimensionality reduction and cluster analysis
- **Methods**:
  - Principal Component Analysis (PCA)
  - Variance explained analysis
  - Scree plot interpretation
  - K-Means clustering
  - Cluster characterization
- **Output**: Reduced dimensional representations and cluster assignments

### Predictive Modeling Phase

#### `phase1/RandomForest_GradientBoosting.ipynb`
- **Purpose**: Ensemble method comparison
- **Models**:
  - Random Forest Classifier
  - Gradient Boosting Classifier
- **Evaluation**:
  - Cross-validation results
  - Confusion matrices
  - Precision, recall, F1-score
  - ROC-AUC analysis
  - Feature importance rankings

#### `phase1/Lin&EN.ipynb`
- **Purpose**: Linear and regularized regression models
- **Models**:
  - Linear Regression
  - Ridge Regression
  - Elastic Net (L1 + L2 regularization)
- **Methods**:
  - Hyperparameter tuning via grid search
  - Cross-validation for stability assessment
  - Regularization parameter optimization
  - Performance comparison with tree-based methods

---

## 🚀 Workflow & Reproducibility

### Running the Analysis Locally

```bash
# 1. Clone the repository
git clone https://github.com/vlazo1214/hurricane-analysis.git
cd hurricane-analysis

# 2. Install required dependencies
pip install pandas numpy scipy matplotlib seaborn scikit-learn jupyter

# 3. Launch Jupyter Notebook server
jupyter notebook

# 4. Execute notebooks in order:
```

### Recommended Execution Order
1. **`data_cleaning/data_cleaning.ipynb`** - Creates cleaned baseline
2. **`data_cleaning/ships.ipynb`** - Enriches with environmental data
3. **`phase1/EDA.ipynb`** - Initial exploration
4. **`final_eda.ipynb`** - Comprehensive EDA (alternative: more detailed)
5. **`phase1/feature_selection.ipynb`** - Feature ranking
6. **`final_feature_selection.ipynb`** - Final feature evaluation
7. **`phase1/Clustering & PCA.ipynb`** - Dimensionality reduction
8. **`phase1/RandomForest_GradientBoosting.ipynb`** - Ensemble models
9. **`phase1/Lin&EN.ipynb`** - Linear models

### Key Outputs Generated
- Cleaned datasets in `data/` directory
- Visualizations and plots within notebooks
- Model performance metrics and comparisons
- Feature importance rankings
- PCA transformations and cluster assignments

---

## ✅ Skills Demonstrated

This project showcases professional data science competencies across multiple domains:

### Data Management
✅ Data cleaning and preprocessing  
✅ Missing value imputation and outlier handling  
✅ Train/test splitting and cross-validation  
✅ Data merging and feature enrichment  

### Analysis & Visualization
✅ Exploratory data analysis (EDA)  
✅ Statistical analysis and hypothesis testing  
✅ Correlation and covariance analysis  
✅ Advanced visualization (heatmaps, distributions, relationships)  

### Feature Engineering
✅ Feature selection and ranking  
✅ Correlation-based filtering  
✅ Feature importance interpretation  
✅ Dimensionality reduction (PCA)  

### Machine Learning
✅ Classification model development  
✅ Multiple algorithm comparison (Random Forest, Gradient Boosting, Linear models)  
✅ Hyperparameter tuning and optimization  
✅ Cross-validation and performance evaluation  
✅ Clustering analysis (K-Means, Hierarchical)  

### Model Evaluation
✅ Confusion matrices and classification metrics  
✅ Precision, recall, F1-score, ROC-AUC  
✅ Cross-validation scoring  
✅ Comparative model analysis  

### Professional Development
✅ Jupyter notebook best practices  
✅ Code documentation and markdown explanation  
✅ Reproducible workflow design  
✅ Python data science workflow  

---

## 🔮 Future Enhancements

Potential extensions and advanced analyses:

### Temporal Analysis
- Time series decomposition of hurricane evolution
- Seasonal pattern analysis
- Historical trend identification
- Forecasting models for intensity progression

### Geographic Analysis
- Spatial analysis of hurricane tracks
- Regional pattern identification
- Proximity analysis and geographic clustering
- Heat maps of historical activity

### Advanced Modeling
- Deep learning approaches (Neural Networks, LSTM for sequences)
- Ensemble model stacking
- XGBoost and LightGBM comparison
- Bayesian methods for uncertainty quantification

### Interpretability & Insights
- SHAP values for model explanation
- Partial dependence plots
- Interaction effect analysis
- Decision boundary visualization

### Deployment & Visualization
- Interactive dashboard (Streamlit, Dash)
- API development for predictions
- Real-time data integration
- Automated reporting

---

## 📝 License

This project is provided as-is for educational and analytical purposes. Please review repository ownership and usage restrictions before reuse or redistribution.

---

## 👤 Contributing & Contact

### Questions or Contributions?
- **Repository Owner**: [@vlazo1214](https://github.com/vlazo1214)
- **Project Repository**: [hurricane-analysis](https://github.com/vlazo1214/hurricane-analysis)

Contributions, suggestions, and feedback are welcome! Please feel free to:
- Open issues for bugs or questions
- Submit pull requests with improvements
- Suggest new analyses or features

---

<div align="center">

**Made with ❤️ for data science and meteorological analysis**

*Last Updated: October 2026*

</div>
