## Hands-On Lab: Predicting Loan Risk with AutoML (No-Code)

### Overview

In this lab, you’ll use **AutoML**, a no-code tool, to build a machine learning model that predicts loan risk.  
You’ll practice the three main phases of the ML workflow: **data preparation, model development, and model serving**.

---

### The Dataset

- The dataset contains information about loans from a financial institution.
- There are **2,050 data points** (rows).
- **AutoML requires at least 1,000 data points** to build a model, so this dataset is suitable.

---

### The ML Workflow in Practice

#### 1. Data Preparation

- You’ll upload and prepare the loan dataset in AutoML.
- This involves making sure the data is clean and ready for model training.

#### 2. Model Development

- You’ll train a model to predict whether a borrower will repay a loan or default.
- **Model evaluation** is key to understanding how well your model works.

##### Understanding the Confusion Matrix

When you evaluate your model, you’ll see a **confusion matrix**. Here’s how to interpret it:

- **True Positive Rate (TPR):**  
  - *Example:* 100% TPR means the model perfectly identifies everyone who will repay their loan.
  - *Formula:* TPR = True Positives / (True Positives + False Negatives)
- **True Negative Rate (TNR):**  
  - *Example:* 87% TNR means the model correctly identifies 87% of defaulters.
  - *Formula:* TNR = True Negatives / (False Positives + True Negatives)
- **False Positive Rate (FPR):**  
  - *Example:* 13% FPR means 13% of good borrowers are incorrectly labeled as defaulters.
  - *Formula:* FPR = False Positives / (False Positives + True Negatives)
- **False Negative Rate (FNR):**  
  - *Example:* 0% FNR means the model never misses a good borrower.
  - *Formula:* FNR = False Negatives / (True Positives + False Negatives)

**Why does this matter?**  
- A high false positive rate means the bank could reject good customers.
- A high false negative rate means the bank could approve risky loans.

##### Precision-Recall Curve and Confidence Threshold

- The **confidence threshold** controls how certain the model must be before predicting a positive case (e.g., “will repay loan”).
- **Higher threshold:**  
  - Increases precision (fewer false positives), but decreases recall (misses more actual positives).
- **Lower threshold:**  
  - Increases recall (catches more positives), but decreases precision (more false positives).

**Examples:**
- **Threshold = 0:**  
  - Recall = 100% (model says everyone will repay), but precision = 50% (only half actually do).
  - Risk: The bank could lose money by approving too many risky loans.
- **Threshold = 1:**  
  - Precision = 100% (everyone predicted to repay actually does), but recall = 1% (almost everyone is rejected).
  - Risk: The bank loses business by rejecting almost all applicants.

**Key Point:**  
- Setting the right threshold is important to balance business goals and risk.

#### 3. Model Serving

- After training and evaluating, you’ll deploy the model to make predictions on new loan applications.

---

### Key Points for Beginners

- **AutoML** lets you build ML models without writing code.
- Understanding the confusion matrix helps you interpret model results.
- Adjusting the confidence threshold changes the balance between catching all good borrowers and avoiding risky loans.
- The right balance depends on your business needs.

---

## Vertex AI: Predicting Loan Risk with AutoML — Hands-On Lab Guide

### Overview

In this lab, you’ll use **Vertex AI** on Google Cloud to train and serve a machine learning model that predicts loan risk using a tabular dataset.  
You’ll experience the full ML workflow: **uploading data, training a model, evaluating performance, deploying the model, and getting predictions** — all using AutoML (no-code).

---

### Objectives

You will learn how to:
- Upload a dataset to Vertex AI.
- Train a machine learning model with AutoML.
- Evaluate the model’s performance.
- Deploy the model to an endpoint.
- Get predictions from the deployed model.

---

### Setup

- **Browser:** Use a standard browser (Chrome recommended).
- **Lab Access:** Use only the temporary credentials provided by Qwiklabs. Do **not** use your personal Google Cloud account.
- **Lab Timer:** Labs are timed and cannot be paused.

#### How to Start

1. Click **Start Lab**.
2. Copy the username from the credentials panel.
3. Click **Open Google Console** and sign in with the provided credentials.
4. Accept terms, skip recovery options, and do not sign up for free trials.
5. The Cloud Console will open, ready for you to use Vertex AI.

---

### Introduction to Vertex AI

- **Vertex AI** is Google Cloud’s unified AI platform.
- Offers both **AutoML** (no-code) and **Custom Training** (code-based).
- In this lab, you’ll use **AutoML** to build a model that predicts if a customer will repay a loan.

---

### Task 1: Prepare the Training Data

#### Create a Dataset

1. Go to **Vertex AI > Datasets** in the Google Cloud Console.
2. Click **Create dataset**.
3. Name it `LoanRisk`.
4. For data type/objective, select **Tabular** and **Regression/classification**.
5. Click **Create**.

#### Upload Data

- Choose **Select CSV files from Cloud Storage**.
- Enter the path:

#### (Optional) Generate Statistics

- Click **Generate statistics** to see charts and summaries for each column.

---

### Task 2: Train Your Model

1. Click **Train new model** and select **Other**.
2. For **Objective**, choose **Classification** (predicting repay/default, not a continuous value).
3. Name your model (e.g., `LoanRisk`).
4. For **Target column**, select `Default`.
5. (Optional) Adjust advanced options for data split/encryption.
6. For **Add features**, click **Continue**.
7. In **Training options**, exclude irrelevant columns (e.g., remove `ClientID`).
8. Set **Budget** to `1` node hour.
9. Leave **early stopping** enabled.
10. Click **Start training**.

*Note: Training may take several minutes to over an hour. In this lab, you may use a pre-trained model for demonstration.*

---

### Task 3: Evaluate Model Performance (Demonstration Only)

Vertex AI provides several evaluation metrics:

- **Precision/Recall Curve:**  
Adjust the confidence threshold to balance precision (accuracy of positive predictions) and recall (coverage of actual positives).
- **Confusion Matrix:**  
Shows how well the model predicts each class (e.g., 100% repay, 87% default).
- **Feature Importance:**  
Bar chart showing which features (like loan amount, income, age) are most important for predictions.

*Tip: Use these insights to improve your model by adding data, engineering features, or adjusting training methods.*

---

### Task 4: Deploy the Model (Demonstration Only)

*Steps you would follow in a production setting:*

1. On your model page, click **Deploy & test** > **Deploy to Endpoint**.
2. Name the endpoint (e.g., `LoanRisk`).
3. Choose machine type (e.g., `e2-standard-8`).
4. Enable **Feature attribution** for explainability.
5. Set monitoring and objectives as needed.
6. Click **Deploy**.

*After deployment, your model is ready to serve predictions!*

---

### Task 5: Get Predictions

#### Using Cloud Shell

1. Open **Cloud Shell**.
2. Download the input file:
  ```bash
  gcloud storage cp gs://cloud-training/CBL455/INPUT-JSON .
  ```
3. Set environment variables:
  ```bash
  export INPUT_DATA_FILE="INPUT-JSON"
  export PROJECT_NUMBER=$(gcloud projects describe $(gcloud config get-value project) --format="value(projectNumber)")
  export AUTOML_SERVICE="https://automl-proxy-$PROJECT_NUMBER.us-central1.run.app/v1"
  ```
4. Review the contents of `INPUT-JSON`:
  ```json
  {
    "instances": [
      {
        "age": 40.77430558,
        "ClientID": "997",
        "income": 44964.0106,
        "loan": 3944.219318
      }
    ]
  }
  ```
5. Request a prediction:
  ```bash
  curl -X POST -H "Content-Type: application/json" $AUTOML_SERVICE -d "@${INPUT_DATA_FILE}" -s | jq
  ```
6. **Expected Output:**
  ```json
  {
    "predictions": [
      {
        "scores": [0.999998, 0.000002],
        "classes": ["0", "1"]
      }
    ],
    ...
  }
  ```
  - The `scores` array gives the probability for each class (e.g., "0" = repay, "1" = default).

---

### Key Points for Beginners

- **AutoML** lets you train, evaluate, and deploy models without coding.
- **Evaluation metrics** (precision/recall, confusion matrix, feature importance) help you understand and improve your model.
- **Deployment** makes your model available for real-time predictions.
- **Cloud Shell** and API calls let you test your model with new data.

---

### Next Steps

You’re ready to use Vertex AI to build, evaluate, and deploy ML models for real-world prediction tasks!

---

