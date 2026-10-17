# Weka Result: meta.RotationForest

## Run Information

| Item | Value |
|---|---|
| Scheme | `weka.classifiers.meta.RotationForest -G 3 -H 3 -P 50 -F "weka.filters.unsupervised.attribute.PrincipalComponents -R 1.0 -A 5 -M -1 -D" -S 1 -I 10 -W weka.classifiers.trees.J48 -- -C 0.25 -M 2` |
| Relation | Cotton |
| Instances | 2700 |
| Attributes | 20 |
| Test mode | 10-fold cross-validation |
| Time taken to build model | 4.19 seconds |

## Stratified Cross-Validation Summary

| Metric | Value |
|---|---|
| Correctly Classified Instances | 2454 (90.8889 %) |
| Incorrectly Classified Instances | 246 (9.1111 %) |
| Kappa statistic | 0.8633 |
| Mean absolute error | 0.09 |
| Root mean squared error | 0.2104 |
| Relative absolute error | 20.242 % |
| Root relative squared error | 44.6335 % |
| Total Number of Instances | 2700 |

## Detailed Accuracy By Class

| Class | TP Rate | FP Rate | Precision | Recall | F-Measure | ROC Area |
|---|---|---|---|---|---|---|
| Low infection | 0.877 | 0.047 | 0.904 | 0.877 | 0.89 | 0.972 |
| Normal infection | 0.919 | 0.053 | 0.896 | 0.919 | 0.907 | 0.979 |
| High infection | 0.931 | 0.037 | 0.927 | 0.931 | 0.929 | 0.985 |
| **Weighted Avg.** | **0.909** | **0.046** | **0.909** | **0.909** | **0.909** | **0.979** |

## Confusion Matrix

| Actual \ Predicted | a (Low) | b (Normal) | c (High) |
|---|---|---|---|
| **a = Low infection** | 789 | 69 | 42 |
| **b = Normal infection** | 49 | 827 | 24 |
| **c = High infection** | 35 | 27 | 838 |

## Full Weka Output

The complete model output is long, so it is kept in a separate file: [Meta_RotationForest_90.89_full_output.txt](Meta_RotationForest_90.89_full_output.txt)
