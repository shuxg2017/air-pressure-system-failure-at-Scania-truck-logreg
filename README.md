# Air Pressure System (APS) Failure Classification

## Overview
**Task**: a binary classification task. <br>
**Goal**: minimize the cost. <br>
**Classes**: positive = APS failure, negative = others. <br>
**Method**: logistic regression. <br>
**Cost**: 1 false negative = 500 dollars <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
1 false positive = 10 dollars. <br>
**Result**: training cost = 52440 dollars, testing cost = 15690 dollars. <br>

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
