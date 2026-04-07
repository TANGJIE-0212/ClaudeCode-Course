---
name: codebase-to-course-pm
description: 'Turn any codebase into an interactive PM-oriented HTML course that explains architecture, runtime loops, permissions, recovery, and product implications. Use when AI agent PMs, platform PMs, operators, or leadership need a teachable walkthrough of how a codebase actually works and what it implies for capability design, trust, metrics, and extensibility. Trigger on phrases like turn this codebase into a PM course, explain this agent architecture for PMs, make an AI agent PM training from this repo, or teach this code as a product system.'
argument-hint: '[audience and focus, for example: AI agent PM workshop on runtime and guardrails]'
user-invocable: true
disable-model-invocation: false
---

# Codebase To Course PM

This is a PM-focused fork of the codebase-to-course workflow.

## Audience

Default learner:

- AI agent PM
- platform PM
- technical program lead
- operator working with agent systems

Assume the learner is smart and product-literate, but may not be a full-time engineer.

## Goal

Produce a course that teaches not only how the code works, but why the architecture matters for product design.

Every module should help the learner answer at least one of these questions:

- What user problem is this subsystem solving?
- What PM lever does this create?
- What new risk or failure mode does it introduce?
- What metric or operating signal should a PM watch?
- What extension surface does this expose?

## Output Shape

Prefer a self-contained HTML artifact unless the user explicitly asks for a multi-file build.

The HTML should feel course-like, not like a dry report. Use:

- module-based scroll structure
- strong visual hierarchy
- at least one code-to-plain-English translation block per major module
- at least one quiz or scenario challenge per major module
- at least one architecture or flow visualization across the course

## Process

### Phase 1: Understand The Codebase

Read the README, entrypoints, orchestration files, and runtime control flow first.

Prioritize files that reveal:

- startup and initialization
- context assembly
- model query loop
- tool or action orchestration
- permissions and policy
- recovery and state management
- extension surfaces like skills, plugins, bridge, or APIs

### Phase 2: Design The Teaching Arc

Structure the course into 4-6 modules.

Recommended PM arc:

1. What the product really is
2. The runtime loop
3. Capability packaging layers
4. Trust, permissions, and recovery
5. Metrics, costs, and extensibility
6. PM exercises or design challenges

### Phase 3: Build For PM Understanding

For each module:

- anchor explanations in real files
- translate code into product meaning
- use short, dense screens instead of long essays
- include one practical PM takeaway
- include one decision framework, scenario, or quiz

## Mandatory Teaching Elements

- Real code snippets copied exactly from the codebase
- Plain-language explanation next to the code
- One runtime flow or system map
- One PM scenario quiz
- One section comparing commands, tools, skills, and plugins if relevant

## PM-Specific Rules

- Do not stop at implementation detail; always translate to product implications.
- Do not explain abstractions in isolation; explain what decision they enable.
- Do not write like a professor; write like an operator who understands both product and systems.
- Do not overuse AI buzzwords. Prefer concrete descriptions of loops, policies, and state.

## References

- Use [references/pm-course-template.md](./references/pm-course-template.md) for the default module arc.
