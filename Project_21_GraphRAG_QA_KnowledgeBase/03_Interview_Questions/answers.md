# Graph RAG QA Knowledge Base: Interview Answer Guide

## Question 1

**What problem does Graph RAG solve that standard vector RAG cannot?**

### Expected Discussion Points
- It captures explicit relationships between entities instead of only semantic similarity.
- That enables multi-hop reasoning such as coverage and dependency analysis.
- It is especially useful where structure matters as much as text content.
- QA traceability is a strong example of this advantage.

## Question 2

**How would you model QA assets such as bugs, modules, and tests in Neo4j?**

### Expected Discussion Points
- Represent each as a node type with stable identifiers and useful metadata.
- Use edges such as covers, affects, linked_to, or validates to express relationships.
- Keep the schema simple enough to query and maintain.
- Design properties that support filtering, impact analysis, and traceability.

## Question 3

**What is multi-hop reasoning, and why is it valuable in change-impact analysis?**

### Expected Discussion Points
- It means following relationships across more than one edge in the graph.
- A code or module change may affect a feature, which affects tests, which links to bugs.
- This makes hidden dependencies visible.
- That visibility improves release confidence and regression planning.

## Question 4

**How would you validate the correctness of entity and relationship extraction?**

### Expected Discussion Points
- Use sampled human review and benchmark documents.
- Measure precision and recall for important entity types and links.
- Inspect high-impact relationship errors carefully.
- Track drift after prompt or model changes in the extraction pipeline.

## Question 5

**When would you combine graph retrieval with vector search?**

### Expected Discussion Points
- When you need both explicit relationships and semantic document evidence.
- Graph answers can explain structure; vector search can recover rich text context.
- Hybrid retrieval is strong for QA questions that mix traceability and narrative details.
- The combined system should explain which source contributed what.

## Question 6

**How would you explain Graph RAG to a senior QA engineer without graph-database experience?**

### Expected Discussion Points
- Describe it as a smarter traceability layer on top of QA knowledge.
- Instead of only finding similar text, it follows connected facts.
- It answers impact and coverage questions more naturally.
- The graph simply stores how QA artifacts relate to each other.
