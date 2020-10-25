
# Starbucks-ml-model
The reward program is a representative marketing method that induces users to purchase. But program that user are not interested in, user may unsubscribe corporate marketing channels or have a negative image. That’s why it’s important to send a SMS, email of reward program to interested users. In this case, the user’s interest is determined by whether or not the user has viewed the program. By creating a model that predicts whether users will see the program, you can deliver the right program to the right users.

## Table of Contents
1. Requirements
1. Project structure
1. Installation
1. Model Training
1. Result


## Requirements
1. Basic Statistics
1. Python3
1. Library usages
1.



## Project Structure
### data/ 
downloaded file from https://www.kaggle.com/blacktile/starbucks-app-customer-reward-program-data)
- data/portfolio.json
- data/profile.json
- data/trainscript.json
- Train Dataset: data/train.csv, data/train_transactions.csv
- Test Dataset: data/test.csv, data/test_transactions.csv

### Notebooks
- Data Understanding.ipynb: analyze the data and understand the data structure.
- Data Visualization.ipynb: visualize the data
- Generate Train-Test Dataset.ipynb: Generate train/test dataset for creating model which predict who will view the offer. 

## Installation
Python3 is required. Install required packages by below command.
```
pip install -r requirements.txt
```

### Library used
- pandas: manage and process the data 
- numpy: manage the data and conduct mathmatical operations
- seaborn, matplotlib: show data plot & visualization
- xgboost, scikit-learn: train, evaluate the model.

## Model Training
You can train the model using the notebook below

- train_baseline_sklearn.ipynb: Simple baseline model(no transaction in dataset)
- train_pytorch: baseline model with pytorch
- train_sklearn_with_transaction.ipynb: imporve performance with transaction data.
- train_youtube_model: model inspired by Youtube Recommendation System


## How to execute the notebook?
1. Run "Data preparation.ipynb" to preprocess json files
1. Run "Generate Train-Test Dataset.ipynb" 

## Results
### Baseline
```
Report for baseline
Train Report>
Train Accuracy: 0.9652451790633609
              precision    recall  f1-score   support

         0.0       0.96      0.89      0.92     10469
         1.0       0.97      0.99      0.98     34906

    accuracy                           0.97     45375
   macro avg       0.96      0.94      0.95     45375
weighted avg       0.97      0.97      0.96     45375

Test Report>
Test Accuracy: 0.8009053464377472
              precision    recall  f1-score   support

         0.0       0.62      0.50      0.56      6102
         1.0       0.85      0.90      0.87     18419

    accuracy                           0.80     24521
   macro avg       0.73      0.70      0.71     24521
weighted avg       0.79      0.80      0.79     24521
```

### Simple model
```
Report for simple
Train Report>
Train Accuracy: 0.8701836891486043
              precision    recall  f1-score   support

         0.0       0.77      0.62      0.69      9886
         1.0       0.89      0.94      0.92     33067

    accuracy                           0.87     42953
   macro avg       0.83      0.78      0.80     42953
weighted avg       0.86      0.87      0.87     42953

Test Report>
Test Accuracy: 0.8285069914298602
              precision    recall  f1-score   support

         0.0       0.66      0.60      0.63      5362
         1.0       0.88      0.90      0.89     16808

    accuracy                           0.83     22170
   macro avg       0.77      0.75      0.76     22170
weighted avg       0.82      0.83      0.83     22170
```

### Refined model
```
Report for xgb-gcv-refined
Train Report>
Train Accuracy: 0.9078507305051928
              precision    recall  f1-score   support

         0.0       0.73      0.58      0.65      9886
         1.0       0.88      0.94      0.91     33067

    accuracy                           0.85     42953
   macro avg       0.81      0.76      0.78     42953
weighted avg       0.85      0.85      0.85     42953

Test Report>
Test Accuracy: 0.8910629296668429
              precision    recall  f1-score   support

         0.0       0.67      0.61      0.64      5362
         1.0       0.88      0.90      0.89     16808

    accuracy                           0.83     22170
   macro avg       0.77      0.76      0.77     22170
weighted avg       0.83      0.83      0.83     22170
Best Parameter
```

### Evaluation of Youtube Recommendation Model
```
Report for xgb-gcv
Train Report>
Train Accuracy: 0.8644110401689206
              precision    recall  f1-score   support

         0.0       0.80      0.09      0.15      2884
         1.0       0.77      0.99      0.86      8657

    accuracy                           0.77     11541
   macro avg       0.78      0.54      0.51     11541
weighted avg       0.78      0.77      0.69     11541

Test Report>
Test Accuracy: 0.8508780732563974
              precision    recall  f1-score   support

         0.0       0.32      0.03      0.06      2874
         1.0       0.75      0.98      0.85      8667

    accuracy                           0.74     11541
   macro avg       0.54      0.50      0.45     11541
weighted avg       0.65      0.74      0.65     11541

Wall time: 1min 38s
```