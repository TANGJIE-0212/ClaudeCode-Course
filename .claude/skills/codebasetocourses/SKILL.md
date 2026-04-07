---
name: codebasetocourses
description: 'Turn a codebase into a teachable course, workshop, slide deck, or PM briefing. Use when explaining architecture, agent workflows, product implications, or turning engineering systems into training material for AI agent PMs, PMs, operators, or new teammates.'
argument-hint: '[audience and desired artifact, for example: AI agent PM slide deck on core architecture]'
user-invocable: true
disable-model-invocation: false
---

# Codebase To Courses

Convert a codebase into training material that a mixed audience can understand and reuse.

## When To Use

- Explain a complex repo to PMs, founders, operators, sales engineers, or new hires.
- Produce a course, workshop, brown-bag session, onboarding module, or HTML slide deck.
- Translate implementation details into product, platform, and operating-model implications.
- Teach people how an AI agent system works without forcing them to read source files first.

## Outputs This Skill Should Produce

- A short audience profile
- A teaching thesis: what learners should understand at the end
- A system explanation from top-level concepts down to runtime flow
- A capability map tied to real modules in the codebase
- Product and PM implications, not just engineering detail
- A reusable training asset such as HTML, Markdown, or both

## Procedure

1. Identify the learner.
   Use the requested audience if provided. Otherwise infer one of: engineers, AI agent PMs, operators, or new hires.

2. Build a system mental model first.
   Explain the product as a set of loops:
   - input loop
   - context assembly loop
   - model reasoning loop
   - tool execution loop
   - permission and governance loop
   - memory and recovery loop

3. Anchor every concept in real files.
   Start from repo entrypoints and control-flow files. Use file references instead of vague architecture claims.

4. Translate architecture into product meaning.
   For each major subsystem, answer:
   - what user problem it solves
   - what PM lever it creates
   - what failure mode it introduces
   - what metric or operating signal it implies

5. Produce layered teaching content.
   The artifact should be teachable in three passes:
   - executive summary
   - system walkthrough
   - operating lessons and exercises

6. End with decision frameworks.
   For AI agent PM audiences, include guidance on:
   - capability packaging
   - permissions and trust
   - evaluation and observability
   - cost and latency tradeoffs
   - agent UX and fallback design

## Teaching Frame For AI Agent PMs

Use this framing whenever the audience includes PMs:

- Agent = product surface plus runtime policy plus execution substrate.
- Tools are not features by themselves; tools are controllable affordances.
- Commands, skills, prompts, and tools are different packaging layers.
- Great agent products succeed on reliability, legibility, and recoverability, not only raw model quality.

## Artifact Guidance

- For HTML or slides, keep each section focused on one teaching claim.
- For Markdown courses, include learning goals, module breakdown, exercises, and discussion prompts.
- Prefer a concrete architecture diagram or flow narrative over generic AI buzzwords.
- Use plain language, but do not flatten away the true system mechanics.

## References

- Use the outline in [references/course-outline.md](./references/course-outline.md).
- Use the PM lens in [references/pm-lens.md](./references/pm-lens.md).
