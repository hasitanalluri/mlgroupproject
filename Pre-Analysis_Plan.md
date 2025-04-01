## 1. What is an observation in your study?
An observation in our study is a daily state aggregated report from a state on several factors relating to hospital capacity and COVID-19. Most notable, each observation in our study includes information on the number of hospitals with and without critical staff shortages, number of hospitals with COVID-19 patients, number of inpatient COVID-19 patients in total, and how many inpatient beds are available and used. 

## 2. Are you doing supervised or unsupervised learning? Classification or regression?
We plan to do supervised learning. Specifically, we want to run regression models on two situations. (1) We want to see if we can predict the percentage of hospitals with critical staff shortages in a state based on how many inpatient COVID-19 patients there are and how many inpatient beds are used in that state. (2) We want to see if we can predict the the COVID-19 onset in hospitals based on inpatient bed utilization and critical staff shortages. 

## 3. What models or algorithms do you plan to use in your analysis? How?

## 4. How will you know if your approach "works"? What does success mean?

(djx3rn): Depending on the model approach we decide to use, there is a general class of predictor metrics for each of them. They will mainly be cross-entropy, R^2, RMSE, MSE, and Accuracy. Usually, the success of a predictive model just means better than if you predicted the "normal" choice i.e. predicting the majority class or predicting the mean or median value of the target value.

## 5. What are weaknesses that you anticipate being an issue? How will you deal with them if they come up? If your approach fails, what might you learn from this unfortunate outcome?

### Identify potential weaknesses and how you plan to address them:
1. If the dataset is incomplete, inconsistent, or contains errors, this could significantly affect model performance. Missing data could be particularly problematic if certain states do not report consistently, which is entirely possible due to how busy and hectic they would be during this period. Thus, we will rely on imputation techniques (e.g., mean, median, or regression-based imputation) and in certain cases, may exclude unreliable data points. 
2. Overfitting could be an issue, especially since this dataset is huge and there are, in fact, a lot of variables in play. Thus, we will need to use cross-validation and regularization, as well as divide the data into train/test sets to make sure we're not working off of noise.
3. For this specific dataset, we may have to worry about non-stationarity; hospital rates likely fluctuate regardless of COVID-19 cases, and lurking trends and seasonality may affect our data. Thus, we may need to apply differencing or detrending to make the data stationary. 

### If your approach fails, consider what you might learn:

(djx3rn): One of the more intriguing things, is actually if this works, is understanding the nature of predictive modelling. The professor has brought up the problem of drawing causal inferences from models in class and how that is an entirely different ball game than statistical learning. I largely agree with that, so it's a question of why it's so effective without theory. That is to say, I have little knowledge of this phenomenon we're modelling, but the model does, and is that enough? Especially considering the NN non-linear proofs about how you can fit/train a non-linear function to match some other function e.g. fitting a representation of kinematics. I don't know, but it intuitively feels wrong to say fitting say observations for F=MA means deriving the equation from theory.

(djx3rn): Besides the above, if it actually does end up failing. We might have run into problems with having unpredictable variables in the model, badly measured data, and the problem of not having domain knowledge when creating models.

### Feature Engineering

### Results Presentation
