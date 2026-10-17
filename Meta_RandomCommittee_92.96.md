# Weka Result: meta.RandomCommittee

## Run Information

| Item | Value |
|---|---|
| Scheme | `weka.classifiers.meta.RandomCommittee -S 1 -I 10 -W weka.classifiers.trees.RandomTree -- -K 0 -M 1.0 -S 1` |
| Relation | Cotton |
| Instances | 2700 |
| Attributes | 20 |
| Test mode | 10-fold cross-validation |
| Time taken to build model | 1.19 seconds |

## Stratified Cross-Validation Summary

| Metric | Value |
|---|---|
| Correctly Classified Instances | 2510 (92.963 %) |
| Incorrectly Classified Instances | 190 (7.037 %) |
| Kappa statistic | 0.8944 |
| Mean absolute error | 0.0471 |
| Root mean squared error | 0.1913 |
| Relative absolute error | 10.5954 % |
| Root relative squared error | 40.5913 % |
| Total Number of Instances | 2700 |

## Detailed Accuracy By Class

| Class | TP Rate | FP Rate | Precision | Recall | F-Measure | ROC Area |
|---|---|---|---|---|---|---|
| Low infection | 0.91 | 0.038 | 0.922 | 0.91 | 0.916 | 0.968 |
| Normal infection | 0.936 | 0.037 | 0.926 | 0.936 | 0.931 | 0.978 |
| High infection | 0.943 | 0.03 | 0.94 | 0.943 | 0.942 | 0.976 |
| **Weighted Avg.** | **0.93** | **0.035** | **0.93** | **0.93** | **0.93** | **0.974** |

## Confusion Matrix

| Actual \ Predicted | a (Low) | b (Normal) | c (High) |
|---|---|---|---|
| **a = Low infection** | 819 | 45 | 36 |
| **b = Normal infection** | 40 | 842 | 18 |
| **c = High infection** | 29 | 22 | 849 |

## Full Weka Output

The complete model output is long, so it is kept in a separate file: [Meta_RandomCommittee_92.96_full_output.txt](Meta_RandomCommittee_92.96_full_output.txt)
