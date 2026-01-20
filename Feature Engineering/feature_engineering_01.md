# Study Guide: Feature Engineering for Predictive Modeling

## Key Concepts

### What is Feature Engineering?

- **Definition:** The process of transforming raw data into measurable input features for use by machine learning models, with the objective of increasing predictive performance.
- **Why Important?**
  - The right features can dramatically increase model accuracy and reduce training time.
  - Feature engineering often involves domain knowledge, creativity, and trial-and-error.

---

### Feature Engineering Process

1. **Problem Understanding and Data Exploration**
   - Review and explore raw data from various business domains (e.g., customer, sales, inventory).
   - Use domain expertise to create or extract features that are relevant to the prediction task.

2. **Transformation & Extraction**
   - **Transformation:** Converting raw data into usable feature vectors (e.g., transforming dates into age or elapsed time).
   - **Extraction:** Deriving new features based on existing ones (e.g., combining latitude and longitude into a geohash).
   - Features can be numerical, categorical, bucketized, crossed, hashed, or embeddings.

3. **Manual vs. Automated Feature Engineering**
   - **Manual:** Constructed through human expertise, using scripting (e.g., Python, TensorFlow).
   - **Automatic:** Computed by algorithms, often used for high-dimensional/raw data (e.g., convolutional neural networks in computer vision).
   - **Hybrid:** Combination of both, often yields best results.

4. **Dimensionality Reduction**
   - Reduces the number of features, helping models generalize better and decrease risk of overfitting.
   - Techniques like Principal Component Analysis (PCA) are common.

5. **Iterative Refinement**
   - Start with basic features and a baseline model, then iteratively add, remove, or transform features and monitor performance improvements.

---

### Types of Feature Engineering

- **Indicator Variables:** One-hot-encoding, flag columns for key categories or groups.
- **Interaction Features:** Arithmetic combinations of existing features (sum, difference, product, quotient).
- **Representation Changes:**
  - Numeric to categorical (e.g., age groups).
  - Grouping sparse classes (consolidate rare categories into "other").
  - Converting categorical features to dummy (one-hot) variables.
- **Domain-Specific Features:** Features based on domain intuition or external knowledge (e.g., time of year for sales, location clustering).

---

### Practical Insights

- **Effective feature engineering is highly problem- and data-specific**—what works for one problem may not work for another.
- **Input format matters:** Many ML models, especially neural networks, require features as real number vectors.
- **Feature vectors:** The set of features input to the model; engineered features can augment or replace the original vector.
- **No universal formula:** Successful feature engineering leverages domain knowledge, creativity, practice, and constant iteration.

---

## Practice Questions

### 1. What is the primary goal of feature engineering?
- A) Making features easier to visualize
- B) Increasing the predictive power and accuracy of models
- C) Reducing data storage requirements
- D) Ensuring data privacy

**Answer:** B

---

### 2. Which of the following is an example of feature extraction?
- A) Creating a new column by summing two existing columns
- B) Dropping a column with too many missing values
- C) Normalizing a numeric feature
- D) Training a baseline ML model

**Answer:** A

---

### 3. Why is dimensionality reduction (like PCA) used in feature engineering?
- A) To increase the number of predictors
- B) To reduce noise and risk of overfitting by using fewer, more meaningful features
- C) To remove all outliers and missing data
- D) To automatically generate labels

**Answer:** B

---

### 4. What is typically required for effective feature engineering?
- A) Only knowledge of algorithms
- B) Domain expertise, creativity, and iterative experimentation
- C) No knowledge of the data
- D) Only high compute power

**Answer:** B

---

### 5. Which feature engineering approach uses both manual and algorithmic methods?
- A) Manual only
- B) Hybrid
- C) Automatic only
- D) None of the above

**Answer:** B

---
# Turning Raw Data into Useful Feature Vectors: The House Price Example

Let's walk through how to convert raw real-world data into the structured **feature vectors** that enable effective machine learning models—using the classic problem of predicting house prices.

---

## Step 1: Identify Potential Features

Begin by brainstorming all the data points that might influence house prices. For houses, common features include:
- **Square footage** (living area size)
- **Lot size**
- **Number of rooms or bedrooms**
- **Sale price history** (previous sale amounts)
- **Location** (e.g., neighborhood, proximity to schools, etc.)
- **Amenities** (garage, driveway)
- **Property type** (categorical: house vs. apartment)

**Key Insight:**  
Your choice of features directly impacts the predictive capability of your model. Features should represent patterns or attributes that are **meaningfully** related to the predicted outcome.

---

## Step 2: Prepare and Engineer Features

### Why isn't raw data ready for models?
- **Raw real estate data** is rarely neatly formatted or fully complete.
- Data may include irrelevant fields, missing values, or inconsistent representations (e.g., "Driveway: yes/no/Missing").

### What is feature engineering?
- The process of **cleaning, selecting, transforming, and encoding** raw data into useful feature vectors for ML models.
- **Tasks include:**
  - Handling missing data
  - Encoding categorical values (e.g., "house"/"apartment" → numerical labels or one-hot encoding)
  - Scaling/normalizing values (so model weights behave well)
  - Creating new features (e.g., "price per square foot," "bedrooms per room")

> **Time Investment Insight:**  
> Data scientists often spend **50–75% of model development time** on feature engineering. It's a crucial phase that dramatically affects the model's final performance.

---

## Step 3: Map to Model Inputs

- Each **feature vector** is a structured list or array where each column represents a cleaned, ready-to-use feature value for a single home.
- This vectorized format is required by ML algorithms for both training and prediction stages.

**Example:**  
Suppose your cleaned feature set for each house is:
- `[Square Footage, Lot Size, Bedrooms, Garage (1/0), Driveway (1/0), Type (house=0, apartment=1)]`

A sample feature vector:
- `[1600, 4000, 3, 1, 1, 0]` (1600 sqft house, 4000 sqft lot, 3 bedrooms, has garage & driveway, house)

---

## Conclusion

- **Choosing the right features** is foundational to model accuracy.
- **Good feature engineering** bridges the raw data you have and the input your model needs for optimal predictions.

---

## Practice Question

**What is the main reason feature engineering often takes the majority of a data scientist's time?**
- A) Models are unreliable
- B) Raw data is rarely in a model-ready format and requires significant cleaning, transformation, and encoding
- C) Algorithms don't accept numbers
- D) Feature engineering is unnecessary

**Answer:** B

---

# What Makes a Good Feature? – Key Principles and Practical Examples

Creating good features is vital for effective machine learning. Here are the core principles—based on the transcript—and a few practical examples for reinforcement.

---

## Essential Qualities of a Good Feature

1. **Relevance to the Objective**
   - **Directly related to the prediction target:** A good feature must have a logical, data-driven reason for its inclusion.
   - *If you can’t build a hypothesis about the relationship, discard the feature!*

2. **Availability at Prediction Time**
   - **Must be known when making predictions:** Avoid features that won’t be available when the model is deployed.

3. **Numeric (or Easily Convertible)**
   - Most ML models work best with numerical input, so categorical or text features must be encoded (e.g., one-hot, label encoding).

4. **Sufficient Representation**
   - **Enough examples exist in the data:** A feature needs to have a wide enough distribution in the dataset to be useful.

5. **Human Insight/Domain Knowledge**
   - Use intuition or knowledge of the domain to hypothesize why a feature could influence the outcome.

6. **Avoid Data Dredging**
   - Don’t include features just because they correlate in your dataset. Correlation without causation can produce **spurious relationships** that hurt model performance and generalizability.

---

## Examples: Evaluating Features

### **Objective:** Predict use of a discount coupon

- **Font of the advertised text:**  
  *Potentially good* – Might influence if the coupon is noticed and used.

- **Price of the discounted item:**  
  *Good* – Lower prices often increase likelihood of coupon use.

- **Number of items in stock:**  
  *Usually not good* unless user visibility is involved; customers don’t see overall inventory.

### **Objective:** Predict if a credit card transaction is fraudulent

- **Has the cardholder bought from the store before?**  
  *Good* – Unusual purchases can indicate potential fraud.

- **Category of item purchased:**  
  *Good* – Some items are more commonly associated with fraudulent activity than others.

- **Expiry date of the card:**  
  *Generally not good,* as it does not indicate transaction behavior; possibly, issue date is better (new cards are more likely to be used for fraud).

---

## Key Takeaways

- Always **hypothesize the relationship** between feature and label.
- Only include features **reliably available** at prediction time.
- Avoid including arbitrary or unrelated data — it makes the model’s job harder, not easier.
- Use **domain expertise** to guide feature selection, not just brute-force search or correlation.

---

## Practice Question

**Why should "number of items in stock" usually not be included as a feature for predicting coupon usage?**
- A) It is always zero
- B) Users typically don't know how many items are in stock, making it unrelated to their decision to use coupons
- C) It is a text field
- D) It's not numeric

**Answer:** B

---
# Good Features: They Must Be Available at Prediction Time

When engineering features for a machine learning model, **a critical rule is that every feature must be available at the moment of prediction**—not just during training. This aspect is often overlooked and can lead to models that work well in training but fail in real-world scenarios.

---

## Key Principles

### 1. Availability at Prediction Time
- **Features must be known or obtainable in real time** (or at the required prediction moment).
- **Common Pitfall:** Using historical or aggregated data fields from a data warehouse that are not yet available at prediction time (due to processing/reporting delays).

**Example:**  
You might want to use "sales from yesterday" as a feature, but if those numbers are only available a month later due to your reporting system, you cannot use them for real-time predictions.

---

### 2. Define Features with Realistic Timing
- Clearly specify the **time window** or lag for any aggregate or time-dependent feature.  
  - For instance: "Total coupons sold over the previous month" (which you can calculate once the month’s data is finalized).
- Don’t use vague or future-looking variables—use those that can be consistently populated at the point of prediction.

---

### 3. Consistency Between Training and Serving

- **Data staleness:** If you can only access data as of three days ago at prediction time, ensure you train the model using features only as current as three days ago. This avoids a mismatch between training and serving data freshness, which can severely degrade model performance.

---

### 4. Legal and Ethical Considerations

- Some features might be present in your training data but **not legally or ethically collectible** at prediction (e.g., demographic info, private identifiers). If so, these cannot be included.

---

### 5. Stable Feature Definitions

- Avoid using features whose meaning or calculation may change over time (such as the output of another evolving model—“cluster ID from model X”).

---

## Practical Quiz from the Transcript

**For each feature below, consider: Is this knowable at prediction time (and therefore usable)?**

| Feature Description                                   | Usable Feature?      | Comments                                             |
|------------------------------------------------------ |--------------------- |-----------------------------------------------------|
| Total number of discountable items sold (no timeframe)| No                   | Unclear window; availability timing is not defined   |
| Number sold in previous month                        | Yes (with caveat)    | If previous month’s data is ready before prediction  |
| Number of customers who viewed ads                   | Maybe                | Depends on how quickly ad reporting updates arrive   |
| “Is the item new at the store?”                      | Yes                  | Catalog info; available in real time                 |
| Category of item being purchased                     | Yes                  | Known at time of purchase                            |
| Online vs. in-person purchase                        | Yes                  | Known right at transaction                           |

---

## Summary Checklist

Before using any feature, ask:

1. **Am I sure this feature’s value is available in real time during prediction?**
2. **Does the timing of the data match between training and serving?**
3. **Is it ethically and legally appropriate to use?**
4. **Is the feature definition stable/not likely to change unexpectedly?**

---
# Numeric Features & Feature Engineering in Machine Learning

Converting features to numeric form with meaningful magnitude is essential for modern machine learning models. This guide explains why, illustrates good and bad approaches, and gives practical tips for engineering and encoding features.

---

## Why Features Must Be Numeric and Meaningful

- **ML models, especially neural networks, operate on numbers.**  
  Models perform arithmetic (addition, multiplication, etc.) so inputs must be numbers.
- **Magnitude matters.**  
  Numeric values should carry real-world meaning—doubling the value should reflect a meaningful difference.

---

## Good vs. Bad Numeric Features: Examples

### Numeric Features with Meaningful Magnitude

- **Percent Discount (e.g., 10%, 20%)**
  - *Numeric:* Yes  
  - *Magnitude is meaningful:* 20% is twice as much as 10%.
- **Physical Size (cm²):**
  - *Numeric:* Yes  
  - *Magnitude may be meaningful:* A larger area might be more visible but verify with domain knowledge.

### Categorical or Ambiguous Features

- **Coupon Size (‘small’, ‘medium’, ‘large’):**
  - *Not numeric:* Needs encoding (e.g., one-hot).
  - Encoding as 1, 2, 3 is misleading.
- **Font Type (Arial, Times New Roman):**
  - *Not numeric:* Label encoding (Arial=1, Times=2) provides numbers but not meaningful order/magnitude.
- **Color (Red, Blue, Black):**
  - *Not numeric:* RGB could represent color numerically, but arithmetic on them is meaningless for most business uses.
- **Item Category (Dairy=1, Deli=2):**
  - *Not numeric:* Same issue as above; requires one-hot or embedding.

---

## How to Convert Categorical Features

1. **One-Hot Encoding:**  
   For unordered categories. E.g., "medium" = [0,1,0]

2. **Ordinal Encoding:**  
   Only if there is **true order** to the values.

3. **Embeddings:**  
   For complex, high-cardinality data (e.g., Word2Vec for text).

---

## Chart: Feature Types and Numeric Readiness

Here's an example illustration of how different features from a coupon dataset should be handled before use in a machine learning model.

> (For actual presentation, use the chart template below in your tool of choice; colors indicate numeric readiness.)

| Feature Type                  | Numeric/Meaningful | Needs Encoding | Not Directly Usable |
|-------------------------------|--------------------|----------------|---------------------|
| Percent Discount              | 🟢                 |                |                     |
| Coupon Size (cm²)             | 🟢                 |                |                     |
| Coupon Size (small/med/large) |                    | 🟡             |                     |
| Font Type                     |                    | 🟡             |                     |
| Color                         |                    |                | 🔴                  |
| Item Category                 |                    | 🟡             |                     |

- 🟢 = Ready to use as a meaningful number
- 🟡 = Requires encoding (one-hot or embedding)
- 🔴 = Not usable without major transformation

---

### Chart Interpretation

- **Percent Discount** and **Coupon Size (cm²)** are ready to use as numeric features.
- **Coupon Size (as S/M/L)**, **Font Type**, and **Item Category** all require encoding.
- **Color** is difficult to use meaningfully without special transformation.

---

## Key Takeaways

- All features must be numeric for most ML models—but the numbers have to mean something.
- Don’t assign arbitrary numbers to categories (e.g., Category1=1, Category2=2) unless the order is justified.
- Use encoding techniques like one-hot, ordinal (with care), or embeddings for non-numeric features.
- Apply domain knowledge when interpreting or transforming features.

---

## Practical Examples

- **Good:** 20% discount (vs. 10%)—the difference is interpretable by the model.
- **Needs Encoding:** Coupon size as “large” or “small” — encode to make meaningful.
- **Poor Numeric Mapping:** Assigning "Arial"=1 and "Times New Roman"=2 implies an order that doesn't exist.

---
# Ensuring Sufficient Feature Value Examples in Machine Learning

When creating features for machine learning models, it’s not enough to have well-defined and meaningful fields—they also need to be **well-represented in your data**. This ensures your model actually learns from them. Here’s how and why.

---

## Why Feature Value Frequency Matters

- **Machine learning models need patterns, not outliers.**  
  If a value appears too infrequently, the model can’t reliably learn its relationship to the target.
- **Rule of thumb:**  
  *Have at least five examples of each value for every feature used.*

---

## What Does "Enough Examples" Mean?

Suppose you want to use **purchase category** ("auto," "grocery," etc.) as a model feature. You need at least five "auto" purchases (ideally with a mix of positive and negative target values). If a value appears only once or twice, it’s not trustworthy as input.

### The Problem With Rare Values

- **Overfitting:** Rare values may cause the model to make incorrect generalizations.
- **Misleading patterns:** The model may think something is a strong predictor simply because it happened by coincidence.

---

## Practical Examples

| Feature Example                               | Is Frequency Likely Enough?   | Handling if Too Rare                  |
|-----------------------------------------------|-------------------------------|---------------------------------------|
| **Percent discount (e.g., 10%, 15%)**         | Usually yes                   | Group rare values into bins           |
| **85% discount (rare promo)**                 | No (unless >5 examples)       | Combine with a group (e.g., "≥50%")   |
| **Promo start month (e.g., January)**         | Maybe—check sample size       | Group into quarters if too sparse     |
| **Ad emails opened (1,000; 1,200; 15 million)**| Most: yes; tail: no           | Remove/extreme outliers or group      |
| **Purchased item at store at 8pm Fri**        | Unlikely—too specific         | Generalize time or category           |
| **Distance to store (miles)**                 | Binned grouping needed        | Group into ranges (0-10, 11-50, etc.) |
| **Item category**                             | Typically enough              | Remove rare categories or group       |
| **Purchase channel (online/in-person)**       | Yes—usually just two values   | Safe to use                           |

---


---

## Best Practices

1. **Minimum value frequency:**  
   - Remove or group feature values with fewer than five occurrences.
2. **For continuous features:**  
   - Discretize (bin) values so every bin has enough examples.
3. **For outliers/rare cases:**  
   - Either exclude or aggregate into broader categories.

---

## Self-Check Questions

### 1. Why do we avoid including rare feature values in the model?
  - a) They slow down training
  - b) They don’t occur often enough for the model to learn reliable patterns
  - c) They improve accuracy
  - d) They cause memory errors

<details>
<summary>Answer</summary>
b) They don’t occur often enough for the model to learn reliable patterns.
</details>

### 2. What should you do if most "Promo Start Month" values are in January, but a few are scattered across many months with only 1-2 examples each?
  - a) Remove the “month” feature entirely
  - b) Group months into quarters or seasons
  - c) Convert them to numeric values
  - d) Ignore the problem

<details>
<summary>Answer</summary>
b) Group months into quarters or seasons.
</details>

---

## Summary

- Always ensure every feature value occurs enough times—at least five is a good starting point.
- For infrequent values: group, bin, or drop as appropriate.
- Plot histograms to visually inspect your feature value frequencies.
- Well-populated features help models learn robust patterns—infrequent ones can lead to overfitting or misleading results.

---
# The Importance of Human Insight in Feature Engineering

While machine learning relies on data, **human expertise is essential to successful feature engineering**. Your understanding of the domain helps ensure that the features you create are meaningful, practical, and likely to improve model performance.

---

## Why Human Insight Matters

- **Subject Matter Expertise (SME):**
  - Knowing the business or scientific context helps you select features that truly influence the outcome.
  - Example: In fraud detection, an SME knows which transaction patterns are genuinely suspicious.

- **Creativity and Curiosity:**
  - Thinking outside of raw data columns can reveal valuable derived or composite features.
  - Example: Combining “time of purchase” with “type of item” could flag unusual activity more effectively.

- **Iterative Improvement:**
  - Feature engineering is not a one-time process. After your first model iteration, expert review can reveal gaps or inspire new features for better results.
  - Example: After reviewing model errors, you might realize that seasonality or customer lifetime value are missing predictors.

---

## Best Practices

1. **Collaborate with Domain Experts**
   - Involve business owners, analysts, or those close to the data/problem.
2. **Be Willing to Iterate**
   - Review model outputs, feature importances, and error cases to refine your feature set with each new model cycle.
3. **Ask “What else could matter?”**
   - Approach the data with curiosity; look for new angles or relationships not initially in the dataset.

---

## Example Workflow

1. **Initial Model:**
   - Start with obvious features using SME suggestions.
2. **Evaluate:**
   - Use model performance metrics and error analysis.
3. **Refine:**
   - Add, remove, or transform features based on both model results and expert feedback.
4. **Repeat:**
   - Continue cycles to improve and adapt your feature set.

---

## Key Takeaway

**Domain knowledge and curiosity are just as important as technical skills in effective feature engineering. Bring both to the table—iterate, collaborate, and keep asking new questions as you refine your models.**

---
# Representing Features: Making Raw Data Model-Ready

Effective machine learning requires all input features to be represented *numerically* and in a way that preserves their real-world meaning. Below is a guide, with examples, on how to convert various data types into features ready for use in neural networks (or other ML models)—including how to handle categories, IDs, and missing data.

---

## 1. Numeric, Continuous Features

- **Examples:** `Wait Time`, `Price`
- **Approach:** Use these values *as is*; they are already real-valued and meaningful.
- **In TensorFlow:** Use `tf.feature_column.numeric_column`.

---

## 2. IDs and Categorical Features

IDs can be misleading because their magnitude isn’t meaningful (Employee ID 72365 isn’t “twice” employee 36182). Categorical data needs proper encoding.

### a) One-Hot Encoding (Sparse Columns)

- **Use for:** Small, known sets of categorical values (e.g., five employees).
- **Method:** Represent each unique value as a binary vector with only one "hot" (1) position.
  - Example (for Employee IDs 8345, 72365, 36182, 24001, 10001):  
    - If employee ID is 72365: `[0, 1, 0, 0, 0]`
- **In TensorFlow:** Use `tf.feature_column.categorical_column_with_vocabulary_list`.

### b) Vocabulary Lookup

- **When:** You don’t know all possible categories in advance.
- **Method:** Preprocess training data to build a *vocabulary* of known values; use that mapping during prediction.
- **Important:** The vocabulary must be identical at training and prediction time.

### c) Unknown Categories (New/Unseen)

- **Problem:** A new category appears that wasn’t in training data.
- **Solutions:**  
  - Assign a default “unknown” encoding.
  - Aggregate statistics until enough data exists for the new category.
  - Use average values, then retrain when more data is collected.

### d) Integerized Features

- **Best for:** Naturally integer features representing ordered or cyclic values (like hour of day: 0-23).
- **Note:** Only use if numbers are consecutive and order is meaningful.

### e) Hash Bucketing

- **Use for:** Very high-cardinality categories, or when enumerating all possible keys isn’t practical.
- **Method:** Hash categorical value into one of N buckets.
- **Downside:** Different categories may “collide” into the same bucket.

---

## 3. Handling Ratings (Ordinal or Categorical)

- **Options:**  
  - Treat as continuous (e.g., 1–5) if the difference between ratings is meaningful.
  - One-hot encode (e.g., 4 stars = `[0, 0, 0, 1, 0]` for possible values 1–5) if you don’t want the model to assume a linear relationship between ratings.

---

## 4. Handling Missing Data

- **Never use magic numbers** (e.g., -1, 999) to represent missing values; this confuses models.
- **Best practice:**  
  - Use **two columns**: one with the value (if present), and another indicating whether the value was observed (`1` if present, `0` if missing).
  - For one-hot encoding, use an all-zero vector for missing, plus a binary “was rated?” column.

---

## 5. Practical Example Table

| Raw Feature     | Good Numeric Representation(s)     | Notes                           |
|-----------------|------------------------------------|---------------------------------|
| Wait Time       | Real-valued column                 | Use as-is                       |
| Price           | Real-valued column                 | Use as-is                       |
| Transaction ID  | *Discard*                          | Not useful; value meaningless   |
| Employee ID     | One-hot, hashed, or vocab encoding | Use binary vector or hash       |
| Store Location  | One-hot, vocab, geo-coordinates    | Prefer categorical/geo info     |
| Customer Rating | Numeric (1–5) or one-hot           | Add “observed”/missing column   |

---

## 6. Key Best Practices & Questions

### Best Practices
- Only include numbers with meaningful size and order.
- Use proper categorical encoding—don’t treat arbitrary IDs as numbers.
- Always account for missing data with an extra indicator column.
- Keep vocabularies consistent from training to inference.

### Self-Check Questions

1. Why is it incorrect to use Employee ID as a numeric feature?
2. What should you do if a new category appears at prediction time?
3. Why should you use an extra column to indicate missing data?

<details>
<summary>Answers</summary>
1. Employee ID as a number misleads the model because the value does not encode order or meaning.
2. Assign an "unknown" bucket or average, and retrain after collecting more data.
3. To distinguish between true zero/blank input and genuinely missing data, which helps the model treat them differently.
</details>

---

## Summary

- Neural networks and most ML models require all features to be numeric.
- Use *real-valued columns* for continuous data, and *one-hot encoding, vocabulary hashing, or bucketing* for categorical or ID-like features.
- Always handle missing data explicitly.
- Feature representation choices have a direct impact on model quality.

---
# Quiz: Raw Data to Features

**Passing score: 75%**

---

### 1. Which of the following statements is true about preprocessing?

- [ ] Preprocessing without the context of Cloud ML allows you to do it at scale.
- [ ] Both options are correct.
- [ ] None of the options are correct.
- [x] Preprocessing within the context of Cloud ML allows you to do it at scale.

---

### 2. A good feature has which of the following characteristics?

- [ ] It should be known at prediction time.
- [ ] It should be numeric with meaningful magnitude.
- [ ] It should be related to the objective.
- [x] All of the options are correct.

---

### 3. In what form can raw data be used inside ML models?

- [x] After turning your raw data into a useful feature vectors
- [ ] After turning your raw data into multidimensional vectors
- [ ] After turning your raw data into a useful feature matrix
- [ ] None of the options are correct.

---

### 4. Which of the following statements is true?

- [ ] Same problems in the same domain may need different features.
- [ ] None of the options are correct.
- [x] Different problems in the same domain may need different features.
- [ ] Different problems in different domains may need the same features.

Even within the same domain (such as finance, healthcare, or retail), 
the specific problem you are trying to solve (e.g., predicting churn vs. detecting fraud) often requires a unique set of features tailored to that objective.


---

### 5. Which of the following are the requirements to build an effective machine learning model?

- [x] All of the options are correct.
- [ ] It should scale to a large dataset.
- [ ] It should be able to preprocess with Vertex AI Platform.
- [ ] It should find good features.

---

## Answer Key

1. Preprocessing within the context of Cloud ML allows you to do it at scale.
2. All of the options are correct.
3. After turning your raw data into a useful feature vectors
4. Different problems in the same domain may need different features.
5. All of the options are correct.

---

Good luck! Let me know if you want explanations for any answers or want a follow-up practice set.









