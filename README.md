# HEO-prediction
# Rebalancing and Extending an XGBoost Crystal-Structure Predictor for High-Entropy Oxides

## Overview

This project focuses on the design and prediction of crystal structures in High-Entropy Oxides (HEOs) using a combination of experimental materials science concepts and machine learning techniques.

The work demonstrates how configurational entropy stabilizes reversible single-phase solid solutions at high temperatures in multi-component oxides, highlighting their potential for green energy and advanced functional material applications.

To complement the experimental understanding, an XGBoost-based machine learning framework was developed to predict crystal structures directly from composition-based descriptors. The project addresses severe class imbalance in the original dataset and extends the predictor from a 3-class to a balanced 4-class classification problem.

The final model predicts the following crystal structures:

- Fluorite
- Rock-salt
- Spinel
- Perovskite

The improved model achieved:

- 92.6% test accuracy
- 0.927 macro F1-score
- Significant improvement in minority-class prediction performance

---

## Problem Statement

The original dataset was highly imbalanced:

| Structure Type | Percentage |
|---|---|
| Spinel | ~73% |
| Fluorite | ~15% |
| Rock-salt | ~11% |

Because of this imbalance, the model strongly favored predicting the dominant spinel class and performed poorly on minority structures.

The objective of this project was to:

1. Rebalance the dataset using literature-grounded synthetic data generation
2. Introduce a fourth crystal structure class: Perovskite
3. Improve minority-class prediction performance
4. Build a more chemically meaningful and reliable predictor

---

## Features Used

The model uses composition-only descriptors without any DFT-derived leakage.

Key engineered features include:

- Configurational entropy
- Valence electron concentration (VEC)
- Cation size mismatch
- Electronegativity difference
- Radius ratio
- Mixing enthalpy
- Omega parameter
- Number of components
- Element fraction encoding

---

## Machine Learning Pipeline

### Model
- XGBoost Classifier

### Data Processing
- Feature engineering from elemental properties
- Synthetic minority-class augmentation
- Class balancing
- Stratified train-test split

### Evaluation Metrics
- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix
- 10-fold cross validation

---

## Results

| Metric | Old Model | Improved Model |
|---|---|---|
| Accuracy | 76.8% | 92.6% |
| Macro F1 | 0.496 | 0.927 |
| Rock-salt F1 | 0.20 | 0.92 |

The improved model significantly reduced the tendency to overpredict the spinel phase while maintaining strong overall performance.

---

## Dataset Augmentation

Synthetic samples were generated using literature-supported element pools for:

- Fluorite oxides
- Rock-salt oxides
- Perovskites

Perovskite samples were generated using chemically realistic A-site-rich stoichiometry to reflect ABO3 structures.

---

## Repository Structure

```bash
.
├── augment_minority_classes.py
├── feature_engineering.py
├── train_model.py
├── interactive_predictor.py
├── make_report_figs.py
├── heo_augmented_dataset.csv
├── heo_model.pkl
└── README.md
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/your-username/your-repository-name.git
cd your-repository-name
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Usage

### Generate Augmented Dataset

```bash
python augment_minority_classes.py
```

### Train the Model

```bash
python train_model.py
```

### Generate Figures and Reports

```bash
python make_report_figs.py
```

### Run Interactive Predictor

```bash
python interactive_predictor.py
```

---

## Applications

This work has applications in:

- High-entropy oxide discovery
- Green energy materials
- Functional ceramics
- Data-driven materials design
- AI-assisted materials engineering

---

## Future Improvements

- Add more experimentally validated data from Materials Project and OQMD
- Extend perovskite coverage using Ba, Sr, and La systems
- Integrate advanced ensemble learning pipelines
- Explore graph neural networks for structure prediction

---

## Technologies Used

- Python
- XGBoost
- NumPy
- Pandas
- Scikit-learn
- Matplotlib

---


