# AI Test Data Generation: Learning Guide

## What We Are Learning

Generating schema-aware, privacy-safe, edge-case-rich test data for APIs, databases, and workflows.

### Learning Goals
- Understand where AI improves over static fixture generation.
- Learn how to combine schema rules with creative data generation.
- Generate edge cases and persona-driven data without violating constraints.
- Connect synthetic data generation to QA coverage, privacy, and repeatability.

### Core Concepts
- Schema parsing from OpenAPI, SQL, and JSON Schema
- Combining Faker determinism with LLM context awareness
- Generating boundary, invalid, and relationally consistent data
- Privacy-safe synthetic data strategies

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
