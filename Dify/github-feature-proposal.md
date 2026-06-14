# GitHub Feature Proposal

## Title

Proposal: Dify Quality Hub for native evals, traces, feedback triage, and cost analytics

## Summary

I propose adding **Dify Quality Hub**, a native workflow for evaluating, tracing, comparing, and optimizing Dify apps in production.

The first version would help Dify users:

- Turn production logs and feedback into eval datasets.
- Compare draft vs published app versions.
- Inspect node-level workflow traces.
- Track input/output tokens and cost by node/model/provider.
- Add optional quality checks before publishing.

## Problem

Dify makes it fast to build AI workflows, agents, and RAG applications. As users move into production, they need a repeatable way to answer:

- Did this app change improve quality?
- Why did this run fail?
- Was the issue retrieval, prompt, model, tool, or workflow logic?
- Which node or provider is driving cost?
- Is this version safe to publish?

Today, Dify has logs, dashboard metrics, annotations, and tracing integrations, but the native quality loop is fragmented.

## Evidence

- Dify logs show conversation timeline, message details, performance data, token usage, and user feedback ([Logs docs](https://docs.dify.ai/en/use-dify/monitor/logs)).
- The dashboard monitors performance, cost, and engagement ([Dashboard docs](https://docs.dify.ai/en/use-dify/monitor/analysis)).
- Dify supports tracing integrations such as Phoenix, LangSmith, Opik, Arize, and Weave ([Phoenix integration docs](https://docs.dify.ai/en/use-dify/monitor/integrations/integrate-phoenix)).
- Community requests point to execution-chain visibility, log export, rating filters, and workflow token breakdown ([Discussion #11348](https://github.com/langgenius/dify/discussions/11348), [Discussion #3778](https://github.com/langgenius/dify/discussions/3778), [Issue #34315](https://github.com/langgenius/dify/issues/34315)).

## Proposed MVP

- Add feedback filters in logs for rating/comment status.
- Add log export to CSV/JSONL.
- Track workflow input and output tokens separately where provider data supports it.
- Add eval datasets from logs, manual examples, and CSV/JSONL.
- Add eval runs against draft and published versions.
- Add a node-level trace drawer with inputs, outputs, status, latency, tokens, cost, and errors.

## Out of Scope

- Replacing external observability tools.
- Full release environment management.
- Automated prompt rewriting.
- Enterprise-only governance in the first PR.

## Suggested First PRs

1. Add feedback rating/comment filters to logs.
2. Add log export for CSV/JSONL.
3. Add workflow input/output token breakdown.
4. Add eval dataset data model behind a feature flag.
5. Add minimal eval runner for deterministic checks.

## Community Question

How do Dify users currently decide whether a workflow, chatflow, or RAG app is ready to publish? Would a log-to-eval and draft-vs-published comparison workflow solve a real production pain?

