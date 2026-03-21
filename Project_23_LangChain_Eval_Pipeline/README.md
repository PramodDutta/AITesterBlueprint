# Project 23: LangChain Evaluation Pipeline for QA

## Overview

This project builds automated evaluation pipelines that treat LLM and RAG quality the way QA teams treat software quality — with regression suites, golden datasets, drift detection, and CI/CD gates. Instead of manually spot-checking AI outputs, you will construct continuous monitoring systems that measure faithfulness, relevance, correctness, and consistency across every deployment, using industry-standard frameworks like RAGAS and DeepEval.

## Objective

Implement a comprehensive evaluation pipeline that continuously monitors RAG and LLM output quality, manages golden test datasets, detects quality drift over time, integrates into CI/CD workflows, and surfaces results through a live dashboard.

## Tech Stack

| Technology | Purpose |
|------------|---------|
| Python 3.11+ | Core language |
| LangChain | LLM pipeline orchestration |
| RAGAS | RAG-specific evaluation metrics |
| DeepEval | LLM evaluation framework |
| GitHub Actions | CI/CD pipeline integration |
| FastAPI | Dashboard backend API |
| HTML/CSS/JS | Quality dashboard UI |
| SQLite | Evaluation result storage |
| Pydantic | Data validation |
| pytest | Test runner for eval suites |

## What You Will Learn

- Core LLM evaluation metrics: faithfulness, answer relevancy, context precision, context recall, hallucination rate
- Building golden datasets with question-answer-context triples for repeatable evaluation
- Running RAGAS evaluation pipelines on RAG systems
- Using DeepEval for custom metric definitions and threshold enforcement
- Detecting quality drift by comparing evaluation scores across model versions, prompt changes, and data updates
- Integrating evaluation checks into GitHub Actions so PRs that degrade quality are flagged automatically
- Building dashboards that display evaluation trends over time
- Designing evaluation strategies specific to QA-domain outputs (test cases, bug reports, test plans)

## Key Deliverables

1. **RAG Evaluation Pipeline** — End-to-end pipeline that evaluates a RAG system against golden datasets using RAGAS metrics (faithfulness, relevancy, precision, recall).
2. **Golden Dataset Manager** — Tools to create, version, and maintain evaluation datasets with question-answer-context triples curated from real QA scenarios.
3. **Drift Detection Engine** — Automated comparison of evaluation scores across runs, flagging statistically significant regressions with configurable thresholds.
4. **CI/CD Integration** — GitHub Actions workflow that runs evaluation suites on every push, blocking merges when quality metrics drop below defined gates.
5. **Quality Dashboard** — A FastAPI-backed web dashboard displaying evaluation trends, metric breakdowns, and historical comparisons.
6. **Custom QA Metrics** — Domain-specific evaluation metrics for QA outputs: test case completeness, step clarity, expected result specificity, and traceability coverage.

## Project Structure

```
Project_23_LangChain_Eval_Pipeline/
├── README.md
├── requirements.txt
├── .env.example
├── .github/
│   └── workflows/
│       └── eval_pipeline.yml
├── config/
│   ├── eval_config.yaml
│   └── thresholds.yaml
├── golden_datasets/
│   ├── testcase_generation.json
│   ├── bug_analysis.json
│   └── dataset_manager.py
├── evaluation/
│   ├── ragas_evaluator.py
│   ├── deepeval_evaluator.py
│   ├── custom_metrics/
│   │   ├── testcase_completeness.py
│   │   ├── step_clarity.py
│   │   └── traceability_score.py
│   └── runner.py
├── drift/
│   ├── drift_detector.py
│   ├── comparator.py
│   └── alerts.py
├── dashboard/
│   ├── api.py
│   ├── routes/
│   │   ├── results.py
│   │   └── trends.py
│   ├── static/
│   │   ├── index.html
│   │   ├── charts.js
│   │   └── styles.css
│   └── db/
│       └── models.py
├── pipelines/
│   ├── rag_eval_pipeline.py
│   ├── llm_eval_pipeline.py
│   └── ci_runner.py
├── tests/
│   ├── test_evaluators.py
│   ├── test_drift_detection.py
│   └── test_custom_metrics.py
└── notebooks/
    ├── 01_ragas_basics.ipynb
    ├── 02_deepeval_custom_metrics.ipynb
    └── 03_drift_analysis.ipynb
```

## Getting Started

### Prerequisites

- Python 3.11 or higher
- An LLM backend (Ollama or Groq/OpenAI API key)
- A RAG system to evaluate (can use Project 21 or any LangChain RAG pipeline)
- (Optional) GitHub repository for CI/CD integration

### Installation

```bash
cd Project_23_LangChain_Eval_Pipeline
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### Configuration

```bash
cp .env.example .env
# Edit .env with LLM API keys
# Edit config/thresholds.yaml to set quality gates
```

### Run Evaluation

```bash
# Run RAGAS evaluation against the golden dataset
python evaluation/runner.py --evaluator ragas --dataset golden_datasets/testcase_generation.json

# Run DeepEval with custom QA metrics
python evaluation/runner.py --evaluator deepeval --dataset golden_datasets/bug_analysis.json

# Run drift detection comparing two evaluation runs
python drift/drift_detector.py --baseline results/run_001.json --current results/run_002.json
```

### Launch Dashboard

```bash
uvicorn dashboard.api:app --reload --port 8000
# Dashboard at http://localhost:8000
```

### CI/CD Integration

```bash
# Test the CI pipeline locally
python pipelines/ci_runner.py --config config/eval_config.yaml
```

### Run Tests

```bash
pytest tests/ -v
```

## QA Angle

QA engineers understand that untested software is unreliable software. The same principle applies to AI systems. This project applies QA fundamentals — regression testing, threshold enforcement, continuous monitoring — to LLM and RAG outputs:

- **Evaluation as Regression Testing** — Golden datasets function exactly like regression test suites. Every time you change a prompt, swap a model, or update your knowledge base, the evaluation pipeline tells you whether quality improved, held steady, or regressed. No more guessing.
- **Quality Gates in CI/CD** — Just as you would block a deployment when unit tests fail, the GitHub Actions integration blocks merges when evaluation metrics drop below configured thresholds. Faithfulness below 0.85? The PR does not merge.
- **Drift Detection as Monitoring** — Models degrade over time due to data changes, provider updates, or prompt drift. The drift detection engine runs scheduled evaluations and alerts when scores deviate beyond acceptable bounds — the LLM equivalent of production monitoring.
- **QA-Specific Metrics** — Generic metrics like "relevancy" miss domain-specific quality dimensions. The custom metrics evaluate what matters for QA outputs: Does the test case have clear preconditions? Are steps unambiguous? Is the expected result verifiable? Does it trace back to a requirement?
- **Treats AI Quality Like Software Quality** — This project bridges the gap between AI engineering and QA engineering. The evaluation pipeline is something a QA team can own, operate, and evolve — applying the same rigor to AI outputs that they already apply to software products.

This is the project that makes all previous AI-powered QA tools trustworthy. Without evaluation, you are deploying AI outputs on faith. With it, you have evidence.

---

## Learning Companion Structure

This project now also includes a teaching-friendly folder structure for guided study:

```text
Project_23_LangChain_Eval_Pipeline/
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
