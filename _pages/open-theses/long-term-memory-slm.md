---
title: "Efficient Long-Term Memory Architectures for Locally Hosted Small Language Models (SLMs)"
layout: page
sitemap: false
advisor: 
  - albrechtje
  - steigerwaldph
level:
  - Bachelor
  - Master
permalink: /open-theses/long-term-memory-slm
image: /images/open-theses/long-term-memory-slm.png
---

#### Motivation and Abstract

In sensitive application domains such as home care (V2) or psychological counseling (V3), data protection regulations often prohibit the use of cloud-based services. The solution lies in **locally hosted Small Language Models (e.g., Llama-3-8B, Mistral-7B)**. However, these models have a critical disadvantage: their context window is severely limited due to technical and resource constraints.
The challenge of this thesis is to develop a **Long-Term Memory** system that resides *outside* the model (e.g., a Vector Database or Knowledge Graph) and "injects" only the absolutely necessary information for the current dialogue step into the model. The goal is to overcome the "bottleneck" of the limited context window through intelligent retrieval and summarization strategies, enabling a small model on a standard PC to create the impression of remembering weeks of interaction.

#### Exemplary Research Questions

* How can the relevance of past information be evaluated to optimally utilize the limited context window of a local SLM (e.g., 4k or 8k tokens) ("Context Budgeting")?
* Which storage format (e.g., hierarchical summaries vs. pure vector embeddings) is better understood by smaller models and results in fewer hallucinations?
* How does model quantization (used to save resources) affect the ability to correctly integrate external memory information into the response?

#### Objectives of the Thesis

* **Concept:** Design of a memory pipeline ("Read/Write/Update") specifically optimized for the restrictions of local hardware.
* **Implementation:** Development of a resource-efficient prototype (e.g., using Ollama/LocalAI and LangChain) that runs locally.
* **Evaluation:** Benchmarking the solution regarding response quality and resource consumption (latency, VRAM usage) compared to a baseline without memory optimization.

#### Required Data

* Open-source dialogue datasets (e.g., *SODA* or *DailyDialog*) that simulate sequential interactions.
* Synthetic data to test edge cases of "forgetting."
* *No* sensitive real-world data is required.

#### Role in the SPEECHES Project

* **Contribution to CP3 (LLMs for Conversational Interaction):**
    * **WP CP3.1:** Maintaining Dialog Context (Context management under resource constraints).
    * **WP CP3.6:** Best Practices for LLM Development (Focus on "Green AI" and efficient models).
* **Benefiting Sub-projects:**
    * **Vertical V2 (Ambient Assisted Living):** Enables the deployment of intelligent assistants on local hardware (Edge Computing) without data leakage.
    * **Vertical V3 (Online Counseling):** Ensures GDPR compliance through local data processing while maintaining a personalized approach.

