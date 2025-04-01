## 1. What is an observation in your study?
An observation in our study is a daily state aggregated report from a state on several factors relating to hospital capacity and COVID-19. Most notable, each observation in our study includes information on the number of hospitals with and without critical staff shortages, number of hospitals with COVID-19 patients, number of inpatient COVID-19 patients in total, and how many inpatient beds are available and used. 

## 2. Are you doing supervised or unsupervised learning? Classification or regression?
We plan to do supervised learning. Specifically, we want to run regression models on two situations. (1) We want to see if we can predict the percentage of hospitals with critical staff shortages in a state based on how many inpatient COVID-19 patients there are and how many inpatient beds are used in that state. (2) We want to see if we can predict the the COVID-19 onset in hospitals based on inpatient bed utilization and critical staff shortages. 

## 3. What models or algorithms do you plan to use in your analysis? How?
We will begin with **linear regression** to model the relationship between COVID-19 hospitalizations and hospital bed utilization. This will allow us to interpret how increases in COVID-19 cases and staffing shortages are associated with higher usage of hospital resources. Linear regression also gives us interpretable coefficients and diagnostic tools, such as residual analysis and \( R^2 \), to evaluate the model's fit.
We will use **logistic regression** to classify state-day observations into "high strain" or "low strain" based on whether hospital utilization or staff shortage thresholds are exceeded. This approach gives us interpretable odds ratios and is appropriate for binary outcomes.
To capture nonlinear patterns, interaction effects, and threshold behavior (e.g., a certain level of COVID-19 admissions triggering capacity overload), we will use **decision trees**. Building on that, we will apply **random forests** for improved generalization and stability, using the model’s feature importance scores to better understand the drivers of strain.
We may also use **Principal Component Analysis (PCA)** to reduce dimensionality, especially if many of our numerical features are correlated (such as different types of bed usage and admission metrics). PCA will help simplify the feature space while preserving most of the variance.
All models will be evaluated using **cross-validation** to ensure generalizability and avoid overfitting. We’ll compare models based on \( R^2 \), RMSE, and MSE for regression tasks and accuracy, precision, recall, and F1 score for classification.

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
We will engineer features such as rolling 7-day averages of hospitalizations to smooth out reporting noise and add temporal context. We’ll also compute ratios like percent of beds used and percent of beds occupied by COVID-19 patients. If classification thresholds are too noisy day-to-day, we may binarize labels based on smoothed indicators or quantiles.
We will explore correlations among numeric features to identify redundancy and apply **PCA** if needed. Categorical variables, such as state names (if included), may be one-hot encoded or used to group observations for stratified analysis.

### Results Presentation

We will present our results through a combination of tables and visualizations. Regression models will be evaluated with \( R^2 \), RMSE, and residual plots; classification results will include confusion matrices and F1 scores. We will use bar charts to show feature importances, line plots to show hospital utilization trends over time, and scatter plots or heatmaps to reveal correlations. If time permits, we may explore how our model predictions change over time or vary by region, adding depth to our analysis.

