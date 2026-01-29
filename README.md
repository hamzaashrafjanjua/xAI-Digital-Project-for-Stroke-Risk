# xAI-Digital-Project-for-Stroke-Risk

A comprehensive explainable AI (xAI) analysis of stroke risk prediction using machine learning models and advanced interpretability techniques. This project demonstrates the application of SHAP, LIME, Counterfactual Explanations, and ICE/PDP to understand and validate predictive models for clinical decision support.

## Project Overview

This project implements and evaluates multiple machine learning models for stroke risk prediction, with a strong emphasis on model explainability and interpretability. The analysis includes:

- **Predictive Modeling**: Random Forest, CatBoost, and XGBoost classifiers trained on comprehensive health metrics
- **Model Evaluation**: Performance metrics (accuracy, precision, recall, F1, ROC-AUC) with extensive comparative analysis
- **Global Explainability**: SHAP values, SP-LIME, and aggregated feature importance analysis
- **Local Explainability**: LIME-based local explanations with fidelity assessment
- **Feature Interaction Analysis**: ICE (Individual Conditional Expectation) and PDP (Partial Dependence Plots)
- **Counterfactual Analysis**: DiCE-based explanations showing actionable paths to prevent stroke
- **Clinical Validation**: Cohort-wise statistical analysis to ensure fairness and reliability across demographic groups

## Key Findings

### Model Performance
- **XGBoost** demonstrates higher risk-sensitivity and superior overall performance (higher recall), making it favorable for medical applications where missing high-risk cases is costly
- **Random Forest** offers more conservative predictions with greater stability and higher LIME fidelity scores, indicating more reliable local explanations
- **CatBoost** provides competitive performance with efficient handling of categorical variables

### Global Feature Importance (SHAP & SP-LIME)
- **Age** and **Average Glucose Level** consistently emerge as the two most influential features across all three models, aligning with medical literature and validating model trustworthiness
- SHAP values reveal both positive and negative contributions: elevated age and glucose levels increase stroke risk, while certain health metrics show protective effects
- SP-LIME aggregation identifies prototypical high-risk and low-risk patient profiles, enabling pattern recognition across the population

### Local Explanations & LIME Fidelity
- **LIME Fidelity Analysis**:
  - Random Forest achieves **higher average fidelity** (~0.35+) compared to XGBoost (~0.27), indicating more faithful local linear approximations
  - High-fidelity regions (R² > 0.6): LIME weights reliably represent directional influence and approximate magnitudes
  - Moderate-fidelity regions (0.3-0.6): LIME provides directional guidance but should be cross-verified with clinical judgment
  - Low-fidelity regions (< 0.3): Use LIME cautiously; flag instances for manual expert review
- **Key Insight**: Prior hypertension and heart disease show surprisingly low local influence weights, suggesting complex non-linear interactions that warrant clinical expertise review

### Feature Interactions (ICE/PDP Analysis)
- **Partial Dependence Plots (PDP)** reveal marginal effects of individual features on predicted stroke probability
- **ICE Plots** expose heterogeneity in feature effects across different patient profiles:
  - Non-monotonic relationships observed in glucose and age, indicating threshold effects
  - ICE curves cluster into distinct patterns, suggesting patient subgroups with different risk sensitivities
- **Key Finding**: The relationship between features and stroke risk is non-linear, with critical threshold regions where predictions change sharply
- Interaction analysis shows that age effects are modulated by glucose levels and cardiovascular history

### Counterfactual Explanations (DiCE)
- **Actionable Insights**: DiCE generates diverse counterfactual examples showing minimal feature changes needed to flip predictions
- **Clinical Applications**:
  - For high-risk patients: identifies which modifiable risk factors (e.g., glucose control, lifestyle) would most effectively reduce stroke risk
  - For borderline cases: reveals multiple pathways to achieve desired outcomes, allowing personalized intervention strategies
- **Proximity & Feasibility**: Counterfactuals respect data distributions and generate realistic recommendations within achievable ranges
- **Diversity**: Multiple alternative scenarios provide flexibility in choosing interventions based on patient preferences and feasibility

### Calibration Analysis
- Comprehensive cohort-wise analysis reveals model calibration patterns across age groups, smoking status, and cardiovascular history
- Identified calibration gaps inform threshold adjustments for clinical deployment
- Both models show better calibration for extreme risk cases (very high or very low probability) than for borderline cases

## Explainability Methods Explained

### SHAP (SHapley Additive exPlanations)
SHAP provides theoretically grounded explanations based on cooperative game theory. It calculates each feature's contribution to pushing the model's prediction from the base value to the actual prediction. SHAP values offer:
- **Global Interpretation**: Feature importance rankings and summary plots showing feature effects
- **Local Interpretation**: Per-instance explanations showing which features drive individual predictions
- **Force Plots**: Visualize how features combine to produce a prediction
- **Dependence Plots**: Show how feature values affect model outputs across the dataset

### LIME (Local Interpretable Model-agnostic Explanations)
LIME explains individual predictions by fitting local linear models around specific instances. This project uses LIME to:
- Understand decision-making for specific patients
- Assess explanation reliability via fidelity scores
- Identify cases where the linear approximation fails (low-fidelity regions)
- Provide directional guidance for borderline predictions

### ICE/PDP (Individual Conditional Expectation / Partial Dependence Plots)
These techniques visualize how individual features influence model predictions across the dataset:
- **PDP**: Shows the average marginal effect of a feature on predictions
- **ICE**: Reveals individual prediction curves for each instance, exposing heterogeneous feature effects
- **Application**: Identify threshold effects, non-linear relationships, and potential interactions

### Counterfactual Explanations (DiCE)
Counterfactuals provide "what-if" explanations by generating minimal changes to features that would flip model predictions:
- **Actionability**: Suggest realistic, achievable changes to improve outcomes
- **Diversity**: Generate multiple alternative scenarios
- **Proximity**: Ensure recommended changes are close to original feature values
- **Feasibility**: Respect constraints and data distributions

## Technical Stack

- **Data Processing**: pandas, NumPy
- **Machine Learning**: scikit-learn, CatBoost, XGBoost
- **Explainability**: 
  - SHAP (SHapley Additive exPlanations)
  - LIME (Local Interpretable Model-agnostic Explanations)
  - DiCE (Diverse Counterfactual Explanations)
  - PDPbox (Partial Dependence Plots)
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
    ├─ catboost_info/                  # Training artifacts
    └─ Configuration files
```

## Clinical Implications

This analysis demonstrates that machine learning models can provide clinically relevant stroke risk predictions when complemented with robust explainability techniques. Key recommendations for healthcare practitioners:

1. Model Selection: Prefer XGBoost for its superior recall in identifying at-risk patients; use Random Forest explanations as secondary validation
2. Global Insights: Rely on SHAP values and SP-LIME to understand population-level risk patterns and feature importance
3. Individual Predictions: Use LIME for local explanations, but verify with high-fidelity cases; supplement low-fidelity predictions with clinical judgment
4. Feature Effects: Consult ICE/PDP plots to understand non-linear relationships and identify threshold regions
5. Actionable Interventions: Leverage counterfactual explanations to develop personalized intervention strategies based on modifiable risk factors
6. Borderline Cases: For low-fidelity predictions, supplement model recommendations with clinical expertise and multiple explainability methods
7. Fairness: Review cohort-wise calibration gaps to ensure equitable care across demographic groups
8. Continuous Monitoring: Track model performance and explanations across new patient cohorts

## Contributing

For research, analysis, or contribution inquiries, please contact the project authors.

## License

This project is maintained for research and educational purposes.

## Authors

Hamza Ashraf Janjua, Pavitra Chandarana, Yan Jing, Minh Hai Tran.
