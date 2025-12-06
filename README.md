# Brain Age Prediction from MRI Morphometric Features

A machine learning pipeline for predicting chronological age from structural MRI data using cortical surface area, thickness, and volumetric measurements derived from FreeSurfer parcellation.

## Overview

Brain age prediction has emerged as a powerful biomarker in neuroimaging research. The difference between predicted brain age and chronological age (brain age gap) has been associated with:
- Neurodegenerative diseases (Alzheimer's, Parkinson's)
- Psychiatric conditions (schizophrenia, depression)
- Cognitive decline and mortality risk

This project implements and compares multiple machine learning approaches for brain age prediction.

## Dataset

- **Sample size**: N=179 subjects
- **Features**: FreeSurfer-derived morphometric measurements
  - Cortical surface area (68 Desikan-Killiany regions)
  - Cortical thickness (68 regions)  
  - Subcortical volumes and global brain measures (ICV, total gray/white matter, etc.)

**Data Availability**: The neuroimaging data used in this project cannot be shared publicly due to ethical restrictions and institutional review board (IRB) requirements protecting participant privacy. The code is provided for methodological transparency and can be adapted for use with other FreeSurfer-derived datasets.

## Methods

### Models Evaluated

| Category | Models |
|----------|--------|
| Linear | Linear Regression, Lasso, ElasticNet |
| Tree-based | Random Forest, XGBoost, LightGBM, CatBoost |
| Neural Networks | MLP Regressor, TabNet |

### Evaluation
- 5-fold cross-validation
- Metrics: MAE (years), RMSE (years), R²

## Results

| Feature Set | Best Model | MAE | R² |
|-------------|------------|-----|-----|
| Thickness | Random Forest | 1.87 ± 0.21 | 0.613 ± 0.146 |
| Volume | LightGBM | 2.14 ± 0.19 | 0.468 ± 0.165 |
| Area | CatBoost | 2.28 ± 0.20 | 0.454 ± 0.164 |

**Key finding**: Cortical thickness measurements provide the strongest predictive signal for brain age.

## Project Structure

```
brain-age-prediction/
├── brain_age_prediction_mri.ipynb   # Main analysis notebook
├── requirements.txt                  # Python dependencies
├── README.md                        
└── data/
    ├── raw/                         # Original SPSS/CSV files
    └── processed/                   # Cleaned datasets
```

## Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/brain-age-prediction.git
cd brain-age-prediction

# Create virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

## Usage

1. Place your FreeSurfer-derived data files in `data/raw/`
2. Open and run `brain_age_prediction_mri.ipynb`
3. The notebook will:
   - Convert SPSS files to CSV (if needed)
   - Clean and preprocess the data
   - Train and evaluate all models
   - Output comparison metrics

## Requirements

- Python 3.8+
- See `requirements.txt` for full dependencies

## Future Directions

- [ ] Implement nested cross-validation for hyperparameter tuning
- [ ] Add feature importance analysis
- [ ] Include brain age gap correlation with clinical variables
- [ ] Implement stacking/ensemble methods
- [ ] Add visualization of predictions vs. actual age

## References

1. Cole, J. H., & Franke, K. (2017). Predicting age using neuroimaging: Innovative brain ageing biomarkers. *Trends in Neurosciences*, 40(12), 681-690.

2. Fischl, B. (2012). FreeSurfer. *NeuroImage*, 62(2), 774-781.

3. Arik, S. Ö., & Pfister, T. (2021). TabNet: Attentive Interpretable Tabular Learning. *AAAI Conference on Artificial Intelligence*.

## Project Info

This project was developed in 2024 as part of neuroimaging research.

## License

MIT License

## Contact

For questions or collaboration opportunities, please open an issue or reach out directly.