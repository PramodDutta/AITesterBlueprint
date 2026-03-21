# LangChain Evaluation Pipeline: Interview Answer Guide

## Question 1

**Why should LLM or RAG systems have regression pipelines similar to software test suites?**

### Expected Discussion Points
- AI quality changes over time with prompts, data, retrievers, or model updates.
- Regression pipelines make those changes visible before release.
- They turn subjective quality concerns into repeatable evidence.
- This is how AI systems become manageable engineering assets.

## Question 2

**What is a golden dataset, and how would you maintain it over time?**

### Expected Discussion Points
- It is a curated set of high-value test cases used to compare versions consistently.
- Maintain it with versioning, clear rationale, and periodic review.
- Add examples from production incidents or newly discovered risks.
- Avoid changing it casually, or trend analysis loses meaning.

## Question 3

**How would you choose thresholds for metrics such as faithfulness or relevancy?**

### Expected Discussion Points
- Use baseline performance, stakeholder expectations, and risk severity.
- Benchmark multiple versions before locking thresholds.
- Different metrics may require different tolerance bands.
- Thresholds should be revisited with evidence, not intuition alone.

## Question 4

**What is the risk of relying on a single evaluation score in CI/CD?**

### Expected Discussion Points
- One metric can hide failure modes in another dimension.
- Composite quality needs multiple views such as correctness, grounding, and safety.
- Single-score thinking creates blind spots and misleading pass states.
- A QA mindset prefers balanced, interpretable signals.

## Question 5

**How would you explain the role of RAGAS to a QA lead?**

### Expected Discussion Points
- RAGAS provides metrics tailored to RAG quality dimensions.
- It helps quantify retrieval and answer quality instead of relying on manual spot checks.
- It fits naturally into regression monitoring.
- It is a measurement tool, not a substitute for test strategy.

## Question 6

**How would you investigate evaluation drift after a model upgrade?**

### Expected Discussion Points
- Compare old and new outputs across the same golden dataset.
- Inspect prompt behavior, retrieval changes, and model-specific tendencies.
- Check whether the evaluation method itself changed sensitivity.
- Use sampled manual review to confirm whether the drift is real and important.
