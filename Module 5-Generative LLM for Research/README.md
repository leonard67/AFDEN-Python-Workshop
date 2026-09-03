# Module 5: Generative LLM for Research

[Back to main syllabus](../README.md)

Generative LLMs are increasingly used in accounting research for textual-analysis tasks that used to require either dictionary/bag-of-words methods or costly manual human coding — classifying disclosure tone, extracting structured facts from filings, detecting evasive "non-answers" in earnings-call Q&As. This module introduces the Python client libraries for two major providers — OpenAI and Google Gemini — covering the mechanics you need before using an LLM as a research tool (prompts, structured JSON output, multi-turn conversations, multimodal input), then applies them to research settings through two replication exercises and an optional image-analysis exercise.

## 5.1. Using Generative LLM APIs in AccFin Research

This session covers the API-level building blocks a research design is built on: setting up keys securely, sending prompts, requesting schema-conformant structured output, holding a chat, and passing images — with both the OpenAI (`openai`) and Google Gemini (`google-genai`) Python clients.

**Optional reading**

* Choi, J. H., Li, D., & Macciocchi, D. (2026). Human Capital Disclosure and Labor Market Outcomes: Evidence from Regulation S‐K.  *Journal of Accounting Research* 64(4): 1685-1731. ([link](https://doi.org/10.1111/1475-679x.70036))

**Learning Outcomes**

By the end of this session, you will be able to:

- Set up API keys securely via a `.env` file for both OpenAI and Google Gemini.
- Send text prompts and read model output using both providers' Python clients.
- Request structured (JSON) output from a model using a defined schema (e.g., a Pydantic model).
- Hold a multi-turn conversation (chat) with an LLM.
- Pass images as multimodal input.

Our class is based on [5-1-LLM_API-Final.ipynb](5-1-LLM_API-Final.ipynb).

### 5.1e-1. Exercise: Detecting Non-Answers in Earnings Conference Calls

This exercise reproduces the measurement core of the case study in de Kok ([2025](https://doi.org/10.1287/mnsc.2023.03253)) — turning a raw earnings-call transcript into a 0/1 *non-answer* label for every question — worked through on one Tesla Q4 call. A **non-answer** is a response in which a manager signals an inability or unwillingness to provide the information asked for. Following the first three steps of de Kok's framework, the notebook parses the transcript into question–answer pairs with regular expressions, settles on a zero-shot approach and model, develops a prompt with explicit coding rules and a Pydantic output schema (reasoning before the label, expected class distribution stated), and runs the classification as a logged, resumable, concurrent loop.

**Prerequisite reading**

- de Kok, T. (2025). ChatGPT for textual analysis? How to use generative LLMs in accounting research. *Management Science* 71(9): 7888-7906. ([link](https://doi.org/10.1287/mnsc.2023.03253))

**Learning Outcomes**

- Turn a messy Markdown transcript into a structured table of question-answer pairs with regular expressions.
- Weigh the three ways to instruct a generative LLM — zero-shot, few-shot, and fine-tuning — and match the choice to the task.
- Design a zero-shot classification prompt: coding rules, "what is *not*" a non-answer, chain-of-thought field ordering, and stating the expected class distribution.
- Return the completion as a validated Pydantic object with `client.responses.parse()` instead of parsing prose.
- Log raw prompts and completions as the primary data of the study, and build a resumable, concurrent inference loop.

Our class is based on [5-1e-1-No_Answer_in_CC-Final.ipynb](5-1e-1-No_Answer_in_CC-Final.ipynb).

### 5.1e-2. Exercise: Detecting the Use of Generative AI in a Financial Report

This exercise reproduces the measurement core of Blankespoor, deHaan, and Li ([2026](https://doi.org/10.1111/1475-679X.70050)) on a single document — BHP Group's FY2025 Annual Report. The paper introduces `GenScore`, the estimated probability that a disclosure was written with generative AI (GAI), produced by the commercial detector **GPTZero**, and shows both that the detector reliably flags even trace amounts of GAI text in financial reports and that firms' actual filings show statistically significant, rising GAI usage through 2024. The notebook goes from a raw PDF to a cleaned slice of narrative text, scores it via the GPTZero API, reconstructs the paper's `GenScore` definition, reads the score at the sentence level, and interprets it against the paper's human-written and GAI-modified benchmarks.

**Prerequisite reading**

- Blankespoor, E., deHaan, E., & Li, Q. (2026). Generative AI in financial reporting. *Journal of Accounting Research* 64(3): 1189-1232. ([link](https://doi.org/10.1111/1475-679X.70050))

**Learning Outcomes**

- Extract and clean narrative text from a designed PDF report with `PyMuPDF`, handling running headers, typographic characters, and line-break artifacts.
- Follow the paper's measurement protocol: score the first ~5,000 words of a disclosure, rounded to a sentence boundary.
- Call the GPTZero detection API and compute `GenScore` as the document-level probability of AI plus mixed authorship.
- Save the raw API response as the primary data of the measurement, and record the detector's model version.
- Read a detector's sentence-level scores, and interpret a single `GenScore` against same-model human and GAI-modified benchmarks — including why a raw score is not the paper's within-firm regression estimate.

Our class is based on [5-1e-2-Detecting_GenAI_Text.ipynb](5-1e-2-Detecting_GenAI_Text.ipynb).

## 5.2o. Identifying Common Visual Themes in an Annual Report (Optional)

An optional exercise applying the Gemini API skills from 5.1 to a real annual report: extracting embedded photographs from a PDF (filtering out signatures and logos by pixel area), captioning each with Gemini (flagging and excluding director/executive headshots), and summarizing the most common visual themes with a schema-constrained call — motivated by Obaid and Pukthuanthong (2022).

**Optional reading**

- Obaid, N., & Pukthuanthong, K. (2022). A picture is worth a thousand words: Measuring investor sentiment by combining machine learning and photos from news. *Journal of Financial Economics* 144(1): 273-297. ([link](https://doi.org/10.1016/j.jfineco.2021.06.002))

**Learning Outcomes**

- Extract and filter embedded images from a PDF with `PyMuPDF`.
- Send images to Gemini for captioning, and use a lightweight label convention to route the output.
- Summarize a corpus of captions into a structured list of themes with Structured Outputs.

Our class is based on [5-2o-Identifying_Images.ipynb](5-2o-Identifying_Images.ipynb).

[Back to main syllabus](../README.md)
