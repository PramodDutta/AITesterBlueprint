# Project 21: Graph RAG QA Knowledge Base (LangChain + Neo4j)

## Overview

This project builds a full Graph RAG (Retrieval-Augmented Generation) system purpose-built for QA knowledge management. By storing test documentation in a Neo4j knowledge graph — with entities like features, bugs, test cases, and modules connected by explicit relationships — you unlock queries that traditional vector-only RAG cannot answer: "What tests cover the payment module?", "If we change the auth service, which test suites are affected?", and "Show me all bugs linked to checkout that lack regression tests."

## Objective

Design and implement a Graph RAG pipeline that ingests QA documentation into a knowledge graph, extracts entities and relationships, and answers complex test coverage and impact analysis questions using natural language.

## Tech Stack

| Technology | Purpose |
|------------|---------|
| Python 3.11+ | Core language |
| LangChain | RAG orchestration and LLM integration |
| Neo4j | Graph database for knowledge storage |
| FastAPI | REST API backend |
| HTML/CSS/JS | Visual graph explorer UI |
| Ollama / Groq | LLM inference for entity extraction and QA |
| Pydantic | Request/response validation |
| Docker | Neo4j container management |

## What You Will Learn

- How Graph RAG differs from vector-only RAG and when to use each approach
- Modeling QA domain entities (features, test cases, bugs, modules, requirements) as graph nodes and edges
- Automated entity and relationship extraction from unstructured test documentation using LLMs
- Writing and generating Cypher queries for graph traversal
- Combining graph retrieval with vector similarity for hybrid search
- Building a natural language interface over a knowledge graph
- Impact analysis through graph path traversal
- Visualizing knowledge graphs for test coverage exploration

## Key Deliverables

1. **Document Ingestion Pipeline** — Parses test plans, bug reports, requirement docs, and test case spreadsheets into graph-ready entities and relationships.
2. **Entity Extraction Engine** — LLM-powered extraction of features, modules, test cases, bugs, and their interconnections from raw text.
3. **Cypher Query Generator** — Natural language to Cypher translation so testers can ask questions like "What tests cover the payment module?" without learning graph query syntax.
4. **Impact Analysis Engine** — Given a code change or feature modification, trace the graph to identify all affected test cases, dependent modules, and related known bugs.
5. **Visual Graph Explorer** — An HTML-based UI that renders the knowledge graph interactively, letting users click through nodes and relationships.
6. **FastAPI REST Service** — API endpoints for ingestion, querying, and impact analysis.

## Project Structure

```
Project_21_GraphRAG_QA_KnowledgeBase/
├── README.md
├── requirements.txt
├── .env.example
├── docker-compose.yml
├── config/
│   ├── neo4j_config.yaml
│   └── graph_schema.yaml
├── ingestion/
│   ├── document_loader.py
│   ├── entity_extractor.py
│   ├── relationship_mapper.py
│   └── graph_writer.py
├── retrieval/
│   ├── cypher_generator.py
│   ├── graph_retriever.py
│   ├── hybrid_search.py
│   └── impact_analyzer.py
├── api/
│   ├── main.py
│   ├── routes/
│   │   ├── ingest.py
│   │   ├── query.py
│   │   └── impact.py
│   └── models/
│       ├── request_models.py
│       └── response_models.py
├── ui/
│   ├── index.html
│   ├── graph_viewer.js
│   └── styles.css
├── sample_data/
│   ├── test_plans/
│   ├── bug_reports/
│   └── requirements/
├── tests/
│   ├── test_ingestion.py
│   ├── test_cypher_generator.py
│   └── test_impact_analysis.py
└── notebooks/
    ├── 01_graph_modeling.ipynb
    ├── 02_entity_extraction.ipynb
    └── 03_impact_analysis.ipynb
```

## Getting Started

### Prerequisites

- Python 3.11 or higher
- Docker and Docker Compose (for Neo4j)
- Ollama installed locally or a Groq API key

### Launch Neo4j

```bash
cd Project_21_GraphRAG_QA_KnowledgeBase
docker-compose up -d
# Neo4j Browser available at http://localhost:7474
# Default credentials: neo4j / testpassword
```

### Installation

```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### Configuration

```bash
cp .env.example .env
# Edit .env with Neo4j connection details and LLM API keys
```

### Ingest Sample Data

```bash
python ingestion/document_loader.py --source sample_data/
```

### Start the API and UI

```bash
uvicorn api.main:app --reload --port 8000
# API docs at http://localhost:8000/docs
# Graph explorer at http://localhost:8000/ui
```

### Run Tests

```bash
pytest tests/ -v
```

## QA Angle

Traditional RAG retrieves text chunks by similarity — useful for "find me something about payments" but unable to answer structural questions about your test landscape. Graph RAG changes this fundamentally:

- **Test Coverage Mapping** — The knowledge graph explicitly links requirements to test cases to modules. You can query "Which requirements have no test cases?" or "What is the test coverage for the checkout flow?" and get precise, relationship-based answers instead of fuzzy text matches.
- **Impact Analysis** — When a developer says "we changed the authentication service," graph traversal instantly identifies every test case, feature, and downstream module affected. This replaces hours of manual traceability review.
- **Bug-to-Test Traceability** — Bugs are linked to the features they affect and the test cases that should catch them. You can verify whether a reported bug has a corresponding regression test or find patterns in which modules accumulate the most defects.
- **Knowledge Preservation** — QA knowledge often lives in spreadsheets, wikis, and tribal memory. The graph captures relationships that would otherwise be lost when team members leave, making institutional QA knowledge queryable and permanent.

This project demonstrates that the real power of RAG for QA is not just retrieving documents — it is understanding the connections between them.

---

## Learning Companion Structure

This project now also includes a teaching-friendly folder structure for guided study:

```text
Project_21_GraphRAG_QA_KnowledgeBase/
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
