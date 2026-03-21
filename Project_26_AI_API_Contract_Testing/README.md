# Project 26: AI-Assisted API Contract Testing

## Overview

API contracts define the agreement between services. When contracts break, downstream systems fail — often silently. This project uses LLMs to automate the generation, validation, and monitoring of API contracts. Instead of manually writing and maintaining contract tests, you will build an AI-powered system that detects breaking changes, generates contract tests, and keeps specs in sync with implementation.

---

## Objective

Build a Python-based API contract testing toolkit that uses LLMs to auto-generate OpenAPI specifications from code, detect contract drift between spec and implementation, analyze breaking changes with severity assessment, generate consumer-driven contract tests, and produce mock servers from contracts.

---

## Tech Stack

| Tool / Library | Purpose |
|----------------|---------|
| Python 3.10+ | Core language |
| LangChain | LLM orchestration |
| OpenAI API | Contract analysis and test generation |
| FastAPI | Mock API server and sample endpoints |
| Pact (Python) | Consumer-driven contract testing |
| Schemathesis | Property-based API testing from specs |
| OpenAPI / Swagger | Contract specification format |
| deepdiff | Schema comparison and drift detection |

---

## What You Will Learn

- How API contracts work and why they break in microservice architectures
- Using LLMs to generate OpenAPI specs from FastAPI route definitions
- Building automated contract drift detection between spec files and live endpoints
- Classifying breaking vs. non-breaking API changes with AI reasoning
- Generating Pact consumer contract tests using LLM-produced expectations
- Running Schemathesis for property-based contract fuzzing
- Auto-generating mock servers from OpenAPI specs for frontend teams
- Setting up contract verification in CI/CD pipelines
- Prompt engineering for structured API analysis tasks

---

## Key Deliverables

1. **OpenAPI Spec Generator** — AI reads API source code and generates a complete OpenAPI 3.0 specification
2. **Contract Drift Detector** — Compares the declared spec against actual API responses and flags mismatches
3. **Breaking Change Analyzer** — AI classifies changes (removed fields, type changes, new required params) with severity and migration guidance
4. **AI-Generated Contract Tests** — LLM produces Pact-compatible contract tests for each consumer-provider pair
5. **Mock Server Generator** — Auto-generates a FastAPI mock server from any OpenAPI spec with realistic sample responses
6. **Contract Dashboard** — Summary report showing contract health across all monitored endpoints

---

## Project Structure

```text
Project_26_AI_API_Contract_Testing/
├── README.md
├── requirements.txt
├── config/
│   └── settings.yaml
├── specs/
│   ├── v1_spec.yaml
│   └── v2_spec.yaml
├── sample_api/
│   ├── __init__.py
│   ├── main.py
│   ├── routes/
│   │   ├── users.py
│   │   └── orders.py
│   └── models.py
├── src/
│   ├── __init__.py
│   ├── spec_generator.py
│   ├── drift_detector.py
│   ├── breaking_change_analyzer.py
│   ├── contract_test_generator.py
│   ├── mock_server_generator.py
│   ├── llm_chain.py
│   └── report.py
├── contracts/
│   └── generated/
├── tests/
│   ├── test_drift_detector.py
│   ├── test_breaking_changes.py
│   ├── test_contract_generation.py
│   └── contract_tests/
│       └── .gitkeep
└── reports/
    └── .gitkeep
```

---

## Getting Started

1. **Clone the repository and navigate to the project folder**
   ```bash
   cd Project_26_AI_API_Contract_Testing
   ```

2. **Create and activate a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set your OpenAI API key**
   ```bash
   export OPENAI_API_KEY="your-key-here"
   ```

5. **Start the sample FastAPI server**
   ```bash
   uvicorn sample_api.main:app --reload --port 8000
   ```

6. **Generate an OpenAPI spec from the running API**
   ```bash
   python src/spec_generator.py --source sample_api/ --output specs/v1_spec.yaml
   ```

7. **Run contract drift detection**
   ```bash
   python src/drift_detector.py --spec specs/v1_spec.yaml --base-url http://localhost:8000
   ```

8. **Analyze breaking changes between two spec versions**
   ```bash
   python src/breaking_change_analyzer.py --old specs/v1_spec.yaml --new specs/v2_spec.yaml
   ```

9. **Generate contract tests**
   ```bash
   python src/contract_test_generator.py --spec specs/v1_spec.yaml --output tests/contract_tests/
   ```

10. **Run tests**
    ```bash
    pytest tests/ -v
    ```

---

## QA Angle

API contract testing is one of the highest-value QA activities in modern software, and AI makes it accessible at scale:

- **Catch breaking changes before deployment** — The drift detector and breaking change analyzer identify removed fields, type changes, and new required parameters before they reach production.
- **Automate contract test creation** — Writing Pact tests manually is tedious and often skipped. AI generates comprehensive contract expectations in seconds, improving coverage immediately.
- **Bridge the spec-implementation gap** — Many teams have outdated or missing OpenAPI specs. The AI spec generator creates accurate specs from source code, establishing a baseline for contract testing.
- **Enable parallel development** — Auto-generated mock servers let frontend and mobile teams develop against contracts while backend work is still in progress.
- **Shift-left API quality** — Contract tests run in seconds and catch integration issues that would otherwise surface only in expensive end-to-end test environments.

This project equips QA engineers with tools that directly prevent the most common cause of production incidents in microservice architectures: broken API contracts.

---

## Learning Companion Structure

This project now also includes a teaching-friendly folder structure for guided study:

```text
Project_26_AI_API_Contract_Testing/
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
