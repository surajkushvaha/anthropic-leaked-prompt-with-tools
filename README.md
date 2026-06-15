# anthropic-leaked-prompt-with-tools
https://github.com/elder-plinius/CL4R1T4S/blob/main/ANTHROPIC/CLAUDE-FABLE-5.md
An unofficial research archive of prompt material, tool instructions, and skill packages attributed to Anthropic Claude.

This repository is intended for people who want to study how Claude-style skills are organized: how trigger descriptions are written, how workflows are documented, how supporting scripts are bundled, and how packaged `.skill` files map to readable source folders.

## Important Notice

This project is not affiliated with, endorsed by, or maintained by Anthropic. The material in this repository may be incomplete, outdated, proprietary, or incorrectly attributed. Treat it as reference material only.

Do not use this repository to impersonate Anthropic, misrepresent official Claude behavior, bypass safety systems, or redistribute content in a way that violates licenses, terms, or applicable law. If you own rights to material in this repository and want it removed, open an issue or submit a request through the appropriate channel for the repository host.

## Contents

```text
.
+-- agents.md
+-- raw_leaked_prompt_fable5.md
`-- skills/
    +-- public/
    |   +-- *.skill
    |   `-- <skill-name>/
    |       +-- SKILL.md
    |       +-- LICENSE.txt
    |       `-- scripts/, references/, templates/, assets/
    `-- examples/
        +-- *.skill
        `-- <skill-name>/
            +-- SKILL.md
            +-- LICENSE.txt
            `-- scripts/, references/, templates/, assets/
```

## What This Repository Contains

The root Markdown files contain prompt and instruction snapshots.

The `skills/public` directory contains general-purpose Claude skills for common document, data, presentation, PDF, file-reading, frontend, and product-knowledge workflows.

The `skills/examples` directory contains example and domain-specific Claude skills, including creative artifact generation, MCP server building, tutoring, internal communications, personal task automation, forms, expenses, and financial calculation workflows.

Most skills are present in two forms:

- `<skill-name>.skill`: packaged skill archive.
- `<skill-name>/`: unpacked source folder with the readable `SKILL.md` file and supporting resources.

Use the unpacked folders when reading or editing. Use the `.skill` files only when you need the packaged artifact.

## Skill Format

A skill is centered on a `SKILL.md` file. It usually starts with YAML frontmatter:

```yaml
---
name: skill-name
description: When this skill should be used and what it helps the assistant do.
license: Complete terms in LICENSE.txt
---
```

The body of `SKILL.md` contains the actual instructions: workflow steps, rules, examples, scripts to run, constraints, and references. Larger skills may include extra folders such as `scripts/`, `reference/`, `templates/`, `assets/`, or `examples/`.

The `description` field is especially important because it explains when the skill should trigger.

## Included Public Skills

| Skill | Summary |
| --- | --- |
| `docx` | Work with Microsoft Word `.docx` files. |
| `file-reading` | Choose the right strategy for reading uploaded files. |
| `frontend-design` | Apply visual design guidance to frontend work. |
| `pdf` | Create, edit, inspect, fill, split, merge, and process PDFs. |
| `pdf-reading` | Read and extract information from PDFs. |
| `pptx` | Create, inspect, edit, and validate PowerPoint decks. |
| `product-self-knowledge` | Check Anthropic product information before answering. |
| `xlsx` | Work with spreadsheets such as `.xlsx`, `.xlsm`, `.csv`, and `.tsv`. |

## Included Example Skills

| Area | Skills |
| --- | --- |
| Creative generation | `algorithmic-art`, `canvas-design`, `slack-gif-creator`, `theme-factory`, `web-artifacts-builder` |
| Skill and tool development | `skill-creator`, `mcp-builder` |
| Writing and learning | `doc-coauthoring`, `internal-comms`, `learn` |
| Personal workflows | `call-to-book`, `cancel-unsubscribe`, `event-planning`, `grocery-shopping`, `hire-help`, `meal-delivery`, `prescription-refill`, `return-refund` |
| Forms, expenses, and finance | `benepass-reimbursement`, `file-expenses`, `file-form`, `financial-calculator` |
| Brand guidance | `brand-guidelines` |

## Useful Commands

List all unpacked public skills:

```powershell
Get-ChildItem skills\public -Directory
```

List all unpacked example skills:

```powershell
Get-ChildItem skills\examples -Directory
```

List packaged skill archives:

```powershell
Get-ChildItem skills -Recurse -Filter *.skill
```

Open a skill instruction file:

```powershell
Get-Content skills\examples\algorithmic-art\SKILL.md
```

Search skill names and trigger descriptions:

```powershell
rg "^(name|description):" skills -g SKILL.md
```

## Editing Notes

When editing a skill, update `SKILL.md` first. Keep the `name` stable unless you are intentionally renaming the skill, and keep the `description` accurate because it controls discoverability and triggering.

Keep long examples, helper scripts, templates, and reference documents in separate folders instead of overloading the main `SKILL.md`. This makes the skill easier to review and maintain.

If you change assets, templates, scripts, or packaged archives, check the local `LICENSE.txt` file for that skill. Licenses may differ between folders.

## Validation

There is no single build or test command for this repository. Validation is skill-specific.

For document, spreadsheet, PDF, and presentation skills, follow the validation instructions inside the relevant `SKILL.md`. For example, some skills include scripts for unpacking, validating, rendering, or recalculating generated files.

## Disclaimer

This repository is provided for archival, educational, and research purposes. It should not be treated as official Anthropic documentation or as a reliable description of current Claude behavior.
