# Fraud Detection on Unbalanced Data: An EDA-Driven Walkthrough

> This repo is a **learning artifact**, not a production system.
> The goal is to show *how to think* about fraud detection when the data is skewed, the signal is faint, and metrics can easily mislead.

---

## Project Overview

### Purpose

Fraud detection is deceptively hard. In the **STEG dataset**, fraud cases are rare, making naive modeling approaches and accuracy metrics misleading. This project emphasizes:

* Understanding data through Exploratory Data Analysis (EDA)
* Handling imbalanced datasets thoughtfully
* Making preprocessing and modeling decisions grounded in insight, not blindly chasing metrics
* Evaluating models with metrics that reflect operational value

The focus is on *learning and intuition*, rather than producing a deployable system.

### Context

The **Tunisian Company of Electricity and Gas (STEG)** suffered significant financial losses due to meter fraud. Using billing history, the task is to identify customers likely to commit fraud. This dataset provides a realistic scenario for exploring imbalance, feature skew, and subtle signals.

---

## Dataset Insights

### Challenges

* Highly **imbalanced classes** (fraud is rare)
* Non-normal distributions and skewed features
* Different class distributions in training vs. test sets
* Outliers and noisy data that can dominate naive models

### EDA Takeaways

EDA isn’t a formality—it’s the first modeling tool:

* Visualizing target distribution reframes the task: **we’re hunting needles in a haystack**
* Feature distributions reveal subtle shifts unique to fraud cases
* Early insights guide preprocessing, model choice, and evaluation metrics

---

## Preprocessing & Feature Decisions

* Removed mistaken or useless features (e.g., client ID)
* Normalized selected features sensitive to scale (e.g., consumption levels, indices)
* Merged training and test sets, then split again to mitigate distribution differences
* Applied **undersampling** to address imbalance
* Explored **label smoothing** to potentially improve model stability
* Every step evaluated to avoid **data leakage**, a critical risk in fraud detection

---

## Modeling & Evaluation

### Models Explored

* Logistic Regression
* Decision Tree Classifier
* Gradient Boosting Classifier
* CatBoost Classifier
* AdaBoost Classifier

### Evaluation Philosophy

* Accuracy alone is misleading—rare classes make it feel good without operational value
* Precision, recall, and precision–recall curves guide decision-making
* Baseline models help understand what “honest improvement” looks like

### Notable Result

The **Decision Tree Classifier** performed predictably and interpretable:

* Precision: 0.849
* Recall: 0.852
* Accuracy: 0.850

More complex models sometimes improved metrics but reduced trust—illustrating that **better-looking numbers don’t always equal better models**.

---

## Lessons Learned

* EDA can invalidate assumptions before modeling begins
* Simple, well-understood models often outperform complex ones in trust and stability
* Handling imbalance requires **trade-offs** and operational context
* More labeled fraud data, time-aware validation, and cost-sensitive evaluation would meaningfully change the approach

---

## Reproducibility & Next Steps

* Notebooks are designed to be run top-to-bottom and read like a narrative
* **[This Repo](https://github.com/AbdulrahmanElshafie/Fraud-Detection-EDA-on-STEG-Unbalanced-Dataset)** – treat as a learning resource, not a deployment guide
* Production-ready fraud detection systems require monitoring, feedback loops, concept drift detection, and human-in-the-loop review

This repo is a **map for thinking**, not a system to ship.
