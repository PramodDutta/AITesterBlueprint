# MCP Basics for QA: Interview Answer Guide

## Question 1

**What problem does MCP solve for QA teams using AI-assisted tooling?**

### Expected Discussion Points
- It standardizes how AI systems discover and call external tools safely.
- It reduces ad-hoc glue code between models and QA systems such as browsers or defect trackers.
- It makes tool usage inspectable and easier to audit.
- It gives QA teams a structured path from prompting to governed automation.

## Question 2

**How would you prevent an AI agent from taking unsafe browser or issue-tracker actions through MCP?**

### Expected Discussion Points
- Separate read-only tools from write-capable tools.
- Add approval gates before destructive or externally visible actions.
- Validate tool inputs against schemas and business rules.
- Log every invocation with user, input, output, and timestamp metadata.

## Question 3

**What is the difference between a tool call and a resource lookup in an MCP-style workflow?**

### Expected Discussion Points
- A tool call performs an action or computation.
- A resource lookup usually retrieves data or context without side effects.
- Tool calls carry operational risk and usually need stronger validation.
- Resource access is often the safer first step for grounding AI decisions.

## Question 4

**How would you test an MCP server that exposes Playwright actions to an AI system?**

### Expected Discussion Points
- Validate schema correctness and authorization for every exposed tool.
- Test happy paths and failure paths such as navigation errors or missing selectors.
- Confirm screenshots, logs, and evidence are generated consistently.
- Verify that unsafe actions are blocked or require approval as designed.

## Question 5

**Why is auditability important in AI-assisted QA execution platforms?**

### Expected Discussion Points
- QA teams need to reconstruct why an action happened and who approved it.
- Auditability supports compliance, trust, and incident review.
- It distinguishes tool misuse from product defects or model mistakes.
- It makes AI workflows reviewable like any other engineering system.

## Question 6

**How would you explain MCP to an SDET who has worked only with APIs and browser automation?**

### Expected Discussion Points
- Describe MCP as a standard interface layer between the model and external tools.
- Compare it to giving an API client a typed contract instead of raw shell access.
- Show that Playwright, JIRA, and file systems become structured capabilities.
- Emphasize governance: tool access becomes explicit, testable, and observable.
