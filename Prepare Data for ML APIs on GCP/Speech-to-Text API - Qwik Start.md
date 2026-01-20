Speech-to-Text API: Qwik Start
Lab Summary & Key Learnings
Lab Objective

Learn to use Google Cloud’s Speech-to-Text API to transcribe audio.


Key Steps and Commands
1. Lab Setup

Access Google Cloud Console with lab-provided (student) credentials in an Incognito window to avoid account and billing conflicts.

2. Generate API Key

In Console:
Navigation menu → APIs & services → Credentials → Create credentials → API key
Save your API key as an environment variable in the SSH session:Bashexport API_KEY=<YOUR_API_KEY>




3. Connect to Compute Engine via SSH

In Console:
Navigation menu → Compute Engine → VM instances
Click SSH next to the provisioned VM (“linux-instance”).


4. Prepare the API Request Body

Create request.json to define audio & config:Bashtouch request.json
nano request.json


Insert:JSON{
  "config": {
    "encoding":"FLAC",
    "languageCode": "en-US"
  },
  "audio": {
    "uri":"gs://cloud-samples-tests/speech/brooklyn.flac"
  }
}

Save and close file.


5. Make a Speech-to-Text API Call

Run (returns response to screen):Bash
curl -s -X POST -H "Content-Type: application/json" --data-binary @request.json \
  "https://speech.googleapis.com/v1/speech:recognize?key=${API_KEY}"


Or, save output to result.json:Bash
curl -s -X POST -H "Content-Type: application/json" --data-binary @request.json \
  "https://speech.googleapis.com/v1/speech:recognize?key=${API_KEY}" > result.json

curl -s -X POST -H "Content-Type: application/json" --data-binary @request.json \
"https://speech.googleapis.com/v1/speech:recognize?key=${API_KEY}" > result.json


6. Interpret Response

API returns:

transcript: decoded text, e.g. "how old is the Brooklyn Bridge"
confidence: confidence score, e.g. 0.98




What Did You Learn?

How to authenticate (API key usage) with Google Cloud APIs
How to structure and send a Speech-to-Text request using basic tools (curl)
Basic .json configuration for recognition (encoding, language, URI)
How to interpret API’s transcript and confidence outputs
Where key options/configs can be changed for other use cases


Practice Questions (20, Markdown, MCQ—Technical, Logical, Scenario)

1. What is the primary function of the Speech-to-Text API?
A) Translate audio
B) Convert speech audio files to text
C) Edit audio
D) Convert text to audio
Answer:
B) Convert speech audio files to text

2. In this lab, how do you authenticate API requests?
A) OAuth tokens
B) API key
C) SSH keys
D) Service account file
Answer:
B) API key

3. What is the main reason for using an Incognito/private window for this lab?
A) Run multiple labs faster
B) Avoid unintended billing and account conflicts
C) Improve cloud shell performance
D) Access more APIs
Answer:
B) Avoid unintended billing and account conflicts

4. Where do you store the created API key for reuse in requests?
A) /tmp/api.key
B) As an environment variable (API_KEY)
C) Google Cloud Storage
D) /etc/ssh/authorized_keys
Answer:
B) As an environment variable (API_KEY)

5. Which pre-recorded audio file is used in the sample request?
A) brooklyn.mp3
B) gs://cloud-samples-tests/speech/brooklyn.flac
C) gs://cloud-test/speech/test.wav
D) nybridge.flac
Answer:
B) gs://cloud-samples-tests/speech/brooklyn.flac

6. What is the audio encoding specified in the sample request’s config object?
A) WAV
B) OGG
C) FLAC
D) PCM
Answer:
C) FLAC

7. In which programming format is the request payload created?
A) XML
B) YAML
C) JSON
D) CSV
Answer:
C) JSON

8. Which API endpoint is called to process the synchronous recognition in this lab?
A) /v1/speech:translate
B) /v1/speech:recognize
C) /v1/speech:stream
D) /v1/speech:synthesize
Answer:
B) /v1/speech:recognize

9. What HTTP method is used to send the API request?
A) GET
B) POST
C) PUT
D) DELETE
Answer:
B) POST

10. What is the purpose of the “confidence” field in the response?
A) Server latency
B) API request cost
C) Probability that the returned transcript is correct
D) Number of words returned
Answer:
C) Probability that the returned transcript is correct

11. True or False: The API supports both synchronous and asynchronous recognition modes.
A) True
B) False
Answer:
A) True

12. Which section of the JSON request tells the API where to find the audio file?
A) "config"
B) "metadata"
C) "audio"
D) "request"
Answer:
C) "audio"

13. What’s the significance of “languageCode” in the config block?
A) It specifies API version
B) It is required for billing
C) Tells the API which language model to use
D) Only required for asynchronous jobs
Answer:
C) Tells the API which language model to use

14. If your transcript result is blank, what should you check first?
A) Output directory permissions
B) Correctness of audio file URI and encoding/format
C) Your Cloud Console theme
D) Command prompt PATH
Answer:
B) Correctness of audio file URI and encoding/format

15. Which of these are valid use cases for the Speech-to-Text API?
(Select all that apply)

[ ] Real-time voice transcription in apps
[ ] Batch processing of customer support calls
[ ] Translating web pages
[ ] Generating captions for videos

Answer:

[x] Real-time voice transcription in apps
[x] Batch processing of customer support calls
[x] Generating captions for videos


16. What command is used to save the API response directly to a file?
A) curl ... > result.json
B) cp response.json result.json
C) json-save result.json
D) echo API_RESULT > result.json
Answer:
A) curl ... > result.json

17. Scenario: You want to transcribe audio in Spanish. What should you change in request.json?
A) Set encoding to “SPANISH”
B) Change "languageCode" to "es-ES"
C) Use an .mp3 file
D) Remove audio.uri
Answer:
B) Change "languageCode" to "es-ES"

18. Scenario: You want to process a .wav file stored on your local VM. What must you do?
A) Set URI to local file path
B) Choose the right "encoding" in config, and use a "content" field with base64-encoded audio
C) Upload to Cloud Storage first
D) Use the old v1beta1 endpoint
Answer:
B) Choose the right "encoding" in config, and use a "content" field with base64-encoded audio

19. If you receive a 403 error from the API, what is a likely cause?
A) File not found
B) Incorrect or missing API key
C) Wrong encoding
D) API called too quickly
Answer:
B) Incorrect or missing API key

20. What is a best practice after finishing a lab using API keys?
A) Share the key with your team
B) Deactivate or delete unused API keys to protect your project
C) Store API keys in public git repos
D) Hardcode the key in production apps
Answer:
B) Deactivate or delete unused API keys to protect your project

    