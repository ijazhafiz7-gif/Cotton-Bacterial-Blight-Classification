# Weka Result: lazy.IBk (93.22%)

## Run Information

| Item | Value |
|---|---|
| Scheme | `weka.classifiers.lazy.IBk -K 1 -W 0 -A "weka.core.neighboursearch.LinearNNSearch -A \"weka.core.EuclideanDistance -R first-last\""` |
| Relation | Cotton |
| Instances | 2700 |
| Attributes | 20 |
| Test mode | 10-fold cross-validation |
| Nearest neighbours used | 1 |
| Time taken to build model | 0 seconds |

**Attributes:** Objectsrowcoordinate, Objectscolumncoordinate, Area, Centroid(row), Centroid(column), Secondmoment, Perimeter, Eulernumber, Projections_1 to Projections_11, classes

## Stratified Cross-Validation Summary

| Metric | Value |
|---|---|
| Correctly Classified Instances | 2517 (93.2222 %) |
| Incorrectly Classified Instances | 183 (6.7778 %) |
| Kappa statistic | 0.8983 |
| Mean absolute error | 0.0451 |
| Root mean squared error | 0.2086 |
| Relative absolute error | 10.1567 % |
| Root relative squared error | 44.2445 % |
| Total Number of Instances | 2700 |

## Detailed Accuracy By Class

| Class | TP Rate | FP Rate | Precision | Recall | F-Measure | ROC Area |
|---|---|---|---|---|---|---|
| Low infection | 0.912 | 0.038 | 0.922 | 0.912 | 0.917 | 0.963 |
| Normal infection | 0.938 | 0.038 | 0.924 | 0.938 | 0.931 | 0.972 |
| High infection | 0.947 | 0.025 | 0.950 | 0.947 | 0.948 | 0.976 |
| **Weighted Avg.** | **0.932** | **0.034** | **0.932** | **0.932** | **0.932** | **0.970** |

## Confusion Matrix

| Actual \ Predicted | a (Low) | b (Normal) | c (High) |
|---|---|---|---|
| **a = Low infection** | 821 | 51 | 28 |
| **b = Normal infection** | 39 | 844 | 17 |
| **c = High infection** | 30 | 18 | 852 |

## Original Weka Output

```
=== Run information ===

Scheme:       weka.classifiers.lazy.IBk -K 1 -W 0 -A "weka.core.neighboursearch.LinearNNSearch -A \"weka.core.EuclideanDistance -R first-last\""
Relation:     Cotton
Instances:    2700
Attributes:   20
              Objectsrowcoordinate
              Objectscolumncoordinate
              Area
              Centroid(row)
              Centroid(column)
              Secondmoment
              Perimeter
              Eulernumber
              Projections_1
              Projections_2
              Projections_3
              Projections_4
              Projections_5
              Projections_6
              Projections_7
              Projections_8
              Projections_9
              Projections_10
              Projections_11
              classes
Test mode:    10-fold cross-validation

=== Classifier model (full training set) ===

IB1 instance-based classifier
using 1 nearest neighbour(s) for classification

Time taken to build model: 0 seconds

=== Stratified cross-validation ===
=== Summary ===

Correctly Classified Instances        2517               93.2222 %
Incorrectly Classified Instances       183                6.7778 %
Kappa statistic                          0.8983
Mean absolute error                      0.0451
Root mean squared error                  0.2086
Relative absolute error                 10.1567 %
Root relative squared error             44.2445 %
Total Number of Instances             2700     

=== Detailed Accuracy By Class ===

               TP Rate   FP Rate   Precision   Recall  F-Measure   ROC Area  Class
                 0.912     0.038      0.922     0.912     0.917      0.963    Lowinfection
                 0.938     0.038      0.924     0.938     0.931      0.972    Normalinfection
                 0.947     0.025      0.95      0.947     0.948      0.976    HighInfection
Weighted Avg.    0.932     0.034      0.932     0.932     0.932      0.97 

=== Confusion Matrix ===

   a   b   c   <-- classified as

 821  51  28 |   a = Lowinfection
  39 844  17 |   b = Normalinfection
  30  18 852 |   c = HighInfection
```
