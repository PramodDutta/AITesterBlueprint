# AI Security Testing Assistant: Learning Guide

## What We Are Learning

Using AI to generate security tests, analyze scanner results, and probe prompt-injection risks in modern apps.

### Learning Goals
- Understand how AI can make security testing more accessible to QA teams.
- Learn how to design targeted security tests for web and LLM-powered applications.
- Interpret scanner outputs and prioritize real findings over noise.
- Connect traditional security testing with prompt-injection and LLM abuse scenarios.

### Core Concepts
- OWASP Top 10 and context-aware security test design
- XSS, SQLi, and payload-generation strategies
- Scanner integration and false-positive triage
- Prompt injection, jailbreaks, and indirect instruction attacks

## QA/SDET Lens

- Focus on how this topic improves test design, reliability, coverage, or release confidence.
- Look for where AI should assist, where human review is mandatory, and how to measure trust.
- Tie every concept back to a concrete QA artifact such as a test case, report, dashboard, or pipeline gate.

## Concept Flow

```mermaid
flowchart LR
    A["Business Problem"] --> B["Topic Fundamentals"]
    B --> C["QA/SDET Application"]
    C --> D["Implementation Pattern"]
    D --> E["Validation and Review"]
```

## Suggested Study Sequence

1. Read the parent project README for the full project goal.
2. Learn the core concepts in this folder.
3. Try the exercises in `02_Exercises`.
4. Review the interview questions in `03_Interview_Questions`.
5. Return to the project implementation and map the concepts to code and deliverables.
