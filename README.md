# Building Permits Classification Project
*Part of an ongoing personal portfolio exploring applied data science workflows.*

This project explores **City of Las Cruces building permit data** to predict permit categories using machine learning techniques.

### Project Overview
The goal is to build a classification model that identifies the *type of building permit* based on available attributes such as valuation, square footage, project type, and location.

### Tools & Libraries
- **Python** (pandas, numpy, matplotlib, path lib)
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


## Next Steps
This is a work in progress and will evolve over time. Upcoming tasks include:
- [x] Build a baseline Decision Tree classifier with selected attributes (excluding date and coordinates). Target initial accuracy >=75%.
- [x] Compare total vs. individual fee attributes.
- [x] Explore adding coordinates (cluster vs. trigonometric) and check performance impact.
- [x] Evaluate potential seasonal effect from permit issue dates.
- [ ] Test additional models (Random Forest, KNN, SVM, Logistic Regression, Gradient Boosting).
- [ ] Tune top model and document runtime.

## Data Source

Building permit data was obtained from the **City of Las Cruces Open Data Portal**:
https://communal-data-las-cruces.hub.arcgis.com/
 → Transactional Data → Building Permit

Data was downloaded as CSV on **October 26, 2025**.
Per City staff, the dataset is updated daily.

## Acknowledgments

This project is part of a personal learning journey in data analytics and machine learning.
Special thanks to the City of Las Cruces for maintaining public access to this dataset.