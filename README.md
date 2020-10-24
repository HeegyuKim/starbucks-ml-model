# Starbucks-ml-model
Predicts who will view the offer by Starbucks App Customer Reward Program Data(https://www.kaggle.com/blacktile/starbucks-app-customer-reward-program-data)
Download the dataset from url and save 3 files in data/ directory
- data/portfolio.json
- data/profile.json
- data/trainscript.json

## Data Understanding.ipynb
Analyze, visualize the data in Data Understanding notebook.
한 유저는 여러번 received, viewed, completed 가 발생가능하다

<img src="img/offer_received_time_hist.png">


### Generate Train-Test Dataset.ipynb
Generate train/test dataset for creating model which predict who will view the offer. 
- Train Dataset: data/train.csv, data/train_transactions.csv
- Test Dataset: data/test.csv, data/test_transactions.csv

## Model Training
You can train the model using the notebook below

- train_baseline_sklearn.ipynb: Simple baseline model(no transaction in dataset)
- train_pytorch: baseline model with pytorch
- train_sklearn_with_transaction.ipynb: imporve performance with transaction data.
- train_youtube_model: model inspired by Youtube Recommendation System

## Evaluation
In 
```
Report for xgb-gcv
Train Report>
Train Accuracy: 0.9045509699866965
              precision    recall  f1-score   support

         0.0       0.72      0.56      0.63      9886
         1.0       0.88      0.94      0.90     33067

    accuracy                           0.85     42953
   macro avg       0.80      0.75      0.77     42953
weighted avg       0.84      0.85      0.84     42953

Test Report>
Test Accuracy: 0.8907513600941039
              precision    recall  f1-score   support

         0.0       0.67      0.62      0.64      5362
         1.0       0.88      0.90      0.89     16808

    accuracy                           0.83     22170
   macro avg       0.77      0.76      0.77     22170
weighted avg       0.83      0.83      0.83     22170
```

## Evaluation of Youtube Recommendation Model
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