# Project 24: AI-Powered Test Data Generation

## Overview

Test data is one of the most time-consuming and error-prone aspects of QA. This project uses Large Language Models to generate realistic, schema-aware test data for APIs, databases, and UI forms. Instead of manually crafting fixtures or relying on purely random generators, you will build an intelligent data generation pipeline that understands your schema constraints, business rules, and edge case requirements.

---

## Objective

Build a Python-based tool that accepts schema definitions (OpenAPI specs, database schemas, JSON Schema) and uses LLMs combined with traditional data libraries to produce high-quality, contextually appropriate test data — including edge cases, boundary values, and privacy-safe synthetic records.

---

## Tech Stack

| Tool / Library | Purpose |
|----------------|---------|
| Python 3.10+ | Core language |
| LangChain | LLM orchestration and prompt chaining |
| OpenAI API | LLM for intelligent data generation |
| Faker | Baseline synthetic data generation |
| Pydantic | Schema validation and data modeling |
| PostgreSQL / SQLite | Database-aware generation targets |
| JSON Schema / OpenAPI | Input schema formats |

---

## What You Will Learn

- How to parse OpenAPI specs and database schemas programmatically
- Prompt engineering techniques for structured data generation
- Combining LLM creativity with Faker determinism for reliable outputs
- Generating data that respects foreign key relationships and unique constraints
- Producing edge case data: boundary values, Unicode strings, SQL injection payloads, empty fields
- Building persona-based data profiles (e.g., "new user," "enterprise admin," "international customer")
- Techniques for generating privacy-safe synthetic data that mirrors production distributions
- Validating generated data against Pydantic models before use
- Seeding databases with relationally consistent test records

---

## Key Deliverables

1. **OpenAPI Spec Parser and Generator** — Reads an OpenAPI spec and generates valid request payloads for every endpoint
2. **Database-Aware Generator** — Produces INSERT-ready records that respect foreign keys, constraints, and data types
3. **Edge Case Generator** — Targeted generation of boundary values, Unicode, special characters, and injection strings
4. **Persona-Based Generator** — Creates coherent user profiles with consistent cross-field data (name, email, address, preferences)
5. **Privacy-Safe Synthetic Data Pipeline** — Generates production-realistic data without exposing real PII
6. **Validation Layer** — Pydantic-based validation ensuring all generated data conforms to the target schema

---

## Project Structure

```text
Project_24_AI_TestData_Generation/
├── README.md
├── requirements.txt
├── config/
│   └── settings.yaml
├── schemas/
│   ├── sample_openapi.yaml
│   ├── sample_db_schema.sql
│   └── sample_json_schema.json
├── src/
│   ├── __init__.py
│   ├── schema_parser.py
│   ├── openapi_generator.py
│   ├── db_aware_generator.py
│   ├── edge_case_generator.py
│   ├── persona_generator.py
│   ├── privacy_safe_generator.py
│   ├── llm_chain.py
│   └── validators.py
├── output/
│   ├── generated_payloads/
│   └── generated_sql/
├── tests/
│   ├── test_openapi_generator.py
│   ├── test_db_generator.py
│   ├── test_edge_cases.py
│   └── test_persona_generator.py
└── notebooks/
    └── exploration.ipynb
```

---

## Getting Started

1. **Clone the repository and navigate to the project folder**
   ```bash
   cd Project_24_AI_TestData_Generation
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

5. **Run the OpenAPI spec generator**
   ```bash
   python src/openapi_generator.py --spec schemas/sample_openapi.yaml --output output/generated_payloads/
   ```

6. **Run the database-aware generator**
   ```bash
   python src/db_aware_generator.py --schema schemas/sample_db_schema.sql --format sql
   ```

7. **Generate edge case data**
   ```bash
   python src/edge_case_generator.py --schema schemas/sample_json_schema.json --count 50
   ```

8. **Run tests**
   ```bash
   pytest tests/ -v
   ```

---

## QA Angle

This project directly addresses a core QA pain point: test data quality. As a QA engineer, you will gain the ability to:

- **Eliminate data bottlenecks** — Stop waiting for sanitized production dumps or manually writing fixtures. Generate exactly the data you need in seconds.
- **Improve edge case coverage** — LLMs understand context and can generate edge cases that pure random generators miss (e.g., names with apostrophes, addresses in non-Latin scripts, emails with plus-addressing).
- **Validate schema compliance** — Every generated record is validated against the target schema, catching contract mismatches before tests even run.
- **Support shift-left testing** — Generate test data from specs before the API or database is built, enabling parallel development and testing.
- **Address data privacy requirements** — Generate synthetic data that passes statistical similarity checks without containing real PII, satisfying compliance requirements for test environments.

This is a practical skill that transfers directly to any QA team working with APIs, databases, or form-heavy applications.

---

## Learning Companion Structure

This project now also includes a teaching-friendly folder structure for guided study:

```text
Project_24_AI_TestData_Generation/
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
