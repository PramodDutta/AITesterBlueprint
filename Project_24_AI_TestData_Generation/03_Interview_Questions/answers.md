# AI Test Data Generation: Interview Answer Guide

## Question 1

**Why is AI useful for test data generation beyond static factories or Faker?**

### Expected Discussion Points
- It can reason about context, relationships, and realistic combinations.
- It helps generate semantically meaningful edge cases.
- It can read schemas and produce richer first-pass datasets.
- It complements deterministic generators instead of replacing them.

## Question 2

**How would you keep generated data consistent with database constraints?**

### Expected Discussion Points
- Use schema parsing and explicit validation against relational rules.
- Generate parent records before dependent records.
- Check uniqueness, nullability, enums, and foreign keys.
- Reject or repair inconsistent outputs before test execution.

## Question 3

**What privacy risks exist when generating data from production-like examples?**

### Expected Discussion Points
- Too-close examples can leak real user information or sensitive patterns.
- Prompts and stored artifacts may accidentally preserve PII.
- Teams need privacy-safe source material and masking discipline.
- Synthetic data should resemble production statistically, not personally.

## Question 4

**How would you generate edge-case data for an OpenAPI schema?**

### Expected Discussion Points
- Use required fields, enums, ranges, formats, and examples as anchors.
- Generate boundary values, invalid types, missing fields, and malicious strings.
- Validate outputs against the schema to separate valid from intentionally invalid sets.
- Tie each case to a known risk or validation objective.

## Question 5

**Why should QA teams validate AI-generated data before using it in regression runs?**

### Expected Discussion Points
- Bad data creates false failures or false confidence.
- Generated outputs may violate hidden business rules.
- Validation keeps the suite trustworthy and repeatable.
- AI-generated data is helpful only when it behaves like a controlled test asset.

## Question 6

**How would you explain relational consistency in synthetic data generation?**

### Expected Discussion Points
- Related records must agree across keys, states, and business rules.
- An order cannot reference a customer or product that does not exist.
- Cross-table logic matters as much as field-level validity.
- QA value comes from realistic scenarios, not isolated fake rows.
