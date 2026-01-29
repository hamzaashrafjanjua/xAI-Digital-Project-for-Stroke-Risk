# xAI-Digital-Project-for-Stroke-Risk

A comprehensive explainable AI (xAI) analysis of stroke risk prediction using machine learning models and local interpretability techniques. This project demonstrates the application of LIME (Local Interpretable Model-agnostic Explanations) and other xAI methods to understand and validate predictive models for clinical decision support.

## Project Overview

This project implements and evaluates multiple machine learning models for stroke risk prediction, with a strong emphasis on model explainability and interpretability. The analysis includes:

- **Predictive Modeling**: Random Forest and XGBoost classifiers trained on comprehensive health metrics
- **Model Evaluation**: Performance metrics (accuracy, precision, recall, F1, ROC-AUC) with extensive comparative analysis
- **Explainability Analysis**: LIME-based local explanations, feature importance analysis, and fidelity assessment
- **Clinical Validation**: Cohort-wise statistical analysis to ensure fairness and reliability across demographic groups
- **Counterfactual Analysis**: DiCE-based explanations showing actionable paths to prevent stroke

## Key Findings

### Model Performance
- **XGBoost** demonstrates higher risk-sensitivity and superior overall performance (higher recall), making it favorable for medical applications where missing high-risk cases is costly
- **Random Forest** offers more conservative predictions with greater stability and higher LIME fidelity scores, indicating more reliable local explanations

### Feature Importance
- **Age** and **Average Glucose Level** emerge as the two most influential features in both models, aligning with medical literature and validating model trustworthiness
- Prior hypertension and heart disease show surprisingly low local influence weights, suggesting complex non-linear interactions that warrant clinical expertise review

### LIME Fidelity Insights
- Random Forest achieves **higher average fidelity** (~0.35+) compared to XGBoost (~0.27), indicating more faithful local linear approximations
- **High-fidelity regions** (R² > 0.6): LIME weights reliably represent directional influence and approximate magnitudes
- **Moderate-fidelity regions** (0.3-0.6): LIME provides directional guidance but should be cross-verified with clinical judgment
- **Low-fidelity regions** (< 0.3): Use LIME cautiously; flag instances for manual expert review

### Calibration Analysis
- Comprehensive cohort-wise analysis reveals model calibration patterns across age groups, smoking status, and cardiovascular history
- Identified calibration gaps inform threshold adjustments for clinical deployment
- Both models show better calibration for extreme risk cases (very high or very low probability) than for borderline cases

## Technical Stack

- **Data Processing**: pandas, NumPy
- **Machine Learning**: scikit-learn, CatBoost, XGBoost
- **Explainability**: LIME (Local Interpretable Model-agnostic Explanations), DiCE (Diverse Counterfactual Explanations)
- **Visualization**: Matplotlib, Plotly
- **Documentation**: Jupyter Notebook

## Repository Structure

```
xAI-Digital-Project-for-Stroke-Risk/
├─ README.md                           # Project documentation
├─ digitalProject.ipynb                # Main analysis notebook
├─ healthcare-dataset-stroke-data.csv  # Dataset
├─ Project Initial Outline.pdf         # Project specifications
└─ Misc/                               # Supporting materials
    ├─ SeminarPaper_Blueprint/         # LaTeX paper source
    ├─ catboost_info/                  # Training artifacts
    └─ Configuration files
```

## Getting Started

### Prerequisites
- Python 3.8+
- Jupyter Notebook
- Required libraries: pandas, numpy, scikit-learn, xgboost, catboost, lime, dice-ml, matplotlib, plotly

### Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/hamzaashrafjanjua/xAI-Digital-Project-for-Stroke-Risk.git
   cd xAI-Digital-Project-for-Stroke-Risk
   ```

2. Open the Jupyter notebook:
   ```bash
   jupyter notebook digitalProject.ipynb
   ```

3. Execute cells sequentially to:
   - Load and explore the healthcare dataset
   - Train Random Forest and XGBoost models
   - Generate LIME local explanations
   - Analyze fidelity and calibration metrics
   - Visualize counterfactual examples

## Clinical Implications

This analysis demonstrates that machine learning models can provide clinically relevant stroke risk predictions when complemented with robust explainability techniques. Key recommendations for healthcare practitioners:

1. **Model Selection**: Prefer XGBoost for its superior recall in identifying at-risk patients
2. **Explanation Trust**: Use Random Forest-derived LIME explanations as primary decision support due to higher fidelity
3. **Borderline Cases**: For low-fidelity predictions, supplement model recommendations with clinical expertise
4. **Fairness**: Review cohort-wise calibration gaps to ensure equitable care across demographic groups
5. **Continuous Monitoring**: Track model performance and explanations across new patient cohorts

## Contributing

For research, analysis, or contribution inquiries, please contact the project author.

## License

This project is maintained for research and educational purposes.

## Author

Hamza Ashraf Janjua
