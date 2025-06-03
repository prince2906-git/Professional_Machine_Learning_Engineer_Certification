# Vertex AI Quiz (Set 2)

**Passing score: 80%**

---

## 1. A video production company wants to use machine learning to categorize event footage but does not want to train its own ML model. Which option can help you get started?

- AutoML
- BigQuery ML
- **Pre-trained APIs** ✅
- Custom training

**Explanation:**  
Pre-trained APIs (such as Google Cloud Video Intelligence API) allow you to leverage existing machine learning models for tasks like video categorization without the need to train your own model.

---

## 2. Your company has a massive amount of data, and you want to train your own machine learning model to see what insights ML can provide. Due to resource constraints, you require a codeless solution. Which option is best?

- **AutoML** ✅
- Custom training
- BigQuery ML
- Pre-trained APIs

**Explanation:**  
AutoML provides a codeless, user-friendly interface for training custom machine learning models, making it ideal for users with limited coding resources.

---

## 3. Which code-based solution offered with Vertex AI gives data scientists full control over the development environment and process?

- AI Platform
- AI Solutions
- AutoML
- **Custom training** ✅

**Explanation:**  
Custom training in Vertex AI allows data scientists to write their own code, choose frameworks, and have full control over the training process and environment.

---

## 4. tf.keras is a high-level TensorFlow library that has been commonly used to build ML models. Which of the following lets you create a neural network with multiple layers?

- model.compile
- tf.keras.Run
- **tf.keras.Sequential** ✅
- model.fit

**Explanation:**  
`tf.keras.Sequential` is used to build a neural network by stacking multiple layers in a linear fashion.

---

## 5. You work for a global hotel chain that has recently loaded some guest data into BigQuery. You have experience writing SQL and want to leverage machine learning to help predict guest trends for the next few months. Which option is best?

- Pre-trained APIs
- AutoML
- Custom training
- **BigQuery ML** ✅

**Explanation:**  
BigQuery ML enables users to create and execute machine learning models using standard SQL queries, making it ideal for those with SQL experience and data already in BigQuery.

---

## 6. Which of the following can you do with the Natural Language API?

- Classify pictures.
- Complete new areas of an existing image.
- **Analyze sentiment and identify subjects of text.** ✅
- Generate a caption for a YouTube video.

**Explanation:**  
The Natural Language API is designed for text analysis tasks such as sentiment analysis, entity recognition, and syntax analysis—not for image or video processing.

---

# Vertex AI Quiz

**Passing score: 80%**

---

## 1. Which stage of the machine learning workflow includes data upload and feature engineering?

- Model serving
- Model training
- **Data preparation** ✅

**Explanation:**  
Data upload and feature engineering are part of the data preparation stage, where raw data is collected, cleaned, and transformed into features suitable for model training.

---

## 2. When you build an ML pipeline on Vertex AI to automate the ML workflow, what are the components you can use?

- You can only use the prebuilt pipeline template without the flexibility to customize it.
- You can only use prebuilt components.
- **You can include both prebuilt components (by Google) and custom components into the pipeline.** ✅
- You can only rely on custom components.

**Explanation:**  
Vertex AI Pipelines allow you to use both prebuilt (Google-provided) and custom components, giving you flexibility to automate and customize your ML workflow.

---

## 3. Which of the following provides a toolkit to automate, monitor, and govern machine learning systems by orchestrating the workflow in a serverless manner?

- Responsible AI
- Vertex AI Feature Store
- Explainable AI
- **Vertex AI Pipelines** ✅

**Explanation:**  
Vertex AI Pipelines is designed for orchestrating, automating, and monitoring ML workflows in a serverless and scalable way.

---

## 4. Select the correct machine learning workflow.

- Model training, data preparation, model serving
- Model serving, data preparation, model development
- Data preparation, model evaluation, model training
- **Data preparation, model development, model serving** ✅

**Explanation:**  
The standard ML workflow is:  
1. Data preparation  
2. Model development (training and evaluation)  
3. Model serving (deployment and prediction)

---

## 5. A farm uses the machine learning technology of Google to detect defective apples in their crop, like those with irregular sizes or scratches. The goal is to identify only the apples that are actually bad so that no good apples are wasted. Which metric should the model focus on?

- Confusion matrix
- **Precision** ✅
- Feature importance
- Recall

**Explanation:**  
Precision is important when you want to minimize false positives—in this case, ensuring that only truly defective apples are classified as bad, so good apples are not wasted.

---

## 6. A hospital uses the machine learning technology of Google to help pre-diagnose cancer by feeding historical patient medical data to the model. The goal is to identify as many potential cases as possible. Which metric should the model focus on?

- **Recall** ✅
- Confusion matrix
- Precision
- Feature importance

**Explanation:**  
Recall measures how many actual positive cases (cancer) are correctly identified. High recall is crucial in medical diagnosis to ensure as many cases as possible are detected.

---

## 7. Which stage of the machine learning workflow includes model training and evaluation?

- Data preparation
- Model serving
- **Model development** ✅

**Explanation:**  
Model development encompasses both training the model and evaluating its performance before it is deployed for predictions.

---
