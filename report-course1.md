# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Junjie Huang

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
I realize that the number of bike sharing should be non-negative, therefore I do the summary statistic to see whether there are negative outputs and change them to zero if there are nagetive values. However, the minimum output is larger than 0, so I do not need to do the change.

### What was the top ranked model that performed?
The top ranked model is WeightedEnsemble_L3. And its score is -139.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
From the summary statistic, I can find that the season and weather feature are categorical data, which only contain several discrete values. And I set them to the 'categorical' datatype. And as for the datetime, I seperate it into hour, day, month and add the hour variable as a feature into the model. 

### How much better did your model preform after adding additional features and why do you think that is?
The kaggle score reduce from 1.32 to 0.48, which I believe is a huge improvement. And as for the performance of the training model, the r2 increase from 0.58 to 0.93, which also shows that the additional feature will help to enhance the performance of the model a lot.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
I change the evaluation metric from 'root_mean_squared_error' to 'r2', to see whether the performance of the model can be improved. The performance of the model on the training set improved a lot, with the score going from -63.18 to 0.88. However, the performance of the model on the test set does not improve.

### If you were given more time with this dataset, where do you think you would spend more time?
From the above result, I think that a useful feature can be very helpful for the prediction. And I would like to spend more time to take a look at the structure of the dataset and try to find more possible powerful features.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|eval_metrix|time_limit|presets|score|
|--|--|--|--|--|
|initial|'root_mean_squared_error'|600|'best_quality'|1.3264|
|add_features|'root_mean_squared_error'|600|'best_quality'|0.4798|
|hpo|'r2'|600|'best_quality'|0.4886|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![model_test_score.png](img/model_test_score.png)

## Summary
By the AutoGluon tools, I can find that the WeightedEnsemble_L3 model performs the best. And after addinh an additional feature, the performance of the model improves a lot, both on the training set and the test set. However, when I change the eval_metric from 'root meaned squared error' to 'r2', the performance of the model on the training set improves a lot, but not on the test set. Therefore, changing this hyperparameter may not be helpful. And I think it might be helpful to include more useful features.
