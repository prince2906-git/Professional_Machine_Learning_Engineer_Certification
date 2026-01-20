1. Overview & Concepts
Q1. Which of the following best describes Vertex AI Studio?
A) It’s a code-only interface for Python ML APIs
B) It’s a generative AI and ML development platform for predictive and creative applications
C) Only supports vision models, not text
D) A simulation-based ML playground
Answer:
B) It’s a generative AI and ML development platform for predictive and creative applications

Q2. In Vertex AI Studio, which capabilities are supported out-of-the-box without APIs or Python SDKs? (Select all that apply)

[ ] Direct model deployment with one click
[ ] Text, image, and voice generation
[ ] Editing images using inpainting
[ ] Accessing external research databases directly

Answer:

[x] Direct model deployment with one click
[x] Text, image, and voice generation
[x] Editing images using inpainting


2. Lab Setup
Q3. Why are you advised to use an incognito/private browser window for the lab?
A) It disables the lab timer
B) It prevents personal Google account conflicts and extra charges
C) It increases model performance
D) It allows multi-user collaboration
Answer:
B) It prevents personal Google account conflicts and extra charges

Q4. What should you do if the "Deploy as app" feature fails on first attempt due to permissions?
A) Switch browsers and try again
B) Wait about a minute, then click "Update app"
C) Restart the whole lab
D) Ignore the error and continue
Answer:
B) Wait about a minute, then click "Update app"

3. Prompt Engineering
Q5. What is the main difference between zero-shot and few-shot prompting?
A) Zero-shot provides no examples, few-shot gives sample inputs/outputs
B) Zero-shot is for images, few-shot is for text
C) Zero-shot always produces better results
D) Few-shot uses Python only
Answer:
A) Zero-shot provides no examples, few-shot gives sample inputs/outputs

Q6. Which prompt would likely extract data most accurately from freeform claim notes?
A) Zero-shot prompt with a vague instruction
B) Few-shot prompt with clear examples of input and output formats
C) Only using system instructions
D) Random prompt phrasing at high temperature
Answer:
B) Few-shot prompt with clear examples of input and output formats

Q7. How does the “temperature” setting affect model output?

[ ] Higher values lead to more creative and diverse outputs
[ ] Lower values create more focused and deterministic outputs
[ ] It changes the language of the output
[ ] Has no effect unless using images

Answer:

[x] Higher values lead to more creative and diverse outputs
[x] Lower values create more focused and deterministic outputs


4. Experimentation & Comparison
Q8. Which method allows you to directly compare changes in prompt instructions or model settings?
A) Lab timer
B) Compare feature in Vertex AI Studio
C) Only by manually copying and pasting responses
D) API deployment
Answer:
B) Compare feature in Vertex AI Studio

Q9. A scenario prompt asks the model to cite guidelines when identifying the #1 risk factor for a restaurant’s insurance application. What setting or method might increase the likelihood of getting a detailed, justified answer?

[ ] Using compare to test both general and detailed instructions
[ ] Increasing temperature to 2.0
[ ] Adding a few-shot example with detailed justification
[ ] Disabling system instructions

Answer:

[x] Using compare to test both general and detailed instructions
[x] Adding a few-shot example with detailed justification


5. Multimodal & Media Tasks
Q10. What does a “multimodal” prompt in Vertex AI Studio allow you to do?
A) Combine text and image input for analysis
B) Run code in multiple programming languages at once
C) Use video instead of text
D) Limit the output to only text
Answer:
A) Combine text and image input for analysis

Q11. In the media generation tools, what is SynthID?
A) An API key for external plugins
B) A watermarking technology for AI-generated images
C) A library for audio file conversion
D) A debugging tool for model outputs
Answer:
B) A watermarking technology for AI-generated images

Q12. Which actions can image-generation tools like Imagen perform in Vertex AI Studio? (Select all that apply)

[ ] Inpainting (edit regions of image)
[ ] Outpainting (extend image context)
[ ] Add invisible watermark (SynthID)
[ ] Download source code of the model

Answer:

[x] Inpainting (edit regions of image)
[x] Outpainting (extend image context)
[x] Add invisible watermark (SynthID)


6. Tips & Scenarios
Q13. Scenario: What should you do if a Gen AI app, deployed as a web application, is accessible without authentication?
A) Change nothing; unsafe access is fine for production
B) Accept for exploration labs, but ensure proper security in production
C) Share the public link widely
D) Add a personal Google account to the app
Answer:
B) Accept for exploration labs, but ensure proper security in production

Q14. For data extraction tasks (e.g., from insurance claims), which settings are generally best?

[ ] Use a low temperature (e.g., 0.1)
[ ] Use only high temperature (e.g., 2.0)
[ ] Output structure as key:value pairs
[ ] Avoid giving any examples

Answer:

[x] Use a low temperature (e.g., 0.1)
[x] Output structure as key:value pairs


Q15. You want the model to "ground" its answers in real-time, external data. What should you enable?
A) Use the Grounding feature (Google Search or your data)
B) Increase temperature and top-p
C) Only use inpainting
D) Deploy using Cloud Run
Answer:
A) Use the Grounding feature (Google Search or your data)

Q16. When instructed to use only the "student" lab credentials, what is the most important reason?
A) Ensures you get the highest model accuracy
B) Prevents your personal Google Cloud account from getting charged
C) Automatically saves outputs to your private cloud
D) Enables incognito browsing
Answer:
B) Prevents your personal Google Cloud account from getting charged