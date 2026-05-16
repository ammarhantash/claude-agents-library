# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repository Is

A curated library of 34 specialized Claude agent configurations (markdown files) organized by professional role. Each file defines a Claude persona—not a tool—that gives Claude deep, consistent expertise in one domain. Users adopt agents by copying files to `.claude/agents/` in their projects or pasting content as context in Claude Chat.

## Repository Structure

Seven category directories, each containing agent `.md` files:

| Category | Count | Example agents |
|---|---|---|
| `engineering/` | 6 | `backend-architect.md`, `frontend-developer.md`, `devops-automator.md` |
| `marketing/` | 7 | `content-creator.md`, `seo-specialist.md`, `email-marketer.md` |
| `studio-operations/` | 5 | `analytics-reporter.md`, `budget-optimizer.md` |
| `testing/` | 5 | `api-tester.md`, `performance-tester.md` |
| `design/` | 5 | `ui-designer.md`, `brand-designer.md` |
| `product/` | 3 | `product-manager.md`, `growth-hacker.md` |
| `project-management/` | 3 | `project-shipper.md`, `technical-writer.md` |

There are no build systems, test runners, or executable code—this is a pure markdown library.

## Agent File Format

Every agent must follow this exact structure to be consistent with the library:

```markdown
---
name: [Full Agent Name]
category: [engineering|product|marketing|design|project-management|studio-operations|testing]
version: 1.0
---

# [Full Agent Name]

## 🎯 Purpose
[2–3 sentences in second person ("You are...") describing the persona and expertise level]

## 📋 Core Responsibilities
[3–5 grouped categories, each with 3–8 specific bullet tasks]

## 🛠️ Key Skills
[5–8 skill categories with specific tools/technologies listed]

## 💬 Communication Style
[4–6 bullet points defining tone, format preferences, and approach]

## 💡 Example Prompts
[4–6 realistic example prompts a user might give this agent]

## 🔗 Related Agents
[3–5 cross-references to other agents in this library with a one-line description of when to use each]
```

## Naming Conventions

- **File names**: `{descriptor}-{role}.md` (e.g., `backend-architect.md`, `content-creator.md`)
- **Agent names**: Title-cased full role title in frontmatter `name:` field
- **Categories**: Lowercase, match the directory name exactly in frontmatter `category:` field

## Contributing New Agents

1. Place the file in the appropriate category directory
2. Follow the template above exactly—all six sections are required
3. The `Related Agents` section must cross-reference real agents that exist in this library
4. Agent personas are written in second person ("You are a senior backend architect...")
5. `Example Prompts` should be realistic, task-specific, and demonstrate the agent's unique value vs. a general assistant

See `CONTRIBUTING.md` for the full submission checklist and PR process.

## Cross-Agent Workflows

Agents are designed to be composable. The `Related Agents` section in each file deliberately links agents that pair well for multi-step workflows (e.g., Backend Architect → Frontend Developer → DevOps Automator for a full-stack feature). When adding a new agent, consider which existing agents should reference it and update those files accordingly.

## README Maintenance

`README.md` contains the Quick Agent Finder tables (by role and by task) and the category overview. When adding or renaming agents, update the relevant table rows in README.md to keep it in sync.

## Self-Hosting for Contributors

`.claude/agents/` contains symlinks to the agents most useful when working on this repo itself:

| Agent | Symlink target | Use while contributing |
|---|---|---|
| `project-shipper.md` | `project-management/project-shipper.md` | Reviewing PRs, cutting releases |
| `trend-researcher.md` | `product/trend-researcher.md` | Deciding what new agents to add |
| `feedback-synthesizer.md` | `product/feedback-synthesizer.md` | Processing community issues/requests |
| `tool-evaluator.md` | `testing/tool-evaluator.md` | Quality-checking agent submissions |

When adding a new agent that is broadly useful for repo work, add a symlink here too. Keep symlinks relative (e.g. `../../category/agent.md`) so they survive clones.

## Extensibility

The `.claude/` directory is structured to accommodate future additions beyond subagents:

```
.claude/
├── agents/        # Subagents active when working on this repo
├── skills/        # Future: reusable skill definitions
└── fine-tuning/   # Future: training examples, preference data
```

Create these subdirectories as needed; no other changes to the repo structure are required.
