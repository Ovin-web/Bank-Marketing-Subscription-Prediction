# Bank Marketing Subscription Prediction

A data mining project that investigates whether customer and previous-campaign information can help identify clients more likely to subscribe to a bank term deposit.

## Project question

Can customer and previous-campaign information identify clients more likely to subscribe to a term deposit before a marketing call?

## Objective

Explore the UCI Bank Marketing dataset, prepare the data, and build an interpretable Decision Tree classifier to support better-targeted marketing decisions.

## Dataset

- **Source:** UCI Machine Learning Repository — [Bank Marketing](https://archive.ics.uci.edu/dataset/222/bank+marketing)
- **File used:** `bank-full.csv`
- **Records:** 45,211
- **Original attributes:** 17
- **Target:** `y` — whether the client subscribed to a term deposit (`yes` or `no`).

The target is imbalanced: approximately 11.7% of records are positive subscriptions and 88.3% are non-subscriptions.

## Method

The project includes data understanding, exploratory analysis, preprocessing, classification, evaluation, and discussion.

- **Mining task:** Binary classification.
- **Model:** Decision Tree classifier.
- **Leakage prevention:** `duration` is excluded because call duration is not known before a marketing call.
- **Preprocessing:** Median imputation for numerical variables, most-frequent imputation and one-hot encoding for categorical variables. The `pdays = -1` sentinel is handled using a separate indicator for whether the client was previously contacted.
- **Evaluation:** Stratified train/test split, majority-class baseline, confusion matrix, precision, recall, F1-score, ROC-AUC, and stratified five-fold cross-validation.

## Current evaluation results

On the held-out test set, the Decision Tree achieved:

| Metric | Score |
|---|---:|
| Accuracy | 0.8233 |
| Precision | 0.3412 |
| Recall | 0.5482 |
| F1-score | 0.4206 |
| ROC-AUC | 0.7489 |

The majority-class baseline achieved 0.8830 accuracy but zero precision and recall for the subscription class. This illustrates why accuracy alone is insufficient for this imbalanced classification problem.

## Repository contents

The analysis notebook, one-page findings summary, and supporting project files will be added here as the project artifacts are finalized.

## Responsible use and limitations

The model identifies statistical associations, not causes. Its predictions should be treated as decision support rather than automatic decisions about customers. The relatively low positive-class precision means many customers flagged by the model may not subscribe. Any practical use should include human oversight, privacy safeguards, and monitoring for performance and fairness across customer groups.

## Reproducibility

The notebook will document the analysis workflow and the exact preprocessing/model pipeline. Install the Python dependencies listed in `requirements.txt`. See `data/README.md` for dataset access instructions.
