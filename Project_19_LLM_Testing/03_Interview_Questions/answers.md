# LLM Testing: Interview Answer Guide

## Question 1

**Why is LLM testing different from traditional API or UI testing?**

### Expected Discussion Points
- Outputs are probabilistic and often vary while still being acceptable.
- Many quality dimensions are semantic rather than purely deterministic.
- You often need rubrics or model-based judges in addition to exact assertions.
- Safety, grounding, and structured-output behavior become first-class QA concerns.

## Question 2

**How would you measure hallucination risk in a QA-friendly way?**

### Expected Discussion Points
- Create prompts where the correct answer is known or explicitly unavailable.
- Check whether claims are grounded in allowed context or supporting evidence.
- Track unsupported assertions, fabricated facts, and overconfident wording.
- Report the rate and severity of hallucinations across benchmark cases.

## Question 3

**What is the difference between deterministic assertions and rubric-based evaluation?**

### Expected Discussion Points
- Deterministic assertions check exact fields, keywords, or schemas.
- Rubric-based evaluation allows semantic flexibility against defined quality criteria.
- Exact assertions are clearer but less flexible.
- Rubrics are better for natural language quality, with stronger review requirements.

## Question 4

**How would you validate structured output from an LLM in production?**

### Expected Discussion Points
- Use schemas such as Pydantic or JSON Schema at runtime.
- Reject or retry malformed outputs.
- Track schema-failure rates as an operational metric.
- Test both happy-path and adversarial formatting cases.

## Question 5

**What role does a golden dataset play in LLM regression testing?**

### Expected Discussion Points
- It creates a stable benchmark for comparing versions over time.
- It anchors discussions about quality in shared evidence.
- It supports CI/CD gates and drift detection.
- It should evolve carefully with versioning and documented rationale.

## Question 6

**How would you explain DeepEval or Promptfoo to a QA automation engineer?**

### Expected Discussion Points
- They provide structured ways to run LLM evaluations like a test harness.
- They help manage datasets, prompts, metrics, and result reporting.
- They do not remove the need for test design; they operationalize it.
- Think of them as QA tooling for AI quality regression.
