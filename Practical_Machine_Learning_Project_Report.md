Project Report of Practical Machine Learning
================
by Jack Mok

Introduction
------------

This report is for Practical Machine Learning Course Project.

Data Source
-----------

Training data : <https://d396qusza40orc.cloudfront.net/predmachlearn/pml-training.csv>

Testing data : <https://d396qusza40orc.cloudfront.net/predmachlearn/pml-testing.csv>

Source : <http://groupware.les.inf.puc-rio.br/har>

Backgroud
---------

-   In this project, we will be to use data from accelerometers on the belt, forearm, arm, and dumbell of 6 participants. They were asked to perform barbell lifts correctly and incorrectly in 5 different ways. More information is available from the website here: <http://groupware.les.inf.puc-rio.br/har> (see the section on the Weight Lifting Exercise Dataset).

Exploratory Analysis
--------------------

### Dataset Overview

-   This dataset is licensed under the Creative Commons license (CC BY-SA). Read more: [http://groupware.les.inf.puc-rio.br/har\#dataset\#ixzz4LROCJIrX](http://groupware.les.inf.puc-rio.br/har#dataset#ixzz4LROCJIrX)

-   Six young health participants were asked to perform one set of 10 repetitions of the Unilateral Dumbbell Biceps Curl in five different fashions: exactly according to the specification (Class A), throwing the elbows to the front (Class B), lifting the dumbbell only halfway (Class C), lowering the dumbbell only halfway (Class D) and throwing the hips to the front (Class E).

-   Read more: <http://groupware.les.inf.puc-rio.br/har#ixzz4LRQBWXBv>

### Data Loading and Cleaning

-   The dimension of training set is 13737 rows x 160 variables.

-   The dimension of test set is 5885 rows x 160 variables.

-   After remove NA value (Threshold : 95% NA) and the following Unrelevant variables : X, 'user\_name', 'raw\_timestamp\_part\_1', 'raw\_timestamp\_part\_2', 'cvtd\_timestamp', 'new\_window', 'num\_window'

-   The dimension of training set is 13737 rows x 53 variables.

-   The dimension of test set is 5885 rows x 53 variables.

-   The dimension of test case set is 20 rows x 53 variables.

Correlation Analysis
====================

![](https://github.com/jackskmok/Prediction-Assignment-Writeup/blob/master/figure/unnamed-chunk-4-1.png)

There are 53 predictor variables. Notice that clusters of higher positively correlated (darker blue) variables along the diagonal; this will also show the groupings of negatively correlated (darker red) variables throughout the dataset. This plot reveals that several groupings of variables with high correlations exist and that principal component analysis (PCA) may provide a suitable data reduction technique.

### Random Forest

    ## Confusion Matrix and Statistics
    ## 
    ##           Reference
    ## Prediction    A    B    C    D    E
    ##          A 1674    8    0    0    0
    ##          B    0 1130    5    0    0
    ##          C    0    1 1021    4    0
    ##          D    0    0    0  959    1
    ##          E    0    0    0    1 1081
    ## 
    ## Overall Statistics
    ##                                           
    ##                Accuracy : 0.9966          
    ##                  95% CI : (0.9948, 0.9979)
    ##     No Information Rate : 0.2845          
    ##     P-Value [Acc > NIR] : < 2.2e-16       
    ##                                           
    ##                   Kappa : 0.9957          
    ##  Mcnemar's Test P-Value : NA              
    ## 
    ## Statistics by Class:
    ## 
    ##                      Class: A Class: B Class: C Class: D Class: E
    ## Sensitivity            1.0000   0.9921   0.9951   0.9948   0.9991
    ## Specificity            0.9981   0.9989   0.9990   0.9998   0.9998
    ## Pos Pred Value         0.9952   0.9956   0.9951   0.9990   0.9991
    ## Neg Pred Value         1.0000   0.9981   0.9990   0.9990   0.9998
    ## Prevalence             0.2845   0.1935   0.1743   0.1638   0.1839
    ## Detection Rate         0.2845   0.1920   0.1735   0.1630   0.1837
    ## Detection Prevalence   0.2858   0.1929   0.1743   0.1631   0.1839
    ## Balanced Accuracy      0.9991   0.9955   0.9970   0.9973   0.9994

### Decision Tree

![](https://github.com/jackskmok/Prediction-Assignment-Writeup/blob/master/figure/unnamed-chunk-6-1.png)

### Model Evulation

-   The Accuracy of Random Forest is 0.9966015.
-   The Accuracy of Decision Tree is 0.6878505.
-   Therefore, using Random forest is more accurate than using Decision Tree.

Applying Selected Model to the test data
========================================

### Predict Results

    ##  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 
    ##  B  A  B  A  A  E  D  B  A  A  B  C  B  A  E  E  A  B  B  B 
    ## Levels: A B C D E
