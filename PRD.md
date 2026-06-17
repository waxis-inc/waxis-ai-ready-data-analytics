# PRD: Waxis AI-ready Data & Analytics

Document status: Draft v1.0  
Owner: Waxis Inc  
Research snapshot: 2026-06-16 EDT  
Repository: `waxis-ai-ready-data-analytics`

## 1. Problem Statement

Business teams want to ask questions about sales, support, inventory, finance, operations, and customer data in plain language. But most companies do not have AI-ready data. Their metrics are inconsistent, data is scattered across systems, dashboards disagree, and natural-language SQL tools hallucinate when there is no governed semantic layer.

The real problem is not just "chat with data." It is missing data trust:

- Data lives across CRM, ERP, helpdesk, spreadsheets, warehouse systems, and finance tools.
- Business metrics such as revenue, churn, stockout, SLA, and margin are defined differently by team.
- Analysts spend time exporting, cleaning, joining, and explaining data repeatedly.
- Leaders receive reports late and cannot drill into causes quickly.
- Natural-language querying can generate misleading SQL without semantic context, permissions, and verified examples.
- Anomalies are discovered manually after business impact has already occurred.

## 2. Solution Summary

Waxis AI-ready Data & Analytics is a governed analytics platform that turns fragmented operational data into trusted metrics, natural-language querying, recurring reports, anomaly alerts, and decision workflows.

The solution combines:

- Data ingestion and freshness monitoring
- Transformation and data quality checks
- Semantic metric layer
- Natural-language analytics agent
- Verified SQL and query review workflow
- Recurring KPI reports
- Anomaly detection and alerting
- Dashboard and insight workspaces
- Governance, permissions, lineage, and audit

## 3. Research-Backed Product Principles

1. Natural-language analytics must be grounded in a semantic layer, not raw tables alone.
2. Metrics should be defined once and reused everywhere.
3. AI analytics should return SQL, result tables, charts, assumptions, and confidence signals.
4. Analysts should curate domain-specific spaces with datasets, example SQL, business semantics, and instructions.
5. Data must be prepared for Copilot-style consumption; otherwise AI outputs can be inaccurate or misleading.
6. Governance, RBAC, lineage, and access controls are part of the analytics product, not backend details.
7. Recurring reports and anomaly alerts should turn insights into operating rhythm.

## 4. Market And Technology Signals

- Snowflake Cortex Analyst uses Semantic Views to define business concepts, metrics, relationships, and verified examples for accurate SQL generation under Snowflake RBAC.
- Databricks Genie Spaces are domain-specific natural-language chat interfaces curated with Unity Catalog datasets, example SQL, business semantics, and organization terminology.
- Microsoft Power BI Copilot documentation warns that semantic models and users must be prepared, or Copilot outputs may be low quality, inaccurate, or misleading.
- dbt Semantic Layer emphasizes defining governed metrics once and using them across dashboards, apps, agents, and AI workflows.
- NIST and OWASP AI guidance makes privacy, insecure output handling, hallucination, and governance necessary for AI analytics agents.

## 5. Target Customers

### Primary

- B2B companies with fragmented operational data and recurring reporting needs.
- Operations, finance, sales, customer service, supply chain, and executive teams that need trusted metrics and faster decisions.
- Companies that want AI analytics but lack a mature semantic layer.

### Secondary

- SaaS teams embedding analytics into customer-facing products.
- Organizations with a small analyst team supporting many business stakeholders.
- Companies standardizing KPI reporting across departments.

## 6. Personas

### Business Leader

Needs reliable KPI answers, weekly reports, anomaly alerts, and drill-down explanations.

### Business Analyst

Needs governed datasets, metric definitions, query review, data quality checks, and reusable reports.

### Operations Manager

Needs daily performance visibility and alerts tied to action.

### Data Engineer

Needs ingestion, transformations, lineage, freshness, and quality monitoring.

### Finance Or RevOps Owner

Needs consistent definitions for revenue, pipeline, margin, churn, SLA, and cost metrics.

### Executive

Needs concise narrative reporting with source-backed metrics and decision recommendations.

## 7. Goals

1. Ingest data from common business systems into an analytics-ready model.
2. Create a governed semantic metric layer for core business concepts.
3. Enable natural-language querying that generates verified SQL and explainable results.
4. Automate recurring KPI reports with narrative summaries and charts.
5. Detect anomalies and trigger alerts with likely drivers.
6. Provide data quality, lineage, freshness, and permission controls.
7. Reduce repeated manual analysis and increase trust in metrics.

## 8. Non-Goals

- The product will not replace a full enterprise data warehouse in MVP.
- The product will not guarantee correct answers without curated semantic models.
- The product will not allow unrestricted text-to-SQL over raw production databases.
- The product will not replace analyst review for high-stakes financial reporting in MVP.
- The product will not support every BI visualization type on day one.

## 9. Product Scope

### MVP

- Connectors for CSV/upload, CRM, helpdesk, inventory/order systems, and SQL databases.
- Data freshness and sync health monitoring.
- Core canonical models for customers, accounts, orders, tickets, SKUs, inventory, opportunities, and transactions.
- Semantic metrics catalog with definitions, owners, dimensions, filters, joins, and examples.
- Natural-language analytics workspace for approved datasets.
- SQL generation with query preview, explanation, and analyst review flag.
- Standard dashboards and recurring KPI report builder.
- Anomaly detection for configured metrics.
- Role-based access and audit logs.

### V1

- Domain-specific analytics agents for sales, support, supply chain, finance, and executive reporting.
- Verified query library and few-shot examples per domain.
- Metric lineage and impact analysis.
- Automated driver analysis for metric changes.
- Slack/email report delivery.
- Report commentary generation with source links and caveats.
- Analyst workflow for approving semantic layer changes.

### Future

- Embedded analytics API for client products.
- Advanced forecasting and causal diagnostics.
- Multi-agent analytical workflows.
- Write-back tasks and action recommendations.
- dbt project integration and metric-as-code sync.
- Cross-client benchmark templates where legally and contractually allowed.

## 10. Core User Stories

1. As a business leader, I want to ask questions in plain language, so that I can get answers without waiting for a custom report.
2. As an analyst, I want metrics defined once, so that every dashboard and AI answer uses the same business logic.
3. As a data engineer, I want freshness and quality checks, so that stakeholders know when data is safe to use.
4. As an operations manager, I want anomaly alerts, so that I can act before issues compound.
5. As a finance owner, I want approved metric definitions, so that reports do not conflict across teams.
6. As an executive, I want a weekly narrative report with charts and caveats, so that I can make decisions quickly.
7. As an analyst, I want to review generated SQL, so that AI does not run unsafe or misleading queries.
8. As a business user, I want to see how an answer was calculated, so that I can trust the result.
9. As an admin, I want to control which datasets each user can query, so that sensitive data stays protected.
10. As a manager, I want drivers behind metric changes, so that I know what to investigate.
11. As a data owner, I want lineage from metric to source fields, so that changes can be managed.
12. As a business user, I want saved questions and dashboards, so that repeated analysis becomes self-service.
13. As an analyst, I want to add example questions and verified SQL, so that the AI agent improves for our terminology.
14. As a compliance reviewer, I want audit logs for questions and generated queries, so that analytical access is reviewable.
15. As a stakeholder, I want answers to include caveats when data is incomplete, so that I do not over-trust partial data.

## 11. Functional Requirements

### 11.1 Data Ingestion

- FR-001: Support CSV and spreadsheet upload.
- FR-002: Support SQL database connectors.
- FR-003: Support business application connectors for CRM, helpdesk, inventory/order, and finance systems where available.
- FR-004: Track source freshness, sync status, schema changes, row count, and failed records.
- FR-005: Support incremental loads where source systems allow.
- FR-006: Store source metadata for lineage and audit.

### 11.2 Data Modeling And Quality

- FR-010: Provide canonical entities for accounts, contacts, opportunities, tickets, orders, invoices, SKUs, inventory, suppliers, and transactions.
- FR-011: Support transformations, joins, normalization, deduplication, and type validation.
- FR-012: Support quality tests for nulls, uniqueness, referential integrity, accepted values, range checks, and freshness.
- FR-013: Flag data quality issues to admins and downstream report users.
- FR-014: Support certified, draft, deprecated, and blocked dataset states.

### 11.3 Semantic Metric Layer

- FR-020: Define metrics with name, description, owner, formula, grain, dimensions, filters, valid time windows, and caveats.
- FR-021: Define business entities, relationships, dimensions, facts, and join paths.
- FR-022: Support synonyms and business terminology.
- FR-023: Support verified questions and SQL examples.
- FR-024: Support metric versioning, approval workflow, and change history.
- FR-025: Enforce role-based access at dataset, column, metric, and row-scope levels where supported.

### 11.4 Natural-Language Analytics

- FR-030: Allow users to ask questions in natural language within a scoped domain workspace.
- FR-031: Generate SQL using semantic layer definitions and verified examples.
- FR-032: Show generated SQL, assumptions, filters, result table, and visualization.
- FR-033: Ask clarifying questions when terms, time windows, or metrics are ambiguous.
- FR-034: Refuse or escalate questions outside user permissions or semantic coverage.
- FR-035: Capture feedback: correct, incorrect, ambiguous, missing metric, wrong filter, wrong visualization.
- FR-036: Support analyst review mode before query execution for sensitive workspaces.

### 11.5 Dashboards And Reports

- FR-040: Provide configurable dashboards with metric cards, trends, breakdowns, tables, and annotations.
- FR-041: Support recurring reports with scheduled delivery.
- FR-042: Generate narrative summaries with metric values, changes, likely drivers, caveats, and recommended next questions.
- FR-043: Support drill-down from report metric to source query and semantic definition.
- FR-044: Support export to PDF, Markdown, CSV, and shareable links where permissions allow.

### 11.6 Anomaly And Driver Analysis

- FR-050: Monitor configured metrics for unusual changes based on history, thresholds, and seasonality where available.
- FR-051: Alert owners by email, Slack/webhook, or dashboard.
- FR-052: Provide likely drivers using dimension breakdowns, cohort comparisons, and related metrics.
- FR-053: Link anomalies to relevant operational workflows, such as support backlog, inventory risk, or pipeline quality.

### 11.7 Governance And Audit

- FR-060: Log natural-language question, generated SQL, user, datasets accessed, result metadata, and timestamp.
- FR-061: Support retention policies and redaction of sensitive query/result logs.
- FR-062: Provide permission checks before query execution.
- FR-063: Support dataset certification and semantic metric approval.
- FR-064: Provide audit export for admins.

## 12. Non-Functional Requirements

- NFR-001: Common dashboard queries should load within 5 seconds on approved datasets under normal conditions.
- NFR-002: Natural-language query responses should show progress and return a first useful result within 10 seconds for standard queries.
- NFR-003: Generated SQL must be previewable and auditable.
- NFR-004: Data freshness must be visible in all dashboards and reports.
- NFR-005: Semantic metric definitions must be versioned and reversible.
- NFR-006: The system must avoid executing destructive SQL.
- NFR-007: Row and column access rules must be enforced before results are shown.
- NFR-008: Report narratives must include caveats when data is stale, incomplete, or filtered.

## 13. Data Model Concepts

- Source System
- Ingestion Job
- Dataset
- Canonical Entity
- Transformation
- Data Quality Test
- Semantic Model
- Metric
- Dimension
- Fact
- Relationship
- Verified Query
- Analytics Workspace
- Natural-Language Question
- Generated SQL
- Report
- Anomaly
- Alert
- Audit Event

## 14. Key Workflows

### Semantic Model Setup

1. Analyst selects certified datasets.
2. Analyst defines entities, relationships, metrics, dimensions, and synonyms.
3. Analyst adds verified questions and SQL examples.
4. Reviewer approves semantic model for a workspace.
5. Business users can query within that workspace.

### Natural-Language Question

1. User asks a question in a domain workspace.
2. System resolves metric, dimensions, filters, and time range.
3. System asks clarification or generates SQL.
4. SQL is executed if policy allows.
5. User receives result table, chart, explanation, and caveats.
6. Feedback is captured.

### Weekly KPI Report

1. Owner selects metrics, segments, and schedule.
2. System runs approved queries.
3. System detects changes and drivers.
4. Narrative report is generated with charts and caveats.
5. Owner reviews or auto-sends based on policy.

### Anomaly Alert

1. Metric deviates from threshold or expected pattern.
2. System identifies likely drivers.
3. Alert is sent to owner with drill-down link.
4. Owner acknowledges, assigns, or creates follow-up task.

## 15. Analytics And KPIs

### Adoption

- Active analytics users
- Natural-language questions per week
- Dashboards viewed
- Reports scheduled
- Repeat question rate

### Trust And Quality

- Answer acceptance rate
- SQL review approval rate
- Incorrect answer reports
- Clarification rate
- Semantic coverage rate
- Metric definition conflict count

### Data Operations

- Data freshness SLA
- Ingestion failure rate
- Data quality test pass rate
- Certified dataset count
- Lineage completeness

### Business Impact

- Analyst hours saved
- Report cycle time reduction
- Anomalies detected before stakeholder report
- Decision follow-up completion
- Reduction in conflicting KPI definitions

## 16. Security And Governance Requirements

- Enforce user permissions before SQL generation and execution.
- Do not run generated SQL against raw unrestricted databases without approved workspace scope.
- Block destructive SQL and unsupported commands.
- Log questions, generated SQL, datasets accessed, and report delivery.
- Support row-level and column-level restrictions where data backends support them.
- Mark stale, incomplete, or partial data in outputs.
- Require approval for semantic metric changes in certified workspaces.
- Use NIST and OWASP AI risk controls for privacy, hallucination, insecure output handling, and excessive agency.

## 17. UX Requirements

### Business Analytics Workspace

- Natural-language input
- Suggested questions
- Clarifying question flow
- Result table
- Chart recommendation
- SQL and calculation explanation
- Metric definition card
- Feedback controls

### Analyst Console

- Dataset catalog
- Semantic model builder
- Metric definition editor
- Verified query library
- Data quality dashboard
- Query review queue
- Evaluation panel

### Executive Report View

- KPI summary
- Trend charts
- Driver analysis
- Caveats
- Source definitions
- Action recommendations

### Admin Console

- Connector setup
- Permissions
- Retention
- Audit export
- Workspace configuration
- Alert routing

## 18. Implementation Decisions

- Use a governed semantic layer as the core product foundation.
- Scope natural-language analytics to curated workspaces rather than the entire warehouse.
- Return SQL and assumptions with AI answers by default.
- Treat verified SQL examples as product assets.
- Separate data ingestion, semantic modeling, query generation, reporting, and alerting modules.
- Use analyst review mode for high-stakes or early-stage workspaces.
- Include data freshness and caveats in every answer and report.

## 19. Testing Decisions

- Test metric calculations against known fixtures.
- Test natural-language questions against verified SQL examples.
- Test ambiguous query handling and clarification flows.
- Test permission boundaries at dataset, metric, row, and column levels.
- Test stale data warnings.
- Test anomaly detection on historical datasets.
- Test report generation for source-backed values and caveats.
- Test generated SQL safety filters.

## 20. Rollout Plan

### Phase 0: Data Readiness

- Identify top business domains and source systems.
- Define first 20-50 metrics.
- Build canonical datasets.
- Establish data owners and approval process.

### Phase 1: Governed Dashboards And Reports

- Launch certified datasets, metric catalog, dashboards, and recurring reports.
- Keep natural-language querying in analyst-reviewed mode.

### Phase 2: Natural-Language Analytics

- Enable business users in scoped workspaces.
- Add verified query examples and feedback loops.
- Monitor incorrect answer reports and semantic gaps.

### Phase 3: Anomaly And Decision Workflows

- Add anomaly alerts and driver analysis.
- Connect alerts to operations workflows.
- Add executive narratives and action tracking.

## 21. Risks And Mitigations

| Risk | Mitigation |
| --- | --- |
| AI generates misleading SQL | Semantic layer, verified queries, scoped workspaces, SQL preview, and review mode |
| Metrics conflict across teams | Metric owners, approval workflow, versioning, and certification |
| Data is stale or incomplete | Freshness checks, caveats, and visible source timestamps |
| Users over-trust natural-language answers | Show assumptions, SQL, definitions, caveats, and feedback controls |
| Permissions leak sensitive data | Pre-query access checks, row/column restrictions, and audit logs |
| Analysts are bypassed | Give analysts semantic tooling, review queues, and feedback-driven improvement workflows |

## 22. Open Questions

1. Which domains should ship first: sales, support, supply chain, finance, or executive reporting?
2. Which data warehouse and BI tools are most common among Waxis clients?
3. Should metric definitions be stored in Waxis first or synced with dbt/warehouse-native semantic models?
4. What level of SQL visibility should non-technical users see by default?
5. Which anomaly methods are sufficient for MVP?
6. Should report narratives require human approval before delivery?

## 23. Acceptance Criteria

- An analyst can define a metric with formula, dimensions, owner, synonyms, and verified examples.
- A business user can ask an approved natural-language question and receive SQL, table, chart, explanation, and caveats.
- The system asks clarifying questions for ambiguous metrics or time periods.
- Permission checks prevent unauthorized dataset or column access.
- A recurring report can be scheduled with KPI narrative and charts.
- An anomaly alert can identify a metric change and likely driver dimensions.
- Data freshness and quality status are visible in reports and answers.

## 24. Research References

- Snowflake Cortex Analyst and Semantic Views: https://docs.snowflake.com/en/user-guide/snowflake-cortex/cortex-analyst
- Databricks Genie Spaces documentation: https://docs.databricks.com/aws/en/genie/
- Microsoft Power BI Copilot with semantic models: https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-semantic-models
- dbt Semantic Layer: https://www.getdbt.com/product/semantic-layer
- NIST AI Risk Management Framework: https://www.nist.gov/itl/ai-risk-management-framework
- OWASP Top 10 for LLMs and Gen AI Apps 2025: https://genai.owasp.org/llm-top-10/
- Model Context Protocol introduction: https://modelcontextprotocol.io/docs/getting-started/intro

