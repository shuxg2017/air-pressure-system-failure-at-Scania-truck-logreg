# Air Pressure System (APS) Failure Classification By Using Logistic Regression

## Overview
This is a binary classification task. We use logistic regression to classify whether it is APS failure or not. <br>
APS failure is the positive case, and others are the negative case. We are trying to minimize the cost from <br> 
detecting the APS failure. <br>
<br>
If we misclassify a positive case (1 false negative), we have to pay 500 dollars. <br>
If we misclassify a negative case (1 false positive), we have to pay 10 dollars. <br>
<br>
**The final result: cost of training dataset (52440) and cost of testing dataset (15690)** <br>

## What we did:
1. Dataset and Data Clean
2. Feature Engineer: calculate distance, calculate time2death
3. Maxmin Normalization
4. Weighted Learning
5. Threshold Optimization
6. Results

### Dataset and Data Clean
The dataset we have are highly imbalanced. <br>
Each sample has 170 features and 1 label. <br>
<br>
**Train dataset**

category	| positive | 	negative
------|------------|-----------
samples | 1000 |	59000

**Test dataset**

category	| positive | 	negative
------|------------|-----------
samples | 375 |	15625
