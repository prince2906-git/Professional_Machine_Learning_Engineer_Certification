# Google Cloud Professional Machine Learning Engineer Exam Study Guide

## Detailed Study Notes

### Key Challenges in ML Feature Management

- **Feature Reusability and Sharing**
  - Multiple teams may redundantly recreate the same features, which wastes resources and slows project delivery.
  - Limited ability to discover, reuse, or share features.

- **Dependency on Ops Teams**
  - Modelers may rely on ops resources to deploy or update features, creating bottlenecks.

- **Lifecycle Management Complexity**
  - Much time is devoted to moving features from engineering through training, serving, and monitoring.
  - Managing the entire feature lifecycle is challenging without integration and automation.

- **Application Integration**
  - Developers want to deploy ML endpoints in their apps without knowing feature generation/logistics.

- **Infrastructure Maintenance**
  - DevOps requires understanding, monitoring, and updating infrastructure for feature management.

---

### Main Pain Points

- **Difficult Sharing and Reuse:**  
  Teams often can't easily share and reuse features for multiple models/projects.

- **Challenges Serving at Low Latency:**  
  Real-time, reliable production serving is difficult to maintain.

- **Training-Serving Skew:**  
  Differences can occur between feature values at training time and those delivered in production, degrading model performance.

---

### Vertex AI Feature Store: Concepts and Benefits

- **Centralized Feature Repository**
  - Stores, organizes, and serves features for ML in a single location.
  - Enables fast feature discovery and sharing across the organization.

- **Operational Efficiency**
  - Fully managed service—Google Cloud handles scaling and reliability.
  - Lets data scientists focus on engineering new features, not system maintenance.

- **Robust APIs for Feature Lifecycle Management**
  - Register, discover, and fetch features with easy APIs.
  - Integrated permissions and governance.

- **Low-Latency, Scalable Serving**
  - Delivers feature values efficiently for both online (real-time) and batch predictions.

- **Training-Serving Skew Mitigation**
  - Features are computed once and reused for both training and serving, improving model stability.

- **Integrated Monitoring**
  - Ongoing monitoring for drift and feature quality issues.
  - Allows quick detection and remediation.

- **Flexible Ingestion Methods**
  - **Batch ingestion:** Large, periodic loads from, e.g., BigQuery.
  - **Streaming ingestion:** Real-time updates as data streams in.

- **Point-in-Time Lookup**
  - Retrieves features as they existed at any timestamp, essential for preventing data leakage and maintaining model integrity during training.

---

### GCP Services Context (Exam Relevance)

- **BigQuery ML (BQML) & AutoML:**  
  - Used for rapid model prototyping and deployment.

- **Cloud Storage, BigQuery Tables:**  
  - Legacy solutions for ad-hoc feature storage before adopting Feature Store.

- **Vertex AI Pipelines:**
  - Integrate with Feature Store for end-to-end ML workflows.

- **DevOps:**  
  - Managed services reduce time-to-productivity and lower operational risk.

---

## Practice Questions

### 1. Technical/Knowledge-Based

**Q1:** Which of the following is *not* a primary benefit provided by Vertex AI Feature Store in a GCP-based ML workflow?

A. Centralized feature repository  
B. Automated feature engineering  
C. Low-latency online feature serving  
D. Reduction of training/serving skew  

**Answer:** B  
**Explanation:** Vertex AI Feature Store centralizes management, sharing, and serving, but does **not** automate the feature engineering process itself.

---

### 2. Logical/Conceptual

**Q2:** Why does training-serving skew pose a risk to the reliability of machine learning models?

A. It increases computational cost  
B. It causes the training and production data distributions to differ  
C. It prevents data scientists from accessing features  
D. It increases feature ingestion latency  

**Answer:** B  
**Explanation:** Training-serving skew means the data used for training can differ from production data, reducing real-world model effectiveness.

---

### 3. Scenario-Based

**Q3:** The XYZ team is struggling with different teams recreating similar features and inconsistent feature values for their ML applications. Which Vertex AI feature directly addresses these problems?

A. AutoML Tables  
B. Vertex AI Model Monitoring  
C. Feature Store's centralized repository and APIs  
D. BigQuery's UDF library  

**Answer:** C  
**Explanation:** The centralized repository and APIs in Feature Store ensure consistency and feature reuse.

---

### 4. Technical/Knowledge-Based

**Q4:** Which operation is *specifically supported* by Vertex AI Feature Store to help avoid data leakage during model training?

A. Real-time feature streaming  
B. Batch export to Cloud Storage  
C. Point-in-time lookup  
D. Hyperparameter tuning  

**Answer:** C  
**Explanation:** Point-in-time lookup gives features as they existed at training, preventing data leakage.

---

### 5. Scenario-Based

**Q5:** A developer needs to add online prediction endpoints for ML models but lacks expertise in feature creation. How does Vertex AI Feature Store help in this scenario?

A. By generating model predictions using AutoML  
B. By hosting REST APIs for deploying models  
C. By allowing developers to retrieve required features without needing to generate them  
D. By auto-scaling compute resources for model training  

**Answer:** C  
**Explanation:** Developers can fetch needed features via APIs, removing dependency on custom feature creation.

---

### 6. Logical/Conceptual

**Q6:** What is the impact of using a fully managed feature store like Vertex AI Feature Store on an ML team's productivity and operational overhead?

A. Increased time managing infrastructure  
B. Reduced need for operational expertise  
C. Slower model deployment cycles  
D. Higher risk of inconsistent feature use  

**Answer:** B  
**Explanation:** Managed solutions streamline operations and let teams focus on value-add activities.

---

### 7. Technical/Knowledge-Based

**Q7:** Which ingestion methods are supported by Vertex AI Feature Store?

A. Only batch ingestion from BigQuery  
B. Only real-time ingestion from streaming data sources  
C. Both batch and real-time (streaming) ingestion  
D. Ingestion only from Cloud Storage  

**Answer:** C  
**Explanation:** Both batch and real-time ingestion are supported.

---

### 8. Scenario-Based

**Q8:** Which feature of Vertex AI Feature Store helps mitigate redundant feature engineering work across multiple teams?

A. High-availability feature serving  
B. Feature discovery APIs  
C. Model explainability integration  
D. Pre-built AutoML pipelines  

**Answer:** B  
**Explanation:** Discovery APIs facilitate finding and reusing existing features.

---

### 9. Logical/Conceptual

**Q9:** What is a key benefit of leveraging a central feature registry for ML features?

A. Easier management of model training cost  
B. Improvement in ML model interpretability  
C. Consistent and reusable feature definitions across projects  
D. Automated data labeling for supervised learning  

**Answer:** C  
**Explanation:** Central registries ensure project-wide consistency and reuse.

---

### 10. Technical/Knowledge-Based

**Q10:** Which of the following is part of the monitoring capabilities enabled by Vertex AI Feature Store?

A. Hardware resource monitoring for GPUs  
B. Feature drift and data quality monitoring  
C. User access logging  
D. Automated hyperparameter tuning  

**Answer:** B  
**Explanation:** Feature Store supports monitoring for feature drift and quality.

---

# Google Cloud Professional Machine Learning Engineer Exam Study Guide: Feature Store Concepts and Terminology

## Detailed Study Notes

### What is a Feature Store?

- **Feature Store**:  
  - A top-level container for features and their values.
  - Permits defined users to add, share, and manage features without extra engineering.

- **Purpose:**  
  - Centralizes feature management for ease of ingestion, discovery, sharing, and serving.
  - Supports multiple data sources for feature ingestion.

---

### Core Terminology

- **Feature:**
  - A value (scalar, array, or tensor) used as input to a model.
  - Describes some property of an entity (e.g., “age of user,” “price of product”).

- **Entity Type:**
  - A group of semantically related features (e.g., “Movies” and “Users” in a movie service).

- **Entity:**
  - An individual instance within an entity type (e.g., "movie_01").
  - Each entity has a unique ID, which must be a STRING.

- **Entity View:**
  - The projection of features and their values for entities retrieved via serving requests (online or batch).
  - Contains requested feature values with statistics (such as mean, stdev, min, max, missing counts).

- **Feature Value:**
  - The actual data associated with an entity and feature at a particular point in time.
  - Multiple values can exist for a feature–entity pair, distinguished by timestamp.

- **Tuple Identifier:**
  - Combination of entity_ID, feature_ID, and timestamp, uniquely identifies each feature value.

- **Timestamp:**
  - Indicates when a feature value was generated.
  - Can be specified at ingestion. Timestamps are tied to feature values, not features themselves.
  - Retention of data is managed using timestamp (not the import time).

---

### Operations and Workflows

- **Feature Ingestion:**
  - Importing computed feature values from sources such as BigQuery or Cloud Storage.
  - Requires pre-defined entity types and features.
  - Batch ingestion is supported for bulk loading.

- **Feature Serving:**
  - Exporting stored features for use in model training (batch) or online prediction (real-time).
  - **Batch Serving**: High-throughput, large-scale exports (offline training/batch prediction).
  - **Online Serving**: Low-latency, small-batch retrievals (real-time inference).

- **Value Types:**
  - Boolean, double, string, array, etc., define what types of values may be ingested for each feature.

- **Relationships:**
  - One-to-many mapping: One entity can have many associated feature values, each for different points in time.

---

### Example Use Case

- **Movie Service Example:**
  - Entity Types: “Movies” and “Users”
  - Entities: “movie_01”, “user_01”
  - Features: “average_rating,” “genre,” “age”
  - Feature Store captures values (e.g., average_rating=4.4 at T1, average_rating=4.8 at T2).

---

## Practice Questions

### 1. Technical/Knowledge-Based

**Q1:** Which of the following is *true* about an entity in Vertex AI Feature Store?

A. It must have a numeric ID  
B. It represents a unique instance within an entity type  
C. It is always created automatically when features are ingested  
D. It cannot be associated with multiple features  

**Answer:** B  
**Explanation:** Entities are unique instances (e.g., "movie_01") within an entity type. The ID must be a string.

---

### 2. Technical/Knowledge-Based

**Q2:** What is the role of a timestamp in Vertex AI Feature Store?

A. Identifies the entity type  
B. Denotes when a feature value was generated  
C. Tracks user access to the feature store  
D. Specifies the physical storage location  

**Answer:** B  
**Explanation:** The timestamp records when each feature value was generated, allowing retrieval of historic data.

---

### 3. Logical/Conceptual

**Q3:** What does an entity view provide in a feature store context?

A. All entity types stored in the feature store  
B. A projection of the requested features and values for specific entities  
C. Current resource consumption statistics  
D. The actual storage schema for feature tables  

**Answer:** B  
**Explanation:** An entity view is the projection of queried feature values for entities, for batch or online requests.

---

### 4. Scenario-Based

**Q4:** A team needs to support both real-time and offline training workflows for ML models. What serving modes does Feature Store provide to meet these requirements?

A. Online only  
B. Batch only  
C. Both batch (for offline) and online (for real-time)  
D. Streaming only  

**Answer:** C  
**Explanation:** Feature Store supports both batch (offline, high-throughput) and online (low-latency, real-time) serving.

---

### 5. Technical/Knowledge-Based

**Q5:** What is necessary before ingesting feature values into a feature store?

A. A model must be trained  
B. The entity type and features must be predefined in the store  
C. Serving endpoints must be deployed  
D. Feature value types must be Boolean  

**Answer:** B  
**Explanation:** You cannot ingest feature values unless the entity type and features are already defined.

---

### 6. Logical/Conceptual

**Q6:** Which best describes the relationship between entities and features in a feature store?

A. One entity can have only one feature  
B. One entity can have many features, each with potentially multiple values across time  
C. One feature can belong to multiple entities of different types  
D. Feature values do not track which entity they belong to  

**Answer:** B  
**Explanation:** An entity can have multiple feature values, each tracked per timestamp.

---

### 7. Scenario-Based

**Q7:** Where might source data for feature ingestion reside before loading into Vertex AI Feature Store? (Select TWO)

A. BigQuery  
B. Vertex AI Pipelines  
C. Cloud Storage  
D. REST API only  

**Answer:** A and C  
**Explanation:** Source data for ingestion is typically in BigQuery or Cloud Storage.

---

### 8. Technical/Knowledge-Based

**Q8:** When specifying a feature for a Feature Store, what must be configured?

A. Geographic region  
B. Value type (e.g., Boolean, Array, String)  
C. Network firewall settings  
D. Cost quota  

**Answer:** B  
**Explanation:** You must specify value type when defining a new feature.

---

# Google Cloud Professional Machine Learning Engineer Exam Study Guide: Feature Store Data Model

## Detailed Study Notes

### Core Elements of the Feature Store Data Model

- **Data Model Overview**
  - The data model includes four main concepts:  
    - **Entity Type**
    - **Entities**
    - **Features**
    - **Feature Values**
  - Feature Store uses a **time series data model**:  
    - Stores and manages a *series* of values for features as they **change over time**.

---

### Key Concepts Explained

- **Entity Type**
  - High-level grouping for related features (e.g., “movies”).
  - Defined based on your use case/domain.

- **Entities**
  - Specific instances within an entity type (e.g., “movie_01”, “movie_02”).
  - Each entity is uniquely identified (e.g., by movie_id).

- **Features**
  - Properties or attributes of an entity type (e.g., “average_rating”, “title”, “genres” for movies).

- **Feature Values**
  - Specific values that a feature takes for a particular entity at a point in time.

---

### Time Series Nature

- **Time Series Storage**
  - Feature Store can track and retain values for features over time (e.g., changes in “average_rating” for a movie).
- **Timestamps**
  - Each feature value *may* be paired with a timestamp (attribute—not its own resource type).
  - Timestamps indicate *when* feature values were generated.
  - Required only if values were generated at different points in time.
  - If feature values were created simultaneously, a timestamp column isn’t needed; timestamp can be specified during data ingestion.

---

### Practical Example

- **Source Data from BigQuery Table**
  - **Column headers**:  
    - `movie_id` → entity type/ID  
    - `average_rating`, `title`, `genres` → features  
    - Other columns → additional features or entity attributes  
    - `timestamp` → indicates time of value creation
  - **Rows**:  
    - Represent instances/entities, each with its set of feature values at a given timestamp.

---

## Practice Questions

### 1. Technical/Knowledge-Based

**Q1:** What core elements does the Feature Store data model include?

A. Entities, Features, Feature Values, Timestamps  
B. Region, Bucket, File Format, ID  
C. Entity Type, Entities, Features, Feature Values  
D. Feature Set, Value Type, Index, Caching  

**Answer:** C  
**Explanation:** These are the four main elements of the Feature Store data model.

---

### 2. Technical/Knowledge-Based

**Q2:** What is the main advantage of using a time series data model in Vertex AI Feature Store?

A. Enables real-time streaming  
B. Supports automatic data labeling  
C. Maintains and tracks feature values as they change over time  
D. Enables geospatial queries  

**Answer:** C  
**Explanation:** The time series data model allows storage of feature value histories for each entity.

---

### 3. Scenario-Based

**Q3:** A team imports data from BigQuery where some movies have updated average ratings at different times. How should this be modeled in Feature Store?

A. Overwrite all feature values with the latest  
B. Store each average rating with its corresponding timestamp  
C. Only keep the earliest value for each  
D. Store timestamps as a separate resource  

**Answer:** B  
**Explanation:** Tracking each value with its timestamp supports the time series model.

---

### 4. Logical/Conceptual

**Q4:** In Feature Store, what is the purpose of including the timestamp with feature values?

A. To enforce unique entity type constraints  
B. To denote when the feature value was generated  
C. To improve ingestion speed  
D. To determine storage region  

**Answer:** B  
**Explanation:** Timestamps record precisely when each feature value was generated/changing.

---

### 5. Technical/Knowledge-Based

**Q5:** Which statement is true when importing features from a data source where all values were generated at the same time?

A. A timestamp column is mandatory in the table  
B. Timestamps are not needed at import  
C. Timestamp can be provided as part of the ingestion request  
D. Timestamps must be attached to the entity ID  

**Answer:** C  
**Explanation:** If all feature values share a timestamp, it can be specified during ingestion instead of requiring a column.

---
# Google Cloud Professional Machine Learning Engineer Exam Study Guide: Creating and Ingesting into Vertex AI Feature Store

## Detailed Study Notes

### Challenges Solved by Feature Store

- **Feature reusability and sharing:** Reduces duplication and makes sharing easier across teams.
- **Low-latency serving:** Provides reliable, scalable, low-latency serving of feature data.
- **Training-serving skew:** Centralizes feature management, reducing discrepancies between training and serving.

---

### Preparation and Data Requirements

- **Data Preprocessing:**
  - Ensure data is *clean* (no missing values, correct types, encoded categorical values).
  - All columns must have headers of type STRING.
  - Data types in source must match those of feature store definitions.

- **Supported Data Sources for Ingestion:**
  - *BigQuery tables*
  - *Cloud Storage* files (must be in Avro or CSV format)
    - CSV cannot contain array data types; use Avro or BigQuery for arrays.
    - Nulls cannot be present in an array, but empty arrays are supported (except CSV).

- **Entity ID Column:**
  - Required, must be of type STRING.
  - Contains IDs for the entities whose feature values are being ingested.

- **Timestamp Column:**
  - Optional if all feature values generated at the same time (can specify at ingestion).
  - Required formats:
    - BigQuery: TIMESTAMP
    - Avro: long/logical type "timestamp-micros"
    - CSV: RFC 3339 string

- **Minimum Rows:**
  - At least *1,000 rows* required for a data set to be uploaded into Vertex AI Feature Store.

---

### Creating a Feature Store (Console Overview)

1. **Start:** In the Vertex AI console (or Workbench/API), go to Features and select a region.
2. **Create Feature Store:**
   - Name the feature store.
   - (Optional) Select a customer-managed encryption key.
   - Enter the number of nodes (for scaling).
   - Click "Create".
   - *Note*: Deleting or adding a feature store must be done via API, not console.
   
---

### Creating Entity Types and Features

1. **Entity Types:**
   - Groups and contains related features (“budget_id” for media budgets, “movies” for a movie dataset, etc.).
   - Description and monitoring are optional.
   - Select feature store, create entity type, optionally add description.

2. **Features:**
   - Must specify name, value type, and monitoring interval.
   - (Optional) Add description, override monitoring, interval.
   - Can monitor value distributions, data types, and stats directly in the UI.

3. **Feature Monitoring:**
   - Enables monitoring on specific features or entity types.
   - Set up, enable/disable, and update intervals as needed.
   - Monitors for data drift or operational stats (CPU, ingestion health, etc.).

---

### Ingestion Process (Importing Data)

- **Define entity type and features first.**
- Set up batch ingestion:
  - From BigQuery or Cloud Storage (Avro/CSV).
  - Data columns:
    - `entity_id`: ID of the entity (STRING)
    - `timestamp`: when the feature value was generated
    - Feature columns: must match destination feature names.
- Ingestion jobs are tracked with properties like:
  - Creation time, duration, region, number of workers, data source link, entity type, feature store name.
- After ingestion, feature values are ready for batch or online serving.

---

## Practice Questions

### 1. Technical/Knowledge-Based

**Q1:** Which data formats are supported by Vertex AI Feature Store for file-based ingestion from Cloud Storage?

A. Parquet and JSON  
B. Avro and CSV  
C. CSV and Excel  
D. Avro and plain text  

**Answer:** B  
**Explanation:** Only Avro and CSV are supported for file ingestion from Cloud Storage.

---

### 2. Scenario-Based

**Q2:** You have a dataset for import, which includes categorical columns with one-hot encoding, no missing values, and STRING entity IDs. What else must you check before beginning ingestion to Vertex AI Feature Store?

A. Verify that entity ID column is numeric  
B. Ensure all column headers are strings and types match feature definitions  
C. Ensure Avro file is compressed  
D. Confirm that timestamps are in ISO 8601 only  

**Answer:** B  
**Explanation:** Column headers must be strings, and types must align with the feature store schema.

---

### 3. Technical/Knowledge-Based

**Q3:** What is the minimum number of rows required to upload a dataset to Vertex AI Feature Store?

A. 1  
B. 100  
C. 500  
D. 1,000  

**Answer:** D  
**Explanation:** A minimum of 1,000 rows is required for dataset ingestion.

---

### 4. Logical/Conceptual

**Q4:** Why can’t you include array data types in CSV files for Vertex AI Feature Store ingestion?

A. Arrays are not supported by any data source  
B. CSV does not support a standard representation for arrays  
C. Arrays require every element to be a string  
D. Arrays must contain null elements  

**Answer:** B  
**Explanation:** CSV lacks a standard way to encode arrays, so only Avro or BigQuery should be used for arrays.

---

### 5. Scenario-Based

**Q5:** An operations team wants to monitor CPU usage and feature drift for a specific feature store. How should they enable monitoring?

A. Set monitoring at feature and entity type level in the feature store UI  
B. Use only external GCP Stackdriver Monitoring  
C. Enable it only at time of ingestion  
D. Monitoring cannot track operational stats  

**Answer:** A  
**Explanation:** Monitoring can be enabled for specific features or entity types within the store UI.

---

### 6. Technical/Knowledge-Based

**Q6:** When is the timestamp column optional in feature ingestion?

A. Always  
B. Only when importing from BigQuery  
C. When all feature values are generated at the same time  
D. Never; it is required for all imports  

**Answer:** C  
**Explanation:** If all feature values have the same timestamp, it can be provided at ingestion, and a column in the data is not required.

---

### 7. Logical/Conceptual

**Q7:** What must you define before starting any feature ingestion job in Vertex AI Feature Store?

A. Only the feature names  
B. Dataset description and version  
C. Corresponding entity types and features  
D. Monitoring interval only  

**Answer:** C  
**Explanation:** Both entity types and features must be defined in the store before ingesting values.

---

### 8. Scenario-Based

**Q8:** If an ingestion job imports data from BigQuery into a feature store, what properties can you review after ingestion completes?

A. Deployed models only  
B. Source data schema and ingestion job status  
C. Ingestion time, region, number of workers, entity type, and store  
D. Only number of ingested arrays  

**Answer:** C  
**Explanation:** Job properties include time, region, number of workers, entity type, and feature store name.

---

# Google Cloud Professional Machine Learning Engineer Exam Study Guide: Feature Serving – Batch and Online

## Detailed Study Notes

### What Is Feature Serving?

- **Feature serving** is the process of exporting stored feature values from Vertex AI Feature Store for training machine learning models (offline) or generating predictions (online, real-time).

---

### Types of Feature Serving

- **Batch Serving**
  - Retrieves large volumes of feature data from the **offline store** for training or batch inference.
  - Uses the **batch serving API**.
  - Supports historical, point-in-time lookups, which are essential for accurate training datasets and batch predictions.
  - Typical use: training models, generating batch predictions.
  - Output can be written in **CSV** or **TFRecord** format to Cloud Storage.
  - Each batch ingestion job:
    - Imports features for a single entity type.
    - Allows for up to 100 features.
    - Only one batch job per entity type runs at a time.
    - Requires source data to match a single entity type.

- **Online Serving**
  - Provides low-latency, small-batch feature retrieval for real-time applications such as live prediction endpoints.
  - Data is read from the **online store** (holds the latest values).
  - Applications use the **online serving API** to fetch current feature values needed for inference.

---

### Storage Systems and Data Flow

- **Offline Store**
  - Stores historical feature values.
  - Used for training and batch prediction scenarios.
  - Data retained for long-term access and historical retrieval.

- **Online Store**
  - Holds only the latest feature values.
  - Optimized for low-latency, real-time fetches for online prediction.

- **Data Ingestion**
  - Batch ingestion writes reliably to both offline and online stores, ensuring feature parity and consistency for both training and serving.

---

### Example Workflow

- **Scenario:** Predicting baby weight from birth records.
  - Historical data (e.g., date of birth, mother's age, gestational age) ingested into Feature Store via batch ingestion.
  - Batch serving provides this historical data for training.
  - Mobile app uses online serving API to request real-time predictions with user-selected input features.

---

### Batch Serving Process (Key Steps)

1. **Initiate batch ingestion job (API only):**
   - Specify the entity type, source data location, and mapping to features.
2. **After ingestion completes:**
   - Feature values are available to both the online and offline stores.
3. **For batch serving (training or offline inference):**
   - Specify the features, a read instance list (per training example), and destination URI/format (Cloud Storage CSV/TFRecord).
   - Feature Store joins read instances with corresponding feature values and exports them.

---

### API and Limitations

- Batch and online serving use different APIs.
- Only one batch ingestion job per entity type at a time (to prevent collision).
- Batch serving must be configured via the API, not via GUI.

---

## Practice Questions

### 1. Technical/Knowledge-Based

**Q1:** What is the main difference between the offline and online stores in Vertex AI Feature Store?

A. Online store supports only numerical features  
B. Offline store holds historical feature values, online store holds latest values  
C. Offline store is used only for serving, online store only for ingestion  
D. Online store is not accessible by APIs  

**Answer:** B  
**Explanation:** The offline store keeps historical values for training; online keeps only the latest values for real-time prediction.

---

### 2. Scenario-Based

**Q2:** How should you retrieve up-to-date feature values for a real-time mobile prediction app?

A. Query the offline store via batch serving API  
B. Use the online serving API to fetch required feature values  
C. Download the entire feature set from Cloud Storage  
D. Use a scheduled batch job to push values  

**Answer:** B  
**Explanation:** The online serving API is optimized for low-latency, real-time access for prediction apps.

---

### 3. Technical/Knowledge-Based

**Q3:** Which file formats are supported for batch serving output in Vertex AI Feature Store?

A. XML and JSON  
B. CSV and TFRecord  
C. Avro and Parquet  
D. TXT and Excel  

**Answer:** B  
**Explanation:** Batch serving output can be written as CSV or TFRecord files in Cloud Storage.

---

### 4. Logical/Conceptual

**Q4:** Why is point-in-time lookup important for batch serving feature values?

A. To ensure latest model version is used  
B. To match training data to the state of features at the right time, preventing data leakage  
C. To speed up the ingestion process  
D. To clean missing values automatically  

**Answer:** B  
**Explanation:** Point-in-time lookup retrieves feature values as they were at the exact time of the training/inference event.

---

### 5. Scenario-Based

**Q5:** A data scientist is running a batch ingestion job for a dataset with 120 features and two entity types. What restriction applies?

A. All features and entity types will be imported at once  
B. Only up to 100 features for a single entity type can be ingested per job  
C. No restrictions on feature number or entity types  
D. Must use the web UI for ingestion  

**Answer:** B  
**Explanation:** Each batch ingestion job is for one entity type and can import up to 100 features.

---

### 6. Technical/Knowledge-Based

**Q6:** What must be true before you can run a batch ingestion or serving job?

A. You have defined entity types and features in the Feature Store  
B. All data must be in Avro format  
C. Store must contain only historical data  
D. Source data can’t include timestamps  

**Answer:** A  
**Explanation:** Both entity types and features must be predefined in the Feature Store configuration.

---
# Quiz: Introduction to Vertex AI Feature Store – With Answers & Explanations

Passing Score: 75%

---

### 1. Vertex AI Feature Store provides a centralized repository for organizing, storing, and serving ML features. Using a central featurestore, enables an organization to efficiently share, discover, and re-use ML features at scale, which can increase the velocity of developing and deploying new ML applications. What are the key challenges that Vertex AI Feature Store solves?

- Mitigate training-serving skew, which occurs when the feature data distribution that you use in production differs from the feature data distribution that was used to train your model.
- All of the options are correct.
- Detect drift, as a result of significant changes to your feature data distribution over time.
- Mitigate data storage silos, which occurs when you might have built and managed separate solutions for storage and the consumption of feature values.

**Answer:** All of the options are correct.  
**Explanation:** Vertex AI Feature Store addresses all listed challenges: mitigating storage silos, managing drift, and reducing training/serving skew.

---

### 2. Where are the features registered?

- Online Store
- Feature registry
- Offline Store
- Feature Monitoring

**Answer:** Feature registry  
**Explanation:** Features are officially registered and managed in the feature registry. The online and offline stores are for serving and storage, respectively.

---

### 3. What is one definition of a feature in machine learning?

- A value that is passed as input to a model
- A place to store any data
- A method of feature store
- A value that you receive from a model as an output

**Answer:** A value that is passed as input to a model  
**Explanation:** In ML, a feature represents an input variable—some measurable attribute or property used by the model.

---

### 4. What are the two methods feature store offers for serving features?

- Online serving and Offline serving
- Batch serving and Stream serving
- Offline serving and Stream serving
- Batch serving and Online serving

**Answer:** Batch serving and Online serving  
**Explanation:** The two main serving modes are "batch" (for offline/model training) and "online" (for low-latency real-time inference).

---

### 5. Which of the following is the process of importing feature values computed by your feature engineering jobs into a featurestore?

- Feature store
- Feature ingestion
- Feature serving
- Feature Monitoring

**Answer:** Feature ingestion  
**Explanation:** The process of importing or loading feature values is called "feature ingestion."

---

### 6. Which of the following is an instance of an entity type?

- Entity
- Online Store
- Featurestore
- Feature

**Answer:** Entity  
**Explanation:** An "entity" is a unique instance within a given entity type (e.g., "movie_01" within entity type "Movies").

---

*Need explanations for incorrect answers, or more practice questions? Just ask!*



