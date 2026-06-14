# User Research Synthesis

## Method

This is a public-signal research synthesis, not private user interviews. Inputs included:

- Dify GitHub repository, issues, and discussions.
- Dify docs and release discussions.
- Dify forum posts.
- Product review sites and public community threads.
- Competitor public documentation and positioning.

## Repositories Reviewed

| Repository | Purpose |
|---|---|
| [langgenius/dify](https://github.com/langgenius/dify) | Target project |
| [langflow-ai/langflow](https://github.com/langflow-ai/langflow) | Visual AI builder competitor |
| [FlowiseAI/Flowise](https://github.com/FlowiseAI/Flowise) | Visual AI workflow competitor |
| [open-webui/open-webui](https://github.com/open-webui/open-webui) | AI interface and internal portal competitor |
| [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph) | Code-first agent runtime competitor |
| [n8n-io/n8n](https://github.com/n8n-io/n8n) | Automation and AI workflow competitor |
| [CopilotKit/CopilotKit](https://github.com/copilotkit/copilotkit) | Agentic frontend competitor |

## Issues and Discussions Reviewed

| Link | Signal |
|---|---|
| [Discussion #11348](https://github.com/langgenius/dify/discussions/11348) | Workflow plus knowledge base execution chain returned empty retrieval despite recall test working. |
| [Discussion #3778](https://github.com/langgenius/dify/discussions/3778) | Request to export logs from logs and annotations page for analysis. |
| [Discussion #27670](https://github.com/langgenius/dify/discussions/27670) | Release discussion introducing trigger functionality and event-driven workflow direction. |
| [Discussion #20640](https://github.com/langgenius/dify/discussions/20640) | Dynamic knowledge base selection and multi-dataset retrieval needs. |
| [Issue #34315](https://github.com/langgenius/dify/issues/34315) | Workflow usage should track input/output tokens separately. |
| [Issue #31886](https://github.com/langgenius/dify/issues/31886) | Request to filter chatflow logs for ratings. |
| [Issue #36099](https://github.com/langgenius/dify/issues/36099) | Langfuse integration only recording inputs/outputs, not internal nodes. |
| [Issue #31253](https://github.com/langgenius/dify/issues/31253) | Workflow API streaming events sometimes missing end events. |
| [Issue #28484](https://github.com/langgenius/dify/issues/28484) | Workflow-as-tool disabled state confusion. |
| [Issue #37066](https://github.com/langgenius/dify/issues/37066) | Knowledge storage accounting confusion after deletion. |

## Feedback Clusters

| Cluster | Pattern |
|---|---|
| Adoption problems | Users understand the promise, but need clearer production paths and examples. |
| Onboarding friction | Self-hosting, model credentials, plugin setup, and version-specific behavior create friction. |
| UX pain points | Disabled controls, variables, ratings, and logs can be hard to interpret. |
| Missing features | Evals, log export, cost breakdown, RAG diagnostics, and scheduling recur. |
| Enterprise blockers | Auditability, quality proof, retention, permissions, and release governance matter. |
| Scalability concerns | Streaming, queue behavior, storage accounting, and upgrade reliability affect production trust. |
| Analytics concerns | Logs exist, but users need better filtering, export, and actionable quality/cost views. |
| Evaluation concerns | Teams lack native regression tests and comparison workflows. |

## Top 25 Pain Points

Scores: Severity 1-5, Frequency 1-5, Opportunity = relative strategic opportunity score.

| Rank | Pain point | Severity | Frequency | Opportunity |
|---:|---|---:|---:|---:|
| 1 | No unified native eval/regression workflow | 5 | 4 | 40 |
| 2 | Cost and token analytics too coarse | 5 | 4 | 38 |
| 3 | Node-level trace/debugging is fragmented | 5 | 4 | 36 |
| 4 | RAG answer quality is hard to measure | 5 | 4 | 36 |
| 5 | Feedback/ratings are hard to triage | 4 | 4 | 29 |
| 6 | Enterprise teams lack audit-ready quality evidence | 5 | 3 | 28 |
| 7 | Runtime event reliability affects embedded apps | 5 | 3 | 26 |
| 8 | Documentation can lag product behavior | 4 | 4 | 25 |
| 9 | Workflow variables and hidden inputs can confuse users | 4 | 3 | 23 |
| 10 | Connector/plugin limitations hurt trust | 4 | 3 | 22 |
| 11 | Automation triggers and batch jobs trail n8n | 4 | 3 | 22 |
| 12 | App versioning and release gates are not prominent | 4 | 3 | 22 |
| 13 | Collaboration review/approval is limited | 4 | 3 | 21 |
| 14 | Knowledge storage accounting can be confusing | 4 | 3 | 20 |
| 15 | Observability integrations can miss expected internals | 4 | 3 | 20 |
| 16 | Users need clearer model/provider cost guidance | 3 | 4 | 19 |
| 17 | Marketplace/plugin quality varies | 3 | 3 | 17 |
| 18 | Dev/stage/prod workflows are not first-class | 4 | 2 | 16 |
| 19 | Granular permissions need expansion | 4 | 2 | 16 |
| 20 | Frontend app customization can limit delivery | 3 | 3 | 15 |
| 21 | More production templates are needed | 3 | 3 | 14 |
| 22 | Self-host upgrades require operational care | 4 | 2 | 14 |
| 23 | Error messages and disabled controls need clarity | 3 | 3 | 14 |
| 24 | Data source sync and private repo ingestion gaps appear | 4 | 2 | 14 |
| 25 | Community support and education need scaling | 3 | 3 | 13 |

## User Research Conclusion

The research converges on one core problem: Dify users need a production improvement loop. They can build, but they need better ways to measure quality, understand failures, control cost, and justify scaling.

