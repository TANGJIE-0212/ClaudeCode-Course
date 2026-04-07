# AI Agent PM Lens

When explaining a codebase to AI agent PMs, cover five lenses:

## 1. Capability Design

- What abilities are first-class?
- Which capabilities are user-triggered versus model-triggered?

## 2. Trust And Control

- Where are permissions checked?
- What actions need explicit confirmation?
- How does the product remain legible when autonomous behavior increases?

## 3. Reliability And Recovery

- How does the system handle partial failure?
- What retry, compaction, or fallback mechanisms exist?
- What user-visible recovery patterns emerge from the code?

## 4. Operating Economics

- Where do latency and token costs accumulate?
- Which startup or execution paths are optimized?
- Which abstractions improve reuse versus create overhead?

## 5. Extensibility

- How do teams add new commands, skills, plugins, and tools?
- What abstractions define the platform boundary?
- What should be governed centrally versus left to teams?
