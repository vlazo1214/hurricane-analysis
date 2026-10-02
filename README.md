# Hurricane Analysis

This repository contains a comprehensive data analysis and machine learning workflow focused on hurricane-related data. The project explores patterns in hurricane characteristics, applies advanced preprocessing and feature engineering techniques, and evaluates multiple analytical approaches to uncover meaningful insights about hurricane intensity and behavior.

## Project Overview

This project demonstrates a full data science pipeline:
- **Data Cleaning & Preprocessing**: Transforms raw hurricane records into analysis-ready datasets
- **Exploratory Data Analysis (EDA)**: Investigates distributions, correlations, and patterns
- **Feature Engineering & Selection**: Identifies and ranks the most predictive variables
- **Dimensionality Reduction**: Applies PCA to reduce feature space while preserving variance
- **Clustering Analysis**: Groups hurricanes based on similar characteristics
- **Predictive Modeling**: Compares multiple machine learning algorithms (Random Forest, Gradient Boosting, Linear models, Elastic Net)
- **Model Evaluation**: Assesses performance and identifies the best approaches

## Repository Structure

```
hurricane-analysis/
├── data/
│   ├── hurricane_data.csv              # Original dataset
│   ├── cleaned_hurricanes.csv          # Cleaned data with environmental metadata
│   ├── cleaned_data.csv                # Cleaned baseline dataset
│   ├── train.csv & test.csv            # Initial train/test split
│   ├── final_train.csv & final_test.csv # Final processed train/test sets
│
├── data_cleaning/
│   ├── data_cleaning.ipynb             # Primary data preprocessing pipeline
│   └── ships.ipynb                     # Environmental variable integration
│
├── phase1/
│   ├── EDA.ipynb                       # Initial exploratory analysis
│   ├── metadata_exploration.ipynb      # Environmental data investigation
│   ├── feature_selection.ipynb         # Feature importance analysis
│   ├── Clustering & PCA.ipynb          # Dimensionality reduction & clustering
│   ├── RandomForest_GradientBoosting.ipynb  # Ensemble model comparison
│   ├── Lin&EN.ipynb                    # Linear & Elastic Net models
│   └── hurricane_data.csv              # Phase 1 dataset
│
├── final_eda.ipynb                     # Comprehensive final exploratory analysis
├── final_feature_selection.ipynb       # Final feature importance & selection
├── .gitignore
└── README.md
```

## Dataset Overview

The hurricane dataset contains **3,883–5,100 observations** (depending on processing stage) with **25 variables** describing:

### Storm Characteristics
- **Wind Speed**: 65–160 knots (mean ~87 knots)
- **Atmospheric Pressure**: 882–1,005 mb (mean ~968 mb)
- **Storm Diameter**: Tropical storm force (50–870 nm) and hurricane force (10–300 nm)
- **Hurricane Category**: 1–5 (Saffir-Simpson scale)
- **Hurricane Class**: Binary classification (0 = Category 1–2, 1 = Category 3–5)

### Environmental Variables (SHIPS Metadata)
- **CSST**: Climatological Sea Surface Temperature (111–300°K)
- **COHC**: Ocean Heat Content (0–141 kJ/cm²)
- **SHRD**: Vertical Wind Shear (1–650 knots)
- **RHMD**: Mid-level Relative Humidity (23–87%)
- **MTPW**: Mean Total Precipitable Water (289–709 mm)
- **VMPI**: Maximum Potential Intensity (0–183 knots)
- **DTL**: Distance to Land (0–2,431 km)

### Temporal & Geographic Data
- Year, month, day, hour
- Latitude & longitude

## Key Insights (from EDA)

### Class Imbalance
- Category 1 hurricanes dominate the dataset (52–53%)
- Category 5 hurricanes are rare (2–3%)
- Major hurricanes (Category 3–5): 27.3% of observations

### Strong Predictors of Hurricane Intensity
- **Wind Speed** (r = 0.85): Strongest positive correlation with major hurricane classification
- **Atmospheric Pressure** (r = -0.77): Strong negative correlation (lower pressure = more intense)
- **Latitude** (r = -0.30): Moderate negative correlation
- Environmental variables (CSST, COHC, MTPW, VMPI) show meaningful relationships with wind speed

### Data Distributions
- Wind speed: Right-skewed (most 65–100 knots, few extreme events)
- Pressure: Left-skewed (most 950–995 mb)
- SHIPS variables: Highly varied distributions reflecting diverse environmental conditions
- Distance to land: Strong right skew (many coastal observations, few far offshore)

## Notebooks Walkthrough

### Data Cleaning
- **`data_cleaning/data_cleaning.ipynb`**: Primary preprocessing pipeline
  - Handles missing values
  - Standardizes variable formats
  - Merges baseline and SHIPS environmental data
  
- **`data_cleaning/ships.ipynb`**: Integrates SHIPS environmental metadata

### Exploratory Analysis
- **`phase1/EDA.ipynb`**: Initial distribution and correlation analysis
- **`final_eda.ipynb`**: Comprehensive EDA including SHIPS variables
  - Summary statistics for traditional storm variables
  - Distribution analysis for all features
  - Correlation matrix and feature importance

### Feature Engineering & Selection
- **`phase1/metadata_exploration.ipynb`**: Investigates environmental variable behavior
- **`phase1/feature_selection.ipynb`**: Initial feature ranking and selection
- **`final_feature_selection.ipynb`**: Final feature importance evaluation
  - Identifies top predictive features
  - Guides feature space reduction

### Dimensionality Reduction & Clustering
- **`phase1/Clustering & PCA.ipynb`**: Principal Component Analysis
  - Reduces feature dimensionality
  - Analyzes variance explained
  - Enables visualization of high-dimensional data

### Predictive Modeling
- **`phase1/RandomForest_GradientBoosting.ipynb`**: Ensemble methods
  - Random Forest classification
  - Gradient Boosting comparison
  - Performance evaluation

- **`phase1/Lin&EN.ipynb`**: Linear models
  - Linear regression
  - Elastic Net regularization
  - Hyperparameter tuning

## Technologies & Libraries

- **Python 3.x**
- **Jupyter Notebook**: Interactive analysis environment
- **Pandas**: Data manipulation and cleaning
- **NumPy**: Numerical computation
- **Matplotlib & Seaborn**: Data visualization
- **scikit-learn**: Machine learning algorithms, PCA, clustering
- **Preprocessing & Modeling**: 
  - Feature scaling and normalization
  - Train/test splitting
  - Cross-validation
  - Model evaluation metrics

## Key Analyses

### Correlation Analysis
Wind speed and atmospheric pressure show the strongest correlations with hurricane classification, confirming their role as primary intensity indicators. Environmental variables (SHIPS) provide additional predictive value, particularly ocean heat content, wind shear, and maximum potential intensity.

### Class Imbalance Considerations
The dataset's imbalance toward weaker hurricanes is addressed through:
- Stratified train/test splitting
- Appropriate evaluation metrics (precision, recall, F1-score)
- Potential class weighting in models

### Feature Dimensionality
Initial feature space is 16+ dimensions. PCA analysis explores:
- Variance explained at different component levels
- Trade-offs between interpretability and dimensionality
- Optimal feature space for downstream modeling

## Workflow & Reproducibility

To run the analysis:

```bash
# Clone the repository
git clone https://github.com/vlazo1214/hurricane-analysis.git
cd hurricane-analysis

# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn jupyter

# Start Jupyter
jupyter notebook

# Run notebooks in order:
# 1. data_cleaning/data_cleaning.ipynb
# 2. data_cleaning/ships.ipynb
# 3. phase1/EDA.ipynb (or final_eda.ipynb for comprehensive version)
# 4. phase1/feature_selection.ipynb
# 5. phase1/Clustering & PCA.ipynb
# 6. phase1/RandomForest_GradientBoosting.ipynb
# 7. phase1/Lin&EN.ipynb
```

## Skills Demonstrated

✅ Data cleaning and preprocessing  
✅ Exploratory data analysis and visualization  
✅ Feature engineering and selection  
✅ Correlation and statistical analysis  
✅ Dimensionality reduction (PCA)  
✅ Clustering analysis  
✅ Machine learning model development and comparison  
✅ Hyperparameter tuning  
✅ Model evaluation and performance assessment  
✅ Jupyter notebook development and documentation  
✅ Python data science workflow  

## Future Enhancements

- Time series analysis of hurricane evolution
- Geographic/spatial analysis of hurricane patterns
- Deep learning approaches for intensity prediction
- Ensemble model stacking
- Interpretation of feature importance across models
- Interactive dashboard for results visualization

## License

This project is provided as-is for educational and analytical purposes. Please review repository ownership and usage restrictions before reuse.

## Contact

For questions or contributions, please refer to the repository owner: **vlazo1214**
