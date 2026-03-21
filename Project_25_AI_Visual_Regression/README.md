# Project 25: AI Visual Regression Testing

## Overview

Traditional visual regression testing relies on pixel-by-pixel comparison, which generates excessive false positives from antialiasing, font rendering, and minor layout shifts. This project uses multimodal LLMs (GPT-4 Vision, Claude Vision) to analyze screenshot differences with human-like understanding — distinguishing between meaningful UI changes and harmless rendering variations.

---

## Objective

Build an end-to-end visual regression testing pipeline that captures screenshots, uses AI vision models to detect and assess UI changes, classifies their severity, checks accessibility contrast ratios, and produces an HTML report with AI-generated verdicts for each detected difference.

---

## Tech Stack

| Tool / Library | Purpose |
|----------------|---------|
| Python 3.10+ | Core language |
| Playwright | Browser automation and screenshot capture |
| OpenAI Vision API | Multimodal analysis of UI screenshots |
| Claude Vision API | Alternative multimodal analysis |
| Pillow / OpenCV | Image preprocessing and basic diff |
| Jinja2 | HTML report templating |
| pytest | Test runner integration |

---

## What You Will Learn

- Setting up a reliable screenshot capture pipeline with Playwright across multiple viewports
- Encoding and sending images to multimodal LLM APIs for analysis
- Prompt engineering for visual comparison tasks (baseline vs. current)
- Building severity classification systems (critical, major, minor, cosmetic)
- Using AI to assess accessibility implications of visual changes (contrast ratios, text readability)
- Generating structured JSON responses from vision models for programmatic processing
- Building HTML reports with side-by-side comparisons and AI verdicts
- Integrating visual regression checks into CI/CD pipelines
- Managing baseline image storage and versioning strategies

---

## Key Deliverables

1. **Screenshot Capture Pipeline** — Playwright-based capture across configurable pages, viewports, and device emulations
2. **AI-Powered Diff Analysis** — Send baseline and current screenshots to vision LLMs for intelligent comparison
3. **Severity Classification Engine** — AI classifies each change as critical, major, minor, or cosmetic with reasoning
4. **Accessibility Contrast Checker** — AI evaluates whether visual changes introduce WCAG contrast violations
5. **HTML Report Generator** — Rich report with side-by-side images, AI verdicts, severity badges, and filtering
6. **CI Integration Config** — GitHub Actions workflow for automated visual regression on pull requests

---

## Project Structure

```text
Project_25_AI_Visual_Regression/
├── README.md
├── requirements.txt
├── config/
│   ├── pages.yaml
│   └── viewports.yaml
├── src/
│   ├── __init__.py
│   ├── capture.py
│   ├── comparator.py
│   ├── ai_analyzer.py
│   ├── severity_classifier.py
│   ├── accessibility_checker.py
│   ├── report_generator.py
│   └── baseline_manager.py
├── templates/
│   └── report.html
├── baselines/
│   └── .gitkeep
├── screenshots/
│   └── .gitkeep
├── reports/
│   └── .gitkeep
├── tests/
│   ├── test_capture.py
│   ├── test_analyzer.py
│   └── test_report.py
└── .github/
    └── workflows/
        └── visual_regression.yaml
```

---

## Getting Started

1. **Clone the repository and navigate to the project folder**
   ```bash
   cd Project_25_AI_Visual_Regression
   ```

2. **Create and activate a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   playwright install chromium
   ```

4. **Set your API keys**
   ```bash
   export OPENAI_API_KEY="your-key-here"
   # or for Claude Vision
   export ANTHROPIC_API_KEY="your-key-here"
   ```

5. **Capture baseline screenshots**
   ```bash
   python src/capture.py --config config/pages.yaml --output baselines/
   ```

6. **Make changes to your target application, then capture current screenshots**
   ```bash
   python src/capture.py --config config/pages.yaml --output screenshots/
   ```

7. **Run the AI-powered visual comparison**
   ```bash
   python src/comparator.py --baseline baselines/ --current screenshots/ --report reports/
   ```

8. **Open the generated report**
   ```bash
   open reports/visual_regression_report.html
   ```

---

## QA Angle

Visual regression testing is a critical layer in UI quality assurance, and AI transforms it from a noisy, high-maintenance task into a meaningful quality gate:

- **Reduce false positives dramatically** — AI understands that a 1px font rendering difference is not the same as a missing button. This cuts noise by 80-90% compared to pixel-diff tools.
- **Get human-readable explanations** — Instead of a red-highlighted diff image, you get verdicts like "The primary CTA button color changed from blue to green. This is a major change that may affect brand consistency."
- **Catch accessibility regressions** — AI can flag when a color change reduces contrast below WCAG AA thresholds, catching issues that pixel-diff tools completely miss.
- **Scale across viewports** — Test desktop, tablet, and mobile views with AI that understands responsive layout intent rather than flagging every reflow as a failure.
- **Build QA confidence in releases** — Visual regression with AI verdicts gives product teams and stakeholders clear, actionable insights instead of opaque diff images.

This project is directly applicable to any team shipping web applications where UI consistency and accessibility matter.

---

## Learning Companion Structure

This project now also includes a teaching-friendly folder structure for guided study:

```text
Project_25_AI_Visual_Regression/
├── 01_Learning/
├── 02_Exercises/
├── 03_Interview_Questions/
```

### What to Use Each Folder For

- `01_Learning` — topic summary, learning goals, QA/SDET framing, and a concept diagram
- `02_Exercises` — guided practice tasks that students can use before implementation
- `03_Interview_Questions` — QA/SDET-oriented interview prep tied to the same topic

Recommended order:

1. Start with `01_Learning`
2. Work through `02_Exercises`
3. Review `03_Interview_Questions`
4. Return to the implementation assets in the rest of the project
