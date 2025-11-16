# Building Permits Classification Project
*Part of an ongoing personal portfolio exploring applied data science workflows.*

This project explores **City of Las Cruces building permit data** to predict permit categories using machine learning techniques.

### Project Overview
The goal is to build a classification model that identifies the *type of building permit* based on available attributes such as valuation, square footage, project type, and location.

### Tools & Libraries
- **Python** (pandas, numpy, matplotlib, path lib, scikit-learn, time, XGBoost, seaborn)
- **Jupyter Notebooks** for analysis and model training

### Folder Structure
building_permits/
├── data/
│   ├── raw/ → original datasets  
│   └── processed/ → cleaned datasets  
├── notebooks/ → Jupyter notebooks  
├── scripts/ → Python scripts  
├── outputs/ → visualizations, models, and reports  
├── requirements.txt → full environment snapshot  
└── requirements_min.txt → minimal install for running notebooks

## Steps to Date
### Data Import & Cleaning
- [x] Import raw dataset
- [x] Check types
- [x] Missing values
    - [x] Remove missing targets
    - [x] Mean/Median/Mode/Remove missing attributes
- [x] Save cleaned dataset to folder & make copy DataFrame

### Baseline Decision Tree & Attribute Selection
- [x] Create a baseline Decision Tree classifier with selected attributes (excluding date and coordinates). Target initial accuracy >=75%.
    - [x] Use one-hot-encoding for 'Project'
    - [x] Save results (accuracy, weighted precision, weighted recall, weighted f1, feature importance) to list of dictionaries for later use
    - [x] Compare total vs. **individual** fee attributes.
    - [x] Explore adding coordinates and check performance impact.
    - There are four options:
        - [x] Use direct coordinates with no processing
        - [x] Convert to spherical coordinates with trigonometric processing
        - [x] **Cluster** analysis
        - Distance based calculation to central feature. As the locations are dispersed and not centrally located around any feature, this will not be explored.
    - [x] Calculate number of clusters with elbow method & silhouette score
    - [x] Group by cluster & compare mean values
    - [x] Plot Mean CDFEE / Mean project_valuation for each cluster and see if there are any interpretable results.
    - [x] Check for interactions for deeper relationships
    - [x] Explore seasonality for permit types

## Testing Multiple Models
- [x] Test multiple models
    - [x] **Decision Tree** - A single tree that can model complex patterns but can be sensitive to small data changes. Serves as a baseline for comparison, especially with ensemble methods.
        - _**Result**: Performed well, with accuracy slightly below ensemble models and well above other models._
    - [x] **Random Forest** - An ensemble of Decision Trees that generally improves performance.
        - _**Result**: Performed slightly better than the single Decision Tree._
    - [x] **Logistic Regression** - Best suited for binary, evenly distributed data. Unlikely to perform well on this dataset.
        - _**Result**: Accuracy was poor with a multi-class, uneven dataset._
    - [x] **Naive Bayes** - Assumes all features are independent, which is not true for this dataset.
        - _**Result**: Accuracy was poor confirming the assumption of independence doesn't fit this dataset._
    - [x] **K Nearest Neighbors (KNN)** - Works best when nearby data points share similar labels; can be sensitive to scaling & noise. This model is expected to perform at mid-level at best.
        - _**Result**: moderate performance given the dataset features._
    - [x] **Support Vector Machine (SVM)** - Performs best with smaller datasets with clear class boundaries.
        - _**Result**: Lower performance as expected on a complex, mixed-type dataset._
    - [x] **XGBoost** - An ensemble model like Random Forest, but instead of parallel development, a sequential format where each tree informs the next. This is likely to increase performance over both Decision Tree and Random Forest.
         - _**Result**: Best overall performance, validating expectations for boosted models._
         
## Next Steps
This is a work in progress and will evolve over time. Planned next steps include:
- [ ] Tune XGBoost model hyperparameters to improve performance
- [ ] Validate model stability by testing across data subsets and random seeds
- [ ] Analyze feature influence to undertand key drivers behind predictions
- [ ] Finalize and expport model
- [ ] Finalize documentation of process

## Data Source
Building permit data was obtained from the **City of Las Cruces Open Data Portal**:
https://communal-data-las-cruces.hub.arcgis.com/
 → Transactional Data → Building Permit

Data was downloaded as CSV on **October 26, 2025**.
Per City staff, the dataset is updated daily.

## Acknowledgments
This project is part of a personal learning journey in data analytics and machine learning.
Special thanks to the City of Las Cruces for maintaining public access to this dataset.