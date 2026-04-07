# AI Agent PM Course: Claude Code Behind The Scenes

## Course Positioning

- Audience: AI Agent PMs, platform PMs, technical program leads, solution architects
- Duration: 90 minutes
- Format: 45 minutes lecture, 25 minutes walkthrough, 20 minutes workshop
- Outcome: learners can explain an agent runtime, map product requirements to runtime mechanisms, and propose safer capability extensions

## Learning Goals

By the end of the session, learners should be able to:

1. Explain why Claude Code is an agent runtime instead of a simple chat CLI.
2. Describe the role of startup orchestration, context assembly, query loop, tool execution, and permissions.
3. Distinguish commands, tools, skills, and plugins as different product packaging layers.
4. Derive PM implications around trust, observability, reliability, and extensibility.
5. Design one new agent capability with clear guardrails and success metrics.

## Teaching Narrative

### Module 1: What This Product Really Is

Core message: the product is a looped execution system.

- `src/main.tsx` shows that the system starts by assembling runtime dependencies, not by immediately calling the model.
- `src/context.ts` shows that context is intentionally constructed from repo state, date, and memory files.
- `src/query.ts` shows the real product loop: model output, tool calls, tool results, recovery, continuation.

### Module 2: The Five Files That Reveal The System

1. `src/main.tsx`
   The startup and orchestration layer. It loads settings, feature flags, auth state, plugins, commands, skills, and render flow.

2. `src/query.ts`
   The agent core. It implements streaming model turns, tool-use loops, token budgeting, auto compact, and recovery paths.

3. `src/tools.ts`
   The capability registry. It decides what the model can do in the current environment and under what feature gates.

4. `src/Tool.ts`
   The protocol layer. It defines the contract for tools, tool context, permission context, and execution-time dependencies.

5. `src/commands.ts`
   The explicit user entry layer. It exposes top-level command surfaces like review, memory, doctor, tasks, and config.

## Runtime Model For Learners

Teach the system as six loops:

1. Startup loop
   Optimize boot, load dependencies, and shape the environment.

2. Context loop
   Gather repo, memory, and session context before asking the model to act.

3. Reasoning loop
   Ask the model what to do next and parse streaming output.

4. Execution loop
   Run tools, collect results, and continue the turn until completion.

5. Governance loop
   Apply permissions, mode switches, and restrictions before risky actions execute.

6. Recovery loop
   Compact history, retry, summarize, or reduce output when the turn approaches failure.

## PM Lessons

### 1. Capability Packaging Matters

- A command is a user-facing task entry.
- A tool is a model-facing atomic ability.
- A skill is a reusable workflow pattern.
- A plugin or bridge is a platform extension surface.

PM lesson: do not solve every problem with one giant prompt. Choose the right packaging layer.

### 2. Trust Comes From Runtime Policy

PM lesson: user trust grows when the product clearly communicates:

- what the agent can do
- when it will ask
- what it already changed
- how to recover if it went off course

### 3. Reliability Is A Product Feature

`src/query.ts` makes this obvious. Auto compact, max-output recovery, stop hooks, and tool result handling all exist because failure is normal.

PM lesson: if your agent product does not handle partial failure well, it does not matter how strong the model is.

### 4. Observability Must Match The Runtime

Metrics to discuss with learners:

- task completion rate
- mean tool rounds per completed task
- permission prompt acceptance rate
- compact trigger rate
- recovery success rate
- average token cost per task
- startup latency

### 5. Platform Thinking Beats Feature Thinking

This repo has multiple extension seams: commands, tools, skills, plugins, MCP, bridge, and remote control.

PM lesson: once users want domain-specific behavior, product strategy shifts from shipping features to governing extension surfaces.

## Workshop Exercises

### Exercise 1: Map A Request To The Runtime

Prompt learners with: "Review this repository for security risks."

Ask them to map the request to:

1. startup needs
2. context needed
3. likely commands and tools
4. permission checkpoints
5. recovery or retry scenarios

### Exercise 2: Design A Safer Bash Experience

Ask learners to define:

1. which Bash actions can be auto-approved
2. which need explicit user confirmation
3. which should be blocked in enterprise mode
4. how the product should explain each decision

### Exercise 3: Propose A New Skill

Ask learners to create a skill proposal with:

1. target user
2. trigger phrases
3. required tools
4. expected output artifact
5. guardrails
6. success metrics

## Suggested Discussion Questions

1. Which part of this architecture is most directly responsible for user trust?
2. If you had to cut latency by 30 percent, where would you look first?
3. What should be configurable by users versus fixed by platform policy?
4. Which subsystem would you instrument first for enterprise reporting?
5. What new failure mode appears when you add more tools?

## Instructor Notes

- Keep reminding the room that AI agent PM work sits between model capability and operational reliability.
- When learners drift into prompt-only thinking, pull them back to runtime structure.
- Use real file names as anchors so the session stays concrete.
- End by asking learners to pitch one roadmap item that improves legibility, not just intelligence.