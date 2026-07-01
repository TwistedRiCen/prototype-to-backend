# prototype-to-backend

[English](README.md) | [简体中文](README.zh-CN.md)

`prototype-to-backend` is an AI Skill for converting product prototypes and requirement materials into backend development artifacts.

It is designed for backend engineers using Codex. The skill focuses on business meaning, domain modeling, database design, REST API design, workflows, state machines, permissions, development planning, open questions, and design review. It does not generate frontend code by default.

## What This Skill Does

- Analyzes Axure HTML prototype packages, online prototype URLs, PRDs, and screenshots.
- Extracts user roles, module trees, menu trees, page inventories, form fields, search conditions, table columns, buttons, and backend operations.
- Produces backend-ready artifacts for system overview, domain model, database schema, API design, state machine, workflow, permissions, delivery plan, and product confirmation questions.
- Uses Chinese-first bilingual templates for Chinese teams, while preserving English technical names for implementation.
- Preserves Chinese business terms and provides English technical names for entities, APIs, permissions, statuses, and tables.
- Separates confirmed facts, assumptions, and unresolved questions.
- Includes a built-in grill-me style review phase. It first generates backend artifacts, then challenges them to find missing APIs, weak data models, incomplete workflows, permission gaps, and ambiguous business rules.

## Supported Inputs

- Axure HTML prototype packages.
- Online prototype links.
- Product requirement documents.
- Business process documents.
- Screenshots as a fallback when richer artifacts are unavailable.

## Generated Outputs

Templates use Chinese-first bilingual headings and table columns, such as `系统概览 / System Overview` and `字段 / Field`.

- `01-system-overview.md`
- `02-domain-model.md`
- `03-database-design.md`
- `04-api-design.md`
- `05-state-machine.md`
- `06-workflow.md`
- `07-permission-model.md`
- `08-development-plan.md`
- `09-open-questions.md`
- `10-design-review.md`

## Installation

```bash
npx skills@latest add https://github.com/<owner>/prototype-to-backend --skill prototype-to-backend -g -a codex -y
```

Replace `<owner>` with the GitHub account or organization that hosts this repository. The `-a codex` option installs the skill only for Codex, avoiding unrelated agent targets.

## Updating

When this repository publishes a new version, users who installed it with the Skills CLI can update their local copy with:

```bash
npx skills@latest update -g prototype-to-backend
```

Useful related commands:

```bash
# Check installed skills
npx skills@latest list

# Check for available updates
npx skills@latest check

# Update this skill for Codex only if update fails because unrelated agents were selected earlier
npx skills@latest add https://github.com/<owner>/prototype-to-backend --skill prototype-to-backend -g -a codex -y

# Update all global skills
npx skills@latest update -g
```

Codex usually detects skill changes automatically. If the updated skill does not appear, restart Codex.

## Uninstalling

To remove the Codex global installation:

```bash
npx skills@latest remove prototype-to-backend -g -a codex -y
```

If you previously installed this skill for multiple agents, remove only the Codex copy with the command above, or replace `codex` with the agent name you want to remove.

## Usage Examples

```text
Use prototype-to-backend to analyze the Axure HTML package in ./prototype and generate backend development artifacts. Focus on domain model, SQL Server friendly database design, REST APIs, approval workflow, permissions, development plan, and open questions. Do not generate frontend code.
```

```text
Analyze this Chinese OA approval PRD from a backend perspective. Preserve Chinese business terms, add English technical names, and separate confirmed facts from assumptions and open questions.
```

```text
The prototype URL is https://example.com/prototype. Inspect the sitemap, pages, forms, tables, buttons, interactions, and notes, then produce backend design documents for Spring Boot REST implementation.
```

## Recommended Workflow

1. Provide the richest available source material, preferably an Axure HTML package or prototype URL.
2. Ask the agent to inventory pages, menus, forms, lists, buttons, statuses, and interactions first.
3. Generate the first nine backend artifacts.
4. Run the built-in grill-me style review phase and generate `10-design-review.md`.
5. Review `09-open-questions.md` and `10-design-review.md` with product owners, business stakeholders, and backend engineers.
6. Update the artifacts after answers and design fixes are confirmed.
7. Use `08-development-plan.md` to split backend implementation tasks.

## Repository Structure

```text
prototype-to-backend/
|-- README.md
|-- README.zh-CN.md
|-- LICENSE
`-- skills/
    `-- prototype-to-backend/
        |-- SKILL.md
        |-- agents/
        |   `-- openai.yaml
        |-- templates/
        |   |-- 01-system-overview-template.md
        |   |-- 02-domain-model-template.md
        |   |-- 03-database-design-template.md
        |   |-- 04-api-design-template.md
        |   |-- 05-state-machine-template.md
        |   |-- 06-workflow-template.md
        |   |-- 07-permission-model-template.md
        |   |-- 08-development-plan-template.md
        |   |-- 09-open-questions-template.md
        |   `-- 10-design-review-template.md
        `-- examples/
            |-- axure-html-package-example.md
            |-- oa-approval-example.md
            |-- procurement-system-example.md
            `-- design-review-example.md
```

## Limitations

- The skill cannot infer hidden business rules that are not present in the prototype or requirement materials.
- Ambiguous rules must be documented as assumptions or open questions.
- Screenshot-only analysis is less reliable than HTML prototype or PRD analysis.
- Generated database and API designs are implementation-ready drafts, not final business approval.
- The design review phase finds risks from the available artifacts; unresolved product or business rules still require stakeholder confirmation.

## License

MIT License. See [LICENSE](LICENSE).
