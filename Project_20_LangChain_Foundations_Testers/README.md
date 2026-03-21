# Project 20: LangChain Foundations for Testers

## Overview

This project provides a hands-on introduction to LangChain built entirely around QA engineering use cases. Instead of generic chatbot tutorials, every example here solves a real testing problem — from generating test cases out of user stories to building agents that assist with test planning. You will learn chains, agents, tools, memory, and output parsing by building artifacts you would actually use on a QA team.

## Objective

Master the core LangChain primitives (chains, agents, tools, memory, output parsers) by constructing practical QA automation workflows that transform how testers interact with LLMs.

## Tech Stack

| Technology | Purpose |
|------------|---------|
| Python 3.11+ | Core language |
| LangChain | LLM orchestration framework |
| Ollama | Local LLM inference (Llama 3, Mistral) |
| Groq | Cloud-based fast inference (fallback) |
| Pydantic | Structured output validation |
| Streamlit | Interactive demo UI |
| pytest | Test runner for validation |

## What You Will Learn

- How LangChain chains compose prompts, LLMs, and output parsers into reusable pipelines
- Building sequential and parallel chains for multi-step QA workflows
- Creating custom LangChain tools that wrap testing utilities (JIRA lookup, Selenium actions, log parsers)
- Designing agents that reason about which tool to call and when
- Using ConversationBufferMemory and ConversationSummaryMemory for context-aware QA assistants
- Enforcing structured output with Pydantic models so LLM responses become machine-readable QA artifacts
- Prompt engineering patterns specific to test case generation and defect analysis
- Comparing local (Ollama) vs. cloud (Groq) model performance for QA tasks

## Key Deliverables

1. **User Story to Test Case Chain** — An LCEL chain that accepts a user story and produces structured test cases (title, steps, expected result, priority) validated by Pydantic.
2. **LangChain Agent with QA Tools** — An agent equipped with tools for test plan lookup, requirement search, and risk scoring that autonomously plans test coverage.
3. **Pydantic Output Parsers for QA Artifacts** — Reusable parsers for test cases, bug reports, test plans, and traceability matrices that guarantee schema-compliant output.
4. **Memory-Enabled QA Chatbot** — A conversational assistant that remembers project context across turns, helping testers iteratively refine test strategies.
5. **Prompt Template Library** — A curated set of QA-specific prompt templates for common testing tasks.

## Project Structure

```
Project_20_LangChain_Foundations_Testers/
├── README.md
├── requirements.txt
├── .env.example
├── config/
│   └── models.yaml
├── chains/
│   ├── user_story_to_testcase.py
│   ├── bug_report_enhancer.py
│   └── test_plan_chain.py
├── agents/
│   ├── qa_planner_agent.py
│   └── tools/
│       ├── jira_lookup.py
│       ├── requirement_search.py
│       └── risk_scorer.py
├── parsers/
│   ├── testcase_parser.py
│   ├── bugreport_parser.py
│   └── traceability_parser.py
├── memory/
│   └── qa_chatbot.py
├── prompts/
│   ├── testcase_prompts.py
│   └── analysis_prompts.py
├── ui/
│   └── streamlit_app.py
├── tests/
│   ├── test_chains.py
│   ├── test_parsers.py
│   └── test_agent.py
└── notebooks/
    ├── 01_chains_basics.ipynb
    ├── 02_output_parsers.ipynb
    ├── 03_agents_and_tools.ipynb
    └── 04_memory_patterns.ipynb
```

## Getting Started

### Prerequisites

- Python 3.11 or higher
- Ollama installed locally with at least one model pulled (`ollama pull llama3`)
- (Optional) Groq API key for cloud inference

### Installation

```bash
cd Project_20_LangChain_Foundations_Testers
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### Configuration

```bash
cp .env.example .env
# Edit .env with your API keys (Groq is optional if using Ollama)
```

### Run Examples

```bash
# Run the user story to test case chain
python chains/user_story_to_testcase.py

# Launch the QA planner agent
python agents/qa_planner_agent.py

# Start the interactive QA chatbot
python memory/qa_chatbot.py

# Launch the Streamlit UI
streamlit run ui/streamlit_app.py
```

### Run Tests

```bash
pytest tests/ -v
```

## QA Angle

This project is not a LangChain tutorial that happens to mention testing — it is a testing project that teaches LangChain. Every chain, agent, and parser is designed around artifacts QA engineers produce daily:

- **Test Case Generation** — The chain does not just "write tests"; it enforces structure (preconditions, steps, expected results, priority) and validates output against a Pydantic schema, ensuring the LLM output is ready for import into test management tools.
- **Agent-Based Test Planning** — The agent mirrors how a senior tester thinks: it checks requirements, assesses risk, looks up existing coverage, and then recommends what to test. This teaches agent reasoning in a domain you already understand.
- **Structured Output Guarantee** — Pydantic parsers ensure every LLM response conforms to a defined contract. This is critical for integrating AI output into CI/CD pipelines where malformed data breaks downstream processes.
- **Conversational Context** — Memory patterns let you build assistants that remember your project's domain, previous test runs, and known issues — turning a stateless LLM into a persistent QA partner.

Mastering these foundations prepares you for the advanced projects that follow: Graph RAG knowledge bases, multi-agent orchestration, and evaluation pipelines.

---

## Learning Companion Structure

This project now also includes a teaching-friendly folder structure for guided study:

```text
Project_20_LangChain_Foundations_Testers/
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
