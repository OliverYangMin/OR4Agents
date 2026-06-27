# A Taxonomy of Decision Problems in AI Agents

> Every decision inside an AI Agent can be viewed as an optimization problem.

## Motivation

Modern AI agents continuously make decisions:

* Which tool should I call?
* Which memories should I retrieve?
* Which task should I execute next?
* Should I continue reasoning?
* Should I ask another agent for help?

Today, most of these decisions are made by prompting an LLM.

OR4Agents takes a different perspective:

> Instead of letting an LLM decide everything, we formulate each decision as an Operations Research (OR) problem.

This document provides a taxonomy of decision problems in AI Agents and their corresponding OR formulations.

---

# 1. Planning

## Decision

Determine the next action or action sequence to accomplish a task.

Examples:

* Search first or use Python?
* Read documentation before coding?
* Finish now or gather more evidence?

---

## Constraints

* Action dependency
* Available tools
* Time budget
* Token budget
* Environment state

---

## Objective

* Maximize task success
* Minimize execution cost
* Minimize latency
* Minimize number of actions

---

## Candidate OR Models

* AI Planning
* Shortest Path
* Dynamic Programming
* Markov Decision Process (MDP)
* A*
* AND-OR Search

---

# 2. Tool Selection

## Decision

Select which tools should be invoked.

Examples:

* Search
* Browser
* Python
* SQL
* Calculator
* Memory

---

## Constraints

* Token budget
* API cost
* Tool availability
* Rate limits
* Permission constraints

---

## Objective

* Maximize answer quality
* Minimize tool cost
* Minimize latency
* Minimize unnecessary tool calls

---

## Candidate OR Models

* 0-1 Knapsack
* Set Cover
* Budgeted Maximum Coverage
* Multi-objective Integer Programming

---

# 3. Memory Retrieval

## Decision

Select which memories should be inserted into the context.

---

## Constraints

* Context window
* Token limit
* Retrieval latency

---

## Objective

* Maximize relevance
* Maximize information coverage
* Minimize redundancy

---

## Candidate OR Models

* Maximum Coverage
* Facility Location
* Submodular Optimization
* Knapsack

---

# 4. Context Compression

## Decision

Compress long contexts while preserving useful information.

---

## Constraints

* Maximum context size
* Token budget
* Information preservation

---

## Objective

* Preserve critical information
* Remove redundancy
* Minimize information loss

---

## Candidate OR Models

* Resource Allocation
* Information Optimization
* Budget Allocation
* Compression Optimization

---

# 5. Workflow Scheduling

## Decision

Determine execution order and parallelism of workflow nodes.

---

## Constraints

* Dependency graph (DAG)
* Resource limits
* Tool availability
* Maximum concurrency

---

## Objective

* Minimize makespan
* Maximize throughput
* Reduce idle resources

---

## Candidate OR Models

* Project Scheduling
* RCPSP
* Job Shop Scheduling
* DAG Scheduling
* Critical Path Method

---

# 6. Multi-Agent Task Allocation

## Decision

Assign tasks to different agents.

Examples:

* Research Agent
* Coding Agent
* Review Agent
* Planning Agent

---

## Constraints

* Agent capability
* Agent workload
* Communication overhead
* Resource limits

---

## Objective

* Maximize overall productivity
* Balance workload
* Minimize communication cost

---

## Candidate OR Models

* Assignment Problem
* Generalized Assignment Problem
* Network Flow
* Multi-Agent Scheduling

---

# 7. Token Budget Allocation

## Decision

Allocate limited token budget across different modules.

Examples:

* Memory
* Reasoning
* Tool outputs
* Final response

---

## Constraints

* Context window
* Model limits
* API budget

---

## Objective

* Maximize overall utility
* Minimize token usage

---

## Candidate OR Models

* Resource Allocation
* Linear Programming
* Knapsack
* Multi-objective Optimization

---

# 8. Reasoning Budget

## Decision

Determine how much reasoning should be performed.

Examples:

* Stop now
* Continue thinking
* Explore another solution

---

## Constraints

* Time limit
* Token budget
* Compute budget

---

## Objective

* Maximize answer quality
* Minimize reasoning cost

---

## Candidate OR Models

* Optimal Stopping
* Multi-Armed Bandit
* Sequential Decision Making

---

# 9. Reflection Decision

## Decision

Determine whether reflection or self-correction is worthwhile.

---

## Constraints

* Remaining budget
* Remaining time
* Confidence score

---

## Objective

* Improve final answer
* Avoid unnecessary reflection

---

## Candidate OR Models

* Optimal Stopping
* Value of Information
* Cost-Benefit Optimization

---

# 10. Search Strategy

## Decision

Determine how the search process should proceed.

Examples:

* Search depth
* Beam width
* Branch expansion
* Early stopping

---

## Constraints

* Search budget
* Memory
* Time

---

## Objective

* Maximize search quality
* Minimize search cost

---

## Candidate OR Models

* A*
* Branch and Bound
* Beam Search
* Monte Carlo Tree Search
* Best-First Search

---

# Summary

| Agent Decision              | Decision Variable             | Candidate OR Models                       |
| --------------------------- | ----------------------------- | ----------------------------------------- |
| Planning                    | Next action / action sequence | MDP, Dynamic Programming, A*, AI Planning |
| Tool Selection              | Tool subset                   | Knapsack, Set Cover                       |
| Memory Retrieval            | Memory subset                 | Maximum Coverage, Facility Location       |
| Context Compression         | Compression strategy          | Resource Allocation                       |
| Workflow Scheduling         | Execution schedule            | RCPSP, Job Shop, DAG Scheduling           |
| Multi-Agent Task Allocation | Agent-task assignment         | Assignment, Network Flow                  |
| Token Budget Allocation     | Token allocation              | LP, Knapsack                              |
| Reasoning Budget            | Reasoning depth               | Optimal Stopping, Bandit                  |
| Reflection Decision         | Reflect or stop               | Value of Information, Optimal Stopping    |
| Search Strategy             | Search policy                 | A*, Branch & Bound, MCTS                  |

---

# Outlook

This taxonomy is only the first step.

Future versions of OR4Agents will investigate:

* Formal mathematical formulations
* Exact optimization algorithms
* Heuristic methods
* Learning-augmented optimization
* Benchmark datasets
* Runtime architectures

Our long-term vision is to build an Optimization Runtime for AI Agents, where every important decision can be analyzed, optimized, and explained using Operations Research.

