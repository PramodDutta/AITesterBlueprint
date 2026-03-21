# Project 18: CI/CD + AI

## Add AI into QA Pipelines and Delivery Reporting

This project focuses on using AI inside CI/CD systems, not as a chatbot but as a delivery assistant.

It covers how AI can summarize failures, improve pipeline debugging, and help QA teams react faster to noisy build results.

---

## Folder Structure

```text
Project_18_CICD_AI/
├── 01_Core_Learning/
├── 02_Learning_Exercises/
├── 03_QA_Projects/
│   ├── 01_Jenkins_LLM_Integration/
│   ├── 02_GitHub_Actions_AI_Summaries/
│   └── 03_AI_Debugging_Pipeline_Step/
└── README.md
```

---

## What This Project Covers

### Core Learning

- where AI fits in CI/CD pipelines
- how to summarize build failures safely
- how to reduce noisy report analysis
- where AI should assist and where it should not make release decisions

### Learning Exercises

- turn raw logs into concise summaries
- design a pipeline summary prompt
- add a safe debugging step to a delivery workflow

### QA Projects

1. `Jenkins pipeline + LLM integration`
2. `GitHub Actions + AI summaries`
3. `AI debugging step in a pipeline`

---

## Recommended Outcome

Students should learn how to use AI to improve delivery visibility without making the pipeline unreliable or untrustworthy.

---

## Future Extension

A later extension can include:

- `Failure clustering with AI (ReportPortal-style workflow)`

---

## Learning Companion Structure

This project now also includes a teaching-friendly folder structure for guided study:

```text
Project_18_CICD_AI/
├── 01_Learning/
├── 02_Exercises/
├── 03_Interview_Questions/
```

### What to Use Each Folder For

- `01_Learning` — topic summary, learning goals, QA/SDET framing, and a concept diagram
- `02_Exercises` — guided practice tasks that students can use before implementation
- `03_Interview_Questions` — QA/SDET-oriented interview prep tied to the same topic

Recommended order:

1. Start with `01_Learning`
2. Work through `02_Exercises`
3. Review `03_Interview_Questions`
4. Return to the implementation assets in the rest of the project
