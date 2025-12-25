# xAI-Digital-Project-for-Stroke-Risk
Implementing xAI Techniques on "healthcare-dataset-stroke"

## Repository structure

```
xAI-Digital-Project-for-Stroke-Risk/
├─ README.md
├─ digitalProject.ipynb
└─ healthcare-dataset-stroke-data.csv
```

## How to run the notebook

1. Open `digitalProject.ipynb` in VS Code (recommended) or Jupyter.
2. Ensure the Python environment has the required packages:
	 - pandas, matplotlib, seaborn
	 - scikit-learn, imbalanced-learn
	 - xgboost, catboost
	 - dice-ml (for counterfactuals)

If needed, install them (example commands):

```bash
pip install -U pandas matplotlib seaborn scikit-learn imbalanced-learn xgboost catboost dice-ml
```

3. The notebook expects the dataset at `healthcare-dataset-stroke-data.csv` in the repository root (same folder as the notebook). The provided notebook already uses this path.
4. Run cells from top to bottom. A roadmap cell at the top outlines the analysis steps (data loading, cleaning, SMOTE, models: RF/XGBoost/CatBoost, metrics, feature importances, counterfactual analysis with DiCE, and conclusions).

## Notes

- Tree-based models are generally robust to outliers; however, the notebook removes a few clinically implausible cases to improve explanation quality.
- In healthcare settings, recall is emphasized to reduce false negatives. The notebook’s grid search prioritizes recall accordingly.

## Collaboration workflow

To keep the notebook up to date and avoid clashing when multiple people work:

- Use branches
	- Create a feature branch per task: `git checkout -b feature/<short-name>`
	- Open a Pull Request to merge into `main` when ready.
	- Keep PRs small and focused for easy review.

- Pull before you start and before you push
	- Always run `git pull --rebase` on your branch to replay your changes on top of the latest remote.
	- Resolve any conflicts locally; test; then push.

- Avoid noisy notebook diffs
	- This repo is configured to strip notebook outputs on commit (nbstripout), so commits don’t include large output diffs.
	- nbdime is enabled globally for notebook-aware diffs/merges, making conflict resolution clearer.

- Commit discipline
	- Write clear messages about what changed and why.
	- Prefer many small commits over a single large one.

- Data files
	- The dataset is kept at the repository root as `healthcare-dataset-stroke-data.csv`. If you plan to commit very large files or frequent changes, consider Git LFS.

- Reviews and protection (on GitHub)
	- Enable branch protection on `main` and require PR reviews and status checks.
	- Optionally require linear history to encourage `--rebase` workflows.

### Typical work cycle

```bash
# start from up-to-date main
git checkout main
git pull

# create a branch
git checkout -b feature/refactor-eda

# do work, commit
git add digitalProject.ipynb
git commit -m "Refactor EDA section: cleaner plots, no outputs committed"

# rebase on latest and push
git pull --rebase
git push -u origin feature/refactor-eda

# open a PR, get review, merge, then clean up
```

