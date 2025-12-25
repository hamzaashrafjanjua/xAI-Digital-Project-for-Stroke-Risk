# xAI-Digital-Project-for-Stroke-Risk
Implementing xAI Techniques on "healthcare-dataset-stroke"

## Repository structure

```
xAI-Digital-Project-for-Stroke-Risk/
├─ README.md
├─ data/
│  └─ healthcare-dataset-stroke-data.csv
└─ notebooks/
	└─ digitalProject.ipynb
```

## How to run the notebook

1. Open `notebooks/digitalProject.ipynb` in VS Code (recommended) or Jupyter.
2. Ensure the Python environment has the required packages:
	- pandas, matplotlib, seaborn
	- scikit-learn, imbalanced-learn
	- xgboost, catboost
	- dice-ml (for counterfactuals)

If needed, install them (example commands):

```bash
pip install -U pandas matplotlib seaborn scikit-learn imbalanced-learn xgboost catboost dice-ml
```

3. The notebook expects the dataset at `../data/healthcare-dataset-stroke-data.csv` relative to the notebook location. The provided notebook already uses this path.
4. Run cells from top to bottom. A roadmap cell at the top outlines the analysis steps (data loading, cleaning, SMOTE, models: RF/XGBoost/CatBoost, metrics, feature importances, counterfactual analysis with DiCE, and conclusions).

## Notes

- Tree-based models are generally robust to outliers; however, the notebook removes a few clinically implausible cases to improve explanation quality.
- In healthcare settings, recall is emphasized to reduce false negatives. The notebook’s grid search prioritizes recall accordingly.

