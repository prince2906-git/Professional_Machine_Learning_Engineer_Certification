Challenge Lab: Prepare Data for ML APIs on Google Cloud
Summary
In this challenge lab, you’re asked to apply everything you’ve learned from prior labs—without step-by-step instructions. You’ll set up a Dataflow job for ETL, run a Spark job on Dataproc, use Speech-to-Text API to transcribe audio, and utilize Cloud Natural Language API for text analysis. Completing all tasks within the time limit demonstrates hands-on skills with Google Cloud data tools, IAM roles, and ML APIs.

Challenge Guide: How to Approach Each Task
1. Environment and Permissions

Use only the provided student account and use Incognito mode to avoid account conflicts/billing issues.
Before starting, confirm the required service account (compute@developer.gserviceaccount.com) exists and has both Editor and Storage Admin roles in IAM.


2. Task 1: Run a Simple Dataflow Job

Objective: Move data from a specified Cloud Storage .csv to BigQuery using a batch template.
Steps:

Create a Cloud Storage bucket (for temp files).
Create a BigQuery dataset and table.
Set up Dataflow via the batch template (Text Files on Cloud Storage to BigQuery) using the input file (gs://spls/gsp323/lab.csv), schema, and output locations given.
Specify machine type and optional params (e.g., UDF for transform).
Wait for the job to finish and verify results in BigQuery.




3. Task 2: Run a Simple Dataproc Job

Objective: Run a Spark job to process sample data.
Steps:

Create a Dataproc cluster (E2 series, correct region, nodes and disk sizes as required).
SSH into a node and copy the input file into HDFS:Bashhdfs dfs -cp gs://spls/gsp323/data.txt /data.txt


Submit the job (SparkPageRank):

Main class: org.apache.spark.examples.SparkPageRank
Jar: file:///usr/lib/spark/examples/jars/spark-examples.jar
Arguments: /data.txt


Wait for completion and check logs/results.




4. Task 3: Use Google Cloud Speech-to-Text API

Objective: Transcribe gs://spls/gsp323/task3.flac and upload the results to a Cloud Storage location.
Steps:

Generate API key if needed.
Construct and send Speech-to-Text API request (pointing to Cloud Storage audio).
Save the transcription JSON.
Upload result file to the designated Cloud Storage bucket.




5. Task 4: Use Cloud Natural Language API

Objective: Analyze sentiment or entities in a provided sentence about Odin, and upload the API result.
Steps:

Create or reuse a service account/key if required.
Compose and send a Natural Language API request (specify the text).
Save the analysis output.
Upload result file to the required Cloud Storage location.




General Tips

Use Google Cloud documentation and console hints.
Double-check resource regions for consistency.
Take note of IAM-related errors and permissions.
For any failures, refer to error messages and documentation.
Monitor the time—all tasks must be completed before lab expiration.


Practice Questions (MCQ/Scenario/Logic)

1. What is the purpose of a challenge lab in this context?
A) Teach new APIs
B) Let you practice troubleshooting and applying skills without step-by-step help
C) Give an open-book exam
D) Practice billing administration
Answer:
B) Let you practice troubleshooting and applying skills without step-by-step help

2. What role(s) must the default compute service account have?

[ ] Editor
[ ] BigQuery Admin
[ ] Storage Admin
[ ] Billing Admin

Answer:

[x] Editor
[x] Storage Admin


3. What should you do if you find the compute service account is missing a required role?
A) Add the role manually in IAM
B) Ignore it
C) Change the region
D) Reboot the VM
Answer:
A) Add the role manually in IAM

4. What is the first input file for the Dataflow job?
A) gs://spls/gsp323/lab.csv
B) gs://spls/gsp323/data.txt
C) gs://spls/gsp323/task3.flac
D) gs://spls/gsp323/lab.schema
Answer:
A) gs://spls/gsp323/lab.csv

5. In the Dataflow template, which parameter specifies the BigQuery table schema?
A) BigQuery Table Name
B) gs://spls/gsp323/lab.schema
C) gs://output/schema.json
D) None
Answer:
B) gs://spls/gsp323/lab.schema

6. When preparing a Dataproc Spark job, what is the first file operation required?
A) Mount an NFS drive
B) Copy data.txt from Cloud Storage to HDFS
C) Compress input file
D) Delete HDFS data
Answer:
B) Copy data.txt from Cloud Storage to HDFS

7. What does the argument /data.txt represent in the SparkPageRank job?
A) The output file
B) Input file in HDFS
C) BigQuery table
D) Jar path
Answer:
B) Input file in HDFS

8. Why should you wait for each cloud job to finish before checking progress?
A) To avoid errors with file locks
B) Automated grading checks for job completion/results
C) To reduce output file size
D) For better pricing
Answer:
B) Automated grading checks for job completion/results

9. To transcribe an audio file via the Speech-to-Text API, you must provide:
A) Audio content inline only
B) A Cloud Storage URI or local file
C) Only a file name
D) BigQuery dataset name
Answer:
B) A Cloud Storage URI or local file

10. What result should be uploaded after Speech-to-Text API processing?
A) The raw audio
B) The transcription JSON
C) The command logs
D) The Dataproc job output
Answer:
B) The transcription JSON

11. When analyzing text with the Natural Language API, which property is often useful for entity analysis?
A) entities
B) audio
C) labels
D) nodes
Answer:
A) entities

12. If you encounter an API permission error, your first action should be:
A) Re-run the command
B) Check IAM roles and permissions for the relevant service account
C) Ignore and continue
D) Change the region
Answer:
B) Check IAM roles and permissions for the relevant service account

13. What region setting is important for cloud jobs?
A) Default is always global
B) Must match the region of your resources and cluster
C) Any region is fine
D) Region must be us-east1
Answer:
B) Must match the region of your resources and cluster

14. Scenario: Your Dataflow job can't write to BigQuery. What is a likely cause?
A) Output table name typo
B) Service account missing BigQuery write permissions
C) Audio file encoding error
D) Not enough cluster nodes
Answer:
B) Service account missing BigQuery write permissions

15. Which Dataflow parameter lets you apply a JavaScript transformation to the data?
A) Machine type
B) UDF path and name
C) Region
D) Disk size
Answer:
B) UDF path and name

16. What’s a benefit of using GCP challenge labs for learning?
A) Unlimited time
B) Immediate, automated feedback on hands-on skills
C) Full answer keys provided
D) Only theoretical questions
Answer:
B) Immediate, automated feedback on hands-on skills

17. How is progress verified in each task?
A) Perform manual peer review
B) Use the Check my progress button to trigger automated grading
C) Email your results
D) Review GitHub issues
Answer:
B) Use the Check my progress button to trigger automated grading

18. Which resource must you not use to avoid unintentional charges?
A) Your personal Google Cloud account
B) The lab-provided student account
C) The Incognito window
D) The Cloud Shell
Answer:
A) Your personal Google Cloud account

19. If you need to upload a result file to a Cloud Storage location, what’s the command?
A) gsutil cp localfile gs://bucket/path
B) curl --upload-file localfile
C) bq upload
D) gcloud create file
Answer:
A) gsutil cp localfile gs://bucket/path

20. What is crucial for finishing this challenge lab successfully?

[ ] Completing all tasks within the time limit
[ ] Carefully reading and applying instructions/hints
[ ] Monitoring IAM and permissions
[ ] Only using default parameter values

Answer:

[x] Completing all tasks within the time limit
[x] Carefully reading and applying instructions/hints
[x] Monitoring IAM and permissions


Let me know if you’d like scenario explanations, troubleshooting common errors, or focused guides on any challenge task!
