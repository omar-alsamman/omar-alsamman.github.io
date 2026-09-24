# Agentic AI Operations Orchestrator

**Portfolio case study** · Evidence snapshot: 2026-09-24

## Summary

I designed and coordinated a multi-workstream assistant system for migration, content production, career operations, personal administration, and travel. The system combines a master orchestration role, specialist workers, and a recurring execution operator. It routes work to canonical tools, records durable checkpoints, verifies writes, and preserves human approval for consequential external actions.

This is a case study of an AI-enabled operating workflow built with existing assistant products and connected services. It is **not** a custom agent runtime, benchmark, or claim that every workflow is production-ready.

## Problem

Long-running work was spread across conversations, documents, trackers, repositories, email, calendars, and recurring tasks. Model memory alone could not serve as a reliable source of truth. The design needed to preserve history, route work to the right owner, prevent duplicate actions, recover from blocked branches, and continue across devices.

## Architecture

- **Master Ops** owns architecture, routing, cross-workstream decisions, blocker handling, and verification.
- **Migration Ops** owns migration, Project, Notion, and control-panel cleanup.
- **Content Ops** owns AI Content Business research, packages, assets, and platform preparation.
- **Unified Ops** is the recurring execution layer for personal, content, and career branches. Its first run was only partially verified; branch completion is not assumed.
- **Canonical services** own mutable operational records, documents, code, communications, and events. Project control panels and a shared checkpoint provide durable routing and concise current state.

See [architecture](architecture.md) and the non-live [workflow example](examples/workflow-pattern.yaml).

## Design decisions

### One coordinator with bounded specialists

The master retains cross-workstream context and delegates substantial work to existing specialist workers. A unified recurring operator compresses overlapping scheduled execution, while legacy tasks remain until replacement branches pass real validation and receive owner approval for retirement.

### Canonical external state

Notion holds mutable operational state; Drive holds documents and assets; GitHub holds code; Gmail holds communications; Calendar holds events. Project control panels and checkpoint files route people and agents to those sources. This reduces reliance on conversational memory and allows read-back verification.

### Verify before advancing

A successful configuration is not treated as a successful workflow. The system distinguishes access, read, write, read-back, and real-run evidence. Reversible tests are cleaned up. A branch that is blocked does not stop unrelated executable work.

### Human approval boundaries

Public posts/profile edits, external messages, job submissions, payments, signatures, credentials, and identity/security actions require human approval. The operator may research, prepare, deduplicate, and stage work while preserving the approval boundary.

## Verified outcomes

- Claude source inventory through Phase 6 was completed and frozen; source material was preserved.
- Cloud migration preparation and destination control-panel material were completed.
- Live reads of Gmail, Drive, GitHub/private repository, and Calendar were verified. A temporary Calendar event was created, read, and deleted.
- Notion access and the canonical operational sources were verified; a single human-facing home uses linked views of existing databases.
- Phone-to-desktop continuity was reported as passed by the owner.
- The Unified Ops first run used existing state and showed no duplicate for one checked appointment/task. Full branch write-back and operator validation remain partial.

These are workflow and migration outcomes, not benchmark results. No performance, revenue, or time-savings figure is claimed because no measurement was collected.

## Current limitations

- The four intended Projects exist, but extra Projects remain; consolidation has been throttled and is incomplete.
- The Notion home loads its six linked views in order, with Today first, but current filtered rows were not visible in the captured view and the headings are not directly aligned with every table.
- Unified Ops has not passed every branch-specific real run with canonical write-back and deduplication.
- The canonical current resume file remains unresolved, so no resume changes are claimed.
- No custom Python agent runtime, durable workflow engine, evaluation harness, or tracing backend was implemented in this project.

## What I would build for production

I would express workflows as typed, versioned state machines, separate planning from side effects, make every mutation idempotent, and persist run state in a transactional store. Each tool would have scoped permissions and structured inputs/outputs. Risky actions would pause for an explicit approval record. I would add trace IDs, structured logs, retry budgets, dead-letter handling, deterministic evaluations, and end-to-end tests against sandbox accounts. I would instrument latency, cost, duplicate rate, completion rate, and human intervention rate before claiming operational improvement.

## Reusable method

1. Inventory sources and preserve original history.
2. Assign each workflow an owner, destination, and canonical source.
3. Define which actions can run automatically and which require approval.
4. Execute in bounded steps with duplicate checks and reversible tests.
5. Read back writes and record evidence, limitations, and the next checkpoint.
6. Retire old workflows only after replacements pass real runs and the owner approves.

## Scope and evidence

The live system uses commercial assistant and connector features, and remains partly in migration. Public artifacts intentionally omit live account identifiers, private links, tracker IDs, local paths, personal records, and source exports. Any illustrative configuration is synthetic and non-executable.

