# PRD: Dify Quality Hub

## Problem Statement

Dify users can build AI workflows quickly, but production teams lack a unified way to evaluate quality, debug runs, triage feedback, attribute cost, and prevent regressions before publishing changes. Existing monitoring and tracing integrations are valuable, but users need an in-product loop that turns production behavior into measurable product improvement.

## Personas

| Persona | Need |
|---|---|
| AI app builder | Know whether prompt, model, workflow, or RAG changes improve quality. |
| App operator | Find failed runs, negative feedback, and cost spikes quickly. |
| AI engineer | Inspect node inputs, outputs, latency, errors, retrieved chunks, and tokens. |
| RAG owner | Measure groundedness, citation quality, retrieval recall, and stale sources. |
| Enterprise admin | Prove release quality, audit decisions, and manage retention. |
| Finance/ops stakeholder | Understand cost by app, provider, model, user, and node. |

## Jobs To Be Done

- When I change a prompt or model, I want repeatable tests so I know whether to publish.
- When users give bad feedback, I want to reproduce the run and identify root cause.
- When a workflow has multiple model calls, I want cost and token breakdown by node.
- When an enterprise stakeholder asks whether an AI app is safe, I want eval history and audit evidence.
- When a RAG app gives a weak answer, I want to know whether retrieval, reranking, prompt synthesis, or the model caused it.

## User Stories

1. As a builder, I can create an eval dataset from logs, CSV/JSONL upload, or manual examples.
2. As a builder, I can run the same dataset against draft and published app versions.
3. As an operator, I can filter logs by feedback rating, comment, error, app version, model, user, and date.
4. As an engineer, I can open a workflow trace and inspect each node.
5. As a RAG owner, I can score citation presence, groundedness, and retrieval quality.
6. As an admin, I can require an eval pass threshold before publishing.
7. As a finance stakeholder, I can view cost by workspace, app, user, model, provider, node, and time range.

## MVP Scope

- Quality Hub navigation entry.
- Eval datasets from logs, CSV/JSONL, and manual examples.
- Eval runs against draft and published versions.
- Basic evaluator types: exact/contains, regex, JSON schema, LLM-as-judge, human rating, citation present.
- Feedback triage filters.
- Node-level trace view.
- Input/output token and cost breakdown where provider metadata supports it.
- Export API for eval runs and traces.

## Out of Scope

- Replacing Langfuse, Phoenix, Opik, Weave, or LangSmith.
- Full CI/CD environment management.
- Automated prompt rewriting without user approval.
- Proprietary benchmark marketplace.
- Full multi-environment release management in MVP.

## Functional Requirements

| Area | Requirement |
|---|---|
| Dataset management | Create, edit, tag, import, and export examples. |
| Eval execution | Run examples against app version and configuration. |
| Evaluators | Exact, regex, JSON schema, LLM judge, human, citation/groundedness. |
| Results | Pass/fail, score, latency, cost, tokens, regression delta. |
| Trace | Node graph timeline, inputs, outputs, errors, retrieved context. |
| Feedback | Filter logs and convert negative feedback into eval cases. |
| Cost | Provider/model/node/user/app breakdown. |
| Comparison | Compare draft vs published, model A vs model B, config A vs config B. |
| Governance | Optional quality thresholds for publishing. |
| API | Trigger eval, list suites, fetch results, export traces. |

## Non-Functional Requirements

- Must not expose secrets in traces.
- Must support configurable retention.
- Must support self-hosted deployments.
- Must degrade gracefully when providers do not return full token metadata.
- Must support async eval execution for large datasets.
- Must support redaction hooks before storing inputs and outputs.
- Must not materially slow production workflow execution.

## Acceptance Criteria

- A user can create an eval suite from at least three sources: logs, CSV/JSONL, manual.
- Results show pass rate, failed cases, latency, total cost, and token breakdown.
- A failed eval case links to its run trace.
- A trace shows node status, latency, inputs, outputs, error, retrieved chunks, and cost metadata.
- Logs can be filtered by rating/comment status.
- App comparison supports draft vs published.
- Core MVP works in self-hosted Community Edition.

## Wireframe: Evaluation Comparison

```text
+--------------------------------------------------------------------------------+
| Evaluation: Support FAQ Regression                                             |
+--------------------------------------------------------------------------------+
| Dataset: 124 cases   Evaluators: Correctness, Groundedness, Citation, JSON     |
| Baseline: Published v18     Candidate: Draft v19                               |
+--------------------------------------------------------------------------------+
| Metric              Baseline       Candidate       Delta        Status          |
| Pass rate           87.1%          92.7%           +5.6%        PASS            |
| Groundedness        81.4%          90.2%           +8.8%        PASS            |
| Citation present    94.0%          96.1%           +2.1%        PASS            |
| Avg latency         3.2s           3.8s            +0.6s        WARN            |
| Avg cost / run      $0.018         $0.021          +$0.003      WARN            |
+--------------------------------------------------------------------------------+
| Failed Cases                                                                  |
| [ ] Refund policy edge case       Retrieval missed current policy              |
| [ ] Warranty transfer             Answer correct, citation missing             |
| [ ] EU return window              Candidate hallucinated unsupported detail     |
+--------------------------------------------------------------------------------+
| [Open trace] [Add to dataset] [Approve publish] [Block release]                |
+--------------------------------------------------------------------------------+
```

## Wireframe: Run Trace

```text
+--------------------------------------------------------------------------------+
| Trace: run_8f39 / Support Agent / v19                                          |
+--------------------------------------------------------------------------------+
| Timeline: Start -> Classifier -> Knowledge Retrieval -> LLM -> HTTP -> Answer  |
+--------------------------------------------------------------------------------+
| Node                    Status   Latency   Tokens in/out   Cost     Notes       |
| Start                   OK       3ms       -               -        input vars  |
| Question Classifier     OK       620ms     421/18          $0.001   support     |
| Knowledge Retrieval     WARN     980ms     -               $0.000   low recall  |
| LLM Answer              FAIL     2.1s      2904/212        $0.014   unsupported |
+--------------------------------------------------------------------------------+
| Selected Node: Knowledge Retrieval                                             |
| Retrieved chunks, scores, source timestamps, and expected missing context       |
+--------------------------------------------------------------------------------+
| [Replay from node] [Create eval case] [Open knowledge doc] [Compare version]    |
+--------------------------------------------------------------------------------+
```

## Success Metrics

- 30 percent of active production workspaces create an eval suite within 90 days.
- 15 percent increase in 8-week retention for workspaces with published apps.
- 30 percent reduction in time from negative feedback to root cause.
- 95 percent of traces available within 5 seconds of run completion.
- Less than 5 percent overhead on default workflow execution.

## Risks and Tradeoffs

| Risk | Mitigation |
|---|---|
| LLM-as-judge false confidence | Make evaluator prompts transparent and support deterministic checks. |
| Trace storage cost | Configurable retention and payload redaction. |
| Provider metadata inconsistency | Show explicit "metadata unavailable" states. |
| Scope creep into full observability | Keep external integrations; focus native product loop. |
| Privacy concerns | Redaction hooks, role permissions, and retention policies. |

