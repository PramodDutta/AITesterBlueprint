# AI-Assisted API Contract Testing: Interview Answer Guide

## Question 1

**What is API contract testing, and why is it important for distributed systems?**

### Expected Discussion Points
- It verifies that services honor agreed request and response behavior.
- In distributed systems, consumers break when those contracts drift or change unexpectedly.
- Contract testing catches integration issues earlier than end-to-end failures.
- It protects confidence across independently deployed services.

## Question 2

**How would you detect drift between an OpenAPI spec and a live API?**

### Expected Discussion Points
- Compare real requests and responses against the declared schema.
- Exercise representative endpoints and payload shapes.
- Flag missing fields, type changes, unexpected enums, or status-code differences.
- Use automation so drift is caught continuously, not only manually.

## Question 3

**What changes are typically considered breaking changes?**

### Expected Discussion Points
- Removing fields or endpoints, changing types incompatibly, and adding new required inputs are common examples.
- Changing semantic meaning can also be breaking even if the schema appears similar.
- Consumer behavior and backward compatibility determine impact.
- Severity should reflect downstream dependence.

## Question 4

**How can AI help generate or maintain contract tests?**

### Expected Discussion Points
- It can translate specs into test cases, identify gaps, and explain diffs in plain language.
- It can suggest contract scenarios from historical defects.
- It should not invent fields or assumptions beyond the contract source.
- Human review is still required for correctness and consumer relevance.

## Question 5

**How would you combine Schemathesis or Pact with AI-driven analysis?**

### Expected Discussion Points
- Use the testing tool for execution and evidence generation.
- Use AI to summarize failures, classify severity, or suggest likely root causes.
- Keep factual validation in the deterministic toolchain.
- This separation preserves trust while improving developer usability.

## Question 6

**What risks appear if teams trust generated OpenAPI specs without validation?**

### Expected Discussion Points
- The generated spec may encode incorrect assumptions or omit edge cases.
- Tests built on a wrong spec give false confidence.
- Consumer teams may align to an inaccurate contract.
- Generated artifacts must always be checked against implementation and product intent.
