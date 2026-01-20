# GCP Professional Machine Learning Engineer: AI Foundation Revision Table

This comprehensive table covers the key tools, model types, workflows, and solution patterns for the AI Foundation part of the GCP Professional Machine Learning Engineer exam. Use this as a quick-reference revision sheet.

---

## 1. Core Tools & Platforms

| Tool/Platform        | Purpose/Scope                                         | Key Features/Components                       | When to Use                                   |
|----------------------|------------------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| **Vertex AI Studio** | Low/no-code interface for Gen AI prototyping, tuning | Prompt design, model tuning, deployment, UI   | Rapid prototyping, prompt engineering, tuning |
| **Model Garden**     | Model library for Google, 3rd-party, open-source     | Model cards, filters, sample code, notebooks  | Discover, compare, deploy models              |
| **Vertex AI Workbench** | Managed Jupyter/Colab environment for ML dev      | Notebooks, integration with Vertex AI         | Custom model dev, experimentation             |
| **Vertex AI Pipelines** | Orchestrate ML workflows (training, deployment)   | Kubeflow-based, CI/CD for ML                  | Production ML, repeatable workflows           |
| **Vertex AI APIs/SDKs** | Programmatic access to models & services          | Python, Java, REST, CLI                       | Automation, integration, custom workflows     |

---

## 2. Model Approaches

| Approach                | Supported Models/Examples                | Workflow/How It Works                         | When to Use                                                                 | Pros                                               | Cons                                                |
|-------------------------|------------------------------------------|-----------------------------------------------|-----------------------------------------------------------------------------|----------------------------------------------------|-----------------------------------------------------|
| **Pretrained AI Models**| Vision AI, Natural Language AI, Translation AI | Use Google APIs for common tasks              | Standard tasks, minimal customization                                      | Fast, scalable, no ML expertise needed             | Limited customization, generic outputs              |
| **AutoML**              | AutoML Vision, Tables, NL, Translation   | Train custom models from your data, no code   | Custom models from labeled data, no/low code                                | Good performance, easy to use                      | Less control, limited to supported data types       |
| **Vertex AI Custom Models** | TensorFlow, PyTorch, XGBoost, Scikit-learn, custom containers | Bring your own code, full control             | Advanced/complex ML, full customization, proprietary needs                  | Maximum flexibility, supports advanced ML           | Requires ML expertise, more dev time                |
| **Gen AI/Foundation Models** | Gemini (multimodal), Imagen (image), Codey (code), Chirp (speech), Gemma (language), Llama, Falcon, etc. | Use pre-trained LLMs for generation, Q&A, summarization, code, etc. | Content generation, LLMs, creative/multimodal tasks                        | State-of-the-art, multimodal, can be fine-tuned     | Prompt engineering needed, higher cost, responsible AI |

---

## 3. Model Selection: When to Use What

| Use Case                         | Recommended Approach         | Example Supported Model(s)         |
|-----------------------------------|-----------------------------|------------------------------------|
| Image classification (common objects) | Pretrained AI Model         | Vision AI API                      |
| Custom product image classification   | AutoML Vision               | AutoML Vision                      |
| Predicting customer churn (complex features) | Vertex AI Custom Model        | XGBoost, TensorFlow                |
| Generating marketing copy, chatbots  | Generative AI Model         | Gemini, Gemma, Llama               |
| Translating documents                | Pretrained AI Model / AutoML| Translation AI, AutoML Translation |
| Summarizing legal documents          | Generative AI Model         | Gemini, Gemma                      |

---

## 4. Prompt Engineering (Gen AI)

| Prompting Method   | Description                                 | Example Use Case           |
|--------------------|---------------------------------------------|----------------------------|
| Zero-shot          | No examples; just the task                  | Simple Q&A                 |
| One-shot           | One example provided                        | Poem generation            |
| Few-shot           | Multiple examples for guidance              | IT help desk Q&A           |

**Prompt Design Best Practices:**
- Be concise and specific.
- Ask one task at a time.
- Use examples to improve quality.
- Experiment with structure and parameters.

**Key Parameters:**
- **Temperature:** Controls randomness (0 = predictable, 1 = creative).
- **Top K:** Randomly samples from top K likely words.
- **Top P:** Samples from smallest set with cumulative probability ≥ P.

---

## 5. Model Garden: Model Discovery & Deployment

| Model Category      | Examples                                   | How to Use / Workflow                        |
|---------------------|--------------------------------------------|----------------------------------------------|
| Foundation Models   | Gemini, Imagen, Chirp, Codey, Gemma        | Use as-is, tune, or deploy via Vertex AI     |
| Task-Specific       | Entity analysis, sentiment, object detection| Use prebuilt APIs for specific tasks         |
| Fine-tunable/Open-source | Llama, Falcon, Owl-ViT, etc.           | Fine-tune via notebooks/pipelines            |

**Filters:**  
- **Modalities:** Language, vision, speech  
- **Tasks:** Generation, classification, detection  
- **Features:** Pipeline, notebook, one-click deploy

---

## 6. AI Solution Patterns

| Solution Type    | Example Solution         | Gen AI Role/Enhancement                      | Key Features/Benefits                |
|------------------|-------------------------|----------------------------------------------|--------------------------------------|
| **Vertical**     | Healthcare Data Engine  | Generates insights, automates reporting      | Summarization, predictive analytics  |
|                  | Vertex AI Search for Retail | Improves search, recommendations           | Conversational search, personalization|
| **Horizontal**   | Contact Center AI (CCAI)| Virtual agents, Agent Assist, Insights       | 24/7 self-service, FAQ generation    |
|                  | Document AI             | Document understanding, extraction           | OCR, summarization, classification   |

---

## 7. CCAI (Contact Center AI) Deep Dive

| Component        | Current Gen AI Features         | Upcoming Enhancements                        |
|------------------|--------------------------------|----------------------------------------------|
| Virtual Agent    | 24/7 chat/voice, handoff, NLU   | Broader coverage, easier bot creation        |
| Agent Assist     | Step-by-step help, summaries    | On-demand coaching, deeper analytics         |
| Insights         | Sentiment, entity, topic analysis| Automated FAQ generation, improved analytics |

---

## 8. Responsible AI & Future Trends

- **Responsible AI:**  
  - Data privacy, fairness, transparency, compliance.
- **Trends:**  
  - Data-to-AI transition is accelerating.
  - Gen AI will drive content creation, productivity, and accessibility.
  - Tools are becoming easier for non-technical users.

---

## 9. Quick Reference: GCP AI Workflow

1. **Define Problem & Data**
2. **Choose Approach:** Pretrained, AutoML, Custom, Gen AI
3. **Model Selection:** Use Model Garden/Vertex AI Studio
4. **Experiment & Tune:** Prompt design, parameter tuning
5. **Deploy:** Vertex AI endpoints, pipelines
6. **Monitor & Improve:** Use Vertex AI tools for monitoring, retraining

---

*Use this table as your last-minute revision guide for the AI Foundation part of the GCP Professional Machine Learning Engineer exam!*
