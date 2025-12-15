---
permalink: /research/speeches/
name: SPEECHES
title: "SPEECHES: Speech Processing in Health Sciences"
start: 2026/08
description: >
  The SPEECHES project aims to develop an on-device speech analysis system for stuttering therapy,
  enabling continuous monitoring and feedback while ensuring GDPR compliance through local data processing.
image: /images/projects/speeches.png
advisor:
  - riedhammerko
  - bockletto
  - albrechtje
  - axeniecr
staff:
  - steigerwaldph
layout: page
sitemap: false
---

#### Project Goals

Similar to a biomarker, speech carries information about the physiological and psychological state of a person, manifesting throughout the complex speech production process. Previous research has demonstrated that neuro-degenerative diseases and psychological conditions can be reliably detected from speech, making speech processing a viable non-invasive diagnostic aid. This Research Impulse aims to push the boundaries of speech processing to design, develop, and deploy systems that can serve as diagnostic aids and support health-related human-machine and human-human interaction.

The research is organized around four overarching objectives: 

  1. **Modeling Conversations**, to accurately describe and enhance interactions between humans and machines, particularly for counseling;
  2. **Modeling Atypical Speech**, to address the bias of current models towards healthy, standard speech; 
  3. **Sustainable AI**, to reduce the computational resource footprint and energy consumption of large models; and 
  4. **Privacy Preserving AI**, to securely handle sensitive speech biomarkers.

#### Challenges

Current state-of-the-art (SOTA) systems face significant limitations when applied to health sciences. Transformer-based ASR systems (like Whisper) are often trained on weakly labeled data and struggle with atypical speech from young, elderly, or impaired individuals. A critical issue is that these models tend to produce "smoothed," readable outputs rather than verbatim transcripts, often filtering out the dysfluencies and hesitations that are crucial for diagnosis. Similarly, Large Language Models (LLMs) are optimized for efficient task completion with minimal turn-taking, rather than the sustained, empathetic dialogue required for conversational agents in therapy.

Beyond modeling accuracy, the deployment of these technologies faces operational hurdles. The trend toward massive neural architectures requires extensive computational resources, making them difficult to use in clinical routines or on edge devices. Furthermore, because speech encodes personal identity and health data, standard cloud-based processing poses severe privacy risks that require new methods in confidential computing.

#### Results

The research is divided into Core Projects (CP) that develop foundational methods—such as rich transcription, foundation models, and low-resource computing—which then enable specific application Verticals (V).

The planned Verticals include a speech-based sleep diary for objective assessment, conversational agents for monitoring impaired users, multi-modal systems for online psychosocial counseling, AI-based voice prostheses, and automated hermeneutic coding for social research.

{% bibliography --cited --group_by none %}