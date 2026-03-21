# Intelligent Test Maintenance: Interview Answer Guide

## Question 1

**What makes a test flaky, and how would you prove it with data?**

### Expected Discussion Points
- A flaky test changes outcome without meaningful product change.
- You prove it with repeated runs, transition patterns, and environmental correlation.
- Pass-rate trends and rerun behavior matter.
- Evidence beats intuition when labeling a test as flaky.

## Question 2

**How can AI help classify automation failures beyond simple log parsing?**

### Expected Discussion Points
- It can synthesize logs, screenshots, stack traces, and context into a likely root cause.
- It can cluster similar failures and summarize repeated patterns.
- It helps triage faster, especially in large suites.
- It still needs strong evidence and a human-check path for low-confidence cases.

## Question 3

**What are the dangers of automatic locator healing?**

### Expected Discussion Points
- A healed selector may point to the wrong element and hide a real defect.
- Teams may trust a test that no longer validates the intended behavior.
- Silent healing can erode suite credibility.
- Healing should be transparent, reviewable, and constrained.

## Question 4

**How would you build trust in a flaky-test detection system?**

### Expected Discussion Points
- Make the scoring logic and evidence visible.
- Benchmark against known flaky and stable tests.
- Track false classifications and refine the rules.
- Expose the reasoning so engineers can verify the conclusions.

## Question 5

**What metrics belong on a test-maintenance dashboard?**

### Expected Discussion Points
- Flaky-test count, failure trends, top root causes, healing attempts, and maintenance backlog are useful.
- Time-to-fix and suite stability trends help leadership.
- Metrics should separate product defects from test debt.
- The goal is actionability, not vanity statistics.

## Question 6

**How would you explain the tradeoff between fast healing and test reliability?**

### Expected Discussion Points
- Faster healing reduces immediate friction but can hide deeper issues.
- Reliability requires confidence that the test still validates the intended user behavior.
- A good system balances speed with transparent approval and validation.
- Trust is more valuable than silent self-repair.
