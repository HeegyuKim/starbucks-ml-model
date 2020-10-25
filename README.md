
# Starbucks-ml-model
The reward program is a representative marketing method that induces users to purchase. But program that user are not interested in, user may unsubscribe corporate marketing channels or have a negative image. That’s why it’s important to send a SMS, email of reward program to interested users. In this case, the user’s interest is determined by whether or not the user has viewed the program. By creating a model that predicts whether users will see the program, you can deliver the right program to the right users.

# Summary of results
- By combining the user's information and the user's information on the offers received, a model was created to predict whether or not the received offer was viewed.
- It was difficult to improve accuracy due to unbalanced data. However, when the F1 score was used as an index, an 0.89 was achieved.
- The accuracy of predicting not to see the offer was low. It is lower if there is no user information
- Even without knowing the user information other than the total transaction amount, it was able to predict quite accurately than I expected. That’s interesting.
- Final Result - Accuracy: 0.9, F1 Score: 0.895


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

### Model Training
You can train the model using the notebook below

- train_baseline_sklearn.ipynb: Simple baseline model(no transaction in dataset)
- train_pytorch: baseline model with pytorch
- train_sklearn_with_transaction.ipynb: imporve performance with transaction data.
- train_youtube_model: model inspired by Youtube Recommendation System


## How to execute the notebook?
1. Run "Data preparation.ipynb" to preprocess json files
1. Run "Generate Train-Test Dataset.ipynb" 

## Training Result
### Baseline
```
Report for baseline(RandomForest)
Train Report>
Train Accuracy: 0.9978115614741695
              precision    recall  f1-score   support

         0.0       1.00      0.99      1.00      9886
         1.0       1.00      1.00      1.00     33067

    accuracy                           1.00     42953
   macro avg       1.00      1.00      1.00     42953
weighted avg       1.00      1.00      1.00     42953

Test Report>
Test Accuracy: 0.8160577356788453
              precision    recall  f1-score   support

         0.0       0.62      0.61      0.62      5362
         1.0       0.88      0.88      0.88     16808

    accuracy                           0.82     22170
   macro avg       0.75      0.75      0.75     22170
weighted avg       0.82      0.82      0.82     22170

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