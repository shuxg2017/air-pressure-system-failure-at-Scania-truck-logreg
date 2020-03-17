# Air Pressure System (APS) Failure Classification

## Overview
**Task**: a binary classification task. <br>
**Goal**: minimize the cost. <br>
**Classes**: positive = APS failure, negative = others. <br>
**Method**: logistic regression. <br>
**Cost**: 1 false negative = 500 dollars <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
1 false positive = 10 dollars. <br>
**Result**: training cost = 52440 dollars, testing cost = 15690 dollars. <br>

## Process:
1. Dataset and Data Clean
2. Maxmin Normalization
3. Weighted Learning
4. Threshold Optimization
5. Results
6. Feature Engineer: calculate distance
7. Feature Engineer: calculate time2death

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

### 5. Results

### 6. Feature Engineer: calculate distance

### 7. Feature Engineer: calculate time2death
