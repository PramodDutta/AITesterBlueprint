# AI Visual Regression Testing: Interview Answer Guide

## Question 1

**Why do traditional image diffs often fail in real QA pipelines?**

### Expected Discussion Points
- They flag many harmless pixel differences from fonts, rendering, or antialiasing.
- That creates false positives and alert fatigue.
- Teams stop trusting the signal.
- Visual testing needs intent-aware interpretation, not just pixel comparison.

## Question 2

**How can multimodal AI reduce visual regression false positives?**

### Expected Discussion Points
- It can reason about layout, content, and user meaning instead of raw pixels alone.
- It helps classify whether a change is meaningful or cosmetic.
- It can describe the impact in plain language.
- The result is fewer noisy alerts when paired with good capture discipline.

## Question 3

**What information should be included when sending screenshots to a vision model?**

### Expected Discussion Points
- Baseline and current images, page context, viewport, and the UI area of interest.
- Instructions about which differences matter and which do not.
- A target output format with severity labels.
- Optional product context helps the model judge business impact.

## Question 4

**How would you distinguish a cosmetic layout change from a release blocker?**

### Expected Discussion Points
- Assess whether the user can still complete the task correctly.
- Consider visibility, overlap, truncation, contrast, and interaction damage.
- Evaluate business-critical flows separately from decorative changes.
- Use severity rules that are tied to user impact, not aesthetics alone.

## Question 5

**How would you test the consistency of AI-generated visual verdicts?**

### Expected Discussion Points
- Reuse a benchmark set of known visual changes and expected classifications.
- Check repeatability across similar screenshots.
- Review borderline cases manually to refine prompts.
- Track false-positive and false-negative rates over time.

## Question 6

**Why should accessibility considerations be part of visual regression analysis?**

### Expected Discussion Points
- A UI can look acceptable while becoming less usable or inaccessible.
- Contrast, readability, and visibility are user-impacting quality dimensions.
- Accessibility regressions are still regressions.
- AI-assisted visual checks are stronger when they include those criteria explicitly.
