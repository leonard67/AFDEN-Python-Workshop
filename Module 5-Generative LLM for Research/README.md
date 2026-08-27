# Module 5: Generative LLM for Research

[Back to main syllabus](../README.md)

Generative LLMs are increasingly used in accounting research for textual-analysis tasks that used to require either dictionary/bag-of-words methods or costly manual human coding — classifying disclosure tone, extracting structured facts from filings, detecting evasive "non-answers" in earnings-call Q&As. This module introduces the Python client libraries for two major providers — OpenAI and Google Gemini — covering the mechanics you need before using an LLM as a research tool (prompts, structured JSON output, multi-turn conversations, multimodal input), then applies them to research settings through a replication exercise and an optional image-analysis exercise.

**Prerequisite reading**

- de Kok, T. (2025). ChatGPT for textual analysis? How to use generative LLMs in accounting research. *Management Science* 71(9): 7888-7906. ([link](https://doi.org/10.1287/mnsc.2023.03253))
- Blankespoor, E., deHaan, E., & Li, Q. (2026). Generative AI in financial reporting. *Journal of Accounting Research* 64(3): 1189-1232. ([link](https://doi.org/10.1111/1475-679x.7005))

## 5.1. Using Generative LLM APIs in AccFin Research

This session covers the API-level building blocks a research design is built on: setting up keys securely, sending prompts, requesting schema-conformant structured output, holding a chat, and passing images — with both the OpenAI (`openai`) and Google Gemini (`google-genai`) Python clients.

**Learning Outcomes**

By the end of this session, you will be able to:

- Set up API keys securely via a `.env` file for both OpenAI and Google Gemini.
- Send text prompts and read model output using both providers' Python clients.
- Request structured (JSON) output from a model using a defined schema (e.g., a Pydantic model).
- Hold a multi-turn conversation (chat) with an LLM.
- Pass images as multimodal input.

Our class is based on [5-1-LLM_API-Final.ipynb](5-1-LLM_API-Final.ipynb).

### 5.1e-1. Exercise: Detecting Non-Answers in Earnings Conference Calls

This exercise replicates the core of the case study in de Kok ([2025](https://doi.org/10.1287/mnsc.2023.03253)) on 13 Tesla Q4 earnings-call transcripts. A **non-answer** is a response in which a manager signals an inability or unwillingness to provide the information asked for. The notebook works through de Kok's four-step framework: parsing raw transcripts into question-answer pairs, choosing a zero-shot approach and model, developing a prompt with explicit coding rules and a Pydantic output schema, running the classification with logging and resumability, and — critically — evaluating construct validity against a keyword baseline and a hand-coded sample before scaling to all 13 calls.

**Learning Outcomes**

- Turn a messy Markdown transcript into a structured table of question-answer pairs with regular expressions.
- Design a zero-shot classification prompt: coding rules, "what is *not*" a non-answer, chain-of-thought field ordering, and stating the expected class distribution.
- Log raw prompts and completions as the primary data of the study, and build a resumable, concurrent inference loop.
- Evaluate a minority-class classifier with precision/recall/F1 (not accuracy), and test a prompt's robustness to its own wording.

Our class is based on [5-1e-1-No_Answer_in_CC-Final.ipynb](5-1e-1-No_Answer_in_CC-Final.ipynb).

### 5.1e-2. Exercise: Detecting the Use of GenAI in 10-K Reports

This exercise applies ZeroGPT to detect the use of generative AI in firms' 10-K reports, based on Blankespoor, deHaan, and Li ([2026](https://doi.org/10.1111/1475-679x.7005)).

## 5.2o. Identifying Common Visual Themes in an Annual Report (Optional)

An optional exercise applying the Gemini API skills from 5.1 to a real annual report: extracting embedded photographs from a PDF (filtering out signatures and logos by pixel area), captioning each with Gemini (flagging and excluding director/executive headshots), and summarizing the most common visual themes with a schema-constrained call — motivated by Obaid and Pukthuanthong (2022).

**Optional reading**

- Obaid, N., & Pukthuanthong, K. (2022). A picture is worth a thousand words: Measuring investor sentiment by combining machine learning and photos from news. *Journal of Financial Economics* 144(1): 273-297. ([link](https://doi.org/10.1016/j.jfineco.2021.06.002))

**Learning Outcomes**

- Extract and filter embedded images from a PDF with PyMuPDF (`fitz`).
- Send images to Gemini for captioning, and use a lightweight label convention to route the output.
- Summarize a corpus of captions into a structured list of themes with Structured Outputs.

Our class is based on [5-2o-Identifying_Images.ipynb](5-2o-Identifying_Images.ipynb).

[Back to main syllabus](../README.md)
