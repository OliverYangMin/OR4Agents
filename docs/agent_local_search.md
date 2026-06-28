# Local Search for Agent  



Paradigm

## Motivation

Unlike deep learning, AI Agent optimization is inherently **non-differentiable**.

Many decision variables are discrete.

Examples include

- Foundation Model
- Prompt
- Tool Set
- Memory Strategy
- Workflow
- Planning Strategy
- Reflection Strategy

These decisions cannot be optimized through gradient descent.

Instead, OR4Agents formulates Agent Optimization as an iterative local search process.

---

## Basic Framework

Starting from an initial Agent configuration,

the optimizer repeatedly searches for a better neighboring solution.

```text
Current Solution

↓

Generate Neighborhood

↓

Feasibility Test

↓

Evaluate

↓

Acceptance Rule

↓

Update Current Solution

↓

Repeat
```

The optimization terminates when no better solution can be found or the search budget is exhausted.

---

## Step 1. Current Solution

The current solution is a complete Agent configuration.

```text
Current Solution

Model = GPT-5

Prompt = Prompt A

Tools = {Search, Python}

Workflow = Sequential

Memory = Top-5
```

---

## Step 2. Neighborhood Generation

Generate neighboring solutions by modifying one or more decision variables.

Examples

```text
Replace Prompt

Replace Model

Add Tool

Remove Tool

Replace Workflow

Change Memory Strategy

Enable Reflection

Disable Reflection
```

Neighborhood Design is one of the core research topics of OR4Agents.

---

## Step 3. Feasibility Test

Before expensive evaluation,

invalid candidates should be discarded.

Examples

```text
Context Overflow

Token Budget Exceeded

Missing Required Tool

Invalid Workflow

Unsupported Configuration
```

Fast feasibility checking significantly reduces optimization cost.

---

## Step 4. Evaluation

Run the candidate Agent on benchmark tasks.

```text
Candidate Agent

↓

Benchmark

↓

Metrics

↓

Reward
```

Typical metrics include

- Task Success
- Accuracy
- Token Cost
- API Cost
- Latency
- Robustness

Evaluation is usually the computational bottleneck.

---

## Step 5. Acceptance Rule

After evaluation,

the optimizer decides whether to replace the current solution.

Possible strategies include

```text
First Improvement

Best Improvement

Hill Climbing

Simulated Annealing

Tabu Search

Adaptive Large Neighborhood Search (ALNS)
```

---

## Repeat Until Termination

The optimization repeats until

```text
Maximum Iterations

or

Maximum Time

or

No Better Neighbor

or

Target Performance Achieved
```

---

# Research Challenges

The Local Search paradigm naturally leads to several research problems.

## Neighborhood Design

How should neighboring Agent configurations be generated?

---

## Fast Evaluation

Can we estimate solution quality without fully executing every candidate?

Possible directions

- Surrogate Model
- Incremental Evaluation
- Multi-stage Evaluation
- Early Stopping

---

## Adaptive Neighborhood

Can LLMs generate promising neighborhoods instead of random modifications?

---

## Learning-Augmented Search

Instead of replacing optimization,

LLMs become intelligent neighborhood generators,

while Operations Research performs the search.

---

# OR4Agents Solver

The overall optimization framework becomes

```text
Agent Optimization Problem (AOP)

↓

Initialize Solution

↓

Local Search

    ├── Neighborhood Generation
    ├── Feasibility Test
    ├── Evaluation
    └── Acceptance Rule

↓

Optimized Agent
```

Unlike existing Agent optimization methods,

OR4Agents treats optimization as a continuous search process rather than a one-shot configuration process.

Every optimized Agent becomes the starting point for discovering an even better Agent.