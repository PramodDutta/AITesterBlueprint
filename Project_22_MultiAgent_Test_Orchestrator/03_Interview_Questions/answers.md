# Multi-Agent Test Orchestrator: Interview Answer Guide

## Question 1

**Why would a QA team use multiple agents instead of one larger agent?**

### Expected Discussion Points
- Specialized agents keep reasoning focused and outputs easier to review.
- They map well to actual QA roles and artifacts.
- They can improve modularity, reuse, and debugging.
- The tradeoff is orchestration complexity and state management.

## Question 2

**How does a supervisor or router improve multi-agent QA workflows?**

### Expected Discussion Points
- It decides which agent should act next based on state and rules.
- It prevents uncontrolled branching or arbitrary agent choice.
- It supports retries, escalation, and human-in-the-loop steps.
- That makes the workflow more deterministic and testable.

## Question 3

**What shared state should be preserved between planner, generator, and executor agents?**

### Expected Discussion Points
- Core context such as the feature scope, risks, and accepted test-plan assumptions.
- Artifacts like generated test cases and review feedback.
- Execution metadata and evidence references.
- State should be minimal, explicit, and versioned enough to debug.

## Question 4

**How would you test a multi-agent workflow for loops or repeated failure states?**

### Expected Discussion Points
- Simulate rejection or error paths deliberately.
- Add counters, stop conditions, and route assertions.
- Check that retries do not continue indefinitely.
- Review state transitions as you would review a workflow state machine.

## Question 5

**What evidence should the executor agent return to the reporter agent?**

### Expected Discussion Points
- Pass/fail status, logs, screenshots, network traces, and timing information are common.
- The evidence should support summary generation and defect triage.
- It should also preserve enough detail for debugging.
- A reporter without good evidence becomes a storytelling layer without trust.

## Question 6

**How would you explain LangGraph to an SDET who already understands test workflow state machines?**

### Expected Discussion Points
- Position it as an AI-aware state machine for agent workflows.
- Nodes represent agent steps and edges represent routing decisions.
- Shared state moves through the graph across turns and tools.
- The SDET mental model transfers well from workflow orchestration and test-state machines.
