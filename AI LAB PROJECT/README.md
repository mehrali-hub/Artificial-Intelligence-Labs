# Network Intrusion Detection - Course Project

This repository contains a complete, submission-ready AI/ML project for binary network intrusion detection using a simplified NSL-KDD style dataset.

## What Makes This Project Complete

- End-to-end notebook pipeline in [project_ai.ipynb](project_ai.ipynb)
- Dataset documentation in [dataset/README.md](dataset/README.md)
- Final written report in [report_template/report_template.tex](report_template/report_template.tex)
- Exported result tables in [outputs/final_model_ranking.csv](outputs/final_model_ranking.csv)

## Project Tasks Implemented

1. Data exploration and visual profiling
2. Simple reflex agent (rule-based AI)
3. Supervised classification:
   - KNN (with CV tuning)
   - Naive Bayes
   - Logistic Regression
4. K-Means clustering with cluster-to-label mapping and PCA visualization
5. Genetic algorithm feature selection with Logistic Regression comparison

## Final Highlights

- Best overall model: KNN (k=1)
- Test Accuracy: 0.9575
- Test F1-score: 0.9579
- GA reduced features (15 -> 11) with almost unchanged performance

## How To Run

1. Install dependencies:

```bash
pip install -r requirements.txt
```

2. Open [project_ai.ipynb](project_ai.ipynb)
3. Run all cells from top to bottom
4. Use exported CSV files in [outputs/final_model_ranking.csv](outputs/final_model_ranking.csv) and related files for report tables

## Report Notes

- Replace placeholder names/roll numbers in [report_template/report_template.tex](report_template/report_template.tex)
- Compile with your LaTeX editor (TeX Live, Overleaf, or MiKTeX)
- If your instructor requires embedded figures in PDF, export notebook plots as PNGs and include them in the report

