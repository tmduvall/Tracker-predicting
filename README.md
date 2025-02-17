# Predicting daily health using a tracker
This is an exploratory project to discover whether tracker data in the morning can predict the health of people with ME throughout the day, starting with my data as a pilot. The predictors consist of six readings from a Garmin Venu 3 that are available upon waking - Sleep Score, resting heart rate, Body Battery, average respiration rate, skin temperature change, and HRV Status. The outcomes comprise: the tracker's estimate of active calories burnt during the rest of the day, a person's self-rating (1-5) of their health over the day, and a binary self-appraisal of whether they are in PEM (a 'crash' phase).

The first step was to create deep-learning models predicting the outcomes ('nn' in the filenames); then those were compared with the sightly more 'traditional' approach of gradient boosted trees ('tree' in the filename). The differences in accuracy between the model types were small in every case. Generally, neither type was very accurate, because, as the EDA showed, there was little correlation between predictors and outcomes. Only one model shows (quite modest) promise for further development - using ordinal classification to predict daily ratings. 

The process of building each model is annotated in its Jupyter notebook. The results are at the end, under the heading, 'Discussion.' These summary comments cover the deep-learning models:

**Daily ratings classification** *(dailypred - rating - classification - nn.ipynb)* 

In sum, this model is weak but still sufficiently suggestive to be 'not useless' - an imperfect source of information, but one that outperforms its components, on which many people with ME currently rely. For example, the correlation between predictions and observations in the test set is 0.272; this is not high but is more than 0.2 higher than the correlation between the observed ratings and any of the predictors. That is, individually the predictors are practically useless, but analyzed together they are not.

If this model is developed further, an important question would be whether to create a single model for all people with ME or, more likely, to continually refine the base model here for each individual as they and their tracker produce more data.

**Daily ratings regression:** *(dailypred - rating - regression - nn.ipynb)*

The model might appear to be moderately accurate and reliable by some measures, but in practice it simply predicts a value close to the overall average and thus does not reliably register important changes.

**PEM classification** *(dailypred - PEM - classification - nn.ipynb)* 

Due to data imbalances, SMOTE balancing was used on the training set, and the F1 score was used as the objective. Bayesian tuning of the hyperparameters yielded a simple logistic regression model that predicted both the validation and test sets quite poorly. As a check, I also tried manual tuning and using AUC as the objective for Bayesian tuning, with no improvement.

**Active calories regression:** (*(dailypred - active calories - regression - nn.ipynb)*)

Although I spent considerable effort on optimizing the model, the results are unimpressive.