Study Notes: EDA using BigQuery and Colab Enterprise
1. Overview

Purpose: Analyze datasets in BigQuery using Colab Enterprise, perform queries, visualize data, and extract patterns.
Tools Used:

BigQuery: Managed cloud data warehouse for large-scale SQL analytics.
Colab Enterprise: Google Cloud Notebook solution for enterprise collaboration, with secure, scalable runtimes and integrations (Vertex AI, BigQuery).



2. Lab Workflow
Environment Setup

Log in to Google Skills using provided credentials.
Launch GCP Console, accept terms, and enable the Vertex AI API.

Creating a Colab Enterprise Notebook

In Vertex AI section, navigate to Notebooks > Colab Enterprise.
Choose a region, click + CREATE NOTEBOOK.
Open notebook; create a runtime (based on templates) if necessary.

Configuring Runtimes

Go to Runtime Templates, click + NEW TEMPLATE.
Step 1: Name, region.
Step 2/3: (Optional) Compute, networking, security.
Save and create the runtime.

Connecting and Executing Code

Python libraries for EDA:

numpy, pandas, seaborn, matplotlib, google.cloud.bigquery


Set up BigQuery client and pull sample data using SQL.
Use %%bigquery magic command for direct integration.
Convert BigQuery results to Pandas dataframe for analysis.

Basic Data Exploration

Use df.head(), df.info(), df.describe() for initial sense of the data.
Plotting using matplotlib and seaborn (histograms, heatmaps, etc.).
Compute correlation matrix and plot with seaborn heatmap.

SQL Queries

Use SQL (Standard dialect) to select specific fields, limit rows, or apply filters directly in notebook cells.

Version Control and Revision History

Access notebook revision history from Notebook Storage section.
View inline diffs, timestamps, and restore previous versions if needed.

Sharing

Share notebooks via the “Share” action; set permissions, roles, and (optionally) grant conditional access to users/groups, or service accounts.

Ending the Lab

Click “End Lab” to clean up resources.
Provide feedback on the lab experience.


3. Best Practices

Always enable necessary APIs (such as Vertex AI) before starting.
Keep data secure—do not share sensitive outputs or credentials.
Use version history to track and revert changes as needed.
Share only with intended collaborators and assign least-privileged roles.
Use BigQuery SQL to be precise and limit query costs (e.g., with LIMIT).


MCQs: EDA using BigQuery & Colab Enterprise
Q1. Which tool allows you to perform large-scale SQL analytics on Google Cloud with a managed, serverless setup?

A) Colab Enterprise
B) Vertex AI SDK
C) BigQuery
D) Vertex AI Workbench
Answer: C) BigQuery


Q2. What is a key advantage of Colab Enterprise over traditional Colab for teams in an enterprise environment?

A) Unlimited compute time
B) Enhanced security, compliance, and integration with enterprise Google Cloud services
C) Free GPUs for everyone
D) Local-only execution
Answer: B) Enhanced security, compliance, and integration with enterprise Google Cloud services


Q3. What should you do before modifying or running code in a Colab Enterprise notebook?

A) Close the notebook
B) Create (or connect to) an appropriate runtime
C) Download the notebook
D) Disable all APIs
Answer: B) Create (or connect to) an appropriate runtime


Q4. Which magic command lets you write and execute SQL for BigQuery directly from a Colab cell?

A) %bq
B) %%bigquery
C) %sql
D) %%bq
Answer: B) %%bigquery


Q5. After importing data from BigQuery into a Pandas DataFrame in Colab Enterprise, which command provides a summary of column data types and non-null counts?

A) df.head()
B) df.describe()
C) df.info()
D) df.summary()
Answer: C) df.info()


Q6. What must you do to plot numerical feature correlation using Seaborn?

A) Only plot categorical fields
B) Use select_dtypes to filter numeric columns, then compute .corr()
C) Use matplotlib’s scatter function only
D) Save the DataFrame as CSV first
Answer: B) Use select_dtypes to filter numeric columns, then compute .corr()


Q7. How can you view or revert previous changes to a Colab Enterprise notebook?

A) By opening the notebook in read-only mode
B) Using Revision History in Notebook Storage
C) With the “Undo” button only
D) Not possible in Colab Enterprise
Answer: B) Using Revision History in Notebook Storage


Q8. Which of the following is true for sharing a Colab Enterprise notebook?

A) Only Google group sharing is allowed
B) Principals (users/groups) can be given specific roles and optional conditions for access
C) Only read access can be granted
D) Notebooks cannot be shared
Answer: B) Principals (users/groups) can be given specific roles and optional conditions for access


Q9. What happens if you click “End Lab” before exporting your work?

A) The resources and your notebook are preserved
B) All work and resources are deleted
C) Only the environment is reset, not your notebook
D) You are logged out but your work is saved
Answer: B) All work and resources are deleted


Q10. Which of the following steps is required to visualize a correlation heatmap for a DataFrame df containing numerical columns only?

A) sns.heatmap(df.corr())
B) sns.heatmap(df.describe())
C) sns.heatmap(df.head())
D) sns.heatmap(df.info())
Answer: A) sns.heatmap(df.corr())


Would you like additional scenario-based questions, deeper technical walkthroughs, or a downloadable study sheet format?



