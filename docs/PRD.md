# PRD: Baizhi Agent Toolkit native research plugin

**Author:** ct-jaryn
**Date:** 2026-10-10
**Status:** Draft

## Problem

The user requesting this contribution wants Baizhi to be discoverable and configurable
inside agent products. This optional community plugin bundles a Baizhi HTTP MCP
connection, a sensitive account-key setting and one explicit research skill. Copying
the skill directory alone cannot register the MCP connection. The bounded current
catalog review found no Baizhi metadata match; this is not proof of marketplace
acceptance, service availability or wider user demand.

## Target users

| User | Context | Primary need |
| --- | --- | --- |
| Developer with a Baizhi account | Comparing public technical sources | Configure the connection once and invoke research explicitly |
| Researcher with an approved budget | Exploring a public topic | Track calls and evidence gaps in a report |
| Existing account holder | Inspecting connected capabilities | See advertised schemas before authorizing research |

## Success criteria

1. The current marketplace validator discovers exactly one skill with the eight required fields and seven sections, no blocking errors and a score meeting the listing bar.
2. An isolated actual Claude Code host installs the frozen complete plugin, registers its skill and dispatches an advertised loopback MCP tool with a synthetic sensitive value and no extra CLI permission grant for the skill case.
3. Missing configuration, denied permission, wrong authorization, key rotation and disabled-plugin cases have explicit observed outcomes.
4. Candidate/runtime hashes show an endpoint-only substitution; real Baizhi/model requests remain zero in these validation receipts.

These are validation criteria until dated execution receipts exist. Deterministic
model replies test host plumbing, not model reasoning, paid-service behavior or
adherence to every workflow instruction.

## Functional requirements

- **FR-1:** Register the intended hosted HTTP MCP URL and bind the user's sensitive account key through native plugin configuration.
- **FR-2:** Load one explicitly invoked skill and its local reference; grant only this plugin's configured MCP server during that turn, subject to the user's overriding permission rules.
- **FR-3:** Guide discovery of current schemas, reuse explicit budgets, minimize disclosed inputs and report supported findings and unresolved work.
- **FR-4:** Keep missing configuration, permission and authentication failures visible; do not report successful research after a failure.
- **FR-5:** Keep personal authorship and MIT plugin licensing accurate; use the required Plugin Submission issue and current source-vetting process without self-setting verified status or borrowing a publisher identity.

## Out of scope

- Hosted backend implementation or backend open-source licensing; the MIT license covers this plugin's files only.
- Automatic or free research, hard spending/quota enforcement, OAuth, guaranteed remote cancellation, or production availability and quality verification.
- Other clients, portable-copy complete setup, editorial featuring or installation through an unapproved marketplace.
- Private-data disclosure without explicit approval. Installation does not authorize paid tool calls; credentials must not enter prompts, logs or reports.
