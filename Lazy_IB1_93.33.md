# Weka Result: lazy.IB1 (93.33%)

## Run Information

| Item | Value |
|---|---|
| Scheme | `weka.classifiers.lazy.IB1` |
| Relation | Cotton |
| Instances | 2700 |
| Attributes | 20 |
| Test mode | 10-fold cross-validation |
| Time taken to build model | 0.05 seconds |

**Attributes:** Objectsrowcoordinate, Objectscolumncoordinate, Area, Centroid(row), Centroid(column), Secondmoment, Perimeter, Eulernumber, Projections_1 to Projections_11, classes

## Stratified Cross-Validation Summary

| Metric | Value |
|---|---|
| Correctly Classified Instances | 2520 (93.3333 %) |
| Incorrectly Classified Instances | 180 (6.6667 %) |
| Kappa statistic | 0.9 |
| Mean absolute error | 0.0444 |
| Root mean squared error | 0.2108 |
| Relative absolute error | 10 % |
| Root relative squared error | 44.7214 % |
| Total Number of Instances | 2700 |

## Detailed Accuracy By Class

| Class | TP Rate | FP Rate | Precision | Recall | F-Measure | ROC Area |
|---|---|---|---|---|---|---|
| Low infection | 0.913 | 0.037 | 0.925 | 0.913 | 0.919 | 0.938 |
| Normal infection | 0.940 | 0.038 | 0.926 | 0.940 | 0.933 | 0.951 |
| High infection | 0.947 | 0.025 | 0.950 | 0.947 | 0.948 | 0.961 |
| **Weighted Avg.** | **0.933** | **0.033** | **0.933** | **0.933** | **0.933** | **0.950** |

## Confusion Matrix

| Actual \ Predicted | a (Low) | b (Normal) | c (High) |
|---|---|---|---|
| **a = Low infection** | 822 | 50 | 28 |
| **b = Normal infection** | 37 | 846 | 17 |
| **c = High infection** | 30 | 18 | 852 |

## Original Weka Output

```
=== Run information ===

Scheme:       weka.classifiers.lazy.IB1 
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

IB1 classifier

Time taken to build model: 0.05 seconds

=== Stratified cross-validation ===
=== Summary ===

Correctly Classified Instances        2520               93.3333 %
Incorrectly Classified Instances       180                6.6667 %
Kappa statistic                          0.9   
Mean absolute error                      0.0444
Root mean squared error                  0.2108
Relative absolute error                 10      %
Root relative squared error             44.7214 %
Total Number of Instances             2700     

=== Detailed Accuracy By Class ===

               TP Rate   FP Rate   Precision   Recall  F-Measure   ROC Area  Class
                 0.913     0.037      0.925     0.913     0.919      0.938    Lowinfection
                 0.94      0.038      0.926     0.94      0.933      0.951    Normalinfection
                 0.947     0.025      0.95      0.947     0.948      0.961    HighInfection
Weighted Avg.    0.933     0.033      0.933     0.933     0.933      0.95 

=== Confusion Matrix ===

   a   b   c   <-- classified as

 822  50  28 |   a = Lowinfection
  37 846  17 |   b = Normalinfection
  30  18 852 |   c = HighInfection
```
