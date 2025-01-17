# Predicting daily health using a tracker
This is an exploratory project to discover whether tracker data in the morning can predict the health of people with ME throughout the day, starting with me as a pilot. The predictors consist of six readings from a Garmin Venu 3 that are available upon waking. The outcomes comprise: the tracker's estimate of active calories burnt during the rest of the day, a person's self-rating (1-5) of their health over the day, and a binary self-appraisal of whether they are in PEM (a 'crash' phase). The first step is to create deep-learning models predicting the outcomes; then these will be compared with slightly more 'traditional' approaches, such as random forests.

Currently, I have completed regressions using deep neural networks to predict the estimated active calories (*dailypred - active calories - regression.ipynb*) and the daily ratings (*dailypred - rating - regression.ipynb*). 

**Active calories regression:** Although I spent considerable effort on optimizing the model, the results are unimpressive. It will be interesting to see how well other approaches work. 

**Daily ratings regression:** The model might appear to be moderately accurate and reliable by some measures, but in practice it simply predicts a value close to the overall average and thus does not reliably register important changes.

**Daily ratings classification** In sum, the model is sufficiently suggestive to be 'not useless' - another imperfect source of information, but one that probably should outweigh its components, on which many people with ME currently rely. If this model is developed further, an important question would be whether to create a single model for all people with ME or to continually refine the base model here for each individual as they and their tracker produce more data. Finally, this model might be improved by preparing data to reflect changes in baseline metrics. For example, today's resting heart rate might be less predictive than the difference between it and the average over the past ten days - or ten days with a neutral rating, or ...

**PEM classification** Coming soon!
