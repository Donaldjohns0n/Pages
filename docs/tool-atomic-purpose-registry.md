# Tool Atomic Purpose Registry

## Overview
The Tool Atomic Purpose Registry provides a persistent, canonical reference for all tooling
available to Pages framework agents. It explains each tool's atomic purpose, prerequisites,
optimal usage patterns, and context alignment criteria so that agents can make deliberate,
justified selections before initiating work. The registry also anchors the live audit cycle,
tool awareness reminders, and utilization analytics that power ongoing optimization.

---

## Phase 1 – Comprehensive Tool Inventory & Documentation

### Tool Catalog
| Tool ID | Tool Name | Atomic Purpose | Prerequisites & Constraints | Optimal Use Cases |
|---------|-----------|----------------|-----------------------------|-------------------|
| context_extractor | Context Extractor | Mine prior conversations, Drive files, and project context to surface relevant artefacts before work begins. | Access to history stores; must run at session start and on context switches; requires read permissions for referenced repositories. | Session initialization, multi-task workflows requiring context transfer, validation of continuity for follow-up requests. |
| workflow_synthesizer | Workflow Synthesizer | Compose cohesive execution plans by combining outputs from multiple agents and coordinating hand-offs. | Requires latest context snapshot and active agent registry entries; should only be invoked after context_extractor confirms materials. | Multi-agent task planning, milestone reviews, dynamic re-planning during execution. |
| audit_critic | Audit Critic | Evaluate intermediate and final artefacts against quality gates, traceability standards, and protocol adherence. | Needs access to decision logs, tool usage rationales, and acceptance criteria; should not be bypassed before commits or milestones. | Pre-commit reviews, workflow milestone checkpoints, automated regression audits. |
| prompt_librarian | Prompt Librarian | Manage reusable meta-prompts, templates, and protocol updates stored in pinned directories. | Requires synchronized prompt library and template directory; depends on context_extractor for latest references. | Template retrieval, protocol evolution, onboarding new agents, ensuring prompt consistency. |
| slack_webhook | Slack Webhook | Publish status updates (READY, delegation, failures) to human oversight channels. | Requires configured webhook credentials and incident routing rules; should respect notification throttle policies. | Delegation announcements, escalation notices, completion signals, failure diagnostics. |
| shell_exec | Shell Exec | Execute approved local scripts, run tests, and scaffold project assets when direct execution is authorized. | Limited to Codex or fallback routing; must validate direct-execution gate is open and sandbox safety checks pass. | Automated test execution, repository scaffolding, maintenance scripts, continuous integration hooks. |
| container.make_pr | PR Submission Tool | Publish the composed pull request once all work is committed and validated. | Only after repository state is clean and tests pass; prohibited if no changes exist. | Final delivery of code/documentation updates to remote repository. |
| container.new_session / container.feed_chars | Container Shell Interface | Provide interactive command execution within the workspace for inspection, editing, and automation. | Requires adherence to repo safety policies (no destructive commands without safeguards); commands must be awaited until completion. | File inspection, editing via heredoc, running scripts, invoking tests. |
| browser_container.run_playwright_script | Browser Automation Interface | Capture UI state and screenshots via Playwright automation when front-end changes require visual validation. | Requires running service bound to forwarded port; only when browser container is available. | End-to-end UI validation, screenshot capture for documentation, interactive workflow demos. |

### Tool Necessity Assessment Criteria
1. **Alignment with Atomic Purpose** – Confirm the intended action maps directly to the tool's atomic scope.
2. **Context Adequacy** – Verify that prerequisite context artefacts are available and current.
3. **Outcome Criticality** – Evaluate whether the task outcome requires the tool's unique capability.
4. **Risk Surface** – Assess security, stability, and audit implications of invoking the tool.
5. **Redundancy Check** – Determine if existing outputs already satisfy the need without additional tool usage.
6. **Resource Efficiency** – Compare effort and system cost versus expected value.

### Decision Matrix (Simplified)
| Trigger Condition | Recommended Tool | Decision Gate | Secondary Options |
|-------------------|------------------|---------------|-------------------|
| Session start or context switch | context_extractor | Confirm context freshness and access scope | prompt_librarian for template sync |
| Multi-agent plan synthesis | workflow_synthesizer | Ensure registry entries are current | audit_critic for validation |
| Pre-commit review required | audit_critic | Verify traceability logs are complete | workflow_synthesizer for remediation plan |
| Template or protocol lookup | prompt_librarian | Check template version compatibility | context_extractor to gather references |
| Human oversight notification | slack_webhook | Confirm webhook target and rate limits | audit_critic if escalation involves quality issues |
| Automation/test execution | shell_exec | Validate execution gate and safety | container feed commands for manual review |
| UI verification or screenshots | browser_container.run_playwright_script | Ensure service endpoint ready and ports forwarded | slack_webhook to distribute captured artefacts |

### Context Dimension Cross-Reference
| Dimension | Description | Influencing Tools | Notes |
|-----------|-------------|-------------------|-------|
| Temporal | Timing of workflow phases (pre-task, in-flight, post-task). | context_extractor, workflow_synthesizer, audit_critic | Temporal markers drive reminder cadence and audit checkpoints. |
| Role-Based | Agent roles (analyzer, executor, coordinator). | workflow_synthesizer, audit_critic, prompt_librarian | Determines delegation order and documentation depth. |
| Communication | Interaction channels for human stakeholders. | slack_webhook | Controls notification routing and transparency compliance. |
| Execution | Direct system manipulation or test running. | shell_exec, container shell interface | Requires safety gates and logging. |
| Validation | Quality assurance and compliance. | audit_critic | Tied to milestone approvals and pre-commit checks. |
| Knowledge Base | Reference materials and templates. | prompt_librarian, context_extractor | Ensures alignment with latest protocols. |
| Delivery | Final artifact publishing. | container.make_pr | Governed by clean-state and validation policies. |

---

## Phase 2 – Persistent Tool Awareness System
- **Pre-Task Reminders**: Agents must broadcast the active tool roster and decision matrix summary at workflow initiation. This is enforced through the `tool_awareness` workflow (see `/registry/workflows/tool_awareness.yaml`).
- **Context-Sensitive Suggestions**: The registry maintains trigger mappings from context dimensions to tool suggestions. Agents query `/registry/contexts/tool_awareness.yaml` prior to execution to receive tailored recommendations.
- **Capability Announcements**: When workflows start, the `workflow_synthesizer` publishes the current capabilities list to the meta-log, ensuring every agent sees available options.
- **Blueprint Integration**: Pages blueprint references this registry as the authoritative source, and agent blueprints must include a "Tool Awareness" step before any execution directives.

---

## Phase 3 – Tool Engagement Tracking & Analytics
- **Engagement Logging**: Every tool invocation must log an entry containing agent ID, tool name, atomic purpose justification, and outcome summary into the tool engagement ledger defined in `/registry/contexts/tool_engagement_tracking.yaml`.
- **Rationale Capture**: Agents append rationale codes that map to the decision matrix, enabling audit-ready traceability.
- **Utilization Metrics**: Aggregated metrics (frequency, success rate, average audit score) are computed via the analytics schema stored in `/registry/workflows/tool_analytics.yaml`.
- **Heat Map Visualization**: Heat map coordinates are derived from context dimension indices, enabling multi-dimensional insight into tool adoption.

---

## Phase 4 – Tool Optimization & Underutilization Detection
- **Unnecessary Tool Flags**: The optimization engine reviews engagement logs against goal outcomes; mismatches trigger alerts recorded in `/registry/contexts/tool_optimization.yaml`.
- **Underutilized Tool Discovery**: Tools with low frequency but high success correlations are highlighted for awareness campaigns.
- **Workflow Recommendations**: Suggested modifications are generated and routed back to workflow owners via `workflow_synthesizer` tasks.
- **Pruning Suggestions**: Automated pruning proposals identify tools whose atomic purpose overlaps or yields low value, prompting review by `audit_critic`.

---

## Phase 5 – Live Audit Cycle Integration
- **Real-Time Validation**: During active workflows, the audit critic monitors tool usage events to ensure they align with declared atomic purposes; deviations raise immediate flags.
- **Effectiveness Scoring**: Each tool carries a rolling effectiveness score updated after every invocation, combining success metrics, audit feedback, and stakeholder satisfaction signals.
- **Context Correlation Analysis**: Analytics correlate tool performance with context dimensions (temporal, role-based, communication) to inform optimization actions.
- **Self-Healing Protocols**: The registry defines maintenance routines that automatically refresh reminders, recalibrate scores, and notify agents when awareness drifts.

---

## Operational Protocols Summary
1. Query `/registry/contexts/tool_awareness.yaml` before initiating work.
2. Announce tool availability and decision triggers in the meta-log.
3. Log every tool interaction in the engagement ledger with rationale codes.
4. Review analytics reports weekly to update workflows and mitigate underutilization.
5. Execute live audit hooks during workflows to enforce atomic purpose adherence.
6. Apply optimization recommendations and pruning suggestions during retrospectives.

This registry is a living document; updates must be versioned alongside registry schemas and reflected in the Pages blueprint to maintain orchestration alignment.
