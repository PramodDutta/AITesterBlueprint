# AI + Test Frameworks: Interview Answer Guide

## Question 1

**Where does AI help most when building a test automation framework?**

### Expected Discussion Points
- Framework scaffolding, boilerplate reduction, and repetitive helper generation are strong use cases.
- AI is especially helpful when turning requirements into first-pass artifacts.
- It accelerates review checklists, prompts, and documentation.
- It should support, not replace, architectural decisions.

## Question 2

**What risks appear when teams copy AI-generated framework code without review?**

### Expected Discussion Points
- Hidden anti-patterns can spread quickly across the suite.
- Generated code may ignore project conventions, error handling, or synchronization practices.
- Selectors, waits, and assertions may be brittle or logically incorrect.
- Poor review turns short-term speed into long-term maintenance debt.

## Question 3

**How would you evaluate whether a generated Page Object follows good design principles?**

### Expected Discussion Points
- Check whether it exposes business actions instead of raw selector noise.
- Ensure it avoids embedding assertions unrelated to page behavior.
- Review naming, reuse, synchronization, and separation of concerns.
- Confirm it is readable and test-framework consistent.

## Question 4

**How can AI assist API framework setup for request models and clients?**

### Expected Discussion Points
- It can generate models, client wrappers, request builders, and sample payloads.
- It can summarize endpoint behavior and expected validation paths.
- It should use the spec as a grounding source rather than invent fields.
- Generated clients still need schema validation and contract review.

## Question 5

**What QA standards would you enforce before merging AI-generated framework code?**

### Expected Discussion Points
- Coding standards, naming rules, linting, and test review must still apply.
- Generated code should have deterministic behavior and clear ownership.
- Peer review should inspect assertions, waits, abstractions, and error handling.
- Changes should be traceable to a requirement or framework objective.

## Question 6

**How would you compare AI-assisted framework design in Selenium versus Playwright?**

### Expected Discussion Points
- Playwright often supports stronger built-in synchronization and cleaner patterns.
- Selenium frameworks may need more deliberate wrapper design and wait strategy control.
- AI can scaffold either, but the review criteria differ by tool capability.
- The framework choice should still reflect team skill, browser needs, and product context.
