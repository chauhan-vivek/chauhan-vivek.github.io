---
layout: post
title: "Docstrings in the Age of Agents"
date: 2026-04-30 00:09:00 -0400
background: '/img/posts/docstrings-in-age-of-ai.png'
---

Docstrings used to be simple: write something helpful so the next developer doesn’t accidentally break production at 2 a.m. They were equal parts documentation and polite warning.

That world has changed.

Today, your docstrings are no longer read only by humans. They are consumed—parsed, compressed, and sometimes misinterpreted—by AI agents that use them to decide what your code *means* and *how* to use it.

And unlike your teammates, these agents don’t appreciate nuance. They appreciate signal.

---

## The Problem: When Good Documentation Goes Bad

Modern docstring styles—NumPy, reST, Google—were designed for clarity and completeness. They optimize for humans who want context, examples, and reasoning.

Agentic systems operate differently.

They work within strict context limits, where every token competes with actual reasoning. This leads to two subtle but important issues.

**Context rot** happens when too much descriptive text dilutes the key instructions. The agent sees everything, but prioritizes nothing.

**Token bloat** is the cost of verbosity. Every extra sentence increases latency and reduces the space available for decision-making.

What reads as “helpful detail” to a human often becomes “unnecessary noise” to an agent.

---

## Agentic Docstrings: Precision Over Prose

Agentic docstrings are written with one goal: make the function unambiguous for a machine.

They are concise, structured, and intentionally boring.

```python
def fetch_user(user_id: str) -> dict:
    """
    Retrieve user by ID.

    Args:
        user_id: Unique identifier.

    Returns:
        User object.

    Raises:
        NotFoundError: If user does not exist.
    """
````

These docstrings work well because they:

* Minimize ambiguity and reduce hallucination risk
* Map cleanly to structured tool schemas
* Keep the context window focused and efficient

But the tradeoff is immediate.

They assume the reader already understands the system. There’s no explanation of *why* this function exists, how it fits into a workflow, or what edge cases matter in practice.

For a human, this is documentation that answers questions only after you already know what to ask.

---

## Human-Readable Docstrings: Clarity With a Cost

Traditional docstrings optimize for understanding. They explain intent, provide examples, and capture the reasoning behind design decisions.

```python
def fetch_user(user_id: str) -> dict:
    """
    Fetch a user from the primary datastore using their unique identifier.

    This function is used in authentication and profile rendering flows.
    It ensures that the returned object is fully populated with user
    attributes required downstream.

    Args:
        user_id (str): Unique user identifier.

    Returns:
        dict: User attributes including name, email, and preferences.

    Raises:
        NotFoundError: If no user exists with the given ID.
    """
```

For humans, this is ideal. It accelerates onboarding, supports debugging, and preserves intent.

For agents, it introduces friction.

The additional context can:

* Obscure the core instruction
* Increase processing time
* Introduce ambiguity through natural language

The model doesn’t always distinguish between what is essential and what is explanatory. It treats both as input to reason over.

---

## The Real Issue: One Docstring, Two Audiences

The underlying problem isn’t which style is better. It’s that they are solving different problems.

Humans need context and reasoning.
Agents need constraints and clarity.

Trying to serve both in a single docstring creates a compromise that satisfies neither.

---

## A Better Approach: Layered Docstrings

Instead of choosing between human-friendly and agent-friendly styles, treat them as separate layers.

### 1. Agent-Facing Layer

Provide a minimal, structured description that is explicitly designed for tool usage.

```python
@tool(description="Fetch user by ID. Error if not found.")
def fetch_user(user_id: str) -> dict:
    ...
```

This layer should be:

* Short and unambiguous
* Focused on inputs, outputs, and constraints
* Free of narrative or background context

It acts as the interface contract for the agent.

---

### 2. Human-Facing Layer

Maintain detailed documentation for developers, but keep it outside the agent’s prompt path.

```python
def fetch_user(user_id: str) -> dict:
    """
    Detailed documentation explaining usage, intent, and edge cases.
    """
```

This layer supports:

* Maintainability
* Knowledge transfer
* System understanding over time

It remains essential, just not always exposed to the agent.

---

### 3. Documentation on Demand

For more complex systems, allow the agent to retrieve deeper context only when necessary.

```python
def get_technical_manual(topic: str) -> str:
    """Return detailed documentation for a given topic."""
```

This pattern keeps the default context lean while still enabling deeper reasoning when required.

Instead of overwhelming the agent upfront, you give it the ability to ask for help.

---

## Final Take

Docstrings are no longer just documentation—they are part of your system design.

Writing them effectively now requires thinking about:

* Who is consuming this information
* When they need it
* How much they can handle at once

The goal isn’t to replace human-readable documentation with machine-friendly instructions. It’s to separate concerns cleanly.

Design for the agent’s efficiency.
Preserve the human’s understanding.

And avoid making either work harder than they need to.

```
```
