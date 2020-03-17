# Air Pressure System (APS) Failure Classification

## Overview
**Task**: a binary classification task. <br>
**Goal**: minimize the cost. <br>
**Classes**: positive = APS failure, negative = others. <br>
**Cost**: 1 false negative = 500 dollars <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
1 false positive = 10 dollars. <br>
**Method**: simple logistic regression. <br>
**Result**: training cost = 52440 dollars, testing cost = 15690 dollars. <br>
**What we tried but not working**: oversampleing, SMOTE and feature engineering.

## Process:
1. Dataset and Data Clean
2. Maxmin Normalization
3. Weighted Learning
4. Threshold Optimization
5. Best Results
6. Other Results
7. Training Plot
8. Feature Engineering

### 1. Dataset and Data Clean
The dataset we have are highly imbalanced. <br>
Each sample has 170 features and 1 label. <br>
<br>
**Training dataset**

category	| positive | 	negative
------|------------|-----------
samples | 1000 |	59000

**Testing dataset**

category	| positive | 	negative
------|------------|-----------
samples | 375 |	15625

**Data clean**

For training dataset, in each column, impute missing values by median of the current column respect on sample's class. <br>
For testing dataset, use mode from the training dataset. <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
In each column, impute missing values by mode of the column regardless of the sample's class. <br>

### 2. Maxmin Normalization

X = (X - X.min)/(X.max - X.min) <br>
Map X between 0 and 1. <br>

### 3. Weighted Learning

For highly imbalanced data, modify weights updating function.
Apply more weights on the minority class.

### 4. Threshold Optimization

 Threshold optimization is based on our training dataset.<br>
 
![threshold optimization](/results/threshold_optimization.png)

### 5. Best Results

Training cost | 	Testing cost
--------------|---------------
52440 |	15690

![confusion matrix](/results/confusion_matrix.png)

### 6. Other Results

Feature Engineer | SMOTE | Training cost | 	Testing cost
-----------------|-------|---------------|---------------
time2death | No | 62770 |	17370
distances | No | 54350 |	16860
distances | Yes | 54940 |	18100

### 7. Training Plot

**distance, SMOTE, 54940, 18100**<br>

Logistic Regression reaches its limit! <br>

![plots](/results/distance%20and%20SMOTE.png)

### 8. Feature Engineering

There are 70 columns/features corresponding to 7 bins. Here I won't mention the names of those columns. <br>
1 bin has 10 columns. <br>
<br>
**Calculating distance**: <br>
<br>
In each class, find those 70 columns' mean. <br>
Let's simplify the problem. We will use only one bin (10 columns) here. <br>
In this bin, calculate the positive and negative distances between the X and the means of 10 columns. <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
X has shape 60000 by 10, and positive/negative mean has shape 1 by 10. <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
**formular: distance = sqrt(sum(squre(X - means)))** <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
distance shape = 60000 by 2, because we have 2 distances. <br>
Thus for each bin, 60000 by 10 maps into 60000 by 2.<br>
<br>

**Calculating time2death**: <br>
<br>
To calculate time2death of each bin, sum up all 10 columns. <br>
Thus, 60000 by 10 maps into 60000 by 1.
