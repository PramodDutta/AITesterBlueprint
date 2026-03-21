# Project 22: LangChain Multi-Agent Test Orchestrator

## Overview

This project builds a multi-agent system where specialized AI agents collaborate to execute complete QA workflows — mirroring how a real testing team operates. A Planner Agent breaks down testing objectives, a Generator Agent writes test cases, a Reviewer Agent critiques them, an Executor Agent runs automated checks, and a Reporter Agent compiles results. A Supervisor routes tasks between agents using LangGraph's state machine architecture.

## Objective

Design and implement a multi-agent orchestration system using LangGraph that decomposes complex QA tasks into subtasks, delegates them to specialized agents, manages shared state and handoffs, and produces cohesive test deliverables.

## Tech Stack

| Technology | Purpose |
|------------|---------|
| Python 3.11+ | Core language |
| LangChain | LLM orchestration |
| LangGraph | Multi-agent state machine framework |
| Groq / OpenAI | LLM inference backends |
| Playwright | Browser automation for test execution |
| FastAPI | Orchestration API |
| Pydantic | State and message validation |
| Streamlit | Monitoring dashboard |

## What You Will Learn

- Designing multi-agent architectures with clear role separation
- Building state machines with LangGraph for agent workflow orchestration
- Implementing supervisor routing patterns that decide which agent acts next
- Managing shared state across agents (test plans, coverage data, results)
- Agent-to-agent handoff protocols and message passing
- Integrating Playwright for automated test execution within agent workflows
- Error handling and retry strategies in multi-agent systems
- Monitoring and tracing agent decisions for debugging and audit

## Key Deliverables

1. **Planner Agent** — Accepts a feature description or user story and produces a structured test plan with priorities, risk areas, and scope boundaries.
2. **Generator Agent** — Takes the test plan and generates detailed test cases with steps, expected results, and test data.
3. **Reviewer Agent** — Critiques generated test cases for completeness, edge case coverage, ambiguity, and alignment with requirements.
4. **Executor Agent** — Runs automated checks using Playwright, validates UI flows, and captures evidence (screenshots, network logs).
5. **Reporter Agent** — Aggregates results from all agents into a formatted test execution report with pass/fail summaries and defect candidates.
6. **Supervisor Router** — LangGraph-based supervisor that manages agent sequencing, parallel execution, conditional routing, and human-in-the-loop checkpoints.

## Project Structure

```
Project_22_MultiAgent_Test_Orchestrator/
├── README.md
├── requirements.txt
├── .env.example
├── config/
│   ├── agents.yaml
│   └── workflows.yaml
├── agents/
│   ├── base_agent.py
│   ├── planner_agent.py
│   ├── generator_agent.py
│   ├── reviewer_agent.py
│   ├── executor_agent.py
│   └── reporter_agent.py
├── orchestration/
│   ├── supervisor.py
│   ├── state.py
│   ├── graph.py
│   └── handoff.py
├── tools/
│   ├── playwright_runner.py
│   ├── screenshot_capture.py
│   └── report_formatter.py
├── api/
│   ├── main.py
│   └── routes/
│       ├── orchestrate.py
│       └── status.py
├── ui/
│   └── dashboard.py
├── sample_inputs/
│   ├── user_stories/
│   └── feature_specs/
├── tests/
│   ├── test_planner.py
│   ├── test_generator.py
│   ├── test_reviewer.py
│   ├── test_orchestration.py
│   └── test_e2e_workflow.py
└── notebooks/
    ├── 01_single_agent.ipynb
    ├── 02_agent_handoffs.ipynb
    └── 03_full_orchestration.ipynb
```

## Getting Started

### Prerequisites

- Python 3.11 or higher
- Groq API key or OpenAI API key
- Playwright browsers installed
- (Optional) A target web application for live test execution

### Installation

```bash
cd Project_22_MultiAgent_Test_Orchestrator
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
playwright install chromium
```

### Configuration

```bash
cp .env.example .env
# Edit .env with your LLM API keys and target application URL
```

### Run Individual Agents

```bash
# Test the planner agent in isolation
python agents/planner_agent.py --input "User can reset password via email"

# Test the generator agent
python agents/generator_agent.py --plan sample_inputs/test_plan.json
```

### Run Full Orchestration

```bash
# Execute the complete multi-agent workflow
python orchestration/graph.py --story "User can add items to shopping cart"

# Start the API server
uvicorn api.main:app --reload --port 8000

# Launch the monitoring dashboard
streamlit run ui/dashboard.py
```

### Run Tests

```bash
pytest tests/ -v
```

## QA Angle

This project models how a high-performing QA team actually works — not as a monolithic process, but as a collaboration between specialists who each contribute their expertise:

- **Mirrors Real Team Dynamics** — The Planner thinks like a QA lead scoping work, the Generator is your senior tester writing cases, the Reviewer is the peer who catches gaps, the Executor is your automation engineer, and the Reporter is the person who makes sense of results for stakeholders. Each agent has focused expertise rather than being a generalist.
- **Agent Handoff as Process Discipline** — In real QA, work products flow through defined stages: plan, generate, review, execute, report. The LangGraph state machine enforces this discipline programmatically, ensuring no step is skipped and each agent receives the context it needs.
- **Reviewer-Generator Loop** — The Reviewer can send test cases back to the Generator for revision, creating an iterative refinement cycle that mimics real peer review. This catches ambiguity, missing edge cases, and unclear expected results before execution.
- **Human-in-the-Loop Checkpoints** — The supervisor supports configurable pause points where a human tester can review and approve before proceeding, maintaining human oversight over AI-generated QA work.
- **Execution Evidence** — The Executor does not just report pass/fail; it captures screenshots, network logs, and console output as evidence — the same artifacts a manual tester would attach to a test run.

This is the architecture pattern used in production AI QA systems. Understanding multi-agent orchestration positions you to build and evaluate enterprise-grade AI testing platforms.

---

## Learning Companion Structure

This project now also includes a teaching-friendly folder structure for guided study:

```text
Project_22_MultiAgent_Test_Orchestrator/
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
