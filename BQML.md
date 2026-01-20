Here’s a comprehensive set of detailed notes and practice questions for the “Create ML Models with BigQuery ML: Challenge Lab.” These map directly to the lab’s tasks and important concepts around using BigQuery ML for classification, feature engineering, model evaluation, and prediction.

Detailed Notes: BigQuery ML Challenge Lab
Overview

BigQuery ML allows data scientists and analysts to build and deploy machine learning models using standard SQL directly in Google BigQuery.
In this challenge lab, you’re asked to:

Create datasets and models in BigQuery
Engineer features to improve model performance
Evaluate and compare model accuracy
Predict business outcomes with ML models


Lab Setup and Environment

Every attempt provides temporary cloud credentials—use the incognito browser, and only lab accounts to avoid unauthorized billing.
Labs are time-limited; work efficiently without pausing.


Task 1: Create a Dataset and an ML Model
Creating a Dataset

In BigQuery, a dataset is a container for tables and ML models.SQL-- In BigQuery Console:
CREATE SCHEMA ecommerce;
-- or via UI



Creating a Logistic Regression Model

Logistic regression: Suitable for binary classification (e.g., predicting if a customer will buy or not).SQLCREATE OR REPLACE MODEL `ecommerce.customer_classification_model`
  OPTIONS(model_type='logistic_reg', labels = ['will_buy_on_return_visit']) AS
SELECT
  * EXCEPT(fullVisitorId)
FROM
  (SELECT
      fullVisitorId,
      IFNULL(totals.bounces, 0) AS bounces,
      IFNULL(totals.timeOnSite, 0) AS time_on_site
   FROM `data-to-insights.ecommerce.web_analytics`
   WHERE totals.newVisits = 1 AND date BETWEEN '20160801' AND '20170430'
  ) a
JOIN
  (SELECT
      fullVisitorId,
      IF(COUNTIF(totals.transactions > 0 AND totals.newVisits IS NULL) > 0, 1, 0) AS will_buy_on_return_visit
   FROM `data-to-insights.ecommerce.web_analytics`
   GROUP BY fullVisitorId
  ) b
USING (fullVisitorId);


Key concepts: Model is trained to predict if a user who’s new will buy after returning (binary label).


Task 2: Evaluate Model Performance

Use ML.EVALUATE to measure accuracy, ROC_AUC, precision, recall, etc.SQLSELECT *
FROM ML.EVALUATE(MODEL `ecommerce.customer_classification_model`, (
  -- Use a held-out or unseen dataset (not used in training)
  SELECT ... FROM ... WHERE date BETWEEN '20170501' AND '20170731'
));


Key metric: roc_auc (Area Under ROC Curve), which reflects the model’s discriminative power (closer to 1 is better).
Always evaluate model on new (holdout) data, never on the same data as training.


Task 3: Feature Engineering and Improved Model

Feature engineering helps improve predictive power by giving the model more or better data characteristics.
Add useful features:

Progress in checkout (latest_ecommerce_progress)
Original traffic source (trafficSource.source, medium, channelGrouping)
User device (device.deviceCategory)
Geography (geoNetwork.country)


Create a new improved model:SQLCREATE OR REPLACE MODEL `ecommerce.improved_customer_classification_model`
OPTIONS(model_type='logistic_reg', labels=['will_buy_on_return_visit']) AS
-- Similar logic to Task 1, but SELECT more/different features as columns


Evaluate:SQLSELECT * FROM ML.EVALUATE(MODEL `ecommerce.improved_customer_classification_model`, (SELECT ... ));


Compare ROC_AUC (and/or other metrics) with the previous (simpler) model.


Task 4: Finalize and Use Your Model for Prediction

Build a finalized, comprehensive model using all effective features and proper SQL grouping.SQLCREATE OR REPLACE MODEL `ecommerce.finalized_classification_model`
OPTIONS (model_type="logistic_reg", labels = ["will_buy_on_return_visit"]) AS
... -- SELECT with most relevant, engineered features as shown in the original prompt.


Run Predictions with ML.PREDICT (usually for recent time windows not in training data):SQLSELECT
  fullVisitorId, predicted_will_buy_on_return_visit, predicted_will_buy_on_return_visit_probs
FROM
  ML.PREDICT(MODEL `ecommerce.finalized_classification_model`,
    (SELECT ... WHERE date BETWEEN '20170501' AND '20170731')
  );


Prediction result: Probability and label for each user/session—enables targeted marketing/actions.


Key BigQuery ML Concepts

Model Types: logistic_reg, linear_reg, boosted_tree, etc.
Partition Data: Always use holdout data for model evaluation.
ML.EVALUATE: Assesses model performance.
ML.PREDICT: Applies the model to new/unseen data for scoring.


Practice & Review Questions: BigQuery ML Challenge
1. What type of model is best for binary classification in BigQuery ML?

A) linear_reg
B) kmeans
C) logistic_reg
D) time_series
Answer: C) logistic_reg


2. Which SQL clause is used to evaluate a trained model in BigQuery ML?

A) ML.TRAIN
B) ML.PREDICT
C) ML.EVALUATE
D) ML.TEST
Answer: C) ML.EVALUATE


3. What is one advantage of adding more relevant features to your model?

A) It always reduces training time
B) It can improve the model's predictive power/accuracy
C) It is required to run a query
D) It replaces the need for evaluation
Answer: B) It can improve the model's predictive power/accuracy


4. When training a model on user data, why must you EXCLUDE identifiers (like fullVisitorId) from features?

A) It is a best practice for privacy only
B) Identifiers can leak target answers to the model, causing overfitting and poor generalization
C) It makes SQL queries faster
D) It's not necessary
Answer: B) Identifiers can leak target answers to the model, causing overfitting and poor generalization


5. What does 'roc_auc' metric represent in ML.EVALUATE() query for a classification model?

A) Ratio of correct to incorrect predictions
B) Probability threshold chosen by the model
C) Ability of the model to separate positive/negative classes (1 is perfect)
D) Number of training examples
Answer: C) Ability of the model to separate positive/negative classes (1 is perfect)


6. To predict new visitor purchases for May–July 2017, which SQL should you use?

A) ML.EVALUATE
B) ML.PREDICT on finalized_classification_model with May–July data
C) SELECT * FROM ecommerce.customer_classification_model
D) CREATE OR REPLACE MODEL
Answer: B) ML.PREDICT on finalized_classification_model with May–July data


7. Why is it important to use “holdout” or “unseen” data to evaluate a model’s accuracy?

A) It speeds up model creation
B) It checks the model’s ability to generalize to new/real-world data
C) It gives higher accuracy scores
D) It is required by BigQuery’s syntax
Answer: B) It checks the model’s ability to generalize to new/real-world data


8. Which of the following is NOT a typical feature engineered into an ecommerce visitor classification model?

A) Visitor’s browser version string
B) Session bounces
C) Checkout progress
D) Geographic country
Answer: A) Visitor’s browser version string (unless browser impacts buy behavior, this info is often too granular)


9. What is a benefit of using BigQuery ML for business analysts or data scientists?

A) No learning curve (no code)
B) Ability to use standard SQL for advanced ML tasks without exporting data
C) Full graphical interface only
D) Limited to linear regression tasks
Answer: B) Ability to use standard SQL for advanced ML tasks without exporting data


10. What does ML.PREDICT output for each predicted row?

A) True/False only
B) Probability score or label (and possibly probability) for the target
C) Model’s AUC
D) The SQL used to train the model
Answer: B) Probability score or label (and possibly probability) for the target


Want more scenario-based questions or a SQL cheat sheet for the most common BigQuery ML commands? Let me know if you want advanced tips for feature engineering or real-world deployment scenarios!
