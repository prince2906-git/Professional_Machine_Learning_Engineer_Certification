Step-by-Step Summary
1. Environment Setup

Access Google Cloud Console using lab-issued credentials (preferably in Incognito to avoid account conflicts or charges).
Activate Cloud Shell for command-line access.

2. Create a Service Account & Authenticate

Create service account:Bashgcloud iam service-accounts create quickstart


Generate service account key:Bashgcloud iam service-accounts keys create key.json --iam-account quickstart@<your-project-123>.iam.gserviceaccount.com

(Replace <your-project-123> with your real project ID.)
Activate the service account:Bashgcloud auth activate-service-account --key-file key.json


Obtain an access token for API requests:Bashgcloud auth print-access-token




3. Make an Annotate Video Request

Create a JSON file describing the request (e.g., requesting label detection on a sample video in Cloud Storage):Bashcat > request.json <<EOF
{
   "inputUri":"gs://spls/gsp154/video/train.mp4",
   "features": [
       "LABEL_DETECTION"
   ]
}
EOF


Call the Video Intelligence API using curl, providing authentication:Bashcurl -s -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer '$(gcloud auth print-access-token)'' \
  'https://videointelligence.googleapis.com/v1/videos:annotate' \
  -d @request.json




4. Check Operation Status & View Results

Use the operation name from the previous response to check annotation status:Bashcurl -s -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer '$(gcloud auth print-access-token)'' \
  'https://videointelligence.googleapis.com/v1/projects/PROJECTS/locations/LOCATIONS/operations/OPERATION_NAME'


Once "done": true is returned, review annotation results (labels, segments, confidence scores, etc.).


Key Learnings

How to authenticate GCP requests using a service account and key
How to send and monitor an asynchronous video annotation (LABEL_DETECTION)
How to interpret the structured response: label annotations, time offsets, and confidence levels
How to work with cloud-based video analytics for rapid metadata extraction


Practice Questions (20, MCQ-style, Markdown)

1. What does the Google Cloud Video Intelligence API do?
A) Encodes audio into video streams
B) Extracts metadata, labels, and key entities from videos
C) Hosts videos on demand
D) Streams live video
Answer:
B) Extracts metadata, labels, and key entities from videos

2. What command is used to create a new service account?
A) gcloud projects create-service-account
B) gcloud iam service-accounts create
C) gcloud acct create
D) gcloud sa new
Answer:
B) gcloud iam service-accounts create

3. Before making API requests, you must authenticate using:
A) IAM role only
B) API key
C) Service account key file
D) Password and username
Answer:
C) Service account key file

4. What does LABEL_DETECTION do in the request?
A) Detects human faces
B) Annotates and identifies objects, actions, and nouns in a video
C) Creates labels for disk devices
D) Marks storage buckets with labels
Answer:
B) Annotates and identifies objects, actions, and nouns in a video

5. Which format is used for the annotate video request body?
A) XML
B) YAML
C) JSON
D) CSV
Answer:
C) JSON

6. Why do we use the gcloud auth print-access-token command?
A) To retrieve the active project name
B) To print the service account password
C) To get a bearer token for API calls
D) To log out of gcloud
Answer:
C) To get a bearer token for API calls

7. What is the correct endpoint for sending an annotation request?
A) /v1/video:upload
B) /v1/videos:annotate
C) /v1/label:detect
D) /v1/files:analyze
Answer:
B) /v1/videos:annotate

8. If your annotation request takes time, what kind of operation is it?
A) Synchronous
B) Ready-to-run
C) Asynchronous
D) Manual
Answer:
C) Asynchronous

9. Once an annotation request is sent, where do you find the status/result?
A) By polling the operations API with the returned operation name
B) By checking Cloud Logging
C) Through an email notification
D) In a file on Cloud Storage
Answer:
A) By polling the operations API with the returned operation name

10. What information does each segmentLabelAnnotation object provide?
A) Entity ID, language, video time offsets, confidence
B) User ID, disk labels, region
C) VM size, memory allocation
D) Cloud billing role
Answer:
A) Entity ID, language, video time offsets, confidence

11. How is video data supplied to the Video Intelligence API?
A) Inline as base64 in JSON
B) In a public HTTP URL
C) As a Cloud Storage URI (gs://...)
D) As a PDF attachment
Answer:
C) As a Cloud Storage URI (gs://...)

12. If you forget to use -H 'Authorization: Bearer ...' in curl, what will happen?
A) The request will still succeed
B) You’ll receive an authentication error (403/401)
C) The response will be empty
D) It will use default permissions
Answer:
B) You’ll receive an authentication error (403/401)

13. How do you know the annotation is finished?
A) Returned status is "success"
B) Your project balance decreases
C) The poll response includes "done": true
D) The cloud shell prints "Video annotated"
Answer:
C) The poll response includes "done": true

14. Scenario: You see "progressPercent": 40 when polling. What should you do?
A) Wait and poll again later
B) Assume an error occurred
C) Restart the operation
D) Change the input video
Answer:
A) Wait and poll again later

15. If you want to annotate your own video, what must you do first?
A) Attach it as a .zip file
B) Email it to Google
C) Upload to Cloud Storage and use its URI
D) Transcribe the video manually
Answer:
C) Upload to Cloud Storage and use its URI

16. Which fields are required in the annotate request to label video content? (Select all that apply)

[ ] inputUri
[ ] features
[ ] password
[ ] operationName

Answer:

[x] inputUri
[x] features


17. Scenario: You want only results above 90% confidence. Where do you look in the API response?
A) segments.confidence
B) annotationResults[].segmentLabelAnnotations[].segments[].confidence
C) features[].params
D) requests.confidence_score
Answer:
B) annotationResults[].segmentLabelAnnotations[].segments[].confidence

18. If you accidentally used the wrong project when creating your service account, what is likely to happen?
A) Your videos annotate successfully
B) The API call fails due to lack of permissions or missing resources
C) You get a larger result set
D) The request uses the correct project automatically
Answer:
B) The API call fails due to lack of permissions or missing resources

19. What is a “feature” in the context of this API?
A) A subscription type
B) A specific video analysis option (e.g., LABEL_DETECTION, SHOT_CHANGE_DETECTION)
C) A Cloud Storage folder
D) A network setting
Answer:
B) A specific video analysis option (e.g., LABEL_DETECTION, SHOT_CHANGE_DETECTION)

20. What is the main advantage of Video Intelligence API compared to manual video review?
A) Faster, scalable, automated annotation and metadata extraction
B) It always produces subtitles
C) Reduces video size
D) Always detects faces
Answer:
A) Faster, scalable, automated annotation and metadata extraction

Let me know if you need explanations to questions, answer-only lists, or more scenario-based/technical challenges!
