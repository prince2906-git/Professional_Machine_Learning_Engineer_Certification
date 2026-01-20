Cloud Natural Language API: Qwik Start
Lab Summary
Objectives

Create an API key and a service account for authentication.
Use Cloud Natural Language API to extract entities from text.


Lab Steps and Key Commands
1. Initial Setup

Use lab-provided credentials and Incognito/Private Window to avoid account conflicts or unwanted charges.
Open the Google Cloud Console from the lab’s Start link.

2. Activate Cloud Shell

Click Activate Cloud Shell in the Google Cloud Console.
(Optional) Verify active account:Bashgcloud auth list


(Optional) Verify project:Bashgcloud config list project




3. Create and Configure Service Account

Set PROJECT_ID variable:Bashexport GOOGLE_CLOUD_PROJECT=$(gcloud config get-value core/project)


Create service account:Bashgcloud iam service-accounts create my-natlang-sa \
  --display-name "my natural language service account"


Generate credentials for the account (save as JSON):Bashg
cloud iam service-accounts keys create ~/key.json \
  --iam-account my-natlang-sa@${GOOGLE_CLOUD_PROJECT}.iam.gserviceaccount.com


Set credentials environment variable for authentication:Bash
export GOOGLE_APPLICATION_CREDENTIALS="/home/USER/key.json"

(Replace USER with your username.)


4. Make an Entity Analysis Request

SSH to the provisioned Compute Engine VM via the Console.
Run entity analysis on sample text:Bash
gcloud ml language analyze-entities --content="Michelangelo Caravaggio, Italian painter, is known for 'The Calling of Saint Matthew'." > result.json


View the analysis result:Bash cat result.json




What does the API output?

List of entities (with type: PERSON, LOCATION, EVENT, etc.)
Metadata (e.g., Wikipedia URL), salience score, and mentions.


Practice Questions (MCQ/Short Answer)

1. What is the main goal of the Cloud Natural Language API?
A) Manage virtual machines
B) Analyze and extract meaning from text
C) Encrypt network traffic
D) Build container images
Answer:
B) Analyze and extract meaning from text

2. Which of the following are features of the Cloud Natural Language API?
(Select all that apply)

[ ] Sentiment Analysis
[ ] Entity Recognition
[ ] Data Encryption
[ ] Information Extraction

Answer:

[x] Sentiment Analysis
[x] Entity Recognition
[x] Information Extraction


3. Before running API requests in the lab, you must:
A) Deploy a Kubernetes cluster
B) Set the lab-provided project as current and authenticate
C) Install Java manually
D) Set up Pay-As-You-Go billing
Answer:
B) Set the lab-provided project as current and authenticate

4. What is the main command to analyze entities in a text snippet using the API?
A) gcloud ml language analyze-syntax
B) gcloud ml language analyze-entities
C) gcloud compute start
D) gcloud dataproc jobs submit
Answer:
B) gcloud ml language analyze-entities

5. What file contains your service account credentials for authentication?
A) ~/mykey.pub
B) ~/key.json
C) /etc/credentials.yaml
D) ~/credentials.private
Answer:
B) ~/key.json

6. What environment variable must be set for service account authentication?
A) GOOGLE_DEFAULT_ACCOUNT
B) GOOGLE_APPLICATION_CREDENTIALS
C) GCLOUD_AUTH
D) PROJECT_JSON_KEY
Answer:
B) GOOGLE_APPLICATION_CREDENTIALS

7. What type of information does entity analysis return for each detected entity?
A) Only the name
B) Name, type, salience, metadata, and mentions
C) Only Wikipedia URL
D) Only sentiment score
Answer:
B) Name, type, salience, metadata, and mentions

8. In the output, what does "salience" represent?
A) If the entity is a person
B) The centrality or importance of an entity in the text
C) The spunness of data
D) The API request priority
Answer:
B) The centrality or importance of an entity in the text

9. Why use Incognito or Private window for this lab?
A) Higher speed
B) Prevents conflicts and extra charges on personal accounts
C) Required for Google Cloud Shell
D) Enables multi-user mode
Answer:
B) Prevents conflicts and extra charges on personal accounts

10. Which API resource is being directly called when issuing: gcloud ml language analyze-entities?
A) Cloud SQL API
B) Compute Engine API
C) Cloud Natural Language API
D) Translation API
Answer:
C) Cloud Natural Language API