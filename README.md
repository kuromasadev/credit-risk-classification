# Credit Score Report



## Overview of the Analysis

The purpose of this analysis was to build a predictive model for assessing loan risk using a dataset containing financial information. The objective was to predict whether a loan would be categorized as a `0` (healthy loan) or a `1` (high-risk loan) based on various features provided in the data.

### about the data

The financial information in the dataset likely included attributes such as credit scores, income levels, loan amounts, interest rates, employment statuses, and more. These variables were used to predict whether a loan applicant's risk profile would be classified as healthy or high-risk.

In the initial analysis, we observed the distribution of labels to understand the class imbalance. By using the `value_counts` method, we determined that the dataset had an uneven distribution of loan labels, with potentially fewer high-risk loans compared to healthy loans.

### about the analysis methodology 

1. **Data Preprocessing:** Importing necessary libraries, reading the data, and separating the features (`X`) and labels (`y`). We also examined the data, checked for class imbalance, and divided it into training and testing sets.
2. **Model Training and Evaluation (Original Data):** We trained a logistic regression model on the original training data and evaluated its performance using various metrics like balanced accuracy, confusion matrix, and classification report.
3. **Oversampling:** Due to class imbalance, we used the `RandomOverSampler` technique to oversample the minority class (high-risk loans) in the training data to achieve better class balance.
4. **Model Training and Evaluation (Oversampled Data):** We trained another logistic regression model using the oversampled training data and evaluated its performance similar to the original model.

## Results

### Machine Learning Model V01:

The logistic regression model demonstrates a strong performance in predicting high-risk loans (label 1), with a precision of 0.86 and a recall of 0.91, indicating that it correctly identifies a substantial portion of actual high-risk loans while also minimizing the false positives.

| Class              | Precision | Recall  | F1-score | Support |
| ------------------ | --------- | ------- | -------- | ------- |
| 0 [low risk loan]  | 0.99693   | 0.995   | 0.99596  | 15001   |
| 1 [high risk loan] | 0.86008   | 0.90927 | 0.88399  | 507     |
| macro average      | 0.9285    | 0.95214 | 0.93998  | 15508   |
| weighted average   | 0.99245   | 0.9922  | 0.9923   | 15508   |

V01 Summary:

- The model demonstrates high precision (0.86) and recall (0.91) for predicting high-risk loans (label 1).
- It maintains strong precision (0.997) and recall (0.995) for predicting low-risk loans (label 0).
- The F1-score for predicting high-risk loans is also respectable at 0.884.

### Machine Learning Model V02:

The logistic regression model, fit with oversampled data, demonstrates excellent predictive performance for both the 0 (healthy loan) and 1 (high-risk loan) labels. With a precision of 85%, the model accurately identifies a significant portion of predicted high-risk loans that are indeed high-risk. Moreover, the high recall value of 0.99 indicates that the model effectively captures a vast majority of the actual high-risk loans. The F1-score of 92% further confirms the model's balanced performance in terms of precision and recall, reflecting its ability to make accurate predictions for both classes while considering their respective proportions.

| Class              | Precision | Recall  | F1-score | Support |
| ------------------ | --------- | ------- | -------- | ------- |
| 0 [low risk loan]  | 0.9998    | 0.99427 | 0.99703  | 15001   |
| 1 [high risk loan] | 0.85424   | 0.99408 | 0.91887  | 507     |
| macro average      | 0.92702   | 0.99418 | 0.95795  | 15508   |
| weighted average   | 0.99504   | 0.99426 | 0.99447  | 15508   |

V02 Summary:

- The model achieves a precision of 0.85 and an impressive recall of 0.99 for high-risk loans (label 1).
- For low-risk loans (label 0), it achieves extremely high precision (0.999) and good recall (0.994).
- The F1-score for predicting high-risk loans is notably improved at 0.919.



## Conclusions

Both models exhibit strengths in different areas. Model V01 shows balanced performance between precision and recall for both classes, while Model V02 excels in capturing high-risk loans with an impressive recall value.

The choice of which model to use depends on the problem's priorities. If correctly identifying high-risk loans is crucial (high recall for label 1), then Model V02 should be favored due to its superior recall and F1-score for high-risk loans. On the other hand, if a balance between precision and recall for both classes is desired, Model V01 can be a suitable option.

In situations where predicting high-risk loans is more critical (e.g., minimizing financial risk), **Model V02** with oversampled data would likely be the preferred choice due to its high recall for high-risk loans. 

