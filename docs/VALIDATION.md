# Validation record — 2026-10-10

This record describes synthetic local verification of the community plugin.
It is not a production test or a maintainer review.

## Content and manifest validation

- Tons of Skills main: `cfae287053f6d06aa2c58b548f263476d520238a`.
- Current `validate-skills-schema.py`: SHA-256 `2b0cb1d864108d593b6207c04fbc60ee856f8c54cb2e916542b5db837ab2e4d4`, validator v7.0 / schema 4.1.0.
- Python 3.12.14, PyYAML 6.0.1; selected kernel `@intentsolutions/core` 0.10.0 and Zod 4.4.3 match the upstream pnpm lock integrities. This is not a full workspace dependency installation.
- `python3 scripts/validate-skills-schema.py --marketplace --verbose <plugin-dir>`: one skill, no agents, 99/100, exit 0.
- Single-skill JSON/kernel shadow: no errors or warnings; required eight fields and plugin-manifest surface agree. The known optional `disallowed-tools` kernel property difference remains advisory.
- Claude Code 2.1.295 validates both plugin.json and marketplace.json. Its README installation advice was addressed after the first manifest check.

The first candidate failed content validation because this marketplace rejects
wildcards in an `allowed-tools` entry. The corrected server-level selector is
accepted by the marketplace and actually grants the installed MCP tools when
the skill is invoked. No validator rule was changed or bypassed.

## Native host observations

The complete candidate was copied to an isolated runtime with only
`mcpServers.baizhi.url` changed to an owned loopback endpoint. Sensitive test
values and model replies were synthetic. Fresh private config directories were
used; no user account key or model credential was loaded.

| Case | Observed result |
| --- | --- |
| Explicit skill, source comparison | Skill text loaded and one MCP tool call; no extra CLI allow grant |
| Explicit skill, bounded-topic example | Skill text loaded and one MCP tool call; no extra CLI allow grant |
| Inspect-tools example | Advertised fixture schema available, zero tool calls |
| Request without invoking the skill | Tool request denied, zero MCP calls |
| Explicit user deny with the skill | Denied tool removed, zero MCP calls |
| Synthetic key rotation | Correct replacement header reached the fixture and one call completed |
| Incorrect authorization | Server marked failed, zero tool calls |
| First install without the required key | Install warning, no MCP server or tools registered |
| Configured after a cold install | Server connected and one tool call completed |
| Empty sensitive CLI input after configuration | Input ignored (`saved: []`), previous value retained |
| Recheck of empty-value behavior | Previous synthetic header still accepted; zero research calls |
| Disabled plugin | No plugin MCP server/tools or registered skill |

All twelve CLI sessions exited normally; assertions also checked outcomes and
observed requests rather than treating exit 0 alone as success. Four owned
listener ports were closed and independently refused connections afterward.
The test installation was disabled or uninstalled.

## Limits

The deterministic fixture can prove loading, permission, binding and transport.
It does not evaluate actual model judgment, compliance with each budget/privacy
instruction, all real-service schemas, credits, asynchronous jobs or citations.
No real Baizhi or model calls were made. No GUI, other host versions, OS platforms,
server cancellation or termination of billing was verified. A local successful
check is not upstream CI approval, human vetting, listing or endorsement.
