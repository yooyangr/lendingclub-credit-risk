# Methodological and Model-Governance Notes

## What the analysis establishes

This project evaluates out-of-sample predictive performance within a historical LendingClub sample. It shows that choices about class weights and decision thresholds materially change which errors a classifier makes. It also shows that a comparatively complex ANN does not clearly dominate simpler benchmarks on the reported metrics.

## What the analysis does not establish

The models estimate associations useful for prediction; they do not identify causal effects. A feature's predictive contribution does not mean that changing the feature would change repayment behavior. Likewise, the analysis does not estimate the welfare effect of adopting a model, the fairness of a lending policy, or the effect of access to credit.

## Why accuracy is misleading here

When most loans are repaid, a classifier can achieve high accuracy while detecting very few defaults. The regularized ANN at the default threshold illustrates this problem: its accuracy is 0.8103, but recall is only 0.0238. Reporting the confusion matrix, recall, F1 score, and ROC-AUC makes the trade-off visible.

## Thresholds are institutional choices

A lower threshold sends more cases to review and can reduce missed defaults, but it also increases false positives and reviewer workload. Selecting a threshold therefore requires explicit assumptions about:

- the relative consequences of false negatives and false positives;
- the capacity and quality of human review;
- whether predicted probabilities are calibrated;
- legal and organizational constraints; and
- how applicants can contest or correct a decision.

The notebook's threshold is an analytic demonstration, not a deployment recommendation.

## Bias and fairness

Historical platform data reflect prior eligibility rules, applicant self-selection, underwriting decisions, economic conditions, and measurement practices. A model can reproduce those patterns even when protected attributes are excluded. Without appropriate demographic information and a legally reviewed audit design, the project cannot make claims about group fairness.

Relevant future checks include subgroup error rates, calibration by group, proxy analysis, intersectional sample adequacy, and evaluation of the downstream review process. Quantitative parity measures should be interpreted alongside the institutional and legal context.

## Human-centered deployment requirements

A responsible decision-support workflow would require:

1. clearly defined roles for the model and the human reviewer;
2. interpretable reasons and access to supporting evidence;
3. an applicant correction or appeal pathway;
4. monitoring for data drift, calibration decay, and changing error rates;
5. versioned documentation and audit logs; and
6. periodic review of whether the system improves decisions rather than merely accelerating them.

These safeguards are part of the information system, not external additions to the model.
