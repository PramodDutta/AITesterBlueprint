# AI Security Testing Assistant: Interview Answer Guide

## Question 1

**How can AI help QA teams participate in security testing without replacing security expertise?**

### Expected Discussion Points
- It can generate targeted ideas, summarize findings, and lower the entry barrier to structured security work.
- It helps QA teams ask better questions and cover more risk earlier.
- It does not replace deep exploitation knowledge or security signoff.
- The best use is augmentation with clear boundaries.

## Question 2

**What is the difference between direct prompt injection and indirect prompt injection?**

### Expected Discussion Points
- Direct prompt injection comes from the user input itself.
- Indirect prompt injection is hidden inside retrieved or external content that the model consumes.
- Indirect attacks are especially relevant in RAG and tool-using systems.
- Testing both matters because the trust boundary differs.

## Question 3

**How would you validate whether an AI-generated XSS or SQLi payload is meaningful?**

### Expected Discussion Points
- Check that it matches the target execution context and input location.
- Validate real behavior, not just a blocked or reflected string.
- Review the evidence such as DOM changes, error messages, timing, or database impact.
- Reject payloads that are unrealistic noise or unsupported by results.

## Question 4

**Why do scanner outputs need human review even when AI summarizes them?**

### Expected Discussion Points
- Scanner outputs contain false positives, duplicates, and context gaps.
- AI summaries can improve readability but cannot guarantee exploitability judgment.
- Human review is required for severity, business impact, and remediation planning.
- Security quality depends on evidence, not only summaries.

## Question 5

**How would you teach OWASP risk thinking to a QA automation team?**

### Expected Discussion Points
- Start from attack surfaces the team already tests: login, search, input forms, and integrations.
- Map each area to common OWASP risks and concrete examples.
- Tie vulnerabilities to user impact and product risk.
- Make the learning scenario-based, not purely theoretical.

## Question 6

**What safeguards should exist before running AI-assisted security tests against real systems?**

### Expected Discussion Points
- Explicit authorization, safe scope, and environment boundaries are mandatory.
- Potentially destructive tests need additional review and containment.
- Logging, rate controls, and rollback plans reduce harm.
- Ethical and legal constraints are part of the test design, not an afterthought.
