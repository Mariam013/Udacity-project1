# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Mariam Suleman

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
The data from the sample submission which countained the date time and count coulumns. the initial count column was replaced with the new predictions

### What was the top ranked model that performed?
 RandomForestMSE_BAG_L2 was the best performed

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
The EDA revealed that some categorical values such as weather were being treated as integers. So i converted them to categorical values. To add new features, I separated the date time column with hour as the new feature.

### How much better did your model preform after adding additional features and why do you think that is?
By adding hour as a new feature, it future provides details into the bike sharing patterns giving the time of day which bike sharing is high or low. For tree models, this creates further splits leading to more accurate predictions.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
Although the hyper paarameter tunig for the lightGMB improved the model performance, there is still more that can be done. The hyperparameter did bring a significant improvement from 0.62743 to 0.56439 on the kaggle score but with a lower performance in the metric score.

### If you were given more time with this dataset, where do you think you would spend more time?
I would spend more time training the model training time, more stacking levels, and optimized hyperparameters for LightGBM/CatBoost with higher num_boost_round and lower learning_rate. 

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|time_limit=600|presets='best_quality'|eval_metric='rmse'|1.80251|
|add_features|time_limit=600|presets='best_quality'|eval_metric='rmse'|0.62743|
|hpo|num_trials=50|searcher='random'|time_limit=3600|0.56439|

### Create a line plot showing the top model score for the three (or more) training runs during the project.


![model_train_score](https://github.com/user-attachments/assets/ebe86e8d-43c8-4f98-aaee-0dd1ce9b3536)


### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.


![model_test_score](https://github.com/user-attachments/assets/d8f1fa62-2905-47e8-bbe9-a83f629e0f6e)


## Summary
From the graphs, it ca be seen that the feature engineering was the most impactful step as it significantly improved the model performance both in the model evaluation and kaggle scores. The consistency between both metrics suggests that the local validation is reasonably well-aligned with the test set.
