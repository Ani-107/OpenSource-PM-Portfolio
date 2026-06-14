# Open Source Contribution Plan

## Contribution Strategy

The best contribution path is incremental. Dify Quality Hub is a large product direction, but it should enter the ecosystem through small PRs and an RFC that maintainers can review without committing to the entire vision at once.

## Step 1: Open Discussion

Start a GitHub discussion titled:

**RFC: Native Quality Hub for evals, traces, feedback triage, and cost analytics**

Goals:

- Validate demand.
- Ask maintainers about architecture.
- Identify existing internal models for logs, workflow run data, annotations, and tracing.
- Find the smallest acceptable first PR.

## Step 2: Open Issue

Open a focused feature issue:

**Feature: Filter logs by feedback rating/comment status**

Rationale:

- Directly tied to user pain.
- Low implementation risk.
- Useful even if the full Quality Hub is not accepted.
- Creates the first step toward feedback triage.

## Step 3: First PR

Suggested first PR:

- Add rating and comment filters to chatflow/application logs.
- Add tests for filter behavior.
- Update docs with examples.

## Step 4: Second PR

Suggested second PR:

- Add CSV/JSONL export for logs or selected feedback.
- Include fields useful for eval datasets: input, output, rating, comment, timestamp, app version, model/provider, token usage.

## Step 5: Third PR

Suggested third PR:

- Track input and output tokens separately for workflow usage where provider metadata supports it.
- Include graceful fallback for providers that do not return full metadata.

## Step 6: RFC Iteration

Use maintainer feedback to refine:

- Eval dataset schema.
- Trace storage policy.
- UI placement.
- Community vs enterprise packaging.
- Migration and retention constraints.

## Suggested Pull Requests

| PR | Title | Value |
|---|---|---|
| PR 1 | Add log filters for feedback rating and comments | Improves monitoring usability |
| PR 2 | Export logs as CSV/JSONL | Enables offline analysis and eval datasets |
| PR 3 | Track workflow input/output tokens separately | Improves cost analytics |
| PR 4 | Add eval dataset model and import | Creates foundation for Quality Hub |
| PR 5 | Add draft vs published eval comparison | Enables release decisions |

## Suggested GitHub Issues

- Feature: Create eval datasets from production logs.
- Feature: Add node-level trace view for workflows.
- Feature: Add RAG retrieval diagnostics to workflow traces.
- Feature: Add cost breakdown by workflow node and provider.
- Feature: Add optional release gates based on eval pass thresholds.

## Suggested Discussions

- How should Dify users evaluate workflow quality before publishing?
- What trace data should Dify store by default in self-hosted deployments?
- Which eval types should be native vs plugin-based?
- Should release gates belong in Community Edition, Cloud, or Enterprise?

## Success Criteria for Contribution

- Maintainers agree on MVP boundary.
- At least one low-risk PR is accepted or shaped by maintainer feedback.
- Community validates the quality/eval problem.
- The RFC becomes a roadmap reference even if implemented in phases.

