# LendingClub Credit Risk Modeling

An end-to-end credit-risk classification project that compares neural networks with interpretable and tree-based benchmarks on historical LendingClub loan outcomes.

The project focuses on the practical cost of class imbalance. Rather than selecting a model on accuracy alone, it compares recall, F1 score, and ROC-AUC, then translates estimated default probability into a business-facing pre-screening score.

## Highlights

- Reproducible 80/10/10 train, validation, and test split on a 200,000-row sample
- Regularized neural network with dropout and callback-based training
- Decision-threshold tuning and class-weighted learning
- Logistic Regression and Random Forest benchmarks
- Business-readable risk bands, screening recommendations, and risk flags
- Explicit discussion of limitations, bias, and responsible use

## Results

| Model | Accuracy | Recall | F1 score | ROC-AUC |
|---|---:|---:|---:|---:|
| Regularized ANN (0.5 threshold) | 0.8103 | 0.0238 | 0.0458 | 0.7102 |
| Threshold-tuned ANN (0.3) | 0.7738 | 0.3548 | 0.3744 | 0.7102 |
| Class-weighted ANN | 0.6528 | 0.6483 | **0.4160** | 0.7084 |
| Logistic Regression | — | **0.6680** | 0.4131 | — |
| Random Forest | — | 0.6208 | 0.4156 | — |

The class-weighted ANN was selected because it achieved the strongest F1 score while retaining high recall. The comparison is intentionally nuanced: the ANN does not dominate every metric, and the models have similar ranking performance.

![Class-weighted ANN confusion matrix](figures/figure_04.png)

## Repository structure

```text
.
├── data/
│   └── README.md
├── figures/
├── notebooks/
│   └── credit_risk_modeling.ipynb
├── results/
│   └── model_metrics.csv
├── .gitignore
├── LICENSE
└── requirements.txt
```

## Running the notebook

1. Create and activate a Python environment.
2. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Follow the instructions in `data/README.md`.
4. Open `notebooks/credit_risk_modeling.ipynb` and run the cells in order.

The notebook reads `data/lending_club_clean.feather` by default. You can instead set the `LENDINGCLUB_DATA` environment variable to an absolute path.

## Responsible-use note

This is an educational portfolio project, not an underwriting system or an official credit score. Historical lending data may encode socioeconomic and geographic bias. Any real lending application would require formal fairness testing, explainability, monitoring, regulatory review, and meaningful human oversight.

## Author

Yang Ren — [GitHub](https://github.com/yooyangr)

## License

The project code is released under the MIT License. The dataset is not redistributed and remains subject to its original terms.
